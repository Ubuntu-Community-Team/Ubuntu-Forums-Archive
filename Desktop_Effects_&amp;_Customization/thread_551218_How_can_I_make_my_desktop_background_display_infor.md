---
title: "How can I make my desktop background display information about my computer?"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by cloud1 on 2007-09-14
How can I make my computer desktop background display information like this?

[http://youtube.com/watch?v=G4bNdznE0qc](http://youtube.com/watch?v=G4bNdznE0qc).

I'm talking about the information that are being display in the upper left side on the desktop background.

---

### Post by rsambuca on 2007-09-14
That is a program called 'conky'. It can be configured to display virtually anything about your system, and can also be configured to look differently as well.  The program runs in the background and uses very little system resources.

The how-to thread on how to set it up is [here,]("http://ubuntuforums.org/showthread.php?t=205865")

And the thread for different set-ups and looks is [here.]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by FuturePilot on 2007-09-14
That would be conky.```
sudo apt-get install conky
```
Then you have to create the config file in your home directory.
```
gedit /home/USER/.conkyrc
```
There's a huge thread here with examples of people's conkyrc files if you want some ideas. 
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")
It's a bit tricky, I'm still trying to figure it out.:)

Edit: rsambuca beat me to it. :p

---

### Post by cloud1 on 2007-09-15
Thanks guys for all of your help.

I always wanted my desktop background to display information like this and now I finally can.

I got it setup and now is running and I'm so happy.

:D

---

### Post by rsambuca on 2007-09-15
Wow!  That was fast.  Great job - How about some screenshots of your handywork?

---

### Post by hyperair on 2007-09-15
There's a sample conky file installed with the conky package. Perhaps you'd like to check it out. ```
zcat /usr/share/doc/conky/examples/conkrc.sample.gz > ~/.conkyrc
```

I'd backup before using it though.

Also, I made a deb of the latest conky since the current one in the Ubuntu Feisty repositories is outdated. 
[http://ubuntuforums.org/showthread.php?t=547440](http://ubuntuforums.org/showthread.php?t=547440)

---

### Post by FuturePilot on 2007-09-15
Feisty's is outdated already? That was fast.
Thanks!

---

