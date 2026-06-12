---
title: "Need help with Unity on 11.04 with Nvidia card."
date: 2011-04-29
forum: Desktop Environments
---

### Post by Ron Jones on 2011-04-29
Last night, I upgraded from 10.10 to 11.04 using the 'System > Administration > Update Manager' utility.

All seemed to go according to plan. No unusual freezes, etc. However, I cannot for the life of me seem to get Unity to work. Ubuntu Classic works fine... and Yes, I know that there are some who seem to hate Unity... but *I want to use Unity* in order to give it a fair shake. 

My troubleshooting steps so far include the following:

Checking 'cat /etc/lsb-release' to make sure I didn't download a Beta version by mistake. Output is shown below.
```

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

Okay... then I checked /usr/lib/nux/unity_support_test -p to make sure my NVIDIA card could support Unity. Output is shown below.
```

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 240/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

In the 'System > Administration > Additional Drivers' utility, I enabled the NVIDIA accelerated graphics driver (version current). 

Oddly (and I don't know if this is relevant), the message at the bottom of the dialog box says "This driver is activated but not currently in use," even though it's active and working (as evidenced by the fact that the "System > Administration > Nvidia Server Settings" utility is active and working. 

In the 'System > Preferences > CompizConfig Settings Manager' utility, I have checked the box that says "Ubuntu Unity Plugin."

And finally, I have followed the troubleshooting guide found at [http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html").

Yet with all this, I still cannot seem to get the Unity desktop up and running.

Can anyone recommend a good troubleshooting guide, or a reference that will help me figure this out?

Thanks,

---

### Post by strangedata on 2011-04-29
Hi!

Take a look here:
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

---

### Post by Ron Jones on 2011-04-29
Thanks! 

I'll have a look at that thread.

---

### Post by Krytarik on 2011-04-29
What happens when you try to log in to "Ubuntu" (thus Unity)?

---

### Post by Ron Jones on 2011-04-30
> **Krytarik said:**
> What happens when you try to log in to "Ubuntu" (thus Unity)?

Just now, I logged out of Ubuntu "classic" and chose Ubuntu (thus Unity). As the background music played, and my desktop came up... I thought I saw the left-hand panel. But in the twinkling of an eye, it was gone, so I'm not sure.

But now, I'm looking at a desktop with no panel, no menus, no nothing... just a desktop populated with the icons of files I have saved over the months.

Regards,

---

### Post by Ron Jones on 2011-04-30
A follow up... whereas before now, when I logged in to the Unity desktop, any file I opened was stuck in the top-left corner of the page, with no frame (and thus, no themeing)... Now, the Chromium browser I've opened up to check this thread, can be grabbed with a mouse click and dragged around the desktop.

---

### Post by Krytarik on 2011-04-30
Ok, you say you checked the settings in CCSM before by following the mentioned guide, and "Ubuntu Unity Plugin" is enabled there?

When you are in Unity and don't have the launcher/panel, check if Compiz is running:
- create a launcher at the desktop for the command "gnome-terminal", if you don't have one already
- launch it and enter:
```
ps ax |grep -v grep |grep compiz
```As for the window decorations, please see this thread (Chromium doesn't use the system's window decoration by default):
[http://ubuntuforums.org/showthread.php?t=1743724](http://ubuntuforums.org/showthread.php?t=1743724)

---

### Post by Ron Jones on 2011-04-30
> **Krytarik said:**
> create a launcher at the desktop for the command "gnome-terminal"
- launch it and enter:
```
ps ax |grep -v grep |grep compiz
```

I've been searching for how to make a terminal launcher :redface:

Output for above is as follows:

```

ron@desk2:~$ ps ax | grep -v grep | grep compiz
2836 ? Ss 0:00 /bin/sh -c /usr/bin/compiz-decorator

```

ADDITIONALLY....I don't know if it's relevant, but per your post here [http://ubuntuforums.org/showthread.php?p=10742307](http://ubuntuforums.org/showthread.php?p=10742307) 

I set up another launcher and opened the Gnome Configuration editor. Within Apps, I have only two compiz folders.
/apps/compiz, which contains the following subfolders:
```

/apps/compiz/general
/apps/compiz/general/allscreens
/apps/compiz/general/allscreens/options

/apps/compiz/general/screen0
/apps/compiz/general/screen0/options

/apps/compiz/plugins
/apps/compiz/plugins/animation
/apps/compiz/plugins/animation/screen0
/apps/compiz/plugins/animation/screen0/options

```

AND... 

/apps/compiz-1 which contains the following subfolders:
```

/apps/compiz-1/plugins
/apps/compiz-1/plugins/animation
/apps/compiz-1/plugins/animation/screen0
/apps/compiz-1/plugins/animation/screen0/options

The pattern above is repeated multiple times. 
The only change being that the term "animation" (above)
 is replaced by the following terms:

colorfilter
expo
ezoom
imgjpeg
kdecompat
mag
mousepoll
neg
opacify
put
resizeinfo
ring
scaleaddon
session
shift
snap
staticswitcher
thumbnail
titleinfo
unitymtgrabhandles
unityshell
vpswitch
wall
winrules
workarounds

```

Hope that helps

And thanks so very much for helping me!

---

### Post by Krytarik on 2011-04-30
Thanks for the effort with gconf-editor. Unfortunately, the result makes it even more confusing, at least in your case. =/
Maybe it's because you did an upgrade, and part of those settings are remnants from Natty, which may be causing the issues.

The result from the process check means that Compiz was running and crashed, so that is consistent with your observation.

You don't have a folder called "/apps/compizconfig*" in gconf-editor?

Try this to reset all Compiz settings:
- from within any Ubuntu* session, run
```
gconftool-2 --shutdown
nautilus
```- backup the respective directories in "~/.gconf/apps"
- remove them
- relogin to Unity

---

### Post by Ron Jones on 2011-04-30
> **Krytarik said:**
> Thanks for the effort with gconf-editor. Unfortunately, the result makes it even more confusing, at least in your case. =/
Maybe it's because you did an upgrade, and part of those settings are remnants from Natty, which may be causing the issues.

I was afraid of that. About halfway through the "Meerkat" cycle, I tried Compiz. It worked well enough... However, I had to uninstall it. It seems that some programs (Skype, Scribus, Stellarium, QTstalker, DeVeDe, and more), as soon as I started them up and moused over them, caused an Xserver crash. When I uninstalled Compiz, everything went back to normal.

Around the same time, I also tried (unsuccessfully) to install the Unity desktop. once I discovered the issues with my applications and Compiz, I abandoned the effort. 

Perhaps, what I'm seeing is artifacts left over from that fiasco.

> **Krytarik said:**
> The result from the process check means that Compiz was running and crashed, so that is consistent with your observation. 
Of course, this observation makes me question the logic in my hypothesis (above).

> **Krytarik said:**
> You don't have a folder called "/apps/compizconfig*" in gconf-editor?

No, and that is one of the things that makes me wonder if a complete purge and reinstall of Compiz & Unity might be the answer. 

Any "gotchas" lurking in that solution I should be aware of? Is there a particular order or protocol I should follow in order to prevent completely ruining my Ubuntu installation?

> **Krytarik said:**
> Try this to reset all Compiz settings:
- from within any Ubuntu* session, run
```
gconftool-2 --shutdown
nautilus
```- backup the respective directories in "~/.gconf/apps"
- remove them
- relogin to Unity

Tried that this morning. But it didn't have any effect... at least not that I can tell. When I log in to Ubuntu (Unity), there is still no menubar, Unity launcher, etc. Only the desktop background, and the files on the desktop.

Opening ~/.gconf/apps shows that the system has recreated folders for a few of the apps (though not all the ones I removed to a backup folder).

As an aside... Is there a hotkey combination, or a launcher I can create that will let me simply logout? The closest thing I've found is Ctrl-Alt-Del, but the only options I have in that application are Shut Down, Restart, Suspend, and Hibernate.

---

### Post by Krytarik on 2011-04-30
> **Ron Jones said:**
> 
No, and that is one of the things that makes me wonder if a complete purge and reinstall of Compiz & Unity might be the answer. 

Any "gotchas" lurking in that solution I should be aware of? Is there a particular order or protocol I should follow in order to prevent completely ruining my Ubuntu installation?
You *have* already the worst that can possibly happen, that you can't run Compiz and therefore also not Unity. So, it can only get better. To do so, we could purge Compiz and Unity completely along with their dependencies, and then reinstall:
```
sudo apt-get purge compiz-core
```This is a one-purges-all command, but upon a simulation (with the option "-s") I noticed that it may also remove packages that have not obviously something to do with it, for me it is "ubuntu-tweak", so please run a simulation before and note the to be removed packages, just copy & paste the output, of course.

To reinstall everything again (I'll include Unity 2D here):
```
sudo apt-get install compiz unity unity-2d compizconfig-settings-manager ADDITIONAL-APPS
```**But before you do all that, please check if you can run Unity within a Natty liveCD! I'm not sure how meaningful that is, but the proprietary Nvidia driver and the Nouveau driver are both included by the CD, so it should work.**
> **Ron Jones said:**
> 
As an aside... Is there a hotkey combination, or a launcher I can create that will let me simply logout? The closest thing I've found is Ctrl-Alt-Del, but the only options I have in that application are Shut Down, Restart, Suspend, and Hibernate.
I was asking this myself some times yesterday, but it seems like the closest one can get is:
```
gnome-session-save --logout
```Which purportedly also saves a session, there seems to be no command to orderly end a session without saving it.

---

### Post by Ron Jones on 2011-05-01
Okay, back in the saddle after a weekend of yard work :D

I'll be pulling an all-nighter working on this. So, in preparation..

> **Krytarik said:**
> 
```
sudo apt-get purge compiz-core
```

This is a one-purges-all command, but upon a simulation (with the option "-s") I noticed that it may also remove packages that have not obviously something to do with it, for me it is "ubuntu-tweak", so please run a simulation before and note the to be removed packages, just copy & paste the output, of course.

When I ran the purge compiz-core simulation, I got the following output:
```

ron@desk2:~$ sudo apt-get purge compiz-core -s
[sudo] password for ron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-orca
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz-core* compiz-plugins* compiz-plugins-main* compizconfig-settings-manager* libcompizconfig0*
  python-compizconfig* ubuntu-desktop* unity*
0 upgraded, 0 newly installed, 8 to remove and 1 not upgraded.
Purg ubuntu-desktop [1.220]
Purg unity [3.8.12-0ubuntu1~ppa1]
Purg compizconfig-settings-manager [0.9.4-0ubuntu2]
Purg python-compizconfig [0.9.4-0ubuntu1]
Purg libcompizconfig0 [0.9.4-0ubuntu2]
Purg compiz-plugins-main [0.9.4+bzr20110406-0ubuntu2]
Purg compiz-plugins [1:0.9.4+bzr20110415-0ubuntu2]
Purg compiz-core [1:0.9.4+bzr20110415-0ubuntu2]
ron@desk2:~$ 

```

When it purges the ubuntu-desktop, am I going to be working from the command line? If so, I can get through it, but it will require more extensive preparation on my part (making sure I've got all the proper commands written down beforehand).

> **Krytarik said:**
> To reinstall everything again (I'll include Unity 2D here):
```
sudo apt-get install compiz unity unity-2d compizconfig-settings-manager ADDITIONAL-APPS
```

Here's hoping I'll be able to get that done tonight!

> **Krytarik said:**
> **But before you do all that, please check if you can run Unity within a Natty liveCD! I'm not sure how meaningful that is, but the proprietary Nvidia driver and the Nouveau driver are both included by the CD, so it should work.**

I tried that... and the strangest thing happened (okay, well maybe not so strange to someone with more experience than myself)... I went into the Bios on my [Gigabyte] motherboard and configured my PC to boot from the CD first; then I restarted, and it booted from the hard drive as though there were nothing on the CD. Then I checked the CD to make *absolutely sure* that I actually burned the Ubuntu live .iso onto it (yep, I did).

"Okay" I thought, "let's try a shut down and restart." So, I turned off the PC completely, counted 15 seconds, and then started it up. Once again, it booted straight from the hard drive.

Next, I went into the Bios, and configured it NOT to boot from the hard drive at all. My boot order menu included ONLY the CD.

Wouldn't you know it, the SAME thing happened. The PC booted right up from the hard drive, as though there was no CD in the drive.

So, I abandoned that effort, figuring perhaps it was a function of having only a SATA hard drive. and decided to move on without it.

---

### Post by Ron Jones on 2011-05-01
**As a follow-on to my previous post...**

> **Krytarik said:**
> ...we could purge Compiz and Unity completely along with their dependencies, and then reinstall:
```
sudo apt-get purge compiz-core
```This is a one-purges-all command, but upon a simulation (with the option "-s")

Since I'm planning to purge and reinstall. Should I plan to purge ONLY compiz? Or should I also plan to purge Unity as well?

When I ran the 
```
sudo apt-get purge unity -s
```
command, I got the following ominous (to me) message:

```

The following packages will be removed:
ubuntu-desktop* unity*

```

---

### Post by Krytarik on 2011-05-01
Sorry that I couldn't join you earlier!

I, too, don't know why your machine still boots from HDD even if it's disabled at all, seems indeed weird.
Let's just move on then, like you said.

"ubuntu-desktop" is just a metapackage (same as "compiz"), and if it's removed, no 'real' packages will be removed, unless you use apt-get's "autoremove" feature which may or may not remove the packages listed as dependencies of "ubuntu-desktop":
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

And, as you can see, "unity" will be removed as a matter of dependency when you remove "compiz-core".

So, after purging "compiz-core" you will be still able to log in to "Ubuntu Classic (No effects)"

To reinstall all removed packages run:
```
sudo apt-get install compiz unity unity-2d compizconfig-settings-manager ubuntu-desktop
```Btw., it seems like "compiz" isn't installed at your system.

---

### Post by Ron Jones on 2011-05-01
> **Krytarik said:**
> Sorry that I couldn't join you earlier!

Not to worry... I hear there's a real world out there, away from the computer. Complete with real life and everything :lolflag:

> **Krytarik said:**
> I, too, don't know why your machine still boots from HDD even if it's disabled at all, seems indeed weird.
Let's just move on then, like you said.

[SIZE="3"]**[COLOR="Sienna"][CENTER]I think it's fixed![/CENTER][/COLOR]**[/SIZE]

Okay... So I was sitting here getting all my ducks in a row before purging compiz/unity. And I was running through the commands with the -s[imulate] switch to get a feel for what the system would tell me.

For no reason at all, I ran 
```
sudo apt-get install unity -s
```
and the output read something like "unity is already the newest version."

But when I ran
```
sudo apt-get install compiz -s
```
I got an unexpected output. I'm paraphrasing here, because I don't remember exactly what it said but... It was something to this effect:
```

The following extra packages will be installed:
compiz-gnome compiz-config-backend-gconf

The following new packages will be installed:
compiz-gnome compizconfig-backend-gconf

```

Well boy howdy I got exited. So, just for grins (sometimes you just have to take a leap of faith)... I ran the "install compiz" command without the -s; Then I logged out (using the handy Logout launcher you gave me the command for yesterday... I didn't need it since I was in Ubuntu 'classic,' but I wanted to try it, and yes, it works just fine).

When I logged back in, I found myself looking at a unity desktop! Everything seems to be working so far.

HOWEVER... Is there some list against which I can check my installed packages to make sure I've got all the unity/compiz stuff there is?

ron@desk2:~$ dpkg -l | grep unity

returns the following:
```

(assorted, unrelated packages with comm"unity" in the name)
libunity-misc0
libunity4
unity
unity-asset-pool
unity-common
unity-place-applications
unity-place-files

```

AND

ron@desk2:~$ dpkg -l | grep compiz

returns the following
```

compiz
compiz-core
compiz-gnome
compiz-plugins
compiz-plugins-main
compizconfig-backend-gconf
compizconfig-settings-manager
libcompizconfig0
python-compizconfig0

```


If those are all the ones I need to make unity/compiz function to its full potential, then I think we've got this problem whipped. How do I mark this thread [Solved]?

Can you point me in the direction of a post or wiki that will help me get up to speed on using/configuring/tweaking Unity?

Thank you for giving your time to help me. I do appreciate it.


Regards,

---

### Post by Krytarik on 2011-05-01
First of all, I'm very glad that it works for you now! :-D

Yeah, I didn't notice that "compiz-gnome" and "compizconfig-backend-gconf" were missing as well, because I didn't check every single package in the output.

To make sure every related package is installed you can either run the commands like planned (the easy way) or check them one-by-one here, it's one of my major references:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

See these guides about Unity:
[http://ubuntu4beginners.blogspot.com/search/label/Unity](http://ubuntu4beginners.blogspot.com/search/label/Unity)
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)
[https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)

And for some needed applet replacements:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Have fun!

---

