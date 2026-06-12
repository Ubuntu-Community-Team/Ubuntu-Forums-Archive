---
title: "sh indication message"
date: 2009-10-06
forum: Desktop Environments
---

### Post by onyxwolf on 2009-10-06
I want to produce a message like the new mail message evolution puts out (one that pops up in the corner and goes away by itself), and was wondering if anyone knew of a sh/bash script way of doing it. The same box and style message is given by my sensors-applet (2.2.1), so I know its possible-- I just don't know if its heavy programing or a simple Zenity style program that outputs it. 

No I'm not looking for zenity. Mainly because I don't want to have to press ok to get rid of it (unless there's a way to conf that specific zenity message to pop-up and go away on its own). Sorry, probably a new thread for old question.

---

### Post by onyxwolf on 2009-10-09
*Bump*

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
Dunno if this helps, but I ran across it:

[http://ubuntuforums.org/showthread.php?t=876618](http://ubuntuforums.org/showthread.php?t=876618)

---

### Post by onyxwolf on 2009-10-09
That was perfect thank you the libnotify-bin package with the notify-send is EXACTLY what I was looking for!!!
For future reference:
sudo apt-get install libnotify-bin ##repository [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe
notify-send "put message here!"

Again thank you and great catch!

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
dumb luck, i just googled popup message in ubuntu. But you're welcome none the less. :D

---

### Post by onyxwolf on 2009-10-09
Cool! I didn't even think of adding popup until I edited it this afternoon. I didn't even think to google the popup. one of those duh, moments.

---

### Post by ST3ALTHPSYCH0 on 2009-10-09
Don't feel bad, my very first post to the forums was a duh instance, a simple forgotten space in a command line.

---

