---
title: "BIG problem with Calendar in Evoultion"
date: 2007-10-22
forum: Desktop Environments
---

### Post by mallow on 2007-10-22
The problem is that I can`t add any event in Evolution`s Calendar. If I try, small window pops up with info that I use wrong date format. What`s up with that? I`ve found somewhere that If I`ll open Evolution with:
```
# LC_TIME=C evolution 
```
then the calendar works. But that`s no solution for me. I want to use calendar in Polish, not English. Besides, I often open Evolution Calendar by clicking a date on the calendar applet. Is there even a way to start this applet with  LC_TIME=C option?? 

Please, tell me if there is a solution to my problem. If there`s not I should go back to ubuntu 7.04, because I really need Evolution working properly :confused:

---

### Post by mallow on 2007-10-22
All right. I did it! Luckily I still have ubuntu 7.04 on my desktop PC and a pl_PL file in it (it`s in the attachment). What I had to do to fix my problem:
- replace pl_PL file with pl_PL from Feisty (as root, copy this file to the /usr/share/i18n/locales folder)
- execute in terminal following command:
```
sudo dpkg-reconfigure locales
```

That`s it. Just run again Evolution and enjoy your perfectly working Calendar.

Maybe some devs shoul look at it? I know that many people using Polish language have problem with Evolution`s Calendar and this fix is quite easy. Could you make an update with pl_PL file from Feisty?

---

### Post by mbartyzel on 2007-11-21
works for me!

thanks

mb

---

