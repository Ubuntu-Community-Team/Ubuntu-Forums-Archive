---
title: "no compiz-config settings manager"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by notatoad on 2007-09-28
i installed compiz fusion following the instructions on the ubuntuguide wiki, but i haven't got a compiz settings manager.

there is an entry in system>preferences called compiz-config settings manager, but when i click it nothing happens.  typing ccsm into a terminal gives this:
```
kyle@kworkstation:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

```

how can i get a settings window?

---

### Post by erasmosis on 2007-10-04
Same problem here.... 
Were you able to find a resolution?

> randy@randy-laptop:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 44, in <module>
    mainWin = ccm.MainWin(context)
  File "usr/lib/python2.5/site-packages/ccm/Window.py", line 81, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Window.py", line 421, in CatSortCompare
KeyError: 'core'


---

### Post by Faud on 2007-10-04
did yall search the repositires sunder compiz for the settings manager, make sure that you have

deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

in your third part software tab

---

### Post by Mohonri on 2007-10-07
I have the exact same problem as notatoad.  Clicking on Compiz-config settings manager did nothing (other than make the UI pause for a second), and I get the same errors/warnings when I type "ccsm" in a terminal.

I've made sure that I've included the repository that Faud suggested, and that didn't help at all.

---

### Post by Fearghal on 2007-10-13
I have or at least had the same issue,perhaps you have sorted.  It appears that the compiz settings manager has disappeared, there is an entry there but no icon either.  I was messing with effects etc and somehow it went wrong...  I tried to re-install using a blog from Kevin van Zonneveld but it really messed things up.
I checked my Applications/System manager and opened Beryl.  I have my cube effects etc but not being managed by Compiz.  I have also tried re-installing Compiz but no good.  I still have my effects etc but being 'MANAGED' by Beryl. 
Right now Im gonna stop messing around, create a dump of my default settings, just incase

---

### Post by Officer Dibble on 2007-10-13
Have you tried:

> Alt-F2

beryl-manager

Select Window Manager

---

### Post by Forlong on 2007-10-13
> **Fearghal said:**
> I have or at least had the same issue,perhaps you have sorted.  It appears that the compiz settings manager has disappeared, there is an entry there but no icon either.  I was messing with effects etc and somehow it went wrong...  I tried to re-install using a blog from Kevin van Zonneveld but it really messed things up.
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by jj420 on 2007-10-16
i am getting the same error 

> **jeff@dell-desktop:~$ ccsm**
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'
**jeff@dell-desktop:~$ dpkg -l | grep compiz**
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager
ii  compiz-core                                0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.3.6-1ubuntu13                        OpenGL window and compositing manager - GNOM
ii  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.3.6-1ubuntu13                        OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1        Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
jeff@dell-desktop:~$

---

### Post by Rupertronco on 2007-10-16
Do as forlong said, and post your package list. Basically what he's looking for is to make sure you have the ccsm package installed. It doesn't come with the compiz-gnome, compiz-core, or effects packages. It's a separate package. Make sure you installed it.

---

### Post by jj420 on 2007-10-17
i got it fixed had to uninstall compiz-gtk and update compiz-core. But now the settings manager doesn't change or effect anything. Why?

---

### Post by messiah89 on 2007-10-19
have you all just upgraded to gutsy?
 the same has happened to me, one boot it was fine then now its not working, gutsy renamed it to "advanced desktop effects"? or something like that, but now it is back to "compiz config settings manager"  and it has no icon..

---

### Post by NS2-10 on 2007-10-20
I just did and I have the same problem. No settings configurator, everything looks exactly the same as for everyone else in this thread... same output...

I have absolutly no idea of how to solve it. I can access the old beryl configurator but it doesn't do much difference.

---

### Post by decimal on 2007-10-20
I solved it by reinstalling compizconfig-settings-manager. Before I upgraded to Gutsy I was using the git repositories of compiz fusion, I don't know if it makes any difference but for the shake of the conversation I thought to mention it.

---

### Post by jamesey on 2007-10-20
I have the same issue. I just upgraded to gutsy and everything works fine except this. I even have the compiz effects. I just can't run the manager.

---

### Post by Scotty1982 on 2007-10-20
Works on my pc... installed the compizconfig-settings-manager package, then go to system > preferences > Appearance > Visual Effects > set to custom and click preferences...

hope this helps...

all i can't get it to do is make the desktop cube... mine's only got 2 sides.

---

### Post by Dean_Harryman on 2007-10-20
I have this same problem, but when i go to the advanced visual effects nothgin happens, and the settings manager is the same story, nothing happens.... 

I also have only 2 sides to the cube. WIERD!

---

### Post by Scotty1982 on 2007-10-20
I just noticed that there's also "Advanced Desktop Effects settings" under system > preferences... it opens the same thing, but the other way *should* enable compiz and open the config.

i have no idea why there's only 2 sides.. i tried increasing the number of 'virtual desktops' but that' didn't help...

---

### Post by Weezer on 2007-10-20
I'm getting the same problems. I've been trying to get Compiz Fusion running.


```

joe@Computer:~$ dpkg -l |grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2    Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070921+3v1ubuntu0  Collection of UNOFFICIAL fusion plugins for 
ii  compiz-fusion-plugins-unsupported          0.5.2~git20071006+3v1ubuntu0  Collection of plugins for Compiz - Unsupport
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0 Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0  GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3    Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1    Compiz configuration system bindings


```

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

---

### Post by Mad_Max_1412 on 2007-10-21
Guys,

I had a similar issue.  A recent computer magazine showed steps on how to install Compiz Fusion, but after the instructions had a paragraph saying that at time of writing, Ubuntu Developers voted in favour of bundling CompizFusion with the next 7.10 release.  Therefore I didn't install it.

I recently upgraded to 7.10 and under System --> Preferences --> Appearance, I had None, Normal and Extra.  When I selected Extra, it gave me bendy windows and when opening/closing windows, they would "flop out" to full screen and then back to their appropriate size.

The above mentioned article mentioned a whole lot of eye candy which I wasn't seeing being available, so I thought that perhaps CompizFusion hadn't got released with 7.10.

Therefore I followed the steps to do the install manually.  These steps were:

Add repository

> deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

Then ran the following commands:

> sudo apt-get remove compiz-core desktop effects

> sudo apt-get install compiz compizconfig-settings-manager emerald emerald-themes

It then said that to install the Fusion Icon, I had to download the binary from

[http://ubuntuforums.org/showpost.php?p=3163821](http://ubuntuforums.org/showpost.php?p=3163821)

Now when I got to Applications --> System Tools --> Compiz Fusion Icon, nothing appears to happen.

Also under System --> Preferences --> Appearance, when I select something like Extra or Custom, I get the message:

> Failed to execute child process "compiz" (No such file or directory)

Also, under Add/Remove, I have installed Advanced Desktop Effects Settings (ccsm)
Compiz configuration settings manager thinking this might help but it hasn't.

I've also lost the wobbly windows (where you click and hold the title bar and shake the window)

Any ideas on how I can fix this?  BTW, I'm a noobie, so instructions might need to be a bit detailed.

Thanks

---

### Post by ipina on 2007-10-21
Hi all. Yes, when I upgraded to gutsy I found that the manager of compiz didn't work. Further, some windows like the one in order to reply an email - option 'reply to sender' - hanged. It was fine to me to uninstall compiz settings manager and reinstall it with synaptics. Hope this helps to those who upgraded to  gutsy.

---

### Post by Franchie on 2007-10-21
> **Scotty1982 said:**
> I have no idea why there's only 2 sides.. i tried increasing the number of 'virtual desktops' but that' didn't help...

You need to increase the number of virtual desktops (for a cube, try 4) in the "general>desktop size" tab of the configuration manager. But you also need to increase the horizontal size to 4 (for example), and set the vertical size to 1. This tells compiz how to place them on the cube, etc.

Otherwise, you are left with a sheet rather than a cube, which can also be interesting...

Hope this helps!

---

### Post by solarswordsman on 2007-10-21
> **Weezer said:**
> I'm getting the same problems. I've been trying to get Compiz Fusion running.


```

joe@Computer:~$ dpkg -l |grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2    Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070921+3v1ubuntu0  Collection of UNOFFICIAL fusion plugins for 
ii  compiz-fusion-plugins-unsupported          0.5.2~git20071006+3v1ubuntu0  Collection of plugins for Compiz - Unsupport
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0 Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0  GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3    Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1    Compiz configuration system bindings


```

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

I'm having this exact same problem.

---

### Post by Weezer on 2007-10-21
My friend suggested Python might be messed up. If that's the case, how do I go about fixing it?

---

### Post by jamesey on 2007-10-23
Anyone got a fix for this?

---

### Post by jamesey on 2007-10-23
I found a fix for this. Go to the compiz forums and read this post
[http://forum.compiz-fusion.org/showthread.php?t=4927](http://forum.compiz-fusion.org/showthread.php?t=4927)

basically there is an old version of the compiz manager getting stuck, and preventing a newer version from installing. Just remove all feisty repositories, then go to the synaptic package manager. Search for compiz and uninstall any package that has "3v1" in it. Then you should be able to install the compiz manager through synaptic and everything will work.

---

### Post by sinistrad on 2007-10-23
> **jamesey said:**
> I found a fix for this. Go to the compiz forums and read this post
[http://forum.compiz-fusion.org/showthread.php?t=4927](http://forum.compiz-fusion.org/showthread.php?t=4927)

basically there is an old version of the compiz manager getting stuck, and preventing a newer version from installing. Just remove all feisty repositories, then go to the synaptic package manager. Search for compiz and uninstall any package that has "3v1" in it. Then you should be able to install the compiz manager through synaptic and everything will work.

Thanks for the help.  This is exactly what my problem was and now everything is working great. :)

---

### Post by Mad_Max_1412 on 2007-10-25
Guys,

What step am I missing.

I went to System --> Administration --> software sources and removed the tick from the 3rd party tab removed the tick from the line which had Fiesty in it.

I then went to Synapic Package Manager and anything shaded under a search for Compiz I marked for deletion and applied changes.

I then went to Add/Remove Applications and searched for Compiz and marked the one showing as "Advanced Desktop Effects Settings (ccsm) Compiz configuration settings manager"

When I go into System --> Preferences --> Appearance, when I select something like Extra or Custom, I am still getting the message:

> Failed to execute child process "compiz" (No such file or directory)

Thanks

---

### Post by Mad_Max_1412 on 2007-10-25
Guys,

I've managed to fix it by searching for Compiz and selecting everything that had a Ubuntu logo.

Thanks

---

