---
title: "Yet more Compiz Fusion and KDE Problems"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by cawill on 2007-11-09
I'm trying to get compiz fusion to run on my kubuntu desktop, and it does finally work apart from window decerations.

I need to use this command to run compiz fusion:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace 
```

But I can't get emerald or kde-window-decorator to work, so I have NO window decorations.

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace  -c emerald
```
Doesnt work as the emerald plugin comes out with an error.

Can anybody help? Thanks in advance, Chris.

---

### Post by Zorael on 2007-11-09
I'm not completely sure I follow, so bear with me.


First of all, did you upgrade from Feisty?

Compiz has some issues with KDE backend configuration, which can be circumvented by using a flat-file configuration instead. Open up the settings manager, export your profile someplace, change to Flat-file Configuration, import it again. Start compiz and add **ccp** as an argument.

```
LIBGL_ALWAYS_INDIRECT=1 compiz ccp --ignore-desktop-hints
```

This will make it use its own flat-file format, which seems to work better. You can also add **decoration** to force it to load the Window Decorations plugin if you have issues with getting it to load, but I gather you're not.


As for the --ignore-desktop-hints, you may want to add it to avoid "some" issues with the desktop switcher (pager) applet not playing nice with Compiz. Furthermore, I don't think you need the --replace argument anymore, and I'm fairly sure -c emerald is also deprecated.

---

### Post by cawill on 2007-11-09
Ok thanks for your help so far, and its a fresh gutsy kubuntu install.

you mean this right?
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp --ignore-desktop-hints 
```

that gives me no window decerations still, windows deceration plugin is set to:
```
kde-window-decorator --replace
``` is that right?

this is the terminal output for your command:
```
chris@sony:~$ LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp --ignore-desktop-hints
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Error: Couldn't load plugin 'ccp'

```

Can you help further?

---

### Post by Zorael on 2007-11-09
Most odd. ccp should work. Do you have all the Compiz packages installed? Like, compiz-fusion-plugins-main and -extra?

```
zorael@azrael:~$ locate libccp
/usr/lib/compiz/libccp.so
```

On another note, just to troubleshoot, have you tried it with Emerald? I couldn't run kde-window-decorator myself, it crashed when I tried to start it, whereas I find Emerald to be stable enough.

And again, I believe you don't need the --replace argument anymore.
```
__GL_YIELD="NOTHING" compiz --loose-binding --ignore-desktop-hints ccp &
```

---

### Post by cawill on 2007-11-09
Yes they are all installed, and the 'locate libccp' command brings up the same output as you.
Yes I still need to the --replace command as it says another window manager is running.
My problem really isnt with kde and compiz, its just getting the window decorations showing, any advice on how to do that?

---

### Post by Zorael on 2007-11-09
I first thought it was an issue with plugins not starting, which happens. The Window Decorator plugin is supposed to start your decorator of choice, but if it refuses to, you end up without borders. You do have the Window Decorator plugin enabled, I hope. Regardless, switching to flat-file eliminate most if not all weird issues with settings not sticking, hence my advice. Also, it could be kde-window-decorator just refusing to cooperate.

Again, try Emerald to see if *it* works. If it does, kde-window-decorator is the culprit.


edit: I just noticed, unable to parse XML metadata from file core.xml?
```
zorael@azrael:~$ locate compiz/core.xml
/usr/share/compiz/core.xml
```

---

### Post by cawill on 2007-11-09
I get what you mean now, is the unable to parse XML metadate from file core.xml a problem?

---

### Post by Zorael on 2007-11-09
It could very well be, at least. Does the file exist on your system?

I imagine it's a part of the compiz-core package.

---

### Post by cawill on 2007-11-10
```
chris@sony:~$ locate compiz/core.xml
/usr/share/compiz/core.xml
chris@sony:~$

```

Yes it does, but only root has read / write access to that file, is that a problem?

---

### Post by cawill on 2007-11-10
I did try and install compiz fusion a while ago using the latest release, but I got error's with the automated installers, would this incomplete install cause these errors?

---

### Post by Zorael on 2007-11-10
Well, only root should have write permissions, but you need to have read permissions or else it might as well not be there.

"Latest release"? Where did you get that?

I can't help you with anything else than the version in the official repositories. And that should work from a fresh install (meaning, completely removing an old one, making sure to remove/comment foreign repositories, update from software sources, installing it again).

The most common issues stem from remnants of old and/or incompatible Compiz installs; either from Amaranth/Treviño/similar repositories, from git sources, etc.

Then again, it could be an issue with the settings on your videocard. What kind do you use? I believe I never asked that.

---

### Post by cawill on 2007-11-10
Latest release was from the GIT Repositories, but I want to completely remove any file this may have created as It might create a problem, so which locations would compiz fusion install files in? Then I will use the Compiz fusion from the offical repositores.

I have a ATI Radeon 9600 and Xorg config is fine (with open drivers).

Thanks for your help with this problem.

---

### Post by Zorael on 2007-11-10
Ah, okay.

```
$ sudo apt-get remove compiz* libcompiz* libdeco* emerald* libemerald*
```

Update from software sources, and then reinstall.

The following command should output this if you succeed.
```
zorael@azrael:~$ apt-cache policy compiz-core
compiz-core:
  Installed: 1:0.6.0+git20071008-0ubuntu1.1
  Candidate: 1:0.6.0+git20071008-0ubuntu1.1
  Version table:
 *** 1:0.6.0+git20071008-0ubuntu1.1 0
        500 http://se.archive.ubuntu.com gutsy-updates/main Packages
        500 http://security.ubuntu.com gutsy-security/main Packages
        100 /var/lib/dpkg/status
     1:0.6.0+git20071008-0ubuntu1 0
        500 http://se.archive.ubuntu.com gutsy/main Packages
```

You could also remove your profile and all settings, if you wish.
```
$ rm -r ~/.config/compiz
```

---

### Post by cawill on 2007-11-10
Hi I did all of that, and deleted all traces of compiz from my system ( and removed deb files from the apt cache) , only thing is I now have this error which is caused by missing files (I think), I also don't understand the part about metacity as I don't even have that WM. Can you help?

One thing I did notice on this was I can now use 'Compiz --replace' as 'Texture_from_pixmap' is found so something is working at least :)

```
chris@sony:~$ compiz --replace -c emerald
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4152 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
exec: 378: /usr/bin/metacity: not found
chris@sony:~$          
```

EDIT: Compiz --replace and LIBGL_ALWAYS_INDIRECT=1 compiz --replace have the same effect.

---

### Post by Zorael on 2007-11-10
It tries to start Metacity (which is part of the compiz-gnome package, I believe), since it requires a window decorator. You have to pick between it and Emerald, I guess. Make sure to enable the Window Decorator plugin in the settings manager, and enter its replace command in the Command field. (in other words; emerald --replace)

Did you compare the package version with the blot of terminal output text I pasted?

I don't have an /usr/local/bin/compiz folder either, so likely it's either the missing window decorator, or there's still some incompatible remnant somewhere you haven't completely removed.


edit: Don't forget --ignore-desktop-hints. :>

---

### Post by cawill on 2007-11-10
I now have the Compiz Gnome Package and Metacity installed and any command I put in brings up the same error.
I'm sure theres no previously installed files of compiz on my system before I installed the current version as I searched my whole hrad disk.
Is there anyone that has the /usr/local/bin/compiz folder?

Is there any repository to install beryl on my system? or do I have to wait for kwin --compositing? As reinstalling is not really an option.

---

