---
title: "eee 901, skydome vanishes after suspend"
date: 2008-12-11
forum: General Help
---

### Post by SalsaDoom on 2008-12-11
Hi fellas.

Kind of a strange problem here. I am compiz setup and working quite nicely on my eee 901, on Ubuntu 8.10. The desktop effects work fine -- surprisingly well for the rather flimsey GMA950 actually. 

Anyway, my problem here is, that when I come out of suspend, the skydome background picture is gone, just black. I searched the forums here and didn't see anything like that. On google there was another guy who had the same problem as me, but no one had a solution for him.

Anyone have any ideas that might be worth a try?

Cheers!
--SD

---

### Post by sim909 on 2009-01-16
> **SalsaDoom said:**
> Hi fellas.

Kind of a strange problem here. I am compiz setup and working quite nicely on my eee 901, on Ubuntu 8.10. The desktop effects work fine -- surprisingly well for the rather flimsey GMA950 actually. 

Anyway, my problem here is, that when I come out of suspend, the skydome background picture is gone, just black. I searched the forums here and didn't see anything like that. On google there was another guy who had the same problem as me, but no one had a solution for him.

Anyone have any ideas that might be worth a try?

Cheers!
--SD

Same problem here, with ubuntu 8.10 interpid ibex. I did not have this problem when I was running 8.04.

lspci tells me:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


Sometimes also the cube caps vanish, but more frequently it is the skydome. Any ideas?

cheers

---

### Post by Matthewthegreat on 2009-04-13
I'm using eeebuntu on a eee 901 and I have same problem too. Anyone have any ideas?

---

### Post by talbain on 2009-05-20
Samsung NC10 (Love it to bits)

Same problem, id love to find a fix for it, as of right now, after suspend the only way to get it back is to open CCSM, disable and re-enable the skydome... way too much work just to have a background behind the cube every time the machine suspends (about 5 to 10 times a day)

Any ideas?

---

### Post by sim909 on 2009-05-20
> **talbain said:**
> Samsung NC10 (Love it to bits)

Same problem, id love to find a fix for it, as of right now, after suspend the only way to get it back is to open CCSM, disable and re-enable the skydome... way too much work just to have a background behind the cube every time the machine suspends (about 5 to 10 times a day)

Any ideas?

I have since changed computer (now a dell latitude e4300) and upgraded to 9.04, the problem has gone for me. 

In any case, what I used to do was just press alt+F2 and type in "compiz --replace", so that compiz would restart and the skydrome reappear. I was finding this workaround more convenient than the one suggested by talbain (and that I myself was using for a while).

---

### Post by talbain on 2009-05-21
> **sim909 said:**
> I have since changed computer (now a dell latitude e4300) and upgraded to 9.04, the problem has gone for me. 

In any case, what I used to do was just press alt+F2 and type in "compiz --replace", so that compiz would restart and the skydrome reappear. I was finding this workaround more convenient than the one suggested by talbain (and that I myself was using for a while).


Were you using an ATOM based computer?

I wonder what really solved your problem... the new system or the new distro, if i knew jaunty would fix this i would upgrade.

EDIT: Thank you for the tip on restarting compiz :)

---

### Post by sim909 on 2009-05-21
> **talbain said:**
> Were you using an ATOM based computer?
Don't even know what that is! I had a Fujitsu Siemens Lifebook S Series

> I wonder what really solved your problem... the new system or the new distro, if i knew jaunty would fix this i would upgrade.
Hard to tell, of course, since both graphic card and OS have changed. Do you have some space on your disk (or an external usb disk) where you could install jaunty just to see if it fixes it? 

> EDIT: Thank you for the tip on restarting compiz :)
You're very welcome!

---

