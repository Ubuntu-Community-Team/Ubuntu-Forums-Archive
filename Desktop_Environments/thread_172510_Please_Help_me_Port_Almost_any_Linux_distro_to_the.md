---
title: "Please Help me Port Almost any Linux distro to the MS Xbox"
date: 2006-05-08
forum: Desktop Environments
---

### Post by raid517 on 2006-05-08
OK I have been trying for some time to find a way to install Kanotix (or any modern distro) on my Xbox and I have had partial success I think. 

Here is what I have done so far.

I created a virtual machine in Vmware with two disks - both large enough to contain a full Kannotix/Sid install.

I booted this and then installed Kannotix on the primary partition.

I downloaded the latest full kernel release from kernel.org which is 2.6..16 (important - this must be a full release and not a point release - as in 2.6.16.7 or whatever, or any patches you try to apply won't work).

I then downloaded the latest performance patches (which are useful if you want to squeeze every last drop of performance out of your Xbox as possible). These can be obtained from here: [http://ck.kolivas.org/patches/2.6/2.6.16/](http://ck.kolivas.org/patches/2.6/2.6.16/) (At the time of writing the latest is 2.6.16-ck9). I downloaded also the latest Xbox Linux kernel patch - which can be found here: [http://sourceforge.net/project/showfiles.p...ckage_id=147485](http://sourceforge.net/project/showfiles.php?group_id=54192&package_id=147485) (again at the time of writing the latest is 2.6.16). For good measure I also downloaded the latest bootsplash patch from bootsplash.de.

I then extracted my new kernel source and applied the patches.

For a detailed guide on how to apply these patches - there is a good tutorial available here:

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560) (it is for Ubuntu Linux - but it works just as well in this instance).

Basically however it involves extracting your kernel source to /usr/src - and then extracting the patches and moving them to your /usr/src/linux-2.6x directory and then doing:

```
patch -p1 < /path/to/patch_file
``` 

(It's probably best to give the full literal path to the patch - as this seems to work better. Also the actual patch extension doesn't matter as tthe patching utility can handle most of them. Or if you don't want to extract them first, just follow the Ubuntu guide).

In any case having done this I did a make old config in my linux source directory - and wherever possible I simply accepted the default answers (as per the official advice) and launched menucofig in my linux source directory (again /usr/src/linux-2.6.x) and loaded the included Xbox Linux kernel.config file (which is called kernel.cofig). A couple of oddities I found were that the included config did not include hotplug support (needed by UDEV in 2.6x kernels and that PS2 mouse support was listed as a module - which doesn't always work - so if you want PS2 mouse support so you can work with your new Linux version on your PC too, select to compile this into your kernel rather than as a module). Also PPP networking support was not included as default - which is generally just useful to enable if you want to do any kind of PPP networking - which most people at some point probably do. (You may also wish to include support for your own specific PC based networking card - and any other PC hardware that you may have - although don't go crazy and enable everything in your kernel - as the idea is to keep the kernel as small and specific for your needs as possible). Also if you want bootsplash support, you must enable Vesa framebuffer support in the graphics section of your kernel otherwise you won't be able to select it. The included 2.6 Xbox kernel.config that is supplied by the 2.6 xbox patch provides a good basis for booting 2.6 kernels on the xbox - but to match your own needs, some slight tweaking may still be required.

(For more details and for an equally useful guide to updating a 2.6.x kernel for the Xbox, you could also look here: [http://www.xbox-linux.org/wiki/Xebian-1.1....el-2.6-Upgrade)](http://www.xbox-linux.org/wiki/Xebian-1.1.4-Kernel-2.6-Upgrade))

OK once you compile and install your new kernel (I'm not going to go into that here as the supplied guides are already useful for Debian and there are countless other equally good guides like this on the net for non Debian users) this is the point where it starts to get interesting. Make sure you update your Grub menu.list accordingly (if this isn't done automatically by your distro) and then reboot your Vmware and test your newly installed Kernel. If it works in Vmware - there is a very good chance that it will work on the Xbox too.

If it does boot, it's OK to go ahead and make your new Kernel the default in grub

So OK now we have the problem of how to get this newly installed Linux version off of Vmware and onto the Xbox. I did this simply by following these guides on how to create a loopback file system within a file: [http://www.anandtech.com/guides/viewfaq.aspx?i=137](http://www.anandtech.com/guides/viewfaq.aspx?i=137). I created a lopopback file of about 3.5GB in size (as I am unsure if fatx has the same 4GB file size limitation of Fat32?) on my /dev/hdb1 partition and I then formatted the new loopback file as per the instructions, with an EXT3 file system and mounted it. Then I launched cfdisk on the /dev/loop0 device and created a new partition (taking up all of the space on the loopback file) and I also for good measure I marked the new file as bootable.

Then I unmounted this newly created file and rebooted Vmware and chose to run from my Kanotix Live CD ISO instead of booting from a virtual hard drive (although any live CD will do). 

Then I followed this guide on how to copy an entire installed OS to a mounted partition:

[http://www.360insider.net/forums/showthread.php?t=203](http://www.360insider.net/forums/showthread.php?t=203)

It talks about OS X and installing to a physical drive - but I figured that it ought to work just as well for installing an OS to a loopback file system.

So instead if following the guide and installing to a physical partition - what you should do is mount your loopback file from within your live CD inside Vmware - by doing for example 

```
mount -o loop -t ext3 path/to/Your_Loopback_File_Name /mnt/loop. 
```

(You may need to create a /mnt/loop directory first.

Then adapting the guide, do 

dd if=/dev/hda1 of=/dev/loop0 bs=8192

Where /dev/hda1 is the partition you installed your favorite Linux distro to and /dev/loop0 is your mounted loopback partition. This should take aboutt 10 minutes (depending on the speed of your machine) to complete. There is no output during this time - so don't worry if you don't see anything happening - other than your hard drive looking quite busy.

After this is complete you should have a loopback file in your /mnt/hdb1 partition containing an exact clone of your Xbox compatible installed OS that (in theory) should be transportable to any suitably modified Xbox system.

To export this all that is required is that you enable Samba share in VMware (networking must be enabled on your own home PC first) (again please seek guides elsewhere on how to do this - as there are a great many of these available).  I suggest sharing both your /dev/hdb1 partition and your home partition for good measure. Then go to network places (or the equivalent in Linux) and copy your loopback file to your PC. You will also need your Kernel and initrd and possibly your grub menu.list (to obtain the correct boot parameters for linuxboot.cfg) so make sure to download these from your VMware machine to your PC too. The next stage of course is to move these files to the partition on your Xbox where you wish Linux to be installed.

Unfortunately this is the point where my guide breaks down a little. First I know nothing about writing .xbe's - so I figured that it ought to be easy enough to just use a default.xbe and linuxboot.cfg file from another distro such as Xebian, or Xdsl. However having read the guide here [http://www.xbox-linux.org/wiki/Cromwell_Ma...boot.cfg_syntax](http://www.xbox-linux.org/wiki/Cromwell_Manual#Linuxboot.cfg_syntax) on the Cromwell manual to writing Linuxboot.cfg files I am still not very clear at all on what to do next.

Here is my linuxboot.cfg file ATM as I currently understand it.

```
title Kanotix_2.6.16
kernel /E//Knoppix/Kannotix_2.6.16
initrd /E/Knoppix/2.6.16_intrd
append kbd-reset root=/E/Knx_fs kbd-reset ro lang=uk apm=power-off nomce ramdisk_blocksize=4096
xboxfb y
```

As you can see I have simply given the literal paths to everything on my sytem here - although I am not certain this is right at all. (Or at least it certainly doesn't work at this time).

So far my system is set up as follows.

I have copied my loopback file system to E. I have copied my Kernel to E/Knoppix and I have copied my initrd to E/Knoppix too. I have also copied a default.xbe and linuxboot.cfg file from a previously installed XDSL version to my E/Kipppix folder too.

So currently my system looks like this:

```
kernel E//Knoppix/Kannotix_2.6.16
initrd E/Knoppix/2.6.16_intrd 
default.xbe /E/Knoppix/default.xbe (taken from a previously installed version of XDSL)
linuxboot.cfg /E/Knoppix/linuxboot.cfg (taken from a previously installed version of XDSL)
root fs E/Knx_fs
Swap E/knoppix.swp
```


So the question is, have I got it right (clearly I haven't because I can't boot my OS) and if not which part of what I have done do I need to fix? Or alternatively have I just completely wasted my time?

Please help me complete my guide.

Again the reasoning behind doing things this way is because the current choice of Linux ditros for the xbox is far too limited - so if I can get this to work it will open up a wold of almost infinite choice, where you will be able to install virtually any flavour of Linux on an Xbox as you see fit. (So no more messing about with 3 year old+ compilers, or broken dependencies for modern applications).

Any input or help anyone can offer at all would be very much appreciated.

GJ

---

