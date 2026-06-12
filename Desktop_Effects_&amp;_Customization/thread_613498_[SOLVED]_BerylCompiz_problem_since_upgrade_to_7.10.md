---
title: "[SOLVED] Beryl/Compiz problem since upgrade to 7.10"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by devilears on 2007-11-15
Beryl was running beautifully when I was still on kubuntu 7.04. However, since upgrading to 7.10, things degraded dramatically. Whenver I select either Beryl or Compiz from the Beryl Manager icon in the taskbar, all my apps open without the title bars, scrollbars etc. This means that i cannot move the around, minimize, click close etc. I've included two screenshots. Anyone seen this? How to fix please?

:confused:

---

### Post by Zorael on 2007-11-15
Okay.

edit-- firstfirst, make sure you don't have any foreign repositories in your software sources, such as Treviño's or Amaranth. You'll want to stick with the official gutsy repos for this one.


First of all, as an upgrader, you're slightly disadvantaged as you have some remnants of old Compiz/Beryl left in your system. I'd recommend you get rid of these - it may not be necessary, but they may potentially mess things up.

To do so, find and **request purging** of everything you can find in Adept Manager (adept_manager) that even rhymes with compiz, beryl, and emerald.

The terminal way would be:
```
sudo apt-get **purge** compiz* libcompiz* libdeco* emerald* libemerald* beryl* libberyl*
```
(I'm not sure about libberyl*, but meh)


Anyway. It seems you're not running a Window Decorator. Your two (only? major?) options would be kde-window-decorator and emerald. I've had *zero* luck with kde-window-decorator - it crashes whenever I try to start it - but emerald works great.

You can get kde-window-decorator by installing the compiz-kde package, and emerald by installing the emerald package.

Once either is installed, you'll need to enable the Window Decorations plugin in the configuration manager (ccsm; if you don't have it, install the compizconfig-settings-manager package). In its options, make sure the Command field is set to 'emerald --replace', or 'kde-window-decorator --replace'; whichever you choose to use.

To try it out, open up a terminal, and from there enter 'compiz --replace --ignore-desktop-hints &'. You will want to use the --ignore-desktop-hints to be able to get the amount of virtual desktops you want. If you get any interesting error messages output to the terminal, copy them and paste them here.

To revert back, enter 'kwin --replace'.


Lastly, **if you have an Nvidia card**, you may need to add some options to the Screen and/or Device section of your /etc/X11/xorg.conf file, if it still doesn't work after having done the above. Again, only for Nvidia cards:

```
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
```

Further, you could start compiz with the following line for further tweaks, though not necessary.
```
__GL_YIELD="NOTHING" compiz --loose-binding --ignore-desktop-hints ccp &
```
They work for me, but your mileage may vary.

---

### Post by devilears on 2007-11-15
OK, I have done the "purging" of the packages. What exactly do I now apt-get install?, Or do I now use Adept Installer to install compiz?

---

### Post by Zorael on 2007-11-15
Either works.

You'll want:
[LIST=1]
[*]compiz-core
[*]compiz-bcop
[*]compizconfig-settings-manager
[*]compiz-extra
[*]compiz-fusion-plugins-extra
[*]compiz-fusion-plugins-main
[*]compiz-kde
[*]compiz-plugins
[*]emerald
[/LIST]

```
$ sudo apt-get update
$ sudo apt-get install compiz-core compiz-bcop compizc* compiz-extra compiz-f* compiz-kde compiz-plugins emerald
```

The 'compiz' package alone is tailored towards Gnome and won't get you compiz-kde, while instead installing some gnomery stuff you won't need. :>

The interesting part comes when you get to the window decorators. This is merely making sure you're on the correct page.

---

### Post by devilears on 2007-11-15
OK, installed all the packages you suggested. where do I now "enable the Window Decorations plugin in the configuration manager " ? In System Settings somewhere?

---

### Post by Zorael on 2007-11-15
The CompizConfig Settings Manager, **ccsm**. If it's not in the menu somewhere, just run it from a terminal or a run box.

---

### Post by devilears on 2007-11-15
GREAT!!! got it working! Thanks a lot!

---

