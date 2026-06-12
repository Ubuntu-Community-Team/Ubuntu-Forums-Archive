---
title: "I can't install ubuntu on a new computer"
date: 2008-12-06
forum: General Help
---

### Post by robofighter on 2008-12-06
Hello I have built a new computer at my houses using an ECS p4m900t-m2 motherboard. I am using an 80 gb hard-drive, 1 gb of ram, and a dual-core Celeron processor. It is currently not connected to the internet.

anyway When I try to put in my ubuntu 8.10 cd but when I try to select the live cd or install to hard drive. Nothing will show up, on live cd it is completly black with two small circles with black and white with squally lights. When I try to install is shows the desktop background and a windows comes up but that windows never loads nor show any data.

When trying the live cd in protected graphic setting it shows the desktop but the images seems to extremely fuzzy like it display a part of a desktop and copys all over the place.

So is there any thing that I can do to allow it to install, the hard drive has nothing on it and still should have a low-level formatting.


also is there any program on the ultimate boot cd to check for bad sectors on the hard drive as when that hard drive came there was little packeting. (like 1 or 2 pieces of paper packeting)

also if you need information about the motherboard here it is: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4088308&Sku=MBM-P4M900T-E1200](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4088308&Sku=MBM-P4M900T-E1200)

---

### Post by Milbauer on 2008-12-06
> **robofighter said:**
> Hello I have built a new computer at my houses using an ECS p4m900t-m2 motherboard. I am using an 80 gb hard-drive, 1 gb of ram, and a dual-core Celeron processor. It is currently not connected to the internet.

anyway When I try to put in my ubuntu 8.10 cd but when I try to select the live cd or install to hard drive. Nothing will show up, on live cd it is completly black with two small circles with black and white with squally lights. When I try to install is shows the desktop background and a windows comes up but that windows never loads nor show any data.

When trying the live cd in protected graphic setting it shows the desktop but the images seems to extremely fuzzy like it display a part of a desktop and copys all over the place.

So is there any thing that I can do to allow it to install, the hard drive has nothing on it and still should have a low-level formatting.


also is there any program on the ultimate boot cd to check for bad sectors on the hard drive as when that hard drive came there was little packeting. (like 1 or 2 pieces of paper packeting)

also if you need information about the motherboard here it is: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4088308&Sku=MBM-P4M900T-E1200](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4088308&Sku=MBM-P4M900T-E1200)

update the firmware on your hardware maybe?

---

### Post by jerome1232 on 2008-12-06
Are you using on board video or an add in video card? Looks like the on board video is a VIA Chrome9 HC IGP Graphics Controller. From what I can see, this VIA video adapter doesn't get along well with Linux in general.

Perhaps [https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807) and [http://ubuntuforums.org/showthread.php?t=767074](http://ubuntuforums.org/showthread.php?t=767074) MAY be of some help I don't have the time to read over them and ensure they have good solutions.

---

### Post by TeXtonyx on 2008-12-06
> **Milbauer said:**
> update the firmware on your hardware maybe?

One goes into bios and changes the boot order to cdrom first.
Then you stick in the cd and save changes to bios and it 
continues to boot, and a screen will say, 'boot from cd'
and after a few seconds, 'tap any key' to boot from cd.
After cdrom, the boot order should continue with hd0.

Are you sure you hooked the hard drive up correctly. If you
have only one drive, the jumper setting should not be set to
slave. It tells you the jumper settings on the back of the drive.

I've heard of cases where people needed to load a driver in
order for the drive to be seen. I doubt that is the case.
I'm pretty sure you can avoid a video card problem by doing
a text install which uses a generic vga driver. Afterward
you can try to install the correct driver.

---

### Post by russofris on 2008-12-06
This honestly sounds like a case of an integrated graphics adaptor that is not yet supported by the kernel/xorg.  Chrome 9 support should be forthcoming now that Via is  contributing to the openchrome project.

[http://www.openchrome.org/](http://www.openchrome.org/)

Until then, you appear to have a few options.

1:  Acquire a cheap, alternate graphics adaptor.
2:  Wait for Openchrome to finish up support and for Ubuntu to add the new bits
3:  Install in text mode, download and try out Openchrome and/or the Via binary blob yourself.

Number 1 is the path of least resistance.  You can often pick lastgen adaptors for $15 (Geforce FX 5200).  Number 2 is for wimps.  Number 3 requires some mid-level linux knowledge (how to patch a kernel, pass kernel FB args to your bootloader, how to compile/insmod a kernel module, how to config parts of xorg by hand).

Frank

---

### Post by robofighter on 2008-12-06
Thanks for that. But can someone give me a walkthrough on how to do option number 3. I really would not go over my budget anymore then I have too and I need this ready by christmas for my brother as a basic computer system, I doubt this would ever used for anything interesting, maybe just watching on dvd at most.

---

### Post by southerngrey on 2008-12-06
If you have a copy you could also try installing the earlier 8.04 LTS version of Ubuntu instead, chances are the latest build of that might give you a more stable install.  Also you could try picking up the 8.04 version of these modified distributions [http://www.linuxmint.com/]("http://www.linuxmint.com/") or [http://ultimateedition.info/]("http://ultimateedition.info/").  I think they come with some additional driver support on the iso.

---

### Post by robofighter on 2008-12-12
Again I ask. Does anyone have any kind of walkthough for me to do a text install and then download and install the p4m900 through that mode.

---

### Post by southerngrey on 2008-12-12
OK, first you'll need to grab a copy of the alternate install cd which contains the text installer.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

And there is a basic walk through to get it installed here

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu")

Once you've got that on there let me know and we can cover the rest.

---

### Post by robofighter on 2008-12-15
I was able to get 8.04 installed. The graphics are still screwly and heavly distorted but I am able to read what is on the screen. So what else do I need to do.

---

### Post by southerngrey on 2008-12-15
I have found that there are driver packages that should work for the VIA chipset in the package manager.

Open up Synaptic from the Administration menu and check to see if the following are installed.

libchromexvmc1
libchromexvmcpro1
xserver-org-video-openchrome

If they aren't then installing them might sort out your graphic problems, although I'm not sure why they wouldn't be installed by default if you have that system.

Could you maybe post a screenshot so I can see what the problem looks like, with the display settings dialogue up would be good.

If you

---

### Post by southerngrey on 2008-12-15
cleared due to double post

---

### Post by robofighter on 2008-12-21
Would missing prongs on my VGA cable be a cause of my problems. I just notice this when I disconnected the VGA cable from the computer.

I looked up the prongs on wikipedia and I am missing the prongs for I²C clock, I²C data, and +5 V DC, also that the male VGA cable is orange instead of blue. Could this be the cause of the ghosting on my computer. I can't make a screenshot of that computer as  I don't have a camera and its a CRT so it would not work so well anyway.

---

### Post by southerngrey on 2008-12-21
Thats entirely dependent on what sort of monitor etc, I don't know enough about that to help you out sorry.  I would definitely try it with another cable/screen if possible though, missing pins are usually bad for business.  Although I seem to recall several connectors where I have seen pins missing, it may just be the model of screen.

---

### Post by sintacto on 2008-12-21
if you boot up in recovery mode and choose to boot to text terminal try
sudo nano /etc/X11/xorg.conf and change "vesa" to "openchrome"
save and then reboot.
but look up openchrome howto for better instructions.

---

