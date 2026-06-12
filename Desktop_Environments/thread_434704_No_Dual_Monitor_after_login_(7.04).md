---
title: "No Dual Monitor after login (7.04)"
date: 2007-05-06
forum: Desktop Environments
---

### Post by mindless1973 on 2007-05-06
Hi,

I have the following problem:

I would like to use dual screen with Ubuntu 7.04. I configured my xorg.conf as described in another article here in the forum. When I reboot my machine, it looks fine as the login screen is in dual mode (so the right monitor shows a blank backgroud while the left monitor offers me the login panel.

However, after logging in, the Ubuntu desktop is in clone mode - so both monitors show the same picture.

If anyone interested, I attached my xorg.conf file for review.

Can anyone give me a hint how to configure my workenvironment for dual view and not clone?

Thanks,

bye
Marcus.

Appendix:
Graphic Device: ATI X1950pro
Drivers: propriatary ATI drivers (fglrx)
Monitors: Daytek (Daewoo) DVI, Daewoo VGA
Ubuntu: 7.04 AMD64 with GNOME

---

### Post by xareck on 2007-05-10
I had the same problem initially and got mine to work doing the following 2 commands.

```
 sudo aticonfig --initial=dual-head --screen-layout=right
```
```
 sudo aticonfig --dtop=horizontal --overlay-on=1
```

P.S. My main monitor is on the left.

---

### Post by randalotto on 2007-05-10
I'm having the exact same problem as the OP. 

Unfortunately, the above solution didn't help.

Some information on my situation:

After the login screen, there is a distinct flicker, then it comes up cloned.

Also, though I'm trying to use fglrx, fglrxinfo tells me that i'm using the mesa driver.

Here's the part I just don't get at all - when I first started trying to get dual monitor support, there was no xorg.conf file ...

there were files named xorg.conf.fglrx-0 and xorg.conf.fglrx-original or something like that, but no straight up xorg.conf.

So, I created one and put in all of the proper settings. That's what got me a dual-monitor boot screen (can even move the mouse over to the right side), but I have no idea what to do. 

It's like the gnome session proper is using something other than xorg.conf, which i can't find. i changed the settings in every variation i *could* find, and still no luck....

EDIT:
wanted to add - i installed the fglrx driver with Envy, hit "Yes" when it asked if I wanted it to configure automatically, and have also tried "aticonfig --initial

---

### Post by Harkins on 2007-08-29
Iäm having this exact same problem using an ATI Radeon x1300. I get perfect dual monitor support before I login, but as soon as I do my displays are cloned instead of one desktop. Anyone have suggestions?

---

### Post by FishFoot on 2007-10-15
I too am having the exact same problem on the X1300.  I've got one monitor connected to the DVI plug and the other to the Analog plug.

To be honest I'm just bumping this in case somebody is watching.  Anybody get this to work?

---

### Post by Harkins on 2007-10-15
I did after a bunch of tinkering, yeah. Let me attach my xorg.conf. I'm using dual-dvi, but maybe it'll help you. Good luck with your setup.

---

### Post by FishFoot on 2007-10-15
Thanks Harkins, I'll check it out when I get home.

---

