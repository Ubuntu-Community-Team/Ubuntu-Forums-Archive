---
title: "Vista dual boot with Fiesty Fawn failed!"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-08-03
Dell Inspiron 1720
t7300, 2GHZ dual core/800MHZ FSB, 4mb cache
256MB Nvidia geForce 8600 GT
2GB Ram
250GB 5400rpm SATA HDD

Wndows vista home premium came pre-installed on my machine.  I created 25GB of unallocated space to install Fiesty Fawn on.  Live cd didn't work so I was forced to use the text installer cd.  Install went smooth, accidentally didn't choose any settings for the video resoulution, but I thought it would autodetect it.  Other than that, install went fine, rebooted system to run Ubuntu, No luck.  Forced into command line, with following errors...

Failed to start the x server, would you like to view the x server output to diagnose the problem.  It isn't reading my monitor, or somethings wrong with my Graphics card drivers...?

I've found various pages to help me try to resolve this issue, but every 2 min in the command line another error pops up regarding my wireless situation.  I can resolve this issue with the bcm43xx-fwcutter program, but I have no GUI interface or connection to the internet unless i'm in Windows.  Also, I can't resolve the monitor situation, because the wireless error continuously pops up.

---

### Post by buzzmandt on 2007-08-03
if you can put the results of the x server diagnostics, or at least what it says in a nutshell that would help

---

### Post by jmnormand on 2007-08-04
to fix your wireless issues create a fat32  partitions and from windows then download and unpack this to the partition.

[URL="http://http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.2.tar.gz"]http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.2.tar.gz
[/URL]

then mount the partition in ubuntu and change to the directory and 

./installbcm43xx

this should fix your wireless issues then you can use apt-get to fix the graphics problems.  not sure on specifics with the nvida card as im running the intel.

---

### Post by AndyQ on 2007-08-04
To boot the live CD on a 1720, you need to add break=top to the beginning of the boot option (press F6 at the boot menu).

That will drop you into a terminal where you type:
modprobe piix

(This loads the piix driver which is needed for mounting the image from the DVD (I think))
Then type exit to continue the boot. This should boot fine until it tries to start X.

This will fail to start because the drivers supplied on the live CD (and I guess the alt cd) don't support the NVidia card.

This is a simple fix, just edit the /etc/X11/xorg.conf file and change the "nv" entry to "vesa".

Save the file and type startx to start X.

You can then install Ubuntu by clicking the install icon.

After a reboot, you should boot up into X (it worked for me but if it fails then you may need to do the vesa bit above again) but you DVD won't be working.

To fix this, edit (as root) /etc/initramfs-tools/modules and add a new line at the end which just contains:
piix

Then run the below command (as root):
update-initramfs

After a reboot all should be well.
You can then then go and install the proper NVidia drivers from the NVidia site (You'll need to exit from X to do this though).

Oh, and wireless works fine when in X, and you can change this to a manual config to get it to start up at boot time (so you an mount samba shares etc) if you need to.

I haven't got suspend or hibernate working yet or the scrolling on the touchpad, and haven't even thought about the webcan either, but everything else works fine.

---

### Post by circuz_phreak on 2007-08-04
THANK YOU!!! after messing around with the config file for a couple hours and doing another autodetect I thought it wasn't going to work.  is vesa a generic driver supported by most video cards?  to dig up the proper driver i'm guessing i should just surf the nvidia website, then change the config file back to "nv" driver??  touchpad and touchpad click buttons seem to be working, number pad on right side of keyboard isn't but it's operators are...wierd?  anyways,  I have roaming enabled, and my wireless issue does seem to be resolved..but i can't seem to connect to my local network, i enter its name, password, and security features all correctly...Just one small step away from getting everything working smoothly.  One more question regarding the driver situation, is there a program called etchy or envy which detects current drivers and installs them itself for linux (thats what i heard from someone)?

---

### Post by AndyQ on 2007-08-05
Vesa should be supported by pretty much most video cards now.

As to changing back to "nv", if you do that, then you'll use the old drivers which won't work. When you install the latest NVidia drivers, it asks you whether to let it modify the xorg.conf file (which I suggest you do) and it sets the correct driver.

Regarding envy, I've heard good and bad things about it - the bad being is can screw your system up. However, as the nvidia driver worked first time no problems, I haven't seen the need to use envy.

---

### Post by circuz_phreak on 2007-08-05
So i'm pretty close to getting my wireless network  up and running.  Wireless runs great when inside windows (where i am now), but it only detects the network and has 100% signal strength in ubuntu but doesn't connect.  I followed the whole bcm43xxcutter solulution in posts except used the approach where someone had written a script so i virtually had to do nothing.  I wonder why it won't connect, even when i ping my router it says network unreachable.  Also now I realised my cd-rom/dvd-burner isn´t being read at all, attempts to mount it failed.  Which is why I can´t download the proper packages to get my video driver up and running (because the libc libraries prompt me to put in the OS cd, which can´t be read).  It says when i try to mount it ¨special device /dev/hda does not exist¨ and doesn´t show up in my system hardware.

/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2254cf8c-f4f5-4662-bf8b-f7fcf95443b6 /               ext3    defaults,erro$
# /dev/sda7
UUID=13497107-d3af-45f6-8e64-b7a938c91833 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

