---
title: "Evolution Calendar High CPU"
date: 2012-12-14
forum: Desktop Environments
---

### Post by cootetom on 2012-12-14
Hi all,

I've recently upgraded to 12.10 and since that upgrade the evolution calendar has been giving me grief. It often crashes entirely at which point I send a crash report using the GUI that asks me to do so. However sometimes it doesn't crash but instead uses 100% CPU which really slows down my laptop. 

My initial question is how can I kill the process when it's using such a high CPU. Normally I'd run "sudo kill id" however that doesn't kill this particular process which I find odd. 

[IMG]http://tomcoote.co.uk/wp-content/top.png[/IMG]

My second question is does anyone have any information on why evolution calendar is so temperamental for me since I've upgraded to 12.10. 

Many thanks.

---

### Post by Soullow11 on 2012-12-26
Just installed 12.10 and it is my first time on a linux OS.
It appear as though I am having the same issue with my evolution calendar running at about CPU 25%. Any help on this would be great. 
 
Thanks

---

### Post by Soullow11 on 2012-12-26
> **Soullow11 said:**
> Just installed 12.10 and it is my first time on a linux OS.
It appear as though I am having the same issue with my evolution calendar running at about CPU 25%. Any help on this would be great. 
 
Thanks
 
Just located a kill for this, worked perfectly
 
sudo killall -9 evolution-calendar-factory

---

