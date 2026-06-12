---
title: "No text mode with Compiz Fusion"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by lomion on 2007-06-29
Hi!
I've installed Compiz Fusion after using Beryl. Everything looks great but there is a problem. When I switch to the text mode (Alt Ctrl F1-F6) the terminal looks is blank and I can do nothing. 

(I use compiz with --indirect-rendering to prevent problems includes black screen and invisible windows!)

Feisty Fawn 7.04.
Dell XPS m1210: nVidia 7400.

---

### Post by fakeollie on 2007-06-29
I have the exact opposite problem. Whenever I jump to terminal mode (^Alt-F1...F6), it works, but I can't come back to X. When I go ^Alt-F7, the screen comes up blank, except for the mouse pointer. 

And when that happens, it's gone. I can't go back to any terminal, or do anything but a hardware reset. It's frustating.

I use Beryl not Compiz Fusion, however. I'd love if someone with more experience could enlighten both of us as to any problems using these window managers and switching to tty modes.

---

### Post by casanostra on 2007-06-30
> **fakeollie said:**
> I have the exact opposite problem. Whenever I jump to terminal mode (^Alt-F1...F6), it works, but I can't come back to X. When I go ^Alt-F7, the screen comes up blank, except for the mouse pointer. 

And when that happens, it's gone. I can't go back to any terminal, or do anything but a hardware reset. It's frustating.

I use Beryl not Compiz Fusion, however. I'd love if someone with more experience could enlighten both of us as to any problems using these window managers and switching to tty modes.

Exact same setup, exact same problem here.

---

### Post by casanostra on 2007-06-30
Forcing AIGLX solved the problem for me, using nvidia.

See [http://ubuntuforums.org/showthread.php?t=396806](http://ubuntuforums.org/showthread.php?t=396806).

---

### Post by fakeollie on 2007-07-02
> **casanostra said:**
> Forcing AIGLX solved the problem for me, using nvidia.

See [http://ubuntuforums.org/showthread.php?t=396806](http://ubuntuforums.org/showthread.php?t=396806).

I'll try that as soon as I can have everything closed/stopped here (in case I need a hard reset again).

By the way, I forgot to mention I'm too using a Nvidia card (geforce 6200) and the restricted drivers. Also, when I turn off beryl and go back to metacity, everything works as it's supposed to.

I further noticed that when I go to a terminal (^Alt+F1, it works) and I try to come back (^Alt+F7, that's where the bug is), while I'm frozen on a black screen, although the mouse pointer shows and moves around, the keyboard stops responding. Caps/Num lock leds don't even respond. That's probably why I can't go back to a terminal to stop/restart gdm.

Anyway, thanks for the tip casanostra. I'm glad it now works for you.

---

### Post by casanostra on 2007-07-02
I would return from a virtual terminal to the exact same black screen with only the mouse pointer visible, as you describe. However, I would then be able to go back to a virtual terminal (and kill beryl in order to fall back to metacity) and return my desktop without having to restart gdm. If I did alt-f7 a second time from a virtual terminal, though, my system was completely unresponsive.

Just for the sake of completeness.

---

