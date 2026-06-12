---
title: "Openbox &amp; bluetooth-applet: how do I tell Nautilus not to manage the desktop?"
date: 2009-02-27
forum: Desktop Environments
---

### Post by Piraja on 2009-02-27
Dear all,

a question I could not find an answer to by a quick look-up. I'm having Intrepid with Openbox as an optional WM, and Bluetooth-Applet as one of the autostarted apps:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

export OOO_FORCE_DESKTOP=gnome

nitrogen --restore & # comment this if you want Feh to set the background (see line 12)
pypanel &
nm-applet &
gnome-volume-manager &
update-notifier &
xcompmgr &
bruce-type &
# bluetooth-applet & # Calls up Naughty Nautilus if ya don't watch out!

#eval `cat $HOME/.fehbg` & # uncomment this to let Feh set the background (see line 6)
```

Now if I use Bluetooth-Applet to browse files in a device, it brings up Nautilus, which would be fine if I just could make it "nautilus --no desktop" instead of Naughty Nautilus taking over.

Openbox :guitar: and you :guitar: too, even more so if you can tell me how to keep Naughtilus from playing its solos for a while! :lolflag:

---

### Post by Piraja on 2009-03-01
Alright, I guess I found the right how-to, at the [#! Forums]("http://crunchbanglinux.org/forums/topic/84/using-nautilus-under-openbox/"). Still had no chance to try it, though, but will as soon as I get my hands on the laptop with both Gnome & Openbox...

_Later_: Yes, works beautifully. I cordially recommend [Corenominal's instructions]("http://crunchbanglinux.org/forums/topic/84/using-nautilus-under-openbox/") — this is how the beginning of my autostart.sh looks now:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

export OOO_FORCE_DESKTOP=gnome

nitrogen --restore & # comment this if you want Feh to set the background (see line 23)
pypanel &
nm-applet &
gnome-volume-manager &
update-notifier &
xcompmgr &
bruce-type &
bluetooth-applet & 
# Disable Nautilus desktop.
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background image.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &
# Make Nautilus use spatial mode, should start-up quicker.
gconftool-2 -s -t bool /apps/nautilus/preferences/always_use_browser false &
# Make Nautilus show the advanced permissions dialog 
gconftool-2 -s -t bool /apps/nautilus/preferences/show_advanced_permissions true &

#eval `cat $HOME/.fehbg` & # uncomment this to let Feh set the background (see line 6)
```

_Later still_: See also [a screenshot]("http://ubuntuforums.org/showpost.php?p=6818286&postcount=14") of the bad boy in action.

---

### Post by thtrgremlin on 2009-03-01
Interesting problem and solution. I am working on a project where that will be useful. Thanks for posting an answer, even though you were the only one.

---

### Post by der_joachim on 2009-03-01
I have stopped using nautilus, but there is a command line option, that explicitly disables desktop management. It is something like --nodesktop, but you should be able to read it in the nautilus documentation.

---

### Post by Piraja on 2009-03-01
Der_Joachim, thanks, I know &#8212; the point in my question was that "nautilus --no-desktop" is not the answer in such cases when I use e.g. bluetooth-applet, which calls Nautilus, etc. etc. In any case, my second post in this thread contains an answer that seems perfect, so this thread is indeed SOLVED (no "Mark this thread as solved" option is offered at the time of writing this, too bad).

---

