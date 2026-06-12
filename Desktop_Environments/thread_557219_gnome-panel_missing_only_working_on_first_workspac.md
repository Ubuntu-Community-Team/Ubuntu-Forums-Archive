---
title: "gnome-panel missing only working on first workspace"
date: 2007-09-22
forum: Desktop Environments
---

### Post by markbza on 2007-09-22
Hi All

My bottom panel is missing on my other workspaces. Workspace 1 loads gnome-panel fine but the others done have it. I tried searching forums for a solution but couldnt get one.

---

### Post by Quid on 2007-09-22
I am new to Ubuntu ( 2 months) ad love it... I have Feisty
I have added Beryl and have it nicely configured - 

Like the above post... it seems that 1/3 of the time i will loose the bottom panel - very frustrating - to make matters more interesting - about 1 time in 10 I will loose both top and bottom panels!

always after a reboot -
rebooting rolls the dice and gets them back! usually :)

I was Blaming Beryl but the previous post has me wondering!

BTW I have used Beryl Manager to switch back to MetaCity ( Gnome Window Manager) when this happens - no effect.

On reboot - ( left at the Metacity option) the frequency of lost panels are the same.

Is this just the pain I must endure to have Beryl ? 


Thanks Forum Readers!

---

### Post by mckooiker on 2007-09-26
in this thread [http://sudan.ubuntuforums.com/showthread.php?t=461513]("http://sudan.ubuntuforums.com/showthread.php?t=461513")  it is suggested that compiz might be the problem, which I can not exclude.
I also have these problems described above and some suggested solutions (which I did not try yet) you can find here [http://http://sudan.ubuntuforums.com/showthread.php?t=493499]("http://http://sudan.ubuntuforums.com/showthread.php?t=493499").
Though these solutions only work for the current session, and these solutions won't prevent the feature from returning.....

---

### Post by Quid on 2007-10-14
I found a solution - at least it seems to work for my setup.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147943]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/147943")

The above bug talks of restarting th GDM with a CTL ALT BKSPACE - which throws you to a black screen and back to login.

Hope this helps others... looks like they are struggling in Gutsy!

---

### Post by FredB on 2007-10-14
The bug you're talking about is fixed. Running Gutsy since beta, and now, compiz works flawlessly. The only missing thing is logout sound... And Gnome 2.20.1 :)

For your information :

```
~$ uname -a ; cat /etc/issue.net
Linux fredo-gutsy 2.6.22-14-generic #1 SMP Wed Oct 10 05:28:36 GMT 2007 x86_64 GNU/Linux
Ubuntu 7.10
```

---

### Post by Quid on 2007-10-14
Thanks...  just learning to read up on the bug reports - :)

---

