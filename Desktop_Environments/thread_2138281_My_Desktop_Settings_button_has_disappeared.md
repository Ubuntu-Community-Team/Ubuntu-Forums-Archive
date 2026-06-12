---
title: "My Desktop Settings button has disappeared"
date: 2013-04-23
forum: Desktop Environments
---

### Post by blanka32 on 2013-04-23
So the other day [I tried out KDE]("http://ubuntuforums.org/showthread.php?t=2137006"), and it had fooled around with a few things I didn't like. I followed everyones guidance on how to get it back. This only worked to a certaint extent. I dont know how much is the same as it was before, because I haven't run through my whole system yet to see what little minute things have changed. One thing I have noticed that bugs me is that my desktop appearance button in the system settings has disappeared.
[ATTACH=CONFIG]241687[/ATTACH]

Not to sure where to go from here, or how to fix this. I can change my desktop background sometimes through the right-click menu on the desktop, but the menu is strange, and its different from before, and I can't change my 'desktop behavior' at all. 

Can somebody help me with this?

---

### Post by ibjsb4 on 2013-04-23
Are you talking about CCSM?

[https://apps.ubuntu.com/cat/applications/quantal/compizconfig-settings-manager/](https://apps.ubuntu.com/cat/applications/quantal/compizconfig-settings-manager/)

---

### Post by blanka32 on 2013-04-24
> **ibjsb4 said:**
> Are you talking about CCSM?

[https://apps.ubuntu.com/cat/applications/quantal/compizconfig-settings-manager/](https://apps.ubuntu.com/cat/applications/quantal/compizconfig-settings-manager/)

My mistake, the [appearance]("http://iloveubuntu.net/pictures_me/system%20settings%20q%20increased%20size%201.png") button is missing.

---

### Post by stinkeye on 2013-04-24
Check you have the package  **gnome-control-center-unity** installed.

I can bring it up by typing appearance in the dash or in the terminal, running...
```
gnome-control-center unity-appearance
```


You could run
```
sudo apt-get install [COLOR="#FF0000"]-s[/COLOR] ubuntu-desktop
```

The [COLOR="#FF0000"]-s[/COLOR] option will simulate the action without installing anything
and will show you what's missing from the Ubuntu desktop system.

---

### Post by blanka32 on 2013-04-25
> **stinkeye said:**
> 
The [COLOR=#FF0000]-s[/COLOR] option will simulate the action without installing anything
and will show you what's missing from the Ubuntu desktop system.

this is what i'm missing, even after the 'reinstall'

```

gnome-control-center unity-appearance

** (gnome-control-center:6551): WARNING **: Could not find settings panel "unity-appearance"

```

---

### Post by stinkeye on 2013-04-26
Did you run...
```
sudo apt-get install ubuntu-desktop
```

That should have installed **gnome-control-center-unity** and other missing packages.

---

### Post by blanka32 on 2013-04-26
> **stinkeye said:**
> Did you run...
```
sudo apt-get install ubuntu-desktop
```

That should have installed **gnome-control-center-unity** and other missing packages.

I have done tis a few times to no avail. I did it again and restarted just in case. Appearance is still missing :(

---

### Post by blanka32 on 2013-04-27
bump

---

### Post by Frogs Hair on 2013-04-27
Does "Change Desktop Background" appear in the context menu  when you right click on the desktop ? Make sure nautilus is set to handle the desktop if no menu appears. The setting is in the Gnome tweak tool. This should be installed but try anyway.```
 sudo apt-get install --reinstall gnome-control-center 
```

---

### Post by blanka32 on 2013-05-03
> **Frogs Hair said:**
> Does "Change Desktop Background" appear in the context menu  when you right click on the desktop ? Make sure nautilus is set to handle the desktop if no menu appears. The setting is in the Gnome tweak tool. This should be installed but try anyway.```
 sudo apt-get install --reinstall gnome-control-center 
```

It does appear but when i press it, it takes me straight to system settings. 

after reinstalling the gnome controller, do i have to restart to see results?

---

### Post by Frogs Hair on 2013-05-03
Yes , or the indicator may not appear.

---

### Post by blanka32 on 2013-05-06
*bump*

Indicator did not appear.

Im a little concerned.

---

### Post by Frogs Hair on 2013-05-06
There are two entries for the gnome control center on my installation  because I have the gnome shell as well as unity. Try the following and restart.
 
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall gnome-control-center-unity[/FONT][/COLOR]
```

---

### Post by blanka32 on 2013-05-24
I started this topic [over here]("http://ubuntuforums.org/showthread.php?t=2138281"). It all started when I installed KDE, and it changed everything about ubuntu. Icons, Startup. The most disturbing thing of all, my 
Desktop 'Appearance' button has completely disappeared. I followed all the instructions I was given in the other topic, and it fixed some issues, but not the main one. The appearance button is still missing. I cannot change my theme, I cannot edit my desktop behavior. The only way I can change my desktop background is through the right click menu on an image. I've been dealing with this issue for the past few weeks without addressing it, but I want my appearance setting back. Please help!

---

### Post by Bucky Ball on 2013-05-24
@ blanka32: Your other post has been merged with this one then deleted on second thoughts. Please do not post duplicate threads. The deleted one was practically the same as this. By posting a duplicate in another sub-forum you are not increasing your chances of getting help but the opposite as its confusing and dilutes community effort. If you are not getting a response on this thread, rather than posting duplicates, bump the thread. Once every twenty four hours is fine. You might like to update this thread and see who joins in. I've bumped it for you with this post anyhow. 

You already have a bunch of helpers trying to help you here. Stick with it. Good luck.

---

### Post by blanka32 on 2013-05-26
*Bump

Appearance button and settings menu is still missing. 
I have tried all of the above and nothing has worked.
Does anyone know any other way I can retrieve my settings.
I cannot change my desktop behavior or theme at all. 
I can only change my desktop background by right clicking on an image. 
Please help.

---

### Post by blanka32 on 2013-05-28
*bump

---

### Post by blanka32 on 2013-05-30
*bump

---

### Post by blanka32 on 2013-06-04
*bump

Guys, I really need this fixed.

Who do I go to if no one here can help me?

---

### Post by stinkeye on 2013-06-04
> **blanka32 said:**
> *bump

Guys, I really need this fixed.

Who do I go to if no one here can help me?
Is doing a reinstall an option?
May be the easiest solution if nothing suggested so far has worked.

---

### Post by blanka32 on 2013-06-05
> **stinkeye said:**
> Is doing a reinstall an option?
May be the easiest solution if nothing suggested so far has worked.

No, I do not have the capabilities for backing up all my data.

---

### Post by stinkeye on 2013-06-05
So **gnome-control-center-unity** is installed.
```
apt-cache policy gnome-control-center-unity
```

> [COLOR="#008000"]glen@Raring:~$[/COLOR] **apt-cache policy gnome-control-center-unity**
gnome-control-center-unity:
  Installed: 1.2daily13.04.09-0ubuntu1
  Candidate: 1.2daily13.04.09-0ubuntu1
  Version table:
 *** 1.2daily13.04.09-0ubuntu1 0
        500 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by blanka32 on 2013-06-12
> **stinkeye said:**
> So **gnome-control-center-unity** is installed.
```
apt-cache policy gnome-control-center-unity
```


```
travmagi@travmagi-Lemur-Ultra:~$ sudo apt-get install ubuntu-desktop[sudo] password for travmagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following package was automatically installed and is no longer required:
  steam:i386
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
travmagi@travmagi-Lemur-Ultra:~$ apt-cache policy gnome-control-center-unity
gnome-control-center-unity:
  Installed: (none)
  Candidate: 1.0-0ubuntu1~ubuntu12.10.1
  Version table:
     1.0-0ubuntu1~ubuntu12.10.1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ quantal/main amd64 Packages



```

The code you asked me to run is not installing gnome controller.

---

### Post by stinkeye on 2013-06-12
> **blanka32 said:**
> ```
travmagi@travmagi-Lemur-Ultra:~$ sudo apt-get install ubuntu-desktop[sudo] password for travmagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following package was automatically installed and is no longer required:
  steam:i386
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
travmagi@travmagi-Lemur-Ultra:~$ apt-cache policy gnome-control-center-unity
gnome-control-center-unity:
  Installed: (none)
  Candidate: 1.0-0ubuntu1~ubuntu12.10.1
  Version table:
     1.0-0ubuntu1~ubuntu12.10.1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ quantal/main amd64 Packages



```

The code you asked me to run is not installing gnome controller.

The command was to see if gnome-control-center-unity was installed,
and shows it isn't.
The command to install was given in an earlier post but not sure if you ran it. 
```
sudo apt-get install gnome-control-center-unity
```

---

