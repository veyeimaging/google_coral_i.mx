# Introduction
This project includes how to use VEYE series and CS series mipi camera modules on google coral dev board.
In general, you only need to use the Image and dtb that we have compiled. Of course, you can also modify or recompile the driver according to our open source code.

http://wiki.veye.cc/index.php/VEYE_CS_Camera_on_google_Coral_board

The following operations are done on Ubuntu Host PC.

## Set up the Host PC environment

Refer to this page to set up the development environment:https://coral.googlesource.com/docs/+/refs/heads/master/GettingStarted.md.

## Build google standard version kernel

Complete the Build the tree steps according to the guide above.

## Patch code
### Driver source code

git clone https://github.com/veyeimaging/nxp_i.mx_veye_bsp.git

The source code path of the camera driver is: linux/drivers/media/platform/mxc/capture, replace the source code of the camera driver in the corresponding directory. The kernel version is 4.14.98 now.

Merge the Config and Makefile in the same path. Add the corresponding camera driver.

### dts file and pakages build config file

git clone https://github.com/veyeimaging/google_coral_i.mx.git

The path of the dts file is: linux/arch/arm64/boot/dts/freescale, places the dts file in this path.

Modify the Config and Makefile in the same path. Add the corresponding dts option.

The path of packages build is :packages/linux-imx/debian/,places the defconfig and rules in this path.

## Build

m docker-linux-imx

Install the new kernel

j product

cd packages/bsp/

mdt install ./linux-image-4.14.98-imx_12-2_arm64.deb
