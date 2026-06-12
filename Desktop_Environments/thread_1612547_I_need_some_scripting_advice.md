---
title: "I need some scripting advice"
date: 2010-11-03
forum: Desktop Environments
---

### Post by pepsifx357 on 2010-11-03
Hey guys, Here's my setup and what I want to do.

I have an Ubuntu server(Bare) install with xorg and a java program called eldy(Elderly Linux).  How can I write a script to solve these steps

Login

startx

cd /eldy23 (The folder that contains the program)

./eldy.sh

I want it so that when the computer boots up it runs these commands above in sequence to get the eldy interface rolling.

I'm not eactly sure how you would solve the logging in problem. I could just make it so that the person logs in and then the following commands are run automaticaly. Or run xdm?  Although I don't need a desktop manager or window manager for that matter.  If I were to run XDM, how would I get it to run before the server login?

Any Ideas?

Thanks

---

### Post by TSJason on 2010-11-03
Hi,

If you're using XDM you can probably just define the eldy script you want to run in the XSession file. Maybe look at /etc/xdm/Xsession?

---

### Post by pepsifx357 on 2010-11-03
thanks, I'll try that.

---

### Post by ender4 on 2010-11-03
```
login -f <username>
``` will login as the specified user without requiring authentication.  

You could place the cd /eldy23 and ./eldy.sh in xinitrc, which would start them up after xorg,

and then you would simply need to make an init script that calls login and startx at runlevel 2.  

See [https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")
[http://www.linux.com/archive/feature/125977?theme=print]("http://www.linux.com/archive/feature/125977?theme=print")
and the update-rc.d man page

---

