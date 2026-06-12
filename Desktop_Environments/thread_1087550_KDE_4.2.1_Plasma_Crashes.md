---
title: "KDE 4.2.1 Plasma Crashes"
date: 2009-03-05
forum: Desktop Environments
---

### Post by coutts99 on 2009-03-05
Upgraded to KDE 4.2.1 this morning and now plasma always crashes.

Anyone else experiencing the same?

---

### Post by Bekker on 2009-03-05
Same here, plasma workspace crashes on startup after update. The packages that got upgraded were probably from the following repositories:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main

I tried removing ~/.kde as was suggested for the same sort of problem a while ago but it didn't help.

---

### Post by coutts99 on 2009-03-05
I've downgraded plasma to 4.2.0 for now and it's working fine again.

I logged a bug with kde (bug no 186197) but not sure if my backtrace is any good.

---

### Post by coutts99 on 2009-03-05
plasma 4.2.0 deb is here -:

[http://launchpadlibrarian.net/22926578/kdebase-plasma_4.2.0-0ubuntu1%7Eintrepid1_i386.deb]("http://launchpadlibrarian.net/22926578/kdebase-plasma_4.2.0-0ubuntu1%7Eintrepid1_i386.deb")

If anyone needs it.

---

### Post by Bekker on 2009-03-05
Didn't do it for me :( Gotta go now anyway, hopefully another upgrade will be ready when I get back.

---

### Post by cnb2412 on 2009-03-05
The same applies for me. After upgrading to Kde 4.2.1 plasma crashes. I've tried the downgrade but this didn't fix it.

---

### Post by Skripka on 2009-03-05
Curiousity question-what version of Qt are you all using?  Considering Plasma is tested against Qt4.5...and Ubuntu doesn't stay anywhere near that up-to-date....this may not be KDE's problem necessarily.

---

### Post by coutts99 on 2009-03-05
Yeah mine stopped working after I restarted my computer.

I've installed the neon nightly packages and am back up and running.

> deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

apt-get install kde-nightly

---

### Post by coutts99 on 2009-03-05
> **Skripka said:**
> Curiousity question-what version of Qt are you all using?  Considering Plasma is tested against Qt4.5...and Ubuntu doesn't stay anywhere near that up-to-date....this may not be KDE's problem necessarily.

4.4.3-0ubuntu1.2

---

### Post by coutts99 on 2009-03-05
> **Skripka said:**
> Curiousity question-what version of Qt are you all using?  Considering Plasma is tested against Qt4.5...and Ubuntu doesn't stay anywhere near that up-to-date....this may not be KDE's problem necessarily.

Upgraded to jaunty which obviously does have Qt4.5, and I have the same issue.

Neon nightly build packages are working fine though

---

### Post by Skripka on 2009-03-05
> **coutts99 said:**
> Upgraded to jaunty which obviously does have Qt4.5, and I have the same issue.

Neon nightly build packages are working fine though

Odds are-Jaunty and Intrepid are using the roughly the same packages....so if one is b0rked the other is too.


4.2.1 works slicker than snot here on Arch-which of course isn't much help for ye on Ubuntu.

Do you have a crash trace for this, and have you reported it to Kubuntu?  It definitely smells like an Ubuntu problem, but without a crash log it is impossible to say.

---

### Post by Blue Duck on 2009-03-06
I get the same crashes since I've upgraded to KDE 4.2.1.

If it can help, I still can use my desktop remotely with NX-Server: the desktop and all its stuff display as usual.

---

### Post by coutts99 on 2009-03-06
I spoke to soon, I'm working fine this morning on Jaunty with Qt4.5

Can anyone provide a backtrace for my reported bug please? You will need to install "kdelibs5-dbg" and "kdebase-workspace-dbg"

---

### Post by Country908 on 2009-03-06
Solution-worked for me in 8.10.Had same problem,so I held back the 5 kdebase-workspace pk.Upgradeded 1 at a time and rebooted each time.SUCCESS

---

### Post by Blue Duck on 2009-03-06
> **coutts99 said:**
> Can anyone provide a backtrace for my reported bug please? You will need to install "kdelibs5-dbg" and "kdebase-workspace-dbg"

Yes, of course, if I were sure of what it means (sorry for my poor English)... What should I do once this packages installed?

---

### Post by Technowizard on 2009-03-10
Look at:

[http://kubuntuforums.net/forums/index.php?topic=3102117.15](http://kubuntuforums.net/forums/index.php?topic=3102117.15)

releated to:

[http://bugs.kde.org/show_bug.cgi?id=186197](http://bugs.kde.org/show_bug.cgi?id=186197)

---

### Post by toallpointswest on 2009-03-10
This worked!

---

### Post by utkjamie on 2009-03-13
> **toallpointswest said:**
> This worked!

What worked?

---

### Post by static0verdrive on 2009-03-14
**sudo rm /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/plasma-appletsrc** worked for me...

---

### Post by utkjamie on 2009-03-15
> **static0verdrive said:**
> **sudo rm /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/plasma-appletsrc** worked for me...

I tried that along with deleting the plasma-appletsrc and plasmarc files from the ~/.kde/share/config directory. It worked after the first reboot but the problem continues after rebooting again.

I'm running KDE 4.2.1 without a problem on my laptop, but for whatever reason my roommate's computer is really suffering the wrath of 4.2.1.

---

### Post by coutts99 on 2009-03-16
Bug seems to have been fixed in latest batch of updates.

---

### Post by txcrackers on 2009-03-17
I've had some widgets actually crash plasma*, so that's where I would actually start.

*Including a somewhat simple one that **I** wrote. Ooops! :p

---

### Post by brel on 2010-03-20
My plasma was crashing as well. I still had my applications and they worked alright but everything else was black. It started after an update.

Deleting the file worked for me as well.

---

