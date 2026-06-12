---
title: "Network &gt;_&lt;"
date: 2005-05-26
forum: Desktop Environments
---

### Post by spockrock on 2005-05-26
Ok I am a gnu/linux n00b...............

I installed ubuntu and I love it........but I tried to transfer 10Gb of files, from my windows xp sp2 computer, to ubuntu, and ubuntu gave me an eta of 60Mins rough math gave me about 20-30Mbps, now that is really slow.  Another machine another windows xp sp2 could do it in 21 mins thats about 60-70Mbps.........Now I could transfer 4.43Gb from ubuntu to windows in 9 mins about the same 60-70Mbps, googling this symptom, a suggestion was to set the both the linux to windows to 100Mbps half duplex if that works to full duplex, well I tried with ethtools, but I couldn't change it in linux for the life of me.......................>_<

I then prolly did the dumbest shit possible but I tried to see if there was an easier way to do this, so I tried etherconf but I feel that did more damage...........so now I have another problem........when I booted up I was told Ubuntu.example.com was missing from /etc/hosts..........I tried to undo the damage,  but nothing, so I tried,

```
sudo gedit /etc/hosts
``` 

and changed

127.0.0.1                            Ubuntu
to
127.0.0.1                            Ubuntu.example.com

this got rid of the error message at the beginning of my bootup, but now when I go to places>network servers it takes forever to find the windows machine but it finally finds, the machines Ubuntu(the linux box) Chewie(the windows box) and Windows Network.......and I still have the same problem with the Ubuntu copying the files very slowly from windows.......but windows can get files at much faster speeds.

-edit-  I have found this and ubutu guide very helpful....................hopefully, linux will replace m$ as my main OS..............

---

### Post by poofyhairguy on 2005-05-26
[QUOTE=spockrock]and I still have the same problem with the Ubuntu copying the files very slowly from windows.......but windows can get files at much faster speeds.
[\QUOTE]

Sounds like you found a bug. Will you please report it?

---

### Post by spockrock on 2005-05-26
[QUOTE=poofyhairguy][QUOTE=spockrock]and I still have the same problem with the Ubuntu copying the files very slowly from windows.......but windows can get files at much faster speeds.
[\QUOTE]

Sounds like you found a bug. Will you please report it?[/QUOTE]
 hmmm.....I dunno if it is, while trying to fix the problem I completly foobared my ubuntu, so I reformatted and re-installed, and now I get around 60-70Mbps instead of 20-30Mbps like I am suppossed to, between windows and ubuntu.......should I still report it??

---

