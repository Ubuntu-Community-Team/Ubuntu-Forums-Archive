---
title: "chmod -r 700 /"
date: 2006-08-01
forum: Desktop Environments
---

### Post by chrluc on 2006-08-01
I just put that command into my computer and now you guessed it... I am sweating big time, I cant do anything... what are my options? I have a lot of files (several gigs) I have to salvage! I have a live cd, I have an external hardrive (usb), and I still have a pretty big hardrive I could partition and reinstall dapper if I could mount the other partition and pull files across the partiotions. please help!

thanks

---

### Post by rmjb on 2006-08-01
Try sudo chmod 755 /
-R means recursive -r means reference. If you did a -R then you'll have to put that option back in to this command.
If you do that however, I think it won't be good for your linux and you might have to back up your files and reinstall.

- rmjb

---

### Post by simonn on 2006-08-01
What is your partition scheme (meaning what partitions do you have)?

---

### Post by aysiu on 2006-08-01
Unfortunately, there's no easy fix for this, as different files are supposed to have different permissions (they are not all supposed to be 755 or 700 or 644).

I would advise doing something like [this](http://www.psychocats.net/ubuntu/separatehome.html) and then reinstalling.

---

