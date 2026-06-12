---
title: "Cedega and dotakeys"
date: 2007-01-17
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2007-01-17
This is a longshot, but does anybody have any idea how to get DotaKeys to function properly in Cedega?  DotaKeys is a program that starts up Warcraft 3 with a customizable set of hotkeys to make playing the DotA maps easier. 

 I can get it installed properly, and it brings up Warcraft 3 just fine, but the hotkeys do not function at all.  Even just hitting F8 to turn them on generates no response.  I've tested it in windows and it works fine.  Using Cedega, I can see the dotakeys system tray icon in the taskbar and it functions properly as well.  The only thing that doesn't work is the in-game functionality.

I've played with some of the options in Cedega, including Managed, Desktop, and Winver.  Does anybody have any other ideas?

Thanks in advance.

[LIST]
[*] [DotA Allstars]("http://www.dota-allstars.com/")
[*] [DotaKeys]("http://dotakeys.3.forumer.com/index.php?showtopic=3") 
[/LIST]

---

### Post by Rhombuss on 2007-03-22
I'd be really interested to know if anyone has been able to get this working as well.

---

### Post by ingenio on 2007-05-04
Ok.

Here the solution for remap keys to mouse or keyboard on warcraft III and Dota map with cedega wine.( It's work for me :-) )

Install:

xbindkey
xvkbd

here a .xbindkeysrc example:


# mouse button UP
"/usr/bin/xvkbd -window cedega -text "h""
  b:4


# mouse Button down
"/usr/bin/xvkbd -window cedega -text "w""
  b:5

# Mid mouse button
"/usr/bin/xvkbd -window cedega -text "e""
  b:2

# control + button 1
"/usr/bin/xvkbd -window cedega -text "b""
  control + b:1

# numpad 0
"/usr/bin/xvkbd -window cedega -text "v""
  c:90 + release

-----

Sorry about my english!

I hope help you.

iNGENIo
----------

---

### Post by ingenio on 2007-06-21
The option DXGrab Must be disable! on cedega properties

bye

---

