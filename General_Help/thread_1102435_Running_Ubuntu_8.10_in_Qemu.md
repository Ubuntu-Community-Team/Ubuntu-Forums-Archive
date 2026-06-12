---
title: "Running Ubuntu 8.10 in Qemu"
date: 2009-03-21
forum: General Help
---

### Post by gamewolf on 2009-03-21
I have Qemu downloaded in Windows XP and I am wanting to put it and ubuntu on my flash drive so that I can take it anywhere and run Ubuntu. I can launch Qemu with the Ubuntu iso loaded and the menu works fine. Once I try to launch the installer or the live cd, "Qemu has encountered an error and needs to close".

Is this because I don't have the accelerator? I don't want to use it because the computers I would be running Ubuntu on would have permission restrictions and I wouldn't be able to install a driver.

How can I fix Qemu or is there another way I could launch Ubuntu portably?

Thanks.

---

### Post by Calmor on 2009-03-21
Sounds like an interesting concept, but unfortunately I don't know anything about Qemu.  Is it a portable application (as in it requires no registry entries or DLLs stored in the Windows\SYSTEM folders)?  If not, the errors that you're getting might have something to do with the fact that it doesn't install well on the flash drive.  It's hard to imagine an emulation software that doesn't need Windows system tie-ins, considering Virtualbox has a required kernel module.

Optionally, you could just make a pen drive linux system ([www.pendrivelinux.com](www.pendrivelinux.com)) if you can choose the boot device on the computers you want to use it on.  Choosing a persistent one will allow you to save changes/documents.

---

### Post by gamewolf on 2009-03-21
Qemu doesn't require tie in to windows, but it runs faster if you install KQemu (an accelerator driver). However, this computer I am wanting to run it on is older and has restrictions with access to bios and even installing everyday programs in general.

I believe I may have found why it was crashing. I disabled ACPI and now it works! I am going to try and install a minimal debian desktop and see how well it will run without the accelerator driver.

Thanks for the help.

---

### Post by Calmor on 2009-03-21
Awesome, glad you found the issue.  It sounds like quite an interesting project - I tried running a Kubuntu persistant install on a USB drive, but my laptop didn't want to play nice with it - it worked on every other machine I tried it on.  I might have to try Qemu to see what it's about.

Fortunately for me, most every computer I come in contact with on a daily basis is pretty much unlocked - even the computers at school, surprisingly.  We have full access to the BIOS and operating system in the engineering lab... and some day they'll learn that's why one of them has a BIOS boot password that nobody knows and why they have to reinstall every few months.

---

### Post by gamewolf on 2009-03-21
Lucky for you. All the computers I come in contact with other than the ones at home are locked. I can't even install Gimp. Thats why I use PortableApps.com

If I can get Qemu working with Debian 5 (Ubuntu run too slow), I will write a How-To with all the steps.

Thanks for your interest!

---

### Post by Calmor on 2009-03-21
I love my PortableApps for Windows machines - even if I can boot to something else, I like having all of MY stuff available - OpenOffice for document compatibility, Thunderbird-Lightning so I can get my mail, Firefox with my bookmarks... it's hard to beat.

---

### Post by gamewolf on 2009-03-21
It is hard beat. I love portable apps. I can take Gimp everywhere I go! :)

Well, here is an update on my progress. My flashdrive is too small for a full GNOME Desktop Enviroment. (Well it isn't too small, but I already have stuff on there and I want to make it as close to a real-world situation as I can get).

So I am going to install just the base system and then install XFCE or Fluxbox. Those are both incredibly small so that should help. Then install Firefox, Gimp, Pidgen, etc. Hopefully I can get it under 1G. If not, it needs to be under 2G.

---

### Post by Calmor on 2009-03-21
Sounds like you're making progress...  Sounds almost like Linux-as-an-application.

Not sure if it helps, but I did an IceWM install on an old laptop, due to processor and RAM limitations more than HDD space, but it worked out very well and was quite light.  I don't know what it's drive footprint was, though.  This particular machine would barely run Windows 98, but was significantly more responsive with an Ubuntu 8.04 minimal install and IceWM.  It requires a LOT more tweaking than XFCE (and a file/desktop manager on top of it, I think I used ROX-Filer), but great for hardware requirements.

---

### Post by gamewolf on 2009-03-22
Sorry for the delay!

Alright it has installed successfully, however there is one problem.
I have installed sudo, fluxbox, and xdm. However, XDM won't launch, even tho it says XDM has started.

Where is the log for xdm?

The other problem is that I cannot access other tty's or XServer session because ctrl-alt is recognized by Qemu for uncaptureing and capturing the mouse. So I cannot do ctrl-alt-f1, etc.

If you have any suggestions for these please let me know!

---

### Post by gamewolf on 2009-03-22
Ah! Nevermind, I got it!
I found a guide that is very good and got me setup quickly.
[http://ubuntuforums.org/showthread.php?t=1102435](http://ubuntuforums.org/showthread.php?t=1102435)

Once you have the Debian Base System installed, you just follow this guide and it gets everything setup for you. I skipped a few things that I thought were unnecessary and replaced certain programs with ones that I prefer. So far so good!

---

