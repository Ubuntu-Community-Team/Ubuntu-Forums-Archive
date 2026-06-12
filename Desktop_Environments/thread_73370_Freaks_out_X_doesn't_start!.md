---
title: "*Freaks out* X doesn't start!?"
date: 2005-10-08
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2005-10-08
Okay, sorry for the beginning rant, but this is the second freaking time this has happened in the last two weeks, and last time I had to do a reinstall of Kubuntu just to fix it. This is coming at a point where I was getting ready to reformat my windows partition, but now am so frustrated at linux that if I cant fix this before the end of the night I'm dumping linux all together and going back to XP. This time, my CPU load was at 100% (after a problem with WINE) so I went to click end session but accidently clicked shut down, so I just started it back up. When I start up the machine, it goes to load up the OS, but ends me in a command line to enter my kubuntu user name and password, then leaves me there. If I type startx I get a screen with a bunch of errors on it, one that says "Fatal, no screens to load" or something like that. Is there anyway I can get this working again? Any help would be appreciated, as it seems Linux is just far too unstable for me to use as a primary OS.

---

### Post by adwait on 2005-10-08
```
sudo /etc/init.d/kdm restart
```

---

### Post by TheIdiotThatIsMe on 2005-10-08
[QUOTE=adwait]```
sudo /etc/init.d/kdm restart
```[/QUOTE]

Brings me right back to the command line and startx still doesn't work.

---

### Post by adwait on 2005-10-08
Hmm......then try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by TheIdiotThatIsMe on 2005-10-08
[QUOTE=adwait]Hmm......then try
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

Nope, when I type in Startx afterwards I still get the same errors. Also I noticed the two errors at the very bottom are:

Fatal IO Error 104
Error in locking authority file .Xauthority

?????

---

### Post by adwait on 2005-10-08
Uhh......no idea really....but is the file /home/<username>/.Xauthority present? What are its permissions. Can you post all the errors that occur? You can find them in the log at /var/log/Xorg.0.log

---

### Post by TheIdiotThatIsMe on 2005-10-08
[QUOTE=adwait]Uhh......no idea really....but is the file /home/<username>/.Xauthority present? What are its permissions. Can you post all the errors that occur? You can find them in the log at /var/log/Xorg.0.log[/QUOTE]

I have no idea how to check its permissions >.<

---

### Post by adwait on 2005-10-08
```
ls -al | grep .Xauthority 
```

On the right there will be someting like -rw-------- , What is it exactly? Mine looks like that.....so that should be how it should be. Anything different on your end?

---

### Post by TheIdiotThatIsMe on 2005-10-08
[QUOTE=adwait]```
ls -al | grep .Xauthority 
```

On the right there will be someting like -rw-------- , What is it exactly? Mine looks like that.....so that should be how it should be. Anything different on your end?[/QUOTE]

-rw------ 1 root root date .Xauthority
-rw------ 2 anthony anthony date .Xauthority-c
-rw------ 2 anthony anthony date .Xauthority-l

---

### Post by TheIdiotThatIsMe on 2005-10-08
[QUOTE=adwait]Hmm......then try
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

Okay I read through the file you showed me before (took me forever to get to errors) and found the errors had to do something with frame buffering, so when I ran through this reconfigure you showed me, I simply turned off the frame buffer and was able to boot back into X. Thank you!

---

### Post by adwait on 2005-10-09
:) No probs......

---

