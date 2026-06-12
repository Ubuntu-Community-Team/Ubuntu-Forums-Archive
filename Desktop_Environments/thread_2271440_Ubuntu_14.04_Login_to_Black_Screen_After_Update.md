---
title: "Ubuntu 14.04 Login to Black Screen After Update"
date: 2015-03-30
forum: Desktop Environments
---

### Post by airilsra on 2015-03-30
I ran update yesterday after reboot i can go to login screen (lightdm). But after login I only see mouse cursor and black screen.

I figure it is gpu driver problem. My computer using onboard Nvidia GeForce 6100 nForce 405, so it's legacy driver for me. I had been using nvidia-304 driver with no problem until yesterdays update.

I tried remove nvidia driver and reboot. I then could boot to desktop but with low resolution. I ran **inxi -b** with these results on graphic card section:
```
X.org: 1.15.1 Drivers: fbdev (unloaded: vesa) FAILED:nouveau.
```

From desktop i opened Additional Driver and reinstalled nvidia-304. Then the same problem as before occurred, I only see a cursor over a black screen. This is **inxi -b **output with nvidia-304
```
Drivers: nvidia (unloaded:fbdev, vesa, nouveau)
```

What should I do to fix this? Help please...

---

### Post by CantankRus on 2015-03-30
See if you can login into a session not using compiz.
Install **gnome-session-flashback**...
At the greeter hit ctrl+alt+F1
Login and then run...
```
sudo apt-get install gnome-session-flashback
```
Once installed type "exit" and press Enter.

Switch back to the greeter ... ctrl+alt+F7
You should now have 2 new session entries when you click on the cog icon.(may have to restart)
[LIST]
[*]Gnome Flashback (metacity)
[*]Gnome Flashback (compiz)
[/LIST]
Login into the metacity session and see if the nvidia driver is working.

---

### Post by airilsra on 2015-03-30
Hi CantankRus,
 
Yes, it works with Gnome Flashback (metacity)! But doesn't work with Gnome Flashback (compiz).

So, the problem is with compiz?
I have tried to reset compiz with **dconf** and then with **setsid unity**, but no luck.
I also tried to install an run **unity-reset** package, it doesn't works.
Then I removed .compiz folder with hope that it will make new config but still the same, a cursor over a black screen.

---

### Post by CantankRus on 2015-03-30
Does inxi show the nvidia driver being used when in the "Gnome Flashback (metacity)" session?

If you can login to the ubuntu/unity session from the guest account and the unity interface shows
we can set dconf settings back to default.

This must be done when not logged in to a normal session.
So if logged in, logout to the greeter.

From the greeter hit ctrl+alt+F1 and login.
Run...
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```
Then type exit and hit Enter.

Press ctrl+alt+F7 which will take you back to the greeter.
Log in to your account in the Ubuntu session and if it worked 
you should see the unity panel and launcher as in a fresh install.
Check inxi.

---

### Post by airilsra on 2015-03-30
Inxi tells nvidia is being used:
```
System:    Host: Ubu Kernel: 3.13.0-48-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: N/A model: NF-MCP61 Bios: Phoenix version: 6.00 PG date: 05/23/2008
CPU:       Dual core AMD Athlon 64 X2 4000+ (-MCP-) clocked at 2100.00 MHz 
Graphics:  Card: NVIDIA C61 [GeForce 6100 nForce 405] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1360x768@60.0hz 
           GLX Renderer: GeForce 6100 nForce 405/integrated/SSE2 GLX Version: 2.1.2 NVIDIA 304.125
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth 
Drives:    HDD Total Size: 1500.3GB (71.3% used)
Info:      Processes: 187 Uptime: 1 min Memory: 430.2/1874.8MB Client: Shell (bash) inxi: 1.9.17
```

I created a new user to test, but still can't login to unity from said account. I tried above command anyway, still can't login to unity.

---

### Post by CantankRus on 2015-03-30
What happens when you log into the guest account?

---

### Post by CantankRus on 2015-03-30
Try purging nvidia drivers and reinstalling.
```
sudo apt-get purge nvidia*
```
Reboot to the nouveau driver and then run ...
```
sudo apt-get install nvidia-304 nvidia-settings
```
Reboot.

---

### Post by airilsra on 2015-03-31
I've tried to purge and reinstall both nvidia-current (304) and nvidia-current-updates (304/proprietary) but the results were still the same.
I remember the last update I installed had update for unity.

I installed gnome-shell and it works.

---

### Post by CantankRus on 2015-03-31
> **airilsra said:**
> I've tried to purge and reinstall both nvidia-current (304) and nvidia-current-updates (304/proprietary) but the results were still the same.
I remember the last update I installed had update for unity.

I installed gnome-shell and it works.
Yeah I don't really know then.
I have a different gfx card that can use the latest nvidia driver although I'm running the 304 driver at the moment to test.
Only other thing I can see different is I am using a later kernel and X.Org: 1.16.0 because I followed this [**_[COLOR="#B22222"]GUIDE[/COLOR]_**]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") to install the newer kernel from 14.10 (Utopic).
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 2.1.2 NVIDIA 304.125
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1254.2GB (13.0% used)
Info:      Processes: 252 Uptime: 5:28 Memory: 1835.8/3934.9MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by airilsra on 2015-03-31
I will install newer kernel and/or reinstall ubuntu-desktop and unity. I will report the result later.

---

### Post by airilsra on 2015-03-31
Apparently reinstalling unity is not helping (**sudo apt-get install --reinstall unity**).

I have unmet dependencies while installing LTS Enablement Stack Kernel.
```
airil@Ubu:~$ sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 account-plugin-facebook : Depends: libaccount-plugin-generic-oauth but it is not going to be installed or
                                    ubuntu-system-settings-online-accounts but it is not going to be installed
 account-plugin-google : Depends: libaccount-plugin-google but it is not going to be installed or
                                  ubuntu-system-settings-online-accounts but it is not going to be installed
 libqt5gui5 : Depends: libgbm1 (>= 8.1~0) but it is not going to be installed
 libqt5multimedia5-plugins : Depends: libqgsttools-p1 (>= 5.2.1-0ubuntu5) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by CantankRus on 2015-04-01
Try these commands and report errors...
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get [COLOR="#FF8C00"]**dist-upgrade**[/COLOR]
```
From **man apt-get**
> [COLOR="#FF8C00"]**dist-upgrade**[/COLOR]
dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; 
apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. 
The dist-upgrade command may therefore remove some packages.


Are you using or have you used any third party ppa's or enabled the Ubuntu proposed ppa?
[ATTACH=CONFIG]261014[/ATTACH]

This will show all **currently enabled** ppa's...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

This will show all **disabled and enabled** third party ppa's....
```
find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
```

---

### Post by airilsra on 2015-04-01
There are no errors with those first commands and everything is updated.

I have never enabled Ubuntu Proposed repo but yes I have xorg-edgers ppa enabled yesterday to see if it would helps.
I reverted to default repository packages with ppa-purge and now I can update to LTS Enablement kernel. Doesn't install the packages yet since I don't have internet connection for updating right now. Will post the result later.

---

### Post by airilsra on 2015-04-02
The new kernel is installed,
```
$ uname -a
Linux Ubu 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
but still doesn't help with the problem. In the last page I said I had unity package update before the error, but now I remember it was actually compiz.

It is shame how can this kind of problem can happen in an LTS release. 
Anyway, thanks for your help Glen, it has been really helpful to sort what was the problem.

---

### Post by CantankRus on 2015-04-02
Unity is a plugin for compiz so often updated at same time.

In this situation it is often easiest to backup and and do a complete Ubuntu re-install.
Quite often a problem relates too something users have done while customizing or trying to fix a minor problem.
I've seen people remove compiz which removes unity because unity depends on compiz.
Then they reinstall compiz but this doesn't pull in unity as a dependency.
Not saying any of this has has occurred here, but a re-install can often fix the issue within half an hour versus days of trouble shooting.
At the least, you get a definitive answer.

---

### Post by airilsra on 2015-04-02
I don't remember tinkering with compiz settings (I don't have ccsm installed) and only change basic behaviors and looks of unity.
I am going to use gnome-shell for now and see if future updates will fix my problem.

---

