---
title: "Open Office"
date: 2009-01-04
forum: General Help
---

### Post by Jara04 on 2009-01-04
Hi,this is my second day using ubuntu (8.04), i'm trying to install open office 3 but it has .tar.gz extension and i don't know how to install it, i know i have to type something in the console but i don't know how...

in the same way my sound card controller is supposed to be installed in the same way, and i don't understand the directions, basically the part of the folder creation, because the folder "linux" doesn't exist, the ones there are linux-headers-2.6.24-22 and linux-headers-2.6.24-22-generic, so that i don't know where to place the folder.

I'd appreciate some helo with this

Thanks :D 

-------------------------------------------------------

Audio driver for CM8338/CM8738 chips by Chen-Li Tien





HARDWARE SUPPORTED

================================================================================

C-Media CMI8338

C-Media CMI8738

On-board C-Media chips





WHAT'S NEW

================================================================================



  1. Support modem interface for 8738. (select in kernel configuration)

  2. Enable S/PDIF-in to S/PDIF-out (S/PDIF loop).

  3. Enable 4 channels analog duplicate mode on 3 jack or 4 jack

     configurateion.

  4. Enable joystick support. (joystick driver needed)





STEPS TO BUILD DRIVER

================================================================================



  1. Backup the Config.in and Makefile in the sound driver directory

     (/usr/src/linux/driver/sound).

     The Configure.help provide help when you config driver in step

     4, please backup the original one (/usr/src/linux/Document) and

     copy this file.

     The cmpci is document for the driver in detail, please copy it

     to /usr/src/linux/Document/sound so you can refer it. Backup if

     there is already one.



  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above

     directory.



  3. Change directory to /usr/src/linux



  4. Config cm8338 driver by 'make menuconfig', 'make config' or

     'make xconfig' command.



  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI

     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.

     For driver option, please refer 'DRIVER PARAMETER'



  6. Compile the kernel if necessary.



  7. Compile the modules by 'make modules'.



  8. Install the modules by 'make modules_install'





INSTALL DRIVER

================================================================================



  1. Before first time to run the driver, create module dependency by

     'depmod -a'



  2. To install the driver manually, enter 'modprobe cmpci'.



  3. Driver installation for various distributions:



    a. Slackware 4.0

       Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules

       file.so you can start the driver automatically each time booting.



    b. Caldera OpenLinux 2.2

       Use LISA to load the cmpci module.



    c. RedHat 6.0 and S.u.S.E. 6.1

       Add following command in /etc/conf.modules:



       alias sound cmpci



	also visit [http://www.cmedia.com.tw](http://www.cmedia.com.tw) for installation instruction.



DRIVER PARAMETER

================================================================================



  Some functions for the cm8738 can be configured in Kernel Configuration

  or modules parameters. Set these parameters to 1 to enable.



  spdif_loop:   Enable S/PDIF loop, this route S/PDIF-in to S/PDIF-out

                directly.

  four_ch:      Enable 4 channels mode, rear-out or line-in will output

                the same as line-out.

  rear_out:     Enable this if you have independent rear-out jacket on

                your sound card, otherwise line-in will be used as

                rear-out.

  modem:	You will need to set this parameter if you want to use

		the HSP modem. You need install the pctel.o, the modem

		driver itself.

  joystich:	Enable joystick. You will need to install Linux joystick

		driver.

---

### Post by AllanPoe on 2009-01-04
Maybe this could help ...

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

