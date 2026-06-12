---
title: "Xubuntu alternate cd"
date: 2006-08-09
forum: Desktop Environments
---

### Post by rem on 2006-08-09
Hi all,

I told some friends of mine about my Ubuntu desktop and one of them came earlier today with a Toshiba laptop, PIII, 500 Mhz, 128 M, 6G HDD. I choosed to install Xubuntu over Ubuntu because of the low resources but couldn't boot from the Xubuntu live CD. I downloaded the alternate CD and procedeed with the text instalation. Everything went great, but I end up having Xubuntu in text mode and I really need XCFE... What should I do to start it in GUI mode? Don't want my friend to think I made a lot of noise for nothing... :)

Thanks a lot for all your help. Any advice is very appreciated.

Regards.

---

### Post by Ziox on 2006-08-09
> **rem said:**
> Hi all,

I told some friends of mine about my Ubuntu desktop and one of them came earlier today with a Toshiba laptop, PIII, 500 Mhz, 128 M, 6G HDD. I choosed to install Xubuntu over Ubuntu because of the low resources but couldn't boot from the Xubuntu live CD. I downloaded the alternate CD and procedeed with the text instalation. Everything went great, but I end up having Xubuntu in text mode and I really need XCFE... What should I do to start it in GUI mode? Don't want my friend to think I made a lot of noise for nothing... :)

Thanks a lot for all your help. Any advice is very appreciated.

Regards.

if it is a standard install, then xfce is already installed...try 

startx

or 

sudo /etc/init.d/gdm start

---

### Post by rem on 2006-08-09
i didn't choosed any custom install session. the install process seems to go as standard. i thought that maybe i did something wrong and right now installing it again. after that i'll try with your suggestion. thanks a lot!

---

### Post by rem on 2006-08-09
i tried startx but what i got was this error:

```
Xsession: unable to start X session --- no "/home/user/.xsession" file, no "/home/user/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.
```

sudo /etc/init.d/gdm start is outputing "command not found"

any ideas?

---

### Post by maniacmusician on 2006-08-09
I guess you don't have gdm installed? try 

sudo apt-get install gdm

instead of startx, you can also try startxfce4 or xserver. but it looks like you don't even have X set up. or havnt created a user, but i doubt thats the case.

---

### Post by rem on 2006-08-09
i created the user indeed ... don't know what happened (twice) but my user folder was empty each time... i downloaded the ubuntu alternate cd and trying with that one this time ( pretty tired of these installs:) ).

thanks a lot, hopefully it'll work with this one..

---

