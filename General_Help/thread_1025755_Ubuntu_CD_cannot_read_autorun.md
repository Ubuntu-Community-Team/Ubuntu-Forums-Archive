---
title: "Ubuntu CD cannot read autorun"
date: 2008-12-30
forum: General Help
---

### Post by Tsukino Kyuuketsuki on 2008-12-30
I upgraded to ubuntu 8.10 but it got stuck at some point and had to restart everything, just a few things were missing (windows decoration and such) but I could live without it.

I finally decided to back up all my stuff and try to fix the whole thing, but when I tried to reinstall ubuntu, it says it cannot read autorun... so I thought something was wrong with the cd, I got another one and same problem... I even tried with my 8.04 cds that worked perfectly last time I used and says exactly the same.

I really don't know what is the problem, I'm still kinda new to ubuntu and it gets frustrating sometimes but the forums have been really useful. Any help it's much appreciated!!

---

### Post by kelean on 2008-12-30
Does the CD start at all?  If it does then if you are going to reinstall it is sometimes helpfull to delete the previous Ubuntu partition.  I have had similar problems trying to reinstall Ubuntu.  I hope that helps, Kelean

---

### Post by namdung on 2008-12-30
How did u upgrade, was it using an Alternate CD?

So have u now upgraded to Intrepid? Post output of ```
lsb_release -a

```

Also try in terminal
```
sudo apt-get update
```

If any error msg, type
```
sudo dpkg --configure -a
```

In *System-->Admin-->Software Sources*, is *Installable from CD/DVD ROM* showing? Also is *Release Update-->Normal Releases* showing in *Updates* tab?

I recommend stable Hardy Heron LTS, 8.04.2 which is out on 1/1/2009.

---

### Post by Tsukino Kyuuketsuki on 2008-12-30
Thanks for the quick response. The cd doesn't start at all, as soon as the tray closes it says "Error autorunning software, cannot find autorun program". The cd does appear in my desktop and I can even open it and see the files, but won't let me install ubuntu.

Outputs:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Reading package lists... Done

I can see the cd in System-->Admin-->Software Sources, but it won't let me use it. I wanted to go back to Hardy Heron since it was working just perfect before the upgrade but I'm having the same problem with the cd for 8.04, I already have back up for everything so I don't mind if I have to reinstall everything from scratch.

Thanks for all your help!!

---

### Post by Tsukino Kyuuketsuki on 2008-12-30
Oh yeah, I forgot to mention, I upgraded from 8.04 to 8.10 using the update manager but at some point when it was almost done the whole system got stuck and I had to restart the computer, when I restarted I had Intrepid installed and everything looked fine, even though I was missing some details and configuration I was able to fix and some other stuff I couldn't but didn't bother me. I got the cd for 8.10 a few days ago and that's when I noticed the autorun problem. It says the same for all the ubuntu cds I have and they were working before.

---

### Post by namdung on 2008-12-30
U already have Intrepid installed. I reckon ur able to install software so update ur system from *System-->Admin-->Update Manger*. This should bring ur system with the latest patches and updates.

Do u have WINE installed?

This seems to be a bug with the autorun:[https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/205414](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/205414)

And there is a patch if u want to try: [https://wiki.ubuntu.com/autorun](https://wiki.ubuntu.com/autorun)

Good luck!!!

---

### Post by Tsukino Kyuuketsuki on 2008-12-30
I have wine but I just got a little bit lost... why would I need wine to run the ubuntu cd installation? I thought that was to emulate windows stuff. :confused:

---

