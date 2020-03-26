`libuvc` is a cross-platform library for USB video devices, built atop `libusb`.
It enables fine-grained control over USB video devices exporting the standard USB Video Class
(UVC) interface, enabling developers to write drivers for previously unsupported devices,
or just access UVC devices in a generic fashion.

## Getting and Building libuvc

Prerequisites: You will need `libusb` and [CMake](http://www.cmake.org/) installed.

To build, you can just run these shell commands:

    git clone https://github.com/libuvc/libuvc
    cd libuvc
    mkdir build
    cd build
    cmake ..
    make && sudo make install

and you're set! If you want to change the build configuration, you can edit `CMakeCache.txt`
in the build directory, or use a CMake GUI to make the desired changes.

There is also `BUILD_EXAMPLE` and `BUILD_TEST` options to enable the compilation of `example` and `uvc_test` programs. To use them, replace the `cmake ..` command above with `cmake .. -DBUILD_TEST=ON -DBUILD_EXAMPLE=ON`.
Then you can start them with `./example` and `./uvc_test` respectively. Note that you need OpenCV to build the later (for displaying image).

## Developing with libuvc

The documentation for `libuvc` can currently be found at https://int80k.com/libuvc/doc/.

Happy hacking!

For Windows

Prerequisites
[Libusb with isochronous support] (https://github.com/pupil-labs/libusb)
Cmake (https://cmake.org/files/v3.7/cmake-3.7.0-rc2-win64-x64.msi)
Installation
Download and extract posix threads for Windows from http://kent.dl.sourceforge.net/project/pthreads4w/pthreads-w32-2-9-1-release.zip Add the dll\x64 directory to the system path
Run cmake. Set the top level libuvc directory as the source path. Set a directory of your choice as the binares location
Click configure. Select "Visual studio 14 2015 Win64" as code generator. Fill in the locations for LIBUSB (set include to /libusb and lib to /x64/Release/dll/libusb-1.0.lib ) and PTHREAD (include to <pthread_dir>/include, lib to <pthread_dir>/lib/x64/pthreadVC2.lib). LIBJPEG is optional. If you are using pyuvc, it provides decoding via turbojpeg.
Click configure again. Click generate.
Open <bin_dir>\libuvc.sln Using Visual Studio. Make sure x64 platform is selected. Select Release configuration. Build the "ALL_BUILD" project
Add the \Release to system path
