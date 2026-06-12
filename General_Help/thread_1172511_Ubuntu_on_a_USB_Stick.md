---
title: "Ubuntu on a USB Stick"
date: 2009-05-28
forum: General Help
---

### Post by beastrace91 on 2009-05-28
So I recently installed a copy of Ubuntu to an 8gig USB stick I had laying around and it works well. My only question is that is there a way I can boot from CD on a system that does not detect/support booting from my USB device right away and then tell it from the Ubuntu LiveDisc to use the install thats on the flash drive?

~Jeff

---

### Post by pytheas22 on 2009-05-28
[This]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/") sounds like what you're looking for.  I haven't tried it yet myself, but found it via Google because I'm also interested in booting to USB on an old computer whose BIOS doesn't support it.

---

### Post by beastrace91 on 2009-05-29
Wow! This link looks just like what I am looking for, I will be trying this tomorrow and will post back my success with Jaunty. If all goes well my Ubuntu on a stick will be booting up on most everything shortly :)

~Jeff

---

### Post by beastrace91 on 2009-05-29
Huh so this *kinda* worked. I followed the instructions using a 9.04 32bit disc and they went off with out a hitch, creating the iso and ripping it to a CD. I went to test it on an old IMB system I had laying around and it boots off the disc just fine, I select Ubuntu from USB and I think it detects my USB drive because it then says ```
Starting up...
Loading, please wait...
``` and then goes to the Jaunty splash screen, how ever after sitting at the splash screen from almost a minute it drops me down to a simple terminal that reads "BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)" 

One odd things I did notice is that it did not say it was booting from a particular disc like Ubuntu normally does at this point, so perhaps it is not seeing my USB drive. Do you think this is just it running from the CD? Going to try disabling the splash screen when it loads up so I can see what it is running - hopefully that will give me a better idea.

~Jeff

---

### Post by beastrace91 on 2009-05-29
Yea I am pretty sure it is not booting from my USB drive, when booting with just the CD in I get to the same BusyBox terminal screen the only difference being that there is an extra line between start up and loading before it displays a splash: ```
Starting up ...
[    2.171978] I0 APIC resources could be not be allocated.
Loading, please wait ...
``` I'm assuming this just means it could not find any USB devices, but the fact that it gets me to the same terminal screen leads me to believe that it was not booting from the USB device anyways.

Downloading an 8.10 ISO now to try creating the disc with that as the guide suggested.

~Jeff

---

### Post by beastrace91 on 2009-05-29
Tried with an Ubuntu 8.10 disc and it does not work either (yields the same result as the Jaunty disc)

Perhaps it does not like my Patriot Pen Drive... Going to move my NixStick install to my memorex and see if that works.

~Jeff

---

### Post by pytheas22 on 2009-05-29
Sorry to hear it's not working.  It may be that it doesn't like the USB drive you're using, but it could also be the computer itself.  Do you have any other machines you could test on?  You could try it on a machine that does support direct booting to USB, but use the boot-up CD anyway, just to see if that works.

Also, how much memory do you have on the computer that you're trying to boot to USB?  If it's really old, it may simply be unable to boot Ubuntu.

I also intend to give this a try on my ten-year-old Pentium 3 machine in the next few days and will report back.

---

### Post by beastrace91 on 2009-05-29
It is decent - 1gig of ram and a 3.0ghz P4 - installing Jaunty to my 4gig pen drive now to see if that works. Will have to try it on my G1Sn later tonight when I get home.

~Jeff

---

### Post by beastrace91 on 2009-05-29
Hrm, I tried it on my G1Sn as well at it also does not appear to see the Patriot drive when selecting "boot from USB" off the custom disc I made... Did not have time to make my memorex a live drive this afternoon but will try it for tomorrow morning to see if perhaps it is just my patriot drive or if indeed this guide is completely fubared.

~Jeff

---

### Post by salvachn on 2009-05-29
I guess you could use this way: [http://tinyurl.com/pendriveubuntu](http://tinyurl.com/pendriveubuntu) This worked on my 4 GB drive.

---

### Post by beastrace91 on 2009-05-30
I think you are missing what we are trying to do here salvachn, I already have Ubuntu installed to a pen drive how ever I am trying to make it boot on older hardware that does not support booting from a USB device.

As for installing to my memorex drive it yields the same result when trying to use the USB boot disc, the funny thing I noticed is that while it was at the splash screen the memorex light that says it is being accessed was flashing how ever it does not appear anything was ever actually loaded off the pen drive. Odd.

~Jeff

---

### Post by pytheas22 on 2009-05-31
Sorry you still haven't found an answer, Jeff.  I still haven't had a chance to try this on my own machine (which I need to dig out of the basement first), but I found a few more links that are of interest.

First, [this page]("https://help.ubuntu.com/community/BootFromUSB") explains two methods of booting to USB on a system whose BIOS doesn't support it.  Apparently you can use the normal grub bootloader to do this on systems where it's installed to an internal hard drive.  The second method is to create a CD that you would boot to and then from there boot to USB, which sounds very similar to what you've already tried--but I'm wondering if these Ubuntu-specific instructions would work better than the ones written by the Pendrive Linux people, who assume that you have their version of Linux installed to your USB drive, rather than Ubuntu.

I also found [this thread]("http://ubuntuforums.org/showthread.php?t=266068"), which contains a couple of links.  Unfortunately one of them seems to be dead, but it might still be possible to get hold of the files that it used to host (one of which seems to be a ready-made .iso file that the people in that thread claimed was able to boot Ubuntu off a USB); I didn't try very hard.

Finally, I found [these instructions]("http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/") explaining how to use a floppy to boot to USB.  They're also from Pendrive Linux and I'm not sure if it matters whether your USB volume label is 'PDL', as the instructions say it should be.

I'll hopefully find time in the next few days to give these things a try myself, but thought you might be interested in these links as well.

---

### Post by beastrace91 on 2009-06-01
So I followed the instructions in [your first link](https://help.ubuntu.com/community/BootFromUSB) and it yields about the same results as the previous disc I tried - how ever this time before it gets to the "BusyBox" terminal it displays these two lines over and over again: ```
kjournald starting. Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
```

Any idea what that means? It appears to be finding my pen drive (which is formatted with ext3 file system) but it does not boot from it. Going to poke through your other links - hopefully they will lead me to something more solid.

~Jeff

---

### Post by pytheas22 on 2009-06-01
That's strange.  Those lines suggest that the system is starting to boot successfully, so I'm not sure why it dumps you down to busybox after them.  Can you access any logs (like /var/log/syslog) from the busybox prompt that might provide a clue?

You may also want to try formatting your USB stick as NTFS, since I think that's what most of these tutorials assume you've done.  The bootable USBs I create using Ubuntu's built-in creator work fine formatted as NTFS.

---

### Post by beastrace91 on 2009-06-01
Ubuntu will install to an ntfs formatted partition? I didn't know that, I'll format it to that and see if that helps.

~Jeff

---

### Post by beastrace91 on 2009-06-01
How do I format the drive to ntfs and install Ubuntu to it? As I though when I went into manually partition selection for installing Jaunty ntfs is not an option.

~Jeff

---

### Post by pytheas22 on 2009-06-01
You can reformat it to NTFS by installing gparted (sudo apt-get install gparted) and launching it from System>Administration>Partition Editor.  Or you can use Windows to reformat the device, of course.

Also, it sounds like you used the Ubuntu installer on the live CD to install to the USB disk.  This works, but NTFS is indeed not an option in that case.  However, I've always used the utility at System>Administration>Create a USB startup disk and it works fine with NTFS.

The system that it creates is like a live CD, which is a little different than what you'd get if you just installed Ubuntu to disk using the traditional method; I'm not sure if this creates a problem for you.  In any case, you could probably tweak the disk to behave as you want.

EDIT: scratch that; it turns out my disk is formatted as FAT32.  NTFS might also work, but you might want to try with FAT32 first.

---

### Post by beastrace91 on 2009-06-01
I have indeed installed Jaunty to the USB stick so it behaves as a normal system install. I need it to work this way to my applications and settings stay with it for each boot. (I use it for avast! and gparted for system maintenance) I *think* that is what those guides are intended to be used with - I'll have to play around with them some more and see if I can get it working, how ever any input you might have is very welcome.

~Jeff

---

### Post by pytheas22 on 2009-06-01
One way to make a USB stick with the applications you need using Ubuntu's built-in CD creator would be to create a custom live CD using [remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys"), and then point the USB-creator utility to your customized .iso file.  It would still technically be a live system rather than a traditional installation, but it would contain all your customizations and they would be persistent throughout reboots.

There may also be an easier way to do this, but remastersys was the first thing that came to mind.

I'm still hoping to get a chance to test those tutorials myself within the next few days and will post back.  If I haven't posted by the end of the week, please bump the thread to remind me.

---

### Post by pytheas22 on 2009-06-02
I found time to try this today and had success with the instructions on [this page]("https://help.ubuntu.com/community/BootFromUSB").

I first followed the instructions under in the section "Booting via grub," attempting to boot the USB stick using the grub bootloader that was already installed on an internal hard disk in the computer (the computer already has Linux on it).  That didn't work at all, as grub didn't seem to be able to recognize my USB drive as a hard disk--it only recognized the floppy drive (which was empty) and the internal hard disk.

I then followed the section of the web page titled "Booting the kernel from a bootable CD."  On another computer, I booted to my live USB stick, created an .iso according to the instructions on the web page, and burned it to a CD.  I then put the CD in the target computer (i.e., the old one), booted to the CD with my USB stick inserted, and selected the "Boot to USB" option after the CD loaded.  This worked great.  I think the trick was creating a custom initrd with the drivers for USB built-in, but I'm not sure.

I didn't try the instructions on the Pendrive Linux site.

Note that I was using an Ubuntu 9.04 live USB that I created using the "Create a USB startup disk" utility.  After reading more about this, however, I don't think it should matter whether your USB stick is "live" or is simply a traditional Linux installation.  All that really needs to happen is that something boots the Linux kernel installed on the USB stick; at that point, nothing should care whether it's a live system or not.

If you have time, I'd recommend that you try following the same instructions I did; hopefully they'll do the trick.

---

