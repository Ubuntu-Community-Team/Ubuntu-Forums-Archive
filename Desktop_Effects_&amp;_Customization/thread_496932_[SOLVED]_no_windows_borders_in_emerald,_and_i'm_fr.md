---
title: "[SOLVED] no windows borders in emerald, and i'm freakin out!!"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by rickycodie on 2007-07-09
i have no windows borders in emerald. i have tried all  i can think of here's the error i get in the command line

emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

also i have tried
 ricky@ricky-laptop:~$ ps a | grep emerald
 6349 pts/0    S+     0:00 grep emerald
and various commands like emerald --replace and beryl --replace
 i had this problem for a while and have not been able to fix it, please help!?!?!

---

### Post by ForensicBroom on 2007-07-09
type this in the terminal:
beryl-manager
and it should restart beryl and hopefully give you borders...

---

### Post by rickycodie on 2007-07-09
it does not. niether does killall emerald and then beryl-manager

---

### Post by rickycodie on 2007-09-26
solved, go here

[http://ubuntuforums.org/showthread.php?t=502771](http://ubuntuforums.org/showthread.php?t=502771)

do the aargblx thing.

---

### Post by altonbr on 2007-09-26
> **rickycodie said:**
> solved, go here

[http://ubuntuforums.org/showthread.php?t=502771](http://ubuntuforums.org/showthread.php?t=502771)

do the aargblx thing.

arrgblx thing?

---

### Post by chekp38 on 2007-09-26
[SIZE="4"]I have tried everything.  I have edited my xorg.conf file.  I tried reloading Beryl.  I tried Compiz.  I tried removing it all and tried it again and I still don't have windows borders.  I am wondering if it isn't just my particular vid card (7900 GS)?[/SIZE]

---

### Post by rickycodie on 2007-09-27
sudo gedit /etc/X11/xorg.conf

then add under devices

Option "AddARGBGLXVisuals" "true"

sorry i didn't make that very clear did i?

---

### Post by rickycodie on 2007-09-27
chekp please don't yell, it might be your card if you've tried everything. although everything would ential quite alot, what all did you try? can you give system details?

---

### Post by chekp38 on 2007-09-27
Sorry about that font.  That was wierd and I didn't mean for it to be that way, lol.

Anyway, I tried editing my xorg.conf file with the Option "AddARGBGLXVisuals" "true". I've tried compiz and beryl both.  I have uninstalled and reinstalled them.  One of the interesting things is that when I switch to Metacity then back to Beryl I see the borders for just a second and then they go away. I used Envy to install the newest nVidia drivers.  Beryl runs really smooth and very fast for me it is just the borders that are missing.  My computer is a Dell XPS laptop model m1710.  If you would like to see the xorg.conf file I can post it I just am not on that computer right now.

I read that sometimes the problem is that the windows decorator isn't loading.  That should be emerald, right?  How can I make sure it is running?

Thanks a bunch for the help.  These forums have been an endless font of help for this linux noob.

---

### Post by rickycodie on 2007-09-27
try this,

in the terminal, with metacity running and beryl closed, type

beryl-manager

then post results here.

this should start beryl and emerald, and tell us what is going wrong with them.

---

### Post by rickycodie on 2007-09-27
also if you haven't done so enter this in the terminal,

glxinfo | grep direct

 and if anything other than yes is output, you have the wrong drivers, or the right drivers are wrongly installed.

---

### Post by Joeblo on 2007-09-28
I have the same problem and adding         

Option          "AddARGBGLXVisuals" "true"

didn't work.

As the previous post my beryl work really smooth but nothing seems to bring back the windows decorator. I've also try the    terminal:  emerald --replace         to bring emerald as the decorator but nothing seem to work.

Do you have anything else to suggest?

Your support really is apreciated.

---

### Post by rickycodie on 2007-09-29
try the same steps and post what happens.

i don't mind helping, but new posts or posts in threads that haven't  been marked solved might get you more involvement.

---

