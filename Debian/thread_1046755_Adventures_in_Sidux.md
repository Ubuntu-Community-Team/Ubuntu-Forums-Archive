---
title: "Adventures in Sidux"
date: 2009-01-21
forum: Debian
---

### Post by oldos2er on 2009-01-21
I burned a LiveCD of sidux-2008-04-pontos-xfce-amd64-200812230009.iso, booted from it, ran md5sum check (all good), and quickly--I mean, FAST, this was no doubt the fastest-booting LiveCD I've ever seen, and I've tried quite a few--the xfce desktop is up and running, ready to go. Sweet. Fire up the web browser, tried [www.google.com]("http://www.google.com"), oops, it appears there's no network (I have broadband wired ethernet). Try a few different sites with the same result. ifconfig only shows 'lo', no 'eth0' as there should be. That's ok, I think, I'll go ahead and install sidux on /dev/sda1, and worry about the network later.

 Installer is very nice; it's easy to move back a tab or two if you overlooked something. Set the partitioner to install / to /dev/sda1 , then comes Grub config. Let me just say that I use /dev/sda1 as a sandbox to install various Linux flavors as the mood strikes me. I never allow them to install Grub or lilo, instead manually editing /boot/grub/menu.lst on my Ubuntu partition (/dev/sdb5) to whatever it needs to be. 

 But I can't seem to get past the Grub screen. There doesn't appear to be an option to install sidux without a bootloader, at least that I can find. Boot Ubuntu, google "install sidux without grub," but I can't find any info. Try a few other searches, but no joy. I'm disappointed. I don't think I've ever seen this option NOT available.

 Sidux is SO fast to run, even from a LiveCD, that I'm tempted to install it anyway and allow its Grub to do whatever it needs, and hope that I can figure out the network failure later (I can't recall a LiveCD distro that hasn't seen my network). Yes, I know I can confine Grub to /dev/sda1 and chainload it, but I'm old and stuck in my ways.

 It's so freaking FAST!

---

### Post by SomeGuyDude on 2009-01-21
I'm noticing a huge bump in Sidux's popularity lately. If you decide to install it, update the thread. It's an interesting distro, definitely one I've been periodically peeping.

---

### Post by oldos2er on 2009-01-21
I'm downloading the kde-lite-amd64 version now, to see how it works out.

---

### Post by RedSquirrel on 2009-01-21
> **oldos2er said:**
>  ... Yes, I know I can confine Grub to /dev/sda1 and chainload it, but I'm old and stuck in my ways.

I was about to suggest chainloading. I'm glad I read right to the end of your post! :)

Just out of curiosity, do you have any USB storage devices? Any trouble accesssing those from the sidux LiveCD? I recently tried out the [sysresccd]("http://www.sysresccd.org/") and it's quite good, but it didn't like my USB stick for whatever reason.

It's interesting that after months of little-to-no comments about sidux, we see two threads about [sidux]("http://ubuntuforums.org/showthread.php?t=1046425") in a matter of hours. :D

---

### Post by zmjjmz on 2009-01-21
I use sidux on my old Gateway (256MB RAM, 700MHz PIII). Even with Xfce it flies.
I can only imagine how fast it would be on a modern computer.

---

### Post by Sorivenul on 2009-01-21
It's been almost a month?!? How did I miss this latest sidux release?

Time to go download. :D

---

### Post by oldos2er on 2009-01-22
"do you have any USB storage devices?"

 I'll try one out tomorrow.

---

### Post by Frak on 2009-01-22
I've always been a sucker for Sidux. It has to be one of the fastest, bleeding edge distros I've used that was also easy to setup.

---

### Post by snowpine on 2009-01-23
Networking in Sidux is handled by a very slick little application called Ceni (invoke it from the command line or from the Network applications menu). It does not auto-connect in the live CD as far as I know. 

Once installed, you can use a different network manager if you like. 

I don't know anything about the Grub issue, sorry.

---

### Post by oldos2er on 2009-01-23
> **snowpine said:**
> Networking in Sidux is handled by a very slick little application called Ceni (invoke it from the command line or from the Network applications menu). It does not auto-connect in the live CD as far as I know. 

Once installed, you can use a different network manager if you like. 

I don't know anything about the Grub issue, sorry.

 Ah, thank you for that.

 I tried the 'kde-lite' version; it wasn't quite as fast as the xfce one, but still snappy. Sorry I haven't checked out the USB issue yet.

---

### Post by RedSquirrel on 2009-01-23
> **oldos2er said:**
> Sorry I haven't checked out the USB issue yet.

No worries. I will be patient. :)

The sysresccd is the only LiveCD I've encountered that had a problem with my USB stick, so I just thought I'd ask about the sidux one... ;)

---

### Post by oldos2er on 2009-01-24
Ok, I just booted the xfce LiveCD again, and sidux recognized every USB device I tried. Aside from mouse and keyboard, that includes printer connection, 4GB flash drive, and ARTcessories analog-to-digital audio converter.

---

### Post by RedSquirrel on 2009-01-25
> **oldos2er said:**
> Ok, I just booted the xfce LiveCD again, and sidux recognized every USB device I tried. Aside from mouse and keyboard, that includes printer connection, 4GB flash drive, and ARTcessories analog-to-digital audio converter.
Thanks for the info.

---

### Post by Vorian Grey on 2009-01-26
> **Frak said:**
> It has to be one of the fastest, bleeding edge distros I've used that was also easy to setup.
I love sidux but it's not bleeding edge at the moment, with Sid being froze for Lenny and all. I'm ready for it to be bleeding edge again!

---

### Post by snowpine on 2009-01-26
I just last night installed this very slick (but "unofficial") Sidux+LXDE remix that includes asus eee pc support!

[http://www.cap.gediam.de/index-en.htm](http://www.cap.gediam.de/index-en.htm)

---

### Post by Frak on 2009-01-26
> **Vorian Grey said:**
> I love sidux but it's not bleeding edge at the moment, with Sid being froze for Lenny and all. I'm ready for it to be bleeding edge again!
Sid is, and will always be, the unstable branch. Lenny is the next release of Debian. Lenny's packages were derrived from the Sid branch around a year ago.

---

### Post by snowpine on 2009-01-26
> **Frak said:**
> Sid is, and will always be, the unstable branch. Lenny is the next release of Debian. Lenny's packages were derrived from the Sid branch around a year ago.

Right, but Sid is semi-frozen until Lenny is released. In other words, Sid is as stable as it gets right now. My understanding is once Lenny is released as stable, Sid will get really exciting. :)

---

### Post by lex1 on 2009-02-03
Sidux does rock and yes its super fast tried it a few times if you go to there web site and loginto the cgi chat they are really helpful. 

I think if you look in the forum one developer has 
developed a sidux for a usb stick.

lex1:popcorn:

---

### Post by Vince4Amy on 2009-02-04
Downloading the KDE-Lite-AMD64 ISO now, I'll try it when I'm home from school.

---

### Post by RJARRRPCGP on 2009-02-14
Your problem with no internet access is a bad sign. 

It's likely that your motherboard is too new. 

I ran into this problem with the Asus P5QL Pro motherboard.

Thus, beware, especially with the Asus P5Q series.

---

