---
title: "Compiz-Fusion Stopped Working After Update"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by GameKing505 on 2007-11-17
I was happily running compiz-fusion up until a few minutes ago. Ubuntu told me that I had updates to install. I naturally installed these updates, but upon rebooting, compiz no longer works. WHen I try to run it from the terminal this is my output:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fusion'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

It was working find until the update, so I think that's what did it. I run Gutsy Gibbon btw, and I'm a noob to ubuntu so bear with me.

---

### Post by cam381 on 2007-11-17
What updates did you install? (What were they for) Did any of them have the name compiz in 'em? Are you using Gutsy 7.10?

---

### Post by GameKing505 on 2007-11-17
I mostly just glanced at them but there were some compiz ones. I can't tell you exactly what because I don't remember.

---

### Post by cam381 on 2007-11-17
Your using gutsy 7.10 right? Do you have the compiz config settings manager installed?

---

### Post by GameKing505 on 2007-11-17
Yes I do but I can't open it for some reason.

---

### Post by cam381 on 2007-11-17
That's weird. I installed my updates and it works ok. Try reinstalling it using synaptic. Click check box and click reinstall. If not do it using the terminal. 
"sudo apt-get install compizconfig-settings-manager"
Hope that helps.

---

### Post by GameKing505 on 2007-11-17
Still won't open. The manager and everything worked fine until the update. Anyone out there know what to do? Help would be really appreciated.

---

### Post by cam381 on 2007-11-17
Whoa whoa whoa whoa whoa do the effects work and not the manager or both don't work?

---

### Post by GameKing505 on 2007-11-17
Both worked till the update. Now none work.

---

### Post by cam381 on 2007-11-17
Sorry I got nothing. I apologize. Hope someone can help.

---

### Post by ubuntu-freak on 2007-11-17
I thought Ubuntu had disabled effects for some intel based graphics cards. If that's not you then try reinstalling compiz and/or your card drivers. As updates sometimes overwrite settings or files.

---

### Post by GameKing505 on 2007-11-17
I resinstalled, and am still getting the same message when I try to run from the terminal. 

Please someone help me.

---

### Post by Forlong on 2007-11-18
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by djuniah on 2007-11-18
I'm having the same issue actually.  What happens for me though, is that the desktop actually turns white.  This happened right after the upgrade.  I however, CAN get to the settings manager.  When it does turn white, i can rotate the cube.  However, there is a slightly darker white bar on the bottom of the screen where AWN should be.  I know this has been a common problem for compositing managers before.  I remember hearing about it alot when i used to use beryl.  It seems like the latest update is what caused it.  Anyone have any suggestions on how to get rid of it?

~DJuniah

---

### Post by GameKing505 on 2007-11-18
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```


Some of the formatting got messed up in the transfer, but there it is.

---

### Post by bmdavis on 2007-11-18
Stopped working for me as well!   Dell Inspiron 6400, definitely linked to the last update.  running Compiz in terminal sends me the, "texture_from_pixmap support: failed".  Although I'm in GNOME right now without starting with compiz.

Crud....

---

### Post by Forlong on 2007-11-18
GameKing505, you have messed up packages. Remove those:
```
sudo apt-get remove compizconfig-settings-manager libcompizconfig-backend-gconf
```
Then go here: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by GameKing505 on 2007-11-18
I didn't use any Trevino repositories though. I'm only using the compiz that came with the installation of ubuntu 7.10. Should I still follow those steps?

EDIT: It turned out that I did have those repositories because I downloaded a dock program called kiba-dock. Anyway, I did that command, used synaptic to reistall the packages, and now I'm running a broken compiz. It does start up but none of the effects work and there are no window borders. I can only have one window open at a time. Using ALT+click doesn't move the windows either. 

Did I possibly miss a package? Someone please help as this is really annoying.

---

### Post by GameKing505 on 2007-11-18
I totally uninstalled anything that even smelled like compiz, reinstalled the necessary packages, and now I still can't run it. This blows.

When I try to run compiz, I get this:

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

---

### Post by djuniah on 2007-11-19
The not having window border issue is related to the window manager.  Try installing emerald(and the related packages) and see if that helps

---

### Post by Forlong on 2007-11-19
Post the output of ```
dpkg -l | grep compiz
``` again.

---

### Post by bmdavis on 2007-11-19
ii  compiz                                     0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20071006+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20071007+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-gnome                               0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0           GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu3           Settings library for plugins - Compiz Fusion
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration

---

### Post by Forlong on 2007-11-19
bmdavis, what version of Ubuntu are you using?

---

### Post by GameKing505 on 2007-11-19
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```

That's mine. 

I've gotten so used to shiny effects that the plain old minimizing with the black square and stuff makes me sad...

---

### Post by Forlong on 2007-11-19
GameKing505, what's the output of ```
compiz
``` in a terminal?

---

### Post by GameKing505 on 2007-11-19
I already posted it before but it's:

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

This results in compiz being launched without any window borders or anything. The whole program is all messed up. I was able to run it fine before this stupid update...

---

### Post by Romanus81 on 2007-11-19
I have the same problem

dpkg -l | grep compiz
```

$owner@ubuntu:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1     OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1     OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2         Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1     OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1     OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1         Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1         Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3         Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1         Compiz configuration system bindings

```

running compiz from terminal yields:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b60 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

glxinfo | grep rendering:

```
owner@ubuntu:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```
I have an radeon-300 graphics card, I believe, with the latest fglrx drivers.

---

### Post by wheels53 on 2007-11-19
I had the same problem after installing the kiba-dock and then updating.  To install the kiba-dock, I added the following to my sources list

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Because I had these in my list, I was prompted to update compizconfig-settings-manager to a newer git version which, is when all my problems started.  So, temporarily remove the above sources from your sources list and uninsatall compizconfig-settings-manager.  Then reinstall the compizconfig-settings-manager and you should be good to go.

---

### Post by Forlong on 2007-11-20
> **Romanus81 said:**
> I have an radeon-300 graphics card, I believe, with the latest fglrx drivers.

The driver is obviously not working correctly, what output gives
```
fglrxinfo
```
GameKing505, post that too.

---

### Post by JunSeok Kang on 2007-11-20
I had the same problem, and was using the "restricted driver" of ATI Graphic Accelerator. 

After the update, the compiz was just turned off and could not load it again even after reboot.

So I turned the restricted driver off and rebooted.

Now compiz works again. (although I lost all the setting I made.)

---

### Post by bmdavis on 2007-11-20
> **Forlong said:**
> bmdavis, what version of Ubuntu are you using?

Feisty Fawn.

---

### Post by Forlong on 2007-11-20
> **bmdavis said:**
> Feisty Fawn.
Then switch to more stable packages - see [here]("http://ubuntuforums.org/showthread.php?t=536149")

---

### Post by GameKing505 on 2007-11-20
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
```

That's my output for fglrxinfo, for whoever asked.

---

### Post by Forlong on 2007-11-22
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by GameKing505 on 2007-11-22
XGL is installed...

---

### Post by Forlong on 2007-11-23
I'm sorry, you are right. There are just too many outputs in this thread...

If you launch Compiz, are you sure it doesn't run at all or do you "just" miss the window decorations (I'm asking because there are no fatal error messages)?
You can check by holding [Alt] and grabbing the window with the mouse - if you are able to move it around, then Compiz is running.

---

### Post by GameKing505 on 2007-11-23
I can't alt-drag the windows, but when I push Alt-F4 to close them, it does the compiz closing animation, so idk what's up.

---

### Post by jdavis on 2007-11-23
Same thing happened to me, and for some reason it was caused by having gutsy's backports repository enabled. Somehow backports was reporting it had version 1:0.6.2 available, when the gutsy and gutsy-updates repo's were still showing as 1:0.6.0.

Removing compiz altogether, removing backports repository from source.list and then reinstalling fixed this for me.

---

### Post by GameKing505 on 2007-11-23
How would I go about doing this? I'm sorry for being so nooby.

---

### Post by jdavis on 2007-11-23
After further investigation it may not be the packages causing this, and may have been my nvidia driver. I will have to look into this further....

---

### Post by GameKing505 on 2007-11-23
Well I replaced the sources.list with the ubuntu sources generator thingy, and uninstalled/reinstalled, but the problem persists.

---

### Post by jdavis on 2007-11-23
Try going through the synaptic package manager, then find the nvidia-glx-new package, if it's installed, click it and go to "package/force version" and roll it back to the last version.

---

### Post by GameKing505 on 2007-11-23
As far as I know, I use ATI, not nvidia.

---

### Post by jdavis on 2007-11-23
in that case, try this

```
sudo gedit /etc/apt/sources.list
```

comment out any lines containing 'backports' by putting a # at the start of the line.


so 

```
deb http://archive.ubuntu.com/ubuntu gutsy-backports main
```

would become....

```
#deb http://archive.ubuntu.com/ubuntu gutsy-backports main
```



then run the following:

```
sudo apt-get remove compiz compizconfig-settings-manager
```

then

```
sudo apt-get update
sudo apt-get install compiz compizconfig-settings-manager
```

hit 'Y' at any prompts that appear.

---

### Post by GameKing505 on 2007-11-23
I don't have anything in my sources that contains "backports." I have the default sources. Also, I don't think the problem is the settings manager, because compiz doesn't work even if I select the "normal" setting, and as far as I know, the settings manager only affects the "custom" setting.

I realize I'm being a royal pain in the @$$ but I really appreciate your help. The ubuntu community is part of what makes the OS so great.

---

### Post by andrewbevitt on 2007-11-26
Make sure you remake any changes to /usr/bin/compiz ...

I'm using the binary ATI driver so I had to add fglrx to the WHITELIST variable; but those changes were over written when I upgraded compiz yesterday. Once I remade the changes compiz started working again for me.

---

### Post by SaiGoN DraGoN on 2007-12-08
[COLOR="Red"]i am using Ubuntu Gutsy  Gibbon; after the update my xserver hung there and did not let me in; so i had to reconfigure the xserver and changed the nvidia driver for the nv driver which is an older version of the nvidia. it let me in but compiz fusion was gone as well as AWN and Emerald. now my Ubuntu is just like Windows:(  i checked and it says that the nvidia driver was not enabled so i enabled it but when i reboot, it hangs again. compiz fusion (advanced desktop effects settings) works but nothing really happens. I ran some other aplications to make sure it was not just compiz fusion, then i realize that the graphic card is not actually working; Nexuiz is not as it was set up, and when i tried to activate the cube trhough gconf-editor all the parameters are correct. It has to be a problem with the Nvidia driver. a compatibility issue.  This totally sucks!!!!   should i downgrade to feisty fawn? or what should i do?[/COLOR]

---

### Post by awag on 2007-12-15
I'm running gutsy and some compiz stuff seems to have gotten messed up with the update for me as well. Compiz Fusion still works, however compizconfig-settings-manager won't load. Tried reinstalling it but still nothing. My previous compiz settings are also completely changed.

---

### Post by radioouman on 2007-12-19
I am having the same problem. Performed the updates and now Compiz is broken.
I have no desktop effects.  I cannot switch to other workspaces by clicking or by CTRL left/right.  I have no menu bars.

I am using a Dell Inspiron e1405 with Intel GM 945 graphics.  Ubuntu is now unusable since I cannot close any windows without right clicking on the bar at the bottom and choosing close.  Cannot get into the Advanced Desktop Effects Settings manager either.

---

### Post by Forlong on 2007-12-21
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by radioouman on 2007-12-21
Still have not been able to fix Compiz on my Inspiron e1405.  
When I go to a terminal and I type: "compiz" this is what I get:

```
$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

```

---

### Post by radioouman on 2007-12-22
After fiddling around with this for a while, I was finally able to solve it.
But first, the problems:
- In Compiz, I had no menu bars, although effects seemed to work
- In Metacity menu bars on windows would be so high that they were behind the task bar at the top.

I went into System -> Preferences -> Appearance -> Visual Effects and set it to None

Then I went into the Synaptic package manager, searched for "compiz" and chose "Mark for complete removal" on everything that was installed with the word "compiz" in it.   (By choosing complete removal, all configuration settings are removed too.)

Once removed, I rebooted.  Metacity was working fine and the menu bars were showing up where they are supposed to.  Then I sent back into the Synaptic package manager, searched from Compiz, and installed it.  I just picked Compiz and let it work out the dependencies.  

Now everything is working fine!

---

### Post by Nilks on 2007-12-24
There is a really simple solution to this problem which helped me out. It seems that the problem happens right after kiba-dock install. It will ask you to update your compiz and then the problem is present.

But you can solve it very easily. Remove the kiba-dock repo's from sources.list and then uninstall the compiz-settings thingie. Then install the thingie again, and it should work. You can then add the kiba-dock repo's again, but dont update the compiz-settings thingie when it asks you.

---

### Post by LUCKIT777 on 2007-12-25
Ya I did that It let me open the window to choose my preferences but in the apperance menu the custom effects settings wont stay selected , no error message , just thinks about then goes back to the none selection. any ideas??

---

### Post by Forlong on 2007-12-25
What's the output of ```
compiz
``` in a terminal?

---

### Post by LUCKIT777 on 2007-12-27
I got it I had enabled some unsupported plug-ins in the synaptic that was making it crash.
Thanks anyway!

---

### Post by lubeck on 2008-01-01
Hello:
I have the same problem and may have a causal effect - not sure.
I am also looking for help to resolve.
I have 3 machines running Ubuntu 7.10.  Issue surfaced after installing KIBA-Dock on all three.  Dock and all worked fine, including Compiz.

Within minutes of installing, however, I was prompted to download 2 Compiz UPDATES.
On 2 of the machines I downloaded/installed the Updates.  
Immediately thereafter, Compiz ceased to work - though a new "CompizConfig Settings Manager" listing appears in System, Preferences.  Selecting it does nothing.

The two Updates that occur - I continue to get bugged on the machine I am not allowing to Update, are ... indicate they are from Compiz Fusion Project: 
compizconfig-settings-manager from version 0.5.2+git20071010-0ubuntu1 to 0.6.0~git20071003+3v1ubuntu0
libcompizconfig-backend-gconf from version 0.5.2+git20071010-0ubuntu1..... same as prior

On the machine I DID NOT allow the updates to install upon - Everything continues to work fine - both KIBA and COMPIZ.

Not sure what all this means but there it is.
Help if you can...

---

### Post by lubeck on 2008-01-01
Oops.  Sorry.  I see someone already mentioned the KIBA association and a fix.
Does this get reported to the grater Ubuntu Org?

---

### Post by LUCKIT777 on 2008-01-01
On mine I enabled some repositories that were for fiesty when i loaded kiba and the update manager assumed i needed the old version of compiz and gave it to me. When i was disabling the software sources and uninstalling through synaptic i had enabled some unoffical and unsupported plugins that was making it crash in the apperance program when I clicked on custom effects. disabling them worked for me.

---

### Post by rrranch on 2008-01-06
I also have the same problem. My Gutsy 7.10 system was working fine before upgrade. As soon as I rebooted I lost compiz. Here is my output.
$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Is it possible to go back to the previous version of Compiz?

---

### Post by Forlong on 2008-01-07
There's no visible error in the output. What exactly is not working for you?

Oh, and what did you update anyway?

---

### Post by LUCKIT777 on 2008-01-08
It seems that I may not of explained it clearly. Check Synaptic Package Manager, search for compiz. Make sure there are no unoffical or unsupported plug-ins installed they can make compiz crash. Then check Software Sources make sure all is enabled. Except for any older versions of ubuntu. Then unistall through add & remove. Then reinstall through add remove. Thats what worked for me.

---

### Post by timbalisto on 2008-01-24
I have a similar problem to what you guys have. Compiz-Fusion desktop effects have allways worked fine for me until a recent update(I think). There are no effects enabled, I go to System>Preferences>Appearance and click the option to enable custom effects but the screen flashes white then pauses then I get an error message "Desktop effects could not be enabled". I can still open Advanced Desktop Effects Settings and configure plugins, but they still won't work. I followed the advice in this thread by completely uninstalling everything "Compiz" through Synaptic, rebooted, reinstalled Compiz, still doesn't work. I run Gutsy with an integrated Intel graphics controller and a 22' HD flat panel monitor running at 1680x1050, It always worked great before, even when I used experimental plugins. 

Here is the output of   dpkg -l | grep compiz
```

ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                            Compiz option code generator
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1                Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libcompizconfig0-dev                       0.5.2+git20070919-0ubuntu3                Development file for plugin settings - OpenC
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

```

here is the output of  compiz
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Please help.

---

### Post by LUCKIT777 on 2008-01-24
I had that problem once. I can't remeber what I did to fix it. I try and remeber.Let you know if think of it. It seems like it had something to do with the graphics driver. Iwas trying to install my card. It seems when i looked up that message it had something to do with the graphics driver.I will keep looking though.BEST OF LUCK

---

### Post by timbalisto on 2008-01-24
The driver I use is the "intel - Experimental modesetting driver for intel integrated graphics chipsets". I've always used this driver and everything used to work fine until very recently.

---

### Post by timbalisto on 2008-01-24
Sorry double post.

I solved my problem. I decided to install a video card, ATI Radeon x600. Used restricted driver for it. Edited xorg.conf to have compositing = 1 instead of 0. Downloaded xserver-xgl via synaptic, restarted X, and DESKTOP EFFECTS WORKED!  I'm happy now:)

---

