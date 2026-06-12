---
title: "Compiz being very slow"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by ProbablyX on 2008-04-19
Hello,

Even if this sounds like a common error, I have been browsing the forum and haven't found an answer so here I go =)

I've just installed "basic 3D effects" in the desktops effect program that comes with Kubuntu. When I start KDE it goes really slow (even though all it starts is Kopete), it like lags.
I can move windows (though there is no effect for this), I can switch desktops (they "roll" to the next one, and I can open and close windows (works semi-ok) but when I try to resize a window the computer freezes for like 5 seconds.

That is: it seems some 3D features work and others dont... My friend can run full effects on his intel graphics card. I have a Geforce 8600GT, an amd64 x2 6000+ cpu, 2GB ram (Kubuntu 8) so there shouldnt be any hardware issue (yes I am using nvidia drivers)

Is there anyway to check compiz logs or so? So I can find out why certain effects work and others dont?
Also when I click "logout" I get scattered lines over the screen, like a graphics glitch.

I installed Compiz via the desktop effects program.

Thanks :)

---

### Post by Zorael on 2008-04-19
The log out effect collides with Compiz, yes. I don't have the link available right now but that part is fixable.

As for being very slow; what is the terminal output from the following command?
```
$ compiz --replace --loose-bindings --ignore-desktop-hints &
```

Also, sooner or later, you'll want to install the **compizconfig-settings-manager** package (via Synaptic or via a terminal; **sudo aptitude install compizconfig-settings-manager**) to get the proper settings manager.

---

### Post by ProbablyX on 2008-04-19
Thanks for replying :)

> 
~$ compiz --replace --loose-bindings --ignore-desktop-hints &
Checking for Xgl: [1] 17979
not present.
Detected PCI ID for VGA: 03:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Warn: Unknown option '--loose-bindings'

Segmentation fault
kwin: Okänd väljare "--loose-bindings".
kwin: Använd --help för att få en lista med de tillgängliga kommandoradsväljarna.

The last two lines saying theres no known parameter called loose-bindings and that --help can be used to view available parameters

Thanks!

---

### Post by Zorael on 2008-04-19
Well, that was supposed to be --loose-binding and not binding**s**. My bad.

It segfaulted, though. Are you sure it's working? It looks to me like Compiz crashed before it could start.

---

### Post by ProbablyX on 2008-04-19
Well when I minimize the window shrinks into the statusbar and I get the swooshy effect changing desktops =/

I tried installing some settings manager (after changing to manual in the desktops effect apps, and logging out and in again) from aptitude and it gives me this:

> 
~$ simple-ccsm
Traceback (most recent call last):
  File "/usr/bin/simple-ccsm", line 28, in <module>
    import gtk.glade as glade
ImportError: No module named glade


I don't know if that means anything...

Running this:
```
compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 03:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Segmentation fault

```

still keeps compiz open, the screen flashes and it leaves an empty line after the command, that is the command is still running I cannot enter a new one

---

### Post by ProbablyX on 2008-04-19
OK I also get fade-ins and fade-outs.

After running "compiz" in the terminal I tried Ctrl+Z (force quit) and the X server just froze, THOUGH amarok continued to play. But everything was frozen solid visually

I have also noticed that I can change window order.

Kopete starts first, then if I start Konqueror I can move it arround, but if I klick Kopete I cant get it to show on top of Konqueror, it remains behind

---

### Post by Zorael on 2008-04-19
Well, that simple-ccsm doesn't seem to be working. Try to find compizconfig-settings-manager. :>

As for you not being able to enter more commands into the terminal, you should add an ampersand (& sign) after the command to make it run in the background.


Is this in Gutsy? If so, did you upgrade from Feisty?
Have you added any extra eyecandy repositories to your software sources?

---

### Post by ProbablyX on 2008-04-19
compizconfig-settings-manager cant be found.

I just meant that as I couldnt enter any command compiz must still be up and running (as you were talking about the segmentation error there)

---

### Post by ProbablyX on 2008-04-19
> **Zorael said:**
> Well, that simple-ccsm doesn't seem to be working. Try to find compizconfig-settings-manager. :>

As for you not being able to enter more commands into the terminal, you should add an ampersand (& sign) after the command to make it run in the background.


Is this in Gutsy? If so, did you upgrade from Feisty?
Have you added any extra eyecandy repositories to your software sources?

Sorry didn't see the last text!

This is Kubuntu 8.04, a fresh install.

I only have virtualbox respos except for the standard ones

---

### Post by Zorael on 2008-04-20
Huh, can't be found? Make sure you enable the universe repositories in Software Sources.
```
$ apt-cache policy compizconfig-settings-manager
```
Do note that it's a package and as such needs to be installed through Synaptic (or similar), or via a terminal. [It should exist.](http://packages.ubuntu.com/hardy/compizconfig-settings-manager)
```
$ aptitude install compizconfig-settings-manager
```


Okay, I realize this has become very messy.
[list][*]You want to run compiz with the command I posted first, to get your number of desktops down to the set amount.
[*]You want to install the settings manager to get a better grip of your compiz settings. The simple-ccsm app didn't seem to work anyway, from what I can tell?
[*]If you "lose control" over your windows (no titlebars or borders, can't move windows or switch focus, nothing really works), that means you're not running a window decorator. Once you have the settings manager (CCSM) installed, make sure to tick the Window Decorator plugin. I also suggest you install Emerald (package name **emerald**); it's Compiz's standard decorator. You can set things up later to run kde-window-decorator instead if you really prefer the KDE themes (Emerald has its own), though I'd start out with Emerald - in my experience, it's more stable, though I haven't tried the Hardy version yet.
[*]If you run compiz and lose borders, before you panic and restart your computer, enter the following in your (hopefully) open terminal.
```
$ kwin --replace &
```
That should return things back to normal. Further, you shouldn't need to restart the whole system; Ctrl+Alt+Backspace will restart the X server (the graphical interface), which should be enough.


[*]If you lose terminal control after entering any command, that means you left out the ampersand (&) at the end. **This ampersand is not necessary to add if you run the commands via a run box (Alt+F2).** In fact, the command you run may terminate anyway when you close the terminal window with the X button, but stay running if you do it by typing **exit**. At this point, we want to run things through the terminal, though, since it's the output we're interested in.
[*]The segfault is still alarming, but from what I can tell Compiz still loads, hmm? So let's just proceed and assume that it's not relevant.[/list]

---

### Post by ProbablyX on 2008-04-20
My sources file has these entries, so theres universe in them:
> 
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates universe


Now apt-get says compizconfig-settings-manager is already the latest version when I run install.

"locate"'ing settings-manager now gives:

> 
locate compizconfig-settings-manager
/usr/share/doc/compizconfig-settings-manager
/usr/share/doc/compizconfig-settings-manager/AUTHORS
/usr/share/doc/compizconfig-settings-manager/changelog.Debian.gz
/usr/share/doc/compizconfig-settings-manager/copyright
/usr/share/pyshared-data/compizconfig-settings-manager
/var/cache/apt/archives/compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb
/var/lib/dpkg/info/compizconfig-settings-manager.list
/var/lib/dpkg/info/compizconfig-settings-manager.md5sums
/var/lib/dpkg/info/compizconfig-settings-manager.postinst
/var/lib/dpkg/info/compizconfig-settings-manager.postrm
/var/lib/dpkg/info/compizconfig-settings-manager.preinst
/var/lib/dpkg/info/compizconfig-settings-manager.prerm


And this is what I get from starting compiz:
> 
~$ compiz --replace --loose-binding --ignore-desktop-hints &
Checking for Xgl: [1] 11638
~$ not present.
Detected PCI ID for VGA: 03:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


No segmentation error any longer :)

The question is how to open the settings manager now.. I think..

Thanks :)

---

### Post by ProbablyX on 2008-04-20
OK after googling for a while I found out I was missing "python-glade2" so after installing it the Simple Compiz config started working, The slowness remains though =/ Also: whats the "big" settings manager called? (So I can check in it for the rezise issues?) -UPDATE: I found ccsm, testing it now Thanks :)

Also changing settings in the compiz settings manager just cashes kwin :S There's also "traces of graphics" when I move / minimize windows on the screen :S is that normal?

---

### Post by ProbablyX on 2008-04-20
OK :) as long as I dont use normal resize Compiz works, and when emerald runs most errors disapear.

The only remaining issues are that compiz prints out these errors constantly in the console:
> 
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Close event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Close event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.


Thanks :)

---

