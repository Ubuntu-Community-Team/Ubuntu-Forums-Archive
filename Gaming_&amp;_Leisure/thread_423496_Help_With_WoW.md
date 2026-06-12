---
title: "Help With WoW"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by XxZtemxX on 2007-04-25
Hi Guys... I'm relatively new to Linux, i just installed Fiesty...


I successfully copied all of my WoW CD Files onto my Hard Disk, and installed it

It runs very very very very.... very choppy though. i cant even get past the main menu. My computer is just barely up to par with WoW, i ran it on Windows a while ago and it was fine, so i dont think running it on Linux should be any different (for the worse at least). Any ideas/help?

I dont know what kind of Video Card i have, its some Dell Integrated PoS that is about 4 years old.

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (If that helps any....)

Also, i was wondering... in my excitement/frustration to get WoW installed, i saved the files in like C:/ProgramFiles/ ...which i know is a Windows Directory... where are they now? :-|


Thanks for any advice/help. :)

---

### Post by hikaricore on 2007-04-25
Intel drivers for linux aren't great, my guess is you're using the i810 intel driver.

This is NOT a fault of linux, but rather Intel being lazy and stopping their development of the drivers for your card series in 2004 (or so).
The linux community has since updated the drivers, but the drivers & your card have terrible opengl support which is required to run WoW under linux.

I'm by no means saying you can't run WoW on your system, it's worth a shot, but success stories with that card aren't flooding these forums.

First check to see if you have direct rendering enabled:

Alt+F2 then type: **gnome-terminal**
and click run (open or whatever it says)

In the terminal type:

```
glxinfo | grep rendering
```

If this returns _Direct rendering: no_

Search around the forums for howto setup hardware rendering on your card with the i810 driver.

If you're unsure which driver for intel series cards you're using type (in the same terminal window)

```
cat /etc/X11/xorg.conf | grep Driver
```

It will return something like this:

>     Driver         "kbd"
    Driver         "mouse"
    Driver         "_nvidia_"

Where mine says nvidia yours will say most likely "i810".

---

### Post by XxZtemxX on 2007-04-26
Hi... thanks for the response... much appreciated :)


direct rendering: No   (:( boo!)

"/etc/X11/xorg.conf | grep Driver"
  Driver "kbd"
  Driver "mouse"
  Driver "wacom"
  Driver "wacom"
  Driver "wacom"

What does that mean? i seem to remember dealing with 'i810" recently before i switched to GNOME (i was using KDE)... im assuming im going to have to mingle with xorg.conf?


Thanks Again, nothing better than seein a response to your thread.

---

### Post by DezSP on 2007-04-26
> **XxZtemxX said:**
> Also, i was wondering... in my excitement/frustration to get WoW installed, i saved the files in like C:/ProgramFiles/ ...which i know is a Windows Directory... where are they now? :-|

You'll probably find them in ~/.wine/drive_c/

---

### Post by XxZtemxX on 2007-04-26
Found the files. thanky. :)

---

### Post by Sammi on 2007-04-26
Here's a tread dealing with i810: [http://ubuntuforums.org/showthread.php?t=324736](http://ubuntuforums.org/showthread.php?t=324736)

---

