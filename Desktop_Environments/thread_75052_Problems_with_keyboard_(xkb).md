---
title: "Problems with keyboard (xkb?)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by tasuki on 2005-10-13
Hello,

I just upgraded from hoary to breezy. When I run gnome-keyboard-properties, tab "Layouts" and try to do anything, it says that there was a mistake activating XKB settings. It also gives the same error when starting a gnome session.

The error pop-up tells me to do this:

```
vita@doma:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "us", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "us", ""
```

and this:

```
vita@doma:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us,cz       cz]
 model = chicony9885
 overrideSettings = false
 options = [grp grp:alts_toggle]
```

I also tried changing keyboard model and layout in /etc/X11/xorg.conf, but it behaves the same whatever I do.

This is my first post here, I hope I didn't make any mistake like sending it into the wrong forum...

Thank you for your patience,
Vit

---

### Post by cthulahoops on 2005-10-13
G ja.d kj...  I have the same problem after upgrading.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "dvorak", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "dvorak", "", ""

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [gb  dvorak,dvorak   gbtd,gb]
 model =
 overrideSettings = false
 options = [grp grp:alts_toggle]

Also:

$ setxkbmap dvorak
Error loading new keyboard description

I'm stuck some hybrid US/UK qwerty.

Thanks,
Adam.

---

### Post by xfranky on 2005-10-13
Same here. I've always used the us_intl layout on any distribution (as for being italian with a us keyboard), but for some reason it doesn't seem to work in 5.10.
As soon as I select the U.S. Internetional layout in the keyboard layout configuration window the theme engine reloads and the layout doesn't get applied.

As above here are the results of the specified commands:

```
xf@xf1:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "us_intl", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "intl", ""
xf@xf1:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us  intl]
 model =
 overrideSettings = true
 options = []
```


As a side note I just noticed that while writing this post the layout has somehow changed and it seems now to be us_intl, but I fear it won'tlast past the next login. Let's see...

---

### Post by paulle on 2005-10-14
same happen to me.  paulle

---

### Post by mpiktas on 2005-10-14
Can confirm this problem on HP nx9105 notebook, with Lithuanian layout. All happened when I've upgraded from Hoary to Breezy. Any help would be greatly appreciated.

---

### Post by bertilow on 2005-10-14
I'll add my voice here. I'm trying to get the Swedish keyboard to work, but nothing happens. I get the word "err" in the system tray instead of the keyboard symbols.

And that's just one of the problems I have after "upgrading" to Kubuntu Breezy. :mad:

---

### Post by tasuki on 2005-10-15
Well, I am happy that I am not alone with the problem, we are at least six... what confuses me is that noone seems to know the solution... :(

Some further info:
I can setxkbmap cz and us, but not cz_qwerty (which is what I want) and several others, it says "Error loading new keyboard description."

I would be very grateful for the solution,
Vit

---

### Post by bertilow on 2005-10-15
[QUOTE=tasuki]Well, I am happy that I am not alone with the problem, we are at least six... what confuses me is that noone seems to know the solution... :([/QUOTE]

Have a look at my possible (but not complete) solution in another thread:

[http://www.ubuntuforums.org/showthread.php?t=76261](http://www.ubuntuforums.org/showthread.php?t=76261)

---

### Post by takuzinis on 2005-10-16
Similar discussion here:

[http://ubuntuforums.org/showthread.php?t=75197](http://ubuntuforums.org/showthread.php?t=75197)

---

### Post by F for Fragging on 2005-10-16
All of these problems are probably related to this - [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) - bug. It's quite a serious bug, but it was too late to implement a fix in Breezy. Download the packages which are mentioned in the comments on the bugreport there, that solved my problem.

---

### Post by bertilow on 2005-10-16
[QUOTE=F for Fragging]All of these problems are probably related to this - [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) - bug. It's quite a serious bug, but it was too late to implement a fix in Breezy. Download the packages which are mentioned in the comments on the bugreport there, that solved my problem.[/QUOTE]

I tried those files, but they didn't help. The reason could be that I hade customized some of the keyboard layout files in Hoary. (When did anyone warn me that touching anything might make it impossible to upgrade later?) In the end I could never get the settings in "Compose" to be used (they worked in sudo mode only!), and there seemed to be some many other things breaking after the upgrade to Breezy. So I made a clean install instead. And now I'm in the process of reinstalling all my programs and adaptations. It will probably take a long while. I wish a simple upgrade would have been possible. :(

---

### Post by pflumm on 2005-11-03
I had also modified my layout to change right Windoze key to a ctrl key...

So setxkbmap only reported "Error loading keyboard layout".

What helped for me was (as root) to go to /etc/X11/xkb/symbols and move the pc directory to pc_old

mv pc pc_old

Then do a 

cp pc.dpkg-new pc

Any customisation done to /etc/X11/xkb/symbols/pc/pc can then be done to /etc/X11/xkb/symbols/pc. You can then remove the pc_old directory.

This was one of the solutions given in the bug report mentioned in this thread. It seems that in breezy, the pc directory has been removed, which confuses the update.

---

### Post by Saul Perdomo on 2005-11-03
[QUOTE=F for Fragging]All of these problems are probably related to this - [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) - bug. It's quite a serious bug, but it was too late to implement a fix in Breezy. Download the packages which are mentioned in the comments on the bugreport there, that solved my problem.[/QUOTE]

Great advice, thank you that worked great. I now can type my accented characters, which is fantástico!

As I'm pretty certain that all users who upgraded from 5.04 to 5.10 --and who also use a keyboard layout other than standard US-- have this same problem, I will post the steps I took in order to help them save a little time:


Step 1: Get the files

As root (die sudo die!) type in a console (p.s. - you can find one in Accesories -> Terminal):
```
wget http://people.ubuntu.com/~daniels/libxkbfile1_7.0.0-3_i386.deb http://people.ubuntu.com/~daniels/xkeyboard-config_0.6-6_all.deb
```

Step 2: Install the downloaded packages

Again, as root type in a terminal:
```
dpkg -i libxkbfile1_7.0.0-3_i386.deb xkeyboard-config_0.6-6_all.deb
```
Hopefully that'll go smoothly, as it did for me.


And, Step 3: Re-select your keyboard layout in the gnome-keyboard-properties application

You can find it in System -> Preferences -> Keyboard. You're gonna have to fiddle around with it for a while, until everything's back to normal. In my case, what I did was set as default some other keyboard layout other than the one I wanted (Latin American), and then set my layout as default again. Oh, and as I found out later on, you also have to set the "Alt/Win key behavior" as "Default" in the "Layout Options" tab if you want your AltGr key to work properly.

That's it! HTH.

---

### Post by Ricardo Dahab on 2005-12-22
This is my first posting. I had the same problems you all had with your keyboard accents. Following Perdomo's instructions worked beautifully. Thank you all.

Ricardo

---

### Post by UphillSkier on 2005-12-24
[QUOTE=Ricardo Dahab]This is my first posting. I had the same problems you all had with your keyboard accents. Following Perdomo's instructions worked beautifully. Thank you all.

Ricardo[/QUOTE]

It worked beautifully for me as well.  Thank you, Saul Perdomo.:D

---

### Post by Domie on 2005-12-26
same here... Finally...

---

### Post by easy_target on 2006-01-04
Is there a way to put this solution visible or in the wiki? It seems to be a recurring problem in Breezy and it would help people trying to work with dead-keys.

---

