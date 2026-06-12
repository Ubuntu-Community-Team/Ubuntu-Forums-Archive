---
title: "Can't boot KDE!!! Help plz!!"
date: 2006-08-21
forum: Desktop Environments
---

### Post by MiniZiper on 2006-08-21
Kubuntu loads fine apparently, but when it finishes loading up everything, it shows the logo and the "loading" bar, and it just sits there.... So I booted with recovery mode, and when I type "sudo startx" I get this "(EE) No devices detected.
Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining."

I havent changed anything. I just booted windows real quick, then I wanted to go back to kubuntu, and I got this...

I REALLY NEED TO FIX THIS WIHTOUT REFORMATING ^^ THANKS FOR ANY HELP!!!

---

### Post by meng on 2006-08-21
Any luck with, from command line:
sudo dpkg-reconfigure xserver-xorg
?

---

### Post by oyvindaa on 2006-08-21
[http://ubuntuforums.org/showthread.php?t=240957](http://ubuntuforums.org/showthread.php?t=240957)

My guess is that your solution lies there. MAYBE!

---

### Post by MiniZiper on 2006-08-21
oh yea... adept told me about a X.org update... sigh thanks! ^^

---

### Post by MiniZiper on 2006-08-21
Thnkas A Lot, I Fixed It :) Thanks!!

---

