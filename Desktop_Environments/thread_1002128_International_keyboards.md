---
title: "International keyboards"
date: 2008-12-04
forum: Desktop Environments
---

### Post by ooddgeirsson on 2008-12-04
International keyboards

I have a problem with keyboard shortcuts. I write in different languages and use three different keyboards. I have installed all three in my 8.04 (hardy), it works while the machine is running and the shortcuts I have selected alt-alt and alt-shift work fine. When I restart the machine however it does not work. I get some crazy layout for the two non-english keyboards. I have to go into systen > preferences > keyboard and do the selection again and then it works, but again just until next restart. The strange thing is that the keyboards are still there - it appears to be the shortcuts which dont work. 
I am using HP with internet keyboard. 
Has anybody experienced the same problem? 
All hints and comments would be greatly appreaciated.

---

### Post by TokyoYank on 2009-10-15
This topic is still alive, even if the thread died a quick death..

**ooddgeirsson**, Did you find a fix?  

In addition...


==> for multiple international keyboards:  does dynamic layout switching exist in a desktop environment today?  My curiosity extends to commercial OSes as well (MS and Apple)


For this forum, I hope a KDE guru (or other) might chime in, because I'm quite ignorant to things non GNOME

---

### Post by prshah on 2009-10-15
> **ooddgeirsson said:**
> I have to go into systen > preferences > keyboard and do the selection again and then it works, but again just until next restart. 

> **TokyoYank said:**
> 
**ooddgeirsson**, Did you find a fix?  



See any of these links to have keyboard layout settings persist across reboots.
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

### Post by TokyoYank on 2009-10-15
Thanks prshah (and thanks for continually helping)

.. upon closer re-read, I realize that my problem is quite different.  Also, I realize that **for me, multiple layout options have always worked** to my satisfaction in 9.04 without the setxkbmap fix you describe.  Presumably it was repaired



FWIW my problem = I have two physical keyboards (one PS2 and one usb), each a different physical layout.  ...  I'll search and possibly start a new thread about dynamic layout switching as required


sorry for reviving an old thread by mistake

---

