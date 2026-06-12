---
title: "ubuntu vs lulubuntu vs xubuntu"
date: 2011-06-22
forum: Desktop Environments
---

### Post by Azyx on 2011-06-22
Hi.

First, is there a difference in xubuntu and lubuntu on older computers?

I have some old computers (600MHz 750MB ram iMac and 900MHz 1GB ram eeePC) and I have tested different desktops (ubuntu and lubuntu) on the same partition and don't seing any big difference in performance. I have then read that if u should see any difference, you need to make a pure installation (not only sudo apt-get install lulubuntu-desktop and ubuntu-desktop) and the let gdm choose the desktop-environment. My problem are that I dont have so much ssd-diskspace and wonder if I can have two different /-partition (one with ubuntu and one with lubuntu and have grub2 to choose, but have a common home-folder and still have the performans benefits with lubuntu (or xubuntu)? As I understand there are some scripts in lubuntu in the home folder, that affect the desktop?

I want to have booth ubuntu and xubuntu or xubuntu cos I am old and a slow learner in new desktop-environment that xubuntu and lubuntu are for me.

Any tips or suggestions are welkomed

/Cheers.

---

### Post by sanderd17 on 2011-06-22
Lubuntu is lighter than Xubuntu, but with 1 GB ram and an ssd, it's quite normal to see not much difference between lubuntu, xubuntu and ubuntu.

A common /home directory is certainly possible, but sometimes it could mess up your theme settings. Just google for installing ubuntu with a separate /home partition, and use the same partition for both installs.

---

### Post by snowpine on 2011-06-22
Hi Azyx, Ubuntu/Lubuntu/Xubuntu/Kubuntu are the same "core" system with different "desktop environments" and different suites of preinstalled applications.

You can install as many desktop environments as you like and choose between them from the login screen. The only disadvantage to this is that your application menus will get cluttered.

Dual booting Ubuntu and Lubuntu is a waste of hard drive space because you are duplicating the core system.

If Ubuntu runs fine for you then stick with it, that's my opinion. :)

ps If you are already running Ubuntu then you might choose to simply install "lxde" instead of "lubuntu-desktop".

---

### Post by Azyx on 2011-06-22
> **sanderd17 said:**
> Lubuntu is lighter than Xubuntu, but with 1 GB ram and an ssd, it's quite normal to see not much difference between lubuntu, xubuntu and ubuntu.

A common /home directory is certainly possible, but sometimes it could mess up your theme settings. Just google for installing ubuntu with a separate /home partition, and use the same partition for both installs.

Thanx for a quick reply. I made a pure install of lubuntu on my iMac and there I saw a performance differens. The problem are that it's quite complicated to install on old ppc mac  and it takes time (compared to x86), so there are a difference with pure installs, probably cos a lot of small applications/services are different, but if you install booth desktop a lot of same application/services are installed, I think. Or?

The SSD on eeePC 900 are slower than an HDD.

cheers

---

### Post by Azyx on 2011-06-22
> **snowpine said:**
> Hi Azyx, Ubuntu/Lubuntu/Xubuntu/Kubuntu are the same "core" system with different "desktop environments" and different suites of preinstalled applications.

You can install as many desktop environments as you like and choose between them from the login screen. The only disadvantage to this is that your application menus will get cluttered.

Dual booting Ubuntu and Lubuntu is a waste of hard drive space because you are duplicating the core system.

If Ubuntu runs fine for you then stick with it, that's my opinion. :)

ps If you are already running Ubuntu then you might choose to simply install "lxde" instead of "lubuntu-desktop".

Thanx. snowpine. Yes, it worked as I suspected that a lot of application get installed, but that also steal RAM and probably cpu. I know i may tweak firefox to not write to ssd, and that is one of the problems....

One more thing to try another desktop is that I don't know for how long Ubuntu support classic desktop, so there are other reason to try lubuntu.

/cheers.

---

### Post by snowpine on 2011-06-22
> **Azyx said:**
> Thanx. snowpine. Yes, it worked as I suspected that a lot of application get installed, but that also steal RAM and probably cpu. I know i may tweak firefox to not write to ssd, and that is one of the problems....

One more thing to try another desktop is that I don't know for how long Ubuntu support classic desktop, so there are other reason to try lubuntu.

/cheers.

Applications only "steal" RAM if you use them. If they are sitting unused on your hard drive, then there is no performance penalty.

---

### Post by Azyx on 2011-06-22
> **snowpine said:**
> Applications only "steal" RAM if you use them. If they are sitting unused on your hard drive, then there is no performance penalty.

But services like networkmanager and so on.. Anyway I notice a differance on my iMac 400MHz (i said wrong cpu-speed before, my 600/500 have burned up.

Anyway, I think I gonna test and see if I notice a differens between ubuntu-live  and lubuntu-live on my eeePC. iMac have also only 100MHz RAM-speed.

---

### Post by snowpine on 2011-06-22
> **Azyx said:**
> But services like networkmanager and so on.. 

Lubuntu uses the same network manager service as Ubuntu.

---

### Post by snowpine on 2011-06-22
If you want to convert your Ubuntu install to "pure" LXDE you can follow this guide:

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by EdwardR on 2011-06-22
As mentioned earlier, sharing a home partition can cause issues with cluttered menus and desktop shortcuts that work in one desktop environment and not the other and other "leakage" between distributions.  What I have started doing is to install each distribution separately; create a new partition with directories for shared documents, music, pictures, videos etc.; then boot into each distribution and delete the Documents, Music, Pictures, and Videos directories and replace them with links to the shared directories.  That way, the configuration files that are found in /home/yourname and the programs are segregated to their respective distributions, and the Documents, Music etc folders appear just as they did before, except that now they are shared.

---

### Post by Azyx on 2011-06-22
> **snowpine said:**
> Lubuntu uses the same network manager service as Ubuntu.

ok. but i toke it as an example. that services my differ, what I know is that lubuntu don't use puls-audio. I havet studied it in detail,  and i don't want to do that, But someting differ in speed between ubuntu and lubuntu on my iMac. but there are maybee different bottlenecks on eeepc and an old imac.

---

### Post by Azyx on 2011-06-22
> **snowpine said:**
> If you want to convert your Ubuntu install to "pure" LXDE you can follow this guide:

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

Thanx. Will take this in considiration :)

---

### Post by Azyx on 2011-06-23
> **EdwardR said:**
> As mentioned earlier, sharing a home partition can cause issues with cluttered menus ........except that now they are shared.

Thanx EdwardR, Seems to be a way.

---

