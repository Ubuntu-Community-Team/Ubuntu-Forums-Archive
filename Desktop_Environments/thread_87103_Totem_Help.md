---
title: "Totem Help"
date: 2005-11-07
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-07
I have been unable to get Totem or any DVD application to work (xine).  I have installed Firefox 1.5, but not the normal way (1.07 is still on my system).  1.5 is in: 

/home/local/firefox/firefox

With a short-cut to my desktop.  It works great (had to do it this way because I couldn't figure the "real" way out).  I do  not believe this is related to the new version or unusual set-up as it did not work at all prior to installing 1.5 (just wanted to mention my background so if you had any thoughts you could undestand my situation).  When I put a DVD in, it starts to play the warning page (copyright stuff) and then it just dies.  Any thoughts or help?

If not obvious from my post, I'm a newb...

Thanks for any help

---

### Post by KingBahamut on 2005-11-07
Sounds like gstreamer...

Try 

apt-get install totem-xine ,  and force totem out of Gstreamer and see what happens.

---

### Post by Georgie-o on 2005-11-07
Tried it and this is what happend.  Am I missing something?


george@ubuntu:~$ apt-get install totem-xine
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
george@ubuntu:~$


Thanks

---

### Post by KingBahamut on 2005-11-07
sudo apt-get install totem-xine 

you cant run apt-get as yourself, have to run as root.

---

### Post by Georgie-o on 2005-11-07
It seemed to the install, but both still quit after the "Rated R" and stop playing (totem and Xine). any thoughts?

---

