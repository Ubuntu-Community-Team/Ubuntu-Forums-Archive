---
title: "Dell Latitude D830 laptop Ubuntu installation problem (dual-boot w/ Vista)"
date: 2007-07-25
forum: Dell  Ubuntu Support
---

### Post by abadfish on 2007-07-25
I got my brand new Dell Latitude D830 laptop pre-installed with Vista.  So before I started loading all my junk on it, I attempted to make a dual-boot system with Ubuntu.

here's what I've done so far:
1.  used SystemRescueCD (with GParted) to shrink the windows partition and create partitions for linux.  So now I have a 30 gb partition for Vista, 30 gb partition for Ubuntu, 4 gb partition for swap, and the rest as shared partition for both Vista and linux.

2.  installed Ubuntu with the alternative cd.  (to my knowledge this went fine.  I didn't see any error messages or anything like that).

3. Used BcdEdit in Vista to make a boot sector for linux in the Vista boot record (procedure listed [here]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")).

When the system boots, I select Linux and then nothing happens.  I just get a blank screen with the cursor blinking in the top left corner.  My windows boot is fine.

Any suggestions?  I'm willing to try installing Ubuntu again but I was hoping to see if this can be salvaged.

Thanks.

---

### Post by jb1789 on 2007-07-25
Looking at the tutorial that you linked, it seems like you need to install Ubuntu first and Vista second.  That might be part of your problem, but I'm not sure.  Is there any particular reason that you do not want to use GRUB?  I have the same laptop with Vista installed and Ubuntu dual-booted and I had to change the video drivers to boot into a graphical interface, but I did receive various errors before Ubuntu resorted to the command-line, so our problems seem different.  I'm relatively new to Linux, so you should probably wait for other opinions, but I would suggest reinstalling Ubuntu and using the GRUB boot loader.

---

### Post by Utopus on 2007-07-26
> When the system boots, I select Linux and then nothing happens. I just get a blank screen with the cursor blinking in the top left corner. My windows boot is fine.


I'm having exactly same problem as the quote above. 

I also tried to uninstall Ubuntu by booting from original CD, however, no response from that either... :(

---

### Post by rmullins on 2007-08-02
More than likely you are having a video driver problem.  I had the same exact problem with my Dell 830.  There is a bit of a work around however.  I have something of a solution on my blog
[http://blog.gaelicmysts.com/?p=74](http://blog.gaelicmysts.com/?p=74)

Seems that there is alot on the Dell 830 that is not supported.  I am currently researching 'sound' issues. on my 830.  This is becoming quite a chore.

---

### Post by mag82008 on 2007-08-04
Have a look here:
[http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu](http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu)

Works for x86, too

Cheers
M.

---

