---
title: "[SOLVED] Yep, another &amp;quot;I've lost my title bars&amp;quot; thread"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by the8thstar on 2007-06-24
Hello all,

I was getting tired of Compiz and Beryl altogether and I decided to remove them from my computer. I opened Synaptics and I removed all related software bearing the name compiz or beryl for that matter.

I was very surprised to see my title bars disappear and no action going on about open windows in the taskbar at all.

Step 1: I reinstalled everything, including some stuff I didn't need just in case, since Linux is quite kabbalistic, I thought I might just get lucky -- WRONG! No change.

Step 2: I reinitialized my xorg.conf -- WRONG AGAIN! Not even a slight change

Step 3: I opened System/Preferences/Theme in a desperate attempt -- the contents DO change, but there is still no title bar or active taskbar

Step3: I opened Beryl Manager -- WORSE!!! my computer hangs everytime and I have to kill X (Ctrl+Alt+Backspace) to be set free

HELP. What should I do?

---

### Post by the8thstar on 2007-06-25
Actually, the problem reappears as soon as I close the terminal

When I input "metacity", here is what I get:
> 
the8thstar@the8thstar-laptop:~$ metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"



... (big sigh) what is the system trying to tell me here?

---

### Post by andrewsomething on 2007-06-25
Try <ALT> F2 to bring up the run dialog and type "metacity --replace"

---

### Post by imcc on 2007-06-25
[http://ubuntuforums.org/showthread.php?t=484319](http://ubuntuforums.org/showthread.php?t=484319)

I posted a fix for what worked for me when I installed Compiz Fusion, but probably in the wrong thread.

When I installed Compiz Fusion I removed Metacity i think. This last part fixed a problem that I couldn't get rid of while using Beryl so I was really happy when I stumbled upon it. Hope it works for you also.

---

### Post by the8thstar on 2007-06-25
Thanks guys

The replace trick worked to an extent and then the following message appeared:

> root@the8thstar-laptop:/home/the8thstar# Fatal: Compiz can't be ran using VESA or VGA divers.

which is odd since I'm using an Intel 945M chipset. Maybe my xorgconf file is messed up. But I don't know what to do to fix it. :(

---

