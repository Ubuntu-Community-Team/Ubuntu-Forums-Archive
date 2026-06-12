---
title: "Just upgraded to 7.10, need compiz settings manager..."
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-10-17
I just upgraded to Gutsy and it removed Beryl for me and replaced it with compiz, which appears to be running smoothly.

But I don't have a settings manager to change animations and customize effects.  I tried adding "compizconfig-settings-manager" with Synaptic, and I'd hit an error; it wouldn't install.

What should I try next?

---

### Post by davem2312 on 2007-10-17
Post the output of...

```
sudo apt-get install compizconfig-seetings-manager
```

---

### Post by diablo75 on 2007-10-17
```
zeke@zeke-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for zeke:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl-core libportaudio2 beryl-settings-bindings libwxgtk2.4-1 libswfdec0.3
  libflac++5c2 liboggflac3 libjack0.100.0-0 guile-g-wrap libpostproc0d
  democracyplayer-data libavformat0d libffi4 libberylsettings0
  libreadline5-dev beryl-settings guile-1.6-dev guile-library libffi4-dev
  libgoffice-0-3 beryl-plugins libgwrap-runtime0-dev libcrypto++5.2c2a g-wrap
  libavcodec0d libncurses5-dev beryl-plugins-data libquicktime0
  libberyldecoration0 libntfs-3g0 libboost-python1.33.1 libgwrap-runtime0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed:
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/540kB of archives.
After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
zeke@zeke-laptop:~$ 

```

---

### Post by Tachyon1000 on 2007-10-17
You shouldn't need a separate install of compiz manager.  All its functionality is included within the Appearances dialog under visual effects.  Select custom and preferences and you have everything you need.  It's been integrated.

---

### Post by steveneddy on 2007-10-17
I get this output when trying to start the Preferences under Visual Effects.

```

 ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


```

I'm just trying to get to the settings so I can use the ones I used to have. Too many shadows in places where I don't want them and not enough in others.

Newly upgraded to Gutsy.

Whoo boy - this is going to be a fun one.

:popcorn:

---

### Post by diablo75 on 2007-10-17
> **Tachyon1000 said:**
> You shouldn't need a separate install of compiz manager.  All its functionality is included within the Appearances dialog under visual effects.  Select custom and preferences and you have everything you need.  It's been integrated.

That's just the thing.  "Custom" wasn't one of the listed options...

---

### Post by Tachyon1000 on 2007-10-18
Your install of compiz manager is failing due to other unrelated packages, tzdata (time zone data) and util-linux.  Considering that these are important base packages, I suggest that you try to reinstall them or figure out what is wrong with those packages.

---

### Post by Forlong on 2007-10-18
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by diablo75 on 2007-10-18
> **Forlong said:**
> Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

```
zeke@zeke-laptop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                    OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plug
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
zeke@zeke-laptop:~$ 

```

---

### Post by Forlong on 2007-10-18
Try this:
```
sudo apt-get -f install
```

---

### Post by steveneddy on 2007-10-18
I had to reinstall compizconfig-settings-manager to get it to work.

Works great now.

:popcorn:

---

### Post by Radh77 on 2007-10-18
I am at a loss here... new to ubuntu/linux (longtime M$ user)... how do you reinstall compizconfig-settings-manager in gg7.10???
I don't have the Custom settings under System -> Appearance -> Visual Effects either. The only settings are None / Normal / Extra


any help would be appreciated...

---

### Post by Forlong on 2007-10-18
Sounds like you just don't have ccsm installed. Type this in a terminal:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Radh77 on 2007-10-18
> **Forlong said:**
> Sounds like you just don't have ccsm installed. Type this in a terminal:
```
sudo apt-get install compizconfig-settings-manager
```

well this is what I get after i type it into terminal
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

do I have to specify some additional repository? :confused:

---

### Post by Forlong on 2007-10-18
How did you install Gutsy?

---

### Post by Radh77 on 2007-10-18
I downloaded the release this morning... i386 installation CD. Burned the image and started the install. Dualboot with XP. Installation went thru without any problems... no error messages.. I am running it on Asus Z62F laptop.

I know that Compiz works fine on this HW cause since last week I was playing around with openSUSE 10.3 on the laptop and everything worked fine.

---

### Post by NoSmokingBandit on 2007-10-18
I have the exact same problem as radh77. I did a clean install of gusty this morning via the i386 install cd. Got my nvidia drivers all settled in and couldnt fing the compiz settings manager thing anywhere. I get the same "package cant be found" message when i try to install it through apt-get. Is there some kind of repository im missing?

---

### Post by Puregrain on 2007-10-18
I have the same situation as well. Fresh install and it is not showing for me either. Same output using sudo apt-get.

---

### Post by Radh77 on 2007-10-18
OK.. got it... all of the entries under System -> Administration -> Software Sources under Ubuntu sources were unchecked. After I checked all of them except the source code one and refreshed the packages in Snaptics I was able to install the compizconfig-settings-manager without a problem.

I did not change any of these settings... But I am just thinking.. these should be checked automatically... no? I have no idea why they were not... maybe something to do with not having the computer connected to the internet during the install???? 
thank you anyway...

---

### Post by NoSmokingBandit on 2007-10-18
thanks dude, i thought it may be something like that because i just tried to install wine and got the same error. :)
That explains why the restricted drivers manager wouldnt install my drivers...

---

### Post by Puregrain on 2007-10-18
yes thanks a ton for finding this. I had been there once before and questioned checking those boxes. I should have followed gut. :o)

---

### Post by steveneddy on 2007-10-18
Sounds like you need to enable another repo.

---

### Post by diablo75 on 2007-10-18
> **Radh77 said:**
> OK.. got it... all of the entries under System -> Administration -> Software Sources under Ubuntu sources were unchecked. After I checked all of them except the source code one and refreshed the packages in Snaptics I was able to install the compizconfig-settings-manager without a problem.

Well this doesn't work for me and my problem as all software sources are checked off....

So I'm still a little bit at a loss...

---

### Post by Gerontius on 2007-10-18
Here is my problem:

compiz settings manager won't work... when i choose visual effects preferences in appearance applet, nothing happens
when i type ccsm... this is what i get

> Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


---

### Post by klikko on 2007-10-19
I found a solution that worked at least for me:

I got the same error as directly above.

I then tried *sudo apt-get install compizconfig-settings-manager*, but it just tells me it's already the newest version:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libportaudio2 libsoundtouch1c2 libwxgtk2.4-1 liboggflac3 libjack0.100.0-0
  libpostproc0d libavformat0d libdb3 liblzo-dev libavcodec0d libquicktime0
  libglademm-2.4-1c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Then, on a whim, I decide to try apt-get remove compizconfig-settings-manager, and then apt-get install compizconfig-settings-manager again.

I then see that the "Compiz Settings Manager" under Settings > Preferences that was left over from my upgrade from 7.4 has changed to "Advanced Desktop Effects Settings"
And now I can access my settings.
It's the most simplistic troubleshoot method ever, and therefore it's always been my favorite: if it doesn't work, reinstall and try again!

---

### Post by falseicon on 2007-10-19
> **Radh77 said:**
> OK.. got it... all of the entries under System -> Administration -> Software Sources under Ubuntu sources were unchecked. After I checked all of them except the source code one and refreshed the packages in Snaptics I was able to install the compizconfig-settings-manager without a problem..

Thanks much for pointing this out.  In my case "Community-maintained OSS" was the only one unchecked, but a click and repost had it all working within moments

---

### Post by kulturloseramerikaner on 2007-10-19
I had to reinstall CCSM also, but I still get this when I try to enable 3D effects:
"The Composite extension is not available"

---

### Post by diablo75 on 2007-10-20
I am unable to reinstall, as I get the following when I try:

```
zeke@zeke-laptop:~$ sudo apt-get autoremove compizconfig-settings-manager
[sudo] password for zeke:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not installed, so not removed
The following packages were automatically installed and are no longer required:
  beryl-core libportaudio2 beryl-settings-bindings libwxgtk2.4-1 libswfdec0.3
  libflac++5c2 liboggflac3 libjack0.100.0-0 guile-g-wrap libpostproc0d
  democracyplayer-data libavformat0d libffi4 libberylsettings0
  libreadline5-dev beryl-settings guile-1.6-dev guile-library libffi4-dev
  libgoffice-0-3 beryl-plugins libgwrap-runtime0-dev libcrypto++5.2c2a g-wrap
  libavcodec0d libncurses5-dev beryl-plugins-data libquicktime0
  libberyldecoration0 libntfs-3g0 libboost-python1.33.1 libgwrap-runtime0
The following packages will be REMOVED:
  beryl-core beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings democracyplayer-data g-wrap guile-1.6-dev
  guile-g-wrap guile-library libavcodec0d libavformat0d libberyldecoration0
  libberylsettings0 libboost-python1.33.1 libcrypto++5.2c2a libffi4
  libffi4-dev libflac++5c2 libgoffice-0-3 libgwrap-runtime0
  libgwrap-runtime0-dev libjack0.100.0-0 libncurses5-dev libntfs-3g0
  liboggflac3 libportaudio2 libpostproc0d libquicktime0 libreadline5-dev
  libswfdec0.3 libwxgtk2.4-1
0 upgraded, 0 newly installed, 32 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 42.4MB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
zeke@zeke-laptop:~$ 

```

---

### Post by diablo75 on 2007-10-20
SOLVED!

tzdata update just came down the wire.  I had no problems uninstalling and reinstalling compizconfig-settings-manager using

sudo apt-get autoremove compizconfig-settings-manager

then

sudo apt-get install compizconfig-settings-manager

:guitar:

---

### Post by DSK on 2007-10-20
> **davem2312 said:**
> Post the output of...

```
sudo apt-get install compizconfig-seetings-manager
```

This is a typo.  should be
```

sudo apt-get install compizconfig-settings-manager
```

---

### Post by B3n3v3nt3 on 2007-10-21
The problem appeared to me after I updated the ccsm, so I removed the updated version compizconfig-settings-manager_0.6.99 in the synaptic, and installed the older version 0.5.2.It's  works fine now.

---

### Post by Raistlin355 on 2007-10-21
Had the same problem with the manager not wanting to load, tried to uninstall and reinstall but to no avail, reverted to the previous version and it works perfectly!!!

Untill after I restart now when I try to start compiz I get a "segmentation fault (core dumped)" message any ideas on what this means and how to fix it?

---

### Post by kooldino on 2007-10-23
I have a unique problem of my own.

I'm running KDE (Kubuntu, not ubuntu with KDE installed) Gutsy Gibbon.

I can install the compizconfig-settings-manager, however, I can't find how to run it.  It doesn't appear in any of my menus, and if I poke around in the folders it creates, I see no executable file.

Help!

---

### Post by kooldino on 2007-10-23
I found it installed on a menu of another machine, and it looked like it ran a command called "ccsm".  Perhaps I'll try that.

---

### Post by kooldino on 2007-10-24
Yup, "ccsm" did it.  All is well.

---

