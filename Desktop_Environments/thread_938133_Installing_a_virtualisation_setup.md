---
title: "Installing a virtualisation setup"
date: 2008-10-04
forum: Desktop Environments
---

### Post by heiowge on 2008-10-04
I am currently running Ubuntu and XP dual booted on an older machine with 2G Ram.  I have recently found myself spending more time that I'd like in XP due to not finding the programs I need under Linux.

I want to set up my machine by reinstalling Ubuntu from scratch - erasing everything after backing up my files to an external hd, then setting up XP to run virtually within Ubuntu off a 20G Partition.

I have never done this before, but Linux Format mag seems to make it seem straightforward enough.

Only problem is that it recommends 512 Mb ram for Linux to run.

Before I do this, I need to test it on another machine.  This machine has 512Mb ram total.  Pulling Ram from this one is a major hassle.  How much Ram do you recommend as a decent test for Ubuntu Hardy and how much shall I allocate for XP?  What about for my 2Gb Ram machine?  Lastly, if I allocate 256mb ram for XP, when I run Linux only do I get all my ram or ram - 256mb?

Ta

---

### Post by keplerspeed on 2008-10-04
You do not need to do a complete reinstall. Just install gparted, the gnome partition editor to remove your windows partition, and expand the ubuntu partition over the entire HD. Also, install virtual box, NOT vitrual box OSE in the repositories, as the open sourse edition doesnt support usb. get virtual box [http://www.virtualbox.org/](http://www.virtualbox.org/) you will need the kernel modules aswell, these are in the repositories. I have successfully used XP in virtual box, and used guest editions to set the guest OS to full screen.

This does look cool to rotate the desktop cube around, from ubuntu to XP!!!

Cheers

EDIT: concerning the ram, I did find my system was a little slow at times buy I only have 1G ram, giving half of that to XP.

---

### Post by howefield on 2008-10-04
It won't be sweet with 512 total ram. I wouldn't imagine.

I think it_will_work but not well.

On your machine with  2 gig, it'll run perfectly. Allocate 384 or even 512 to XP, as far as Ubuntu is concerned it will have 2 gig less the ram you give to the host whilst you are running the host.

---

### Post by heiowge on 2008-10-04
Cheers.  What should I set the ram to on the 512 machine?

---

### Post by howefield on 2008-10-04
I'd give XP the least it needs to run, 128 ? (max 192).

Bear in mind you can change this after the fact via virtualbox setings for your guest, so you are not stuck if you end up not giving it enough.

---

### Post by heiowge on 2008-10-08
Cheers.  I used 192 mb for XP in the end (although I'll probably up that to 512 on the 2Gb machine).  It seems to work fine.  I've not tried running anything major from it yet.  Will it install to the partition allocated for XP or to the Linux partitions or both?  Will these installs be persistant?  Lastly, when I saved the session, it failed to re-establish the mouse (right-ctrl or otherwise).  Is this common?  Is there an easy fix or am I better shutting down each time?

---

### Post by heiowge on 2008-10-12
bump

---

### Post by howefield on 2008-10-12
Sorry, don't understand the question, you start off saying it seems to work well, then go on to ask where it will install.

I'm confused as to what you are asking.

---

### Post by heiowge on 2008-10-13
I'll try and clarify and ask a few more while I'm at it. ;-)

It runs windows (although I had a little fun with the mouse).  If I try to install MS office 2003, will it install?  Where to (the XP partition or linux or other)?  Will the install still be there if I turn the PC off?  If not is there a way to make this happen?

I want to use uTorrent from windows (it used to work in Wine, but no more), can I make the destination within the 10Gb partition I designated to be used with Virtualbox?  Can I point it at another drive entirely?

Cheers

---

