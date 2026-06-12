---
title: "is there any way to automatically lock screen without xscreensaver?"
date: 2021-06-19
forum: Desktop Environments
---

### Post by opus1 on 2021-06-19
The searches I've done on the internet seem to indicate that there is no way to have xubuntu automatically lock the screen without xscreensaver, but I thought i'd ask here.  

It has never been a problem until I upgraded from 16.04 to 18.04 a couple of weeks ago.  After I did that xscreensaver seems to disappear every once in a while after an auto update, leaving my computer unlocked.

it seems ludicrous that a modern operating system will rely on an outside program to lock the screen and then have no fall back if it gets removed.

---

### Post by TheFu on 2021-06-19
The GUI isn't part of the "OS".
GUIs are just another program, like a calculator.  There are standards for what a GUI Window Manager should provide, ICCCM2 2.0. Some of the newest DEs don't follow those standards.  But all of these things are just programs, not part of the OS.

I use xscreensaver on my 18.04 systems. Use the xscreensaver-demo program to set the configuration. See if that doesn't do what you need.

---

### Post by opus1 on 2021-06-19
I understand that the GUI isn't part of the OS and that it is written by the XFCE folks and adapted for use by the xubuntu folks.  I guess I should've said that it is ludicrous that a modern GUI relies on an outside program, but doesn't provide a fall back.

xscreensaver works fine and locks the screen as expected.  The issue I have is that xscreensaver suddenly disappears (e.g., is removed) after an automatic update and my screen is suddenly not locking.  I would like to find a way to ensure that the screen still locks if xscreensaver randomly disappears like it has been.

---

### Post by TheFu on 2021-06-19
There are downsides to not having a single company responsible for all software shipped with an OS release.

Linux is a bazaar, not a cathedral.  Our distros and GUIs are a loose confederacy of programs, not built specifically for any 1 DE.

There are upsides to not having a single company control all the software too.  Why do you use XFCE and not Gnome3, the default Ubuntu Desktop?  Isn't it nice to have a choice?

---

### Post by opus1 on 2021-06-19
I agree with everything you said, which is probably why I have used Linux exclusively since 2005.

However, I am still frustrated when something like this slips through (e.g. no fallback built-in) because physical security is important.

---

### Post by guiverc on 2021-06-20
No supported release of Xubuntu uses `xscreensaver`.

Xubuntu is now fully GTK3 and uses `xfce4-screensaver` (eg. [https://packages.ubuntu.com/focal/xfce4-screensaver](https://packages.ubuntu.com/focal/xfce4-screensaver)) rather than non-Xfce tools (*as was the case in earlier releases*).

Xfce in 16.04 was [*deprecated*] GTK2, in 18.04 it was part [*deprecated*] GTK2 & part GTK3 as *port* was still progressing ..  however now all supported releases of Xfce are GTK3  thus use a specially crafted for Xfce screensaver/tool.

(*the oldest Xubuntu supported Xfce is found in 20.04*).

---

### Post by ajgreeny on 2021-06-20
I can not comment about 18.04 as I no longer run that version of Xubuntu but 20.04 in which I use xscreensaver has no problems, and if I ask it do so, will lock the screen automatically when it activates.
When I was running 18.04 xscreensaver also worked fine, locking the screen if set to do so.

You saying that the xscreensaver simply disappears suggests to me that you have some other problem which needs to be dealt with. 

Have a look in your settings, and go to Session and Autostart to see what command is used for the xscreensaver, and also check that any default screensaver is not also set as one of your autostart applications; maybe the two together are not compatible.

---

### Post by opus1 on 2021-06-20
> No supported release of Xubuntu uses `xscreensaver`.

I did not know that.  When I upgraded, it removed xscreensaver and didn't install a new screensaver in its place so I re-installed xscreensaver since I didn't know there was a replacement.  If I had known that xfce4-screensaver was the approved replacement I would've installed it. 

> Have a look in your settings, and go to Session and Autostart to see what command is used for the xscreensaver, and also check that any default screensaver is not also set as one of your autostart applications; maybe the two together are not compatible.

Thank you for providing an idea for where to look! ;)  I've been through these already, though, so no joy. As I indicated above, there was no "default" screensaver installed when I upgraded -- there was no screensaver at all after upgrading -- so that's not the problem.

---

