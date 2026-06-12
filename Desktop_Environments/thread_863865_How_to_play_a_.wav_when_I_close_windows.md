---
title: "How to play a .wav when I close windows?"
date: 2008-07-18
forum: Desktop Environments
---

### Post by jerome1232 on 2008-07-18
I'm not sure if this is a Gnome thing or a Metacity thing,
but I've found a wav file I would like to have play
when I close a window. I looked under system>>
preferences>>sound and that is not one of the options.

Does anybody know how to get Gnome/Metacity to play
a sound when I close windows?

edit:dang typos!

---

### Post by pauper on 2008-07-19
Could you elaborate more on kind of windows we're talking?

---

### Post by jerome1232 on 2008-07-19
Well any and all windows I have open, like firefox for example, or a Terminal, or well just any open window. Kind of like how KDE will play a system sound when you minimize and close windows.

On Compiz I have the burn effect on for closing windows and I got a wav file that sounds like a rush of flame.

---

### Post by pauper on 2008-07-19
GNOME sound server manages such events.

Conclusion:
(Gutsy) Config files are here:
$HOME/.gconf/desktop/gnome/sound
$HOME/.gnome/sound/events/gnome.soundlist
$HOME/.gnome2/sound/events/gnome-2.soundlist

[edit]: /usr/bin/gnome-sound-properties is hardcoded.

At this point it seems to me there are three choices:
1) find if there is some other utility, which is capable of managing custom
sound events;

2) ask for this feature for any next gnome release;
(Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>)

3) download the source code, rewrite relevant part, compile and install it
[http://packages.ubuntu.com/hardy/gnome-control-center](http://packages.ubuntu.com/hardy/gnome-control-center)

---

### Post by jerome1232 on 2008-07-19
Thanks, seeing as the most my programing goes is an area calculator in python, I'll look into filling a feature request and looking harder for an utility. If do find an utility I'll slap a link down here in case anyone else is interested in that functionality.

---

### Post by umecn2005 on 2008-10-25
Looks like the source code is written in C. Question, I want to change the source code to add this close window sound event. How do I do it?

What packages do I need to download to develop code? Is there an API I can work from? Once I've written the code, how can install it?

If there's a section on developing code for ubuntu somewhere else on the site to help me get started, please let me know, thanks.

---

### Post by jerome1232 on 2008-10-25
I know nothing of API's :) but vim, gedit, emacs, kate are pretty popular with code developers. They are just text editors that are capable of syntax highlighting and other advance features (in the case of vim/emacs very advanced features) If you want a full featured IDE eclipse is pretty nice.

You might want to try the [Development & Programming forums]("http://ubuntuforums.org/forumdisplay.php?f=310")

---

