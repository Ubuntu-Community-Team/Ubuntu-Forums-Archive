---
title: "Computer shuts down or restarts by itself.."
date: 2009-06-21
forum: General Help
---

### Post by tonybeccar on 2009-06-21
Hello, lately I've been experiencing behaviours like this on my pc. Some days when I go to sleep and then wake up, my computer is either restarted or shutted down. I don't know what the hell is going on, the programs that I usually keep open during night are Dvede, which uses mencoder, spumux and dvdauthor and Deluge. I googled around and opened /var/log/messages and extracted the whole log of the date this happened, which was June 21st. That day I used the computer till 3:30 I guess. I read it and around 6 the computer restarted itself 2 times after doing some processes I cannot understand, so I'm posting the log here to see if anyone can help me figure out what is going on. Thanks to all in advance!

PS: I attached the log in 3 parts because the size was too big.. again, thanks for your time!

---

### Post by dhughes on 2009-06-21
I wonder if you're having the same trouble as some other people including myself have had, it was solved by replacing the power supply. 

 There's something about Jaunty and power supplies that's a little odd, it may be your problem but then again it may be something else.

 Here is my post and another discussing a, possibly, similar experience to your problem:

[http://ubuntuforums.org/showthread.php?t=1178833](http://ubuntuforums.org/showthread.php?t=1178833)

[http://ubuntuforums.org/showthread.php?t=1112028](http://ubuntuforums.org/showthread.php?t=1112028)

---

### Post by tonybeccar on 2009-06-21
Thanks for your reply! I read the whole discussion and I remember experiencing this under windows i think like 1 year ago. For now, it does not bother me a lot, as it happens like 2 times in a month I guess. If the problem engraves I'll change the power supply. Thanks again and good luck!

---

### Post by tashirosgt on 2009-06-21
You log shows some "restart" commands.  Did you issue those commands?

---

### Post by cariboo on 2009-06-21
Those restarts are just the syslog deamon restarting, which it does once an hour and is perfectly normal.

---

