---
title: "Computer Won't Shut Down"
date: 2005-12-25
forum: Desktop Environments
---

### Post by twoseids on 2005-12-25
Whenever I click on "shutdown" or "restart" (I think even from "log off"), my computer plays the shut down sound file, and then my screen goes black. I get the same black screen if I try to go to another session. The computer does not shut off. I have let it sit overnight and still nothing. I always have to just hold down the power button to force a shutdown.

Any ideas? This sucks.

---

### Post by JmSchanck on 2005-12-25
if you hit ctrl-alt-f1 does it switch to a VT? or is everything completely locked up

---

### Post by twoseids on 2005-12-27
[QUOTE=JmSchanck]if you hit ctrl-alt-f1 does it switch to a VT? or is everything completely locked up[/QUOTE]
Same thing. Black screen, unresponsive. Not really locked up, but I guess you can say that since I can't do anything except force a shutdown!

---

### Post by singamayya on 2005-12-27
After a fresh boot-up of your machine, 
[LIST]
[*]go to a virtual terminal (ctrl-alt-f1)
[*]log in and type **sudo halt**
[*]when the screen goes blank, press any key and you should see the shutdown sequence (it will show a list of programs/daemons being terminated)
[*]observe the shutdown sequence and tell us the last thing you see before your system freezes
[/LIST]

---

### Post by twoseids on 2005-12-27
[QUOTE=singamayya]After a fresh boot-up of your machine, 
[LIST]
[*]go to a virtual terminal (ctrl-alt-f1)
[*]log in and type **sudo halt**
[*]when the screen goes blank, press any key and you should see the shutdown sequence (it will show a list of programs/daemons being terminated)
[*]observe the shutdown sequence and tell us the last thing you see before your system freezes
[/LIST][/QUOTE]
No dice. When I hit CTRL-ALT-F1, my screen goes black. And then if I hit CTRL-ALT-F6 or F7, I don't get my GUI screen back either.

I then tried logging in using the "Failsafe Terminal" option in the login screen, and from that terminal I typed **sudo halt**. As soon as I entered my sudo password, my screen went black again. Pressing a key did not do anything to change that.

I want to emphasize that the screen isn't going "blank" (meaning you can still see that the monitor is on), but rather "black" (meaning the monitor is off entirely). I suppose it's possible that something is still there if the monitor were to be on, but how to tell?

---

### Post by rasmusbp on 2005-12-27
I'm having similar problems with both restart and shut down. 

I think it's a known bug - see [this thread]("http://www.ubuntuforums.org/showthread.php?t=75314&highlight=shutdown+restart"). Let me know if you find a (easy) solution!

---

### Post by twoseids on 2005-12-28
[QUOTE=rasmusbp]I'm having similar problems with both restart and shut down. 

I think it's a known bug - see [this thread]("http://www.ubuntuforums.org/showthread.php?t=75314&highlight=shutdown+restart"). Let me know if you find a (easy) solution![/QUOTE]
Thanks for that link - it may be the same issue. I wonder if it has anything to do with Automatix that I just installed? Maybe something with the Nvidia drivers it includes?

---

