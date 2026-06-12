---
title: "Can't connect to ubuntuforums!!!"
date: 2005-12-11
forum: Forum Feedback &amp; Help
---

### Post by mal on 2005-12-11
For the last couple of days I have been unable to connect to [www.ubuntuforums.org](www.ubuntuforums.org) from either of my machines running Ubuntu (breezy and hoary).  However, I can connect with no problems with a laptop running Windows XP.  The three machines are on my home LAN and connect through an ADSL modem/router.  I have not noticed any other locations that are unavailable.

I can ping [www.ubuntuforums.org](www.ubuntuforums.org), but a tracepath gives a string of "no reply" messages when it gets to the last step.  On the XP machine the last step is wailuku.xlogicgroup.com

Can anyone provide any suggestions about how I can sort this out?

Mal

---

### Post by ubuntu-geek on 2005-12-12
The server has been up.. :)

---

### Post by Sutekh on 2005-12-12
I can't connect from any computer at home using any OS, haven't been able to since last Thursday, but I have no issues connecting at work.

---

### Post by megamania on 2005-12-12
hmmm. I've read about problems with searching "ubuntuforums.org" in google...

Now I'm really getting curious about what this could be, and if the two things are related in some way...

---

### Post by earobinson on 2005-12-12
could this be at all connected to [http://www.ubuntuforums.org/showthread.php?t=102545](http://www.ubuntuforums.org/showthread.php?t=102545) maybe vBulletin stoped serving something some how

---

### Post by ardchoille on 2005-12-12
[QUOTE=mal]For the last couple of days I have been unable to connect to [www.ubuntuforums.org](www.ubuntuforums.org) from either of my machines running Ubuntu (breezy and hoary).  However, I can connect with no problems with a laptop running Windows XP.  The three machines are on my home LAN and connect through an ADSL modem/router.  I have not noticed any other locations that are unavailable.

I can ping [www.ubuntuforums.org](www.ubuntuforums.org), but a tracepath gives a string of "no reply" messages when it gets to the last step.  On the XP machine the last step is wailuku.xlogicgroup.com

Can anyone provide any suggestions about how I can sort this out?

Mal[/QUOTE]
I had this problem with some websites too. Then someone told me to open /etc/resolv.conf and see if there is a line that read "192.168.0.x" and if there was, remove that line. I did that, saved the file and all is well now.

---

### Post by mal on 2005-12-13
[QUOTE=ardchoille]I had this problem with some websites too. Then someone told me to open /etc/resolv.conf and see if there is a line that read "192.168.0.x" and if there was, remove that line. I did that, saved the file and all is well now.[/QUOTE]

The only entry in my /etc/resolv.conf is "nameserver 192.168.0.1" and deleting this line is not much help - it disables all name resolution.

So, I'm still not able to reach ubuntuforums.org from my Ubuntu machines.  I don't understand why this has just recently become a problem, but I'm glad to see that there are some other people experiencing the same symptons.  Something must have changed at the ubuntuforums site.

I'm still looking for a solution.

Mal

---

