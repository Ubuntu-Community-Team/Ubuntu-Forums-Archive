---
title: "Full screen games fail"
date: 2008-12-03
forum: Gaming &amp; Leisure
---

### Post by magmon on 2008-12-03
I was playing Saurbraten today, and after about 5-10 minutes the game exited full screen mode and froze. I couldnt get my mouse back from it either, so I had to reboot. Most of my other full screen games do the same thing, except for forcing me to reboot. any suggestions?

---

### Post by magmon on 2008-12-03
Uh, guys? I really need a fix for this.

---

### Post by EdThaSlayer on 2008-12-03
Post your graphic card specifications. Could be a driver issue.
Maybe it's only your graphic card,your drivers that are causing this, or some other unknown ailment.

Here is a question: do the games work perfect when not in full-screen mode?

---

### Post by magmon on 2008-12-03
I have an ATI graphics card, have no idea how to get specs for ya tho. All games Ive played that are not in full screen mode work fine, yes.

---

### Post by Perfect Storm on 2008-12-04
1. Try disable compiz 
```
metacity --replace
```
2. Disable screensaver and powersaving mode

---

### Post by magmon on 2008-12-04
Hmm, ok. Lets see if its fixed now.

---

### Post by Perfect Storm on 2008-12-04
note I have change the code in my previous post, wrong command (havn't got my coffee yet).

---

### Post by magmon on 2008-12-04
Entering that code into terminal disabled my keyboard and removed the boarders from everything lol, had to restart. Saurbraten is still at it, btw.

---

### Post by Perfect Storm on 2008-12-04
Did you tried with the other command, as I stated above the first one was wrong.

---

### Post by magmon on 2008-12-04
No, tryed updated command.

---

### Post by magmon on 2008-12-06
Woo, AI, your brilliant. I used the GUI interface to find compiz and turn it off, and now saurbraten works perfectly. Just finished a 40-60 minute play session lol.

---

### Post by jenkinbr on 2008-12-06
That's the real fix - I will edit/reply after posting a script I created for nexuiz.  You will merly need to change one line in the script to get Saurbraten to work.

Edit:
Heres the link to the thread.  Be sure to read the whole thing, as it may not appear at first glance that it will work for other games.  Note that simply disabling gnome-screensaver was the trick that did it for me, so I did not include the command ```
metacity --replace
```

Here you go:
[http://ubuntuforums.org/showthread.php?p=6319479#post6319479](http://ubuntuforums.org/showthread.php?p=6319479#post6319479)

---

