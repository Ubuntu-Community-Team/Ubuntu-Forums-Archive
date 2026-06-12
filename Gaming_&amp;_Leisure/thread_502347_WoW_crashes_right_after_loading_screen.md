---
title: "WoW crashes right after loading screen"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by neoclaw on 2007-07-16
I don't know if this have been asked before, but when i run World of Warcraft using wine, it crashes right after the loading screen. I think it's when it loads my char, because the system freeze totally after 2-3 seconds right before I can see my char. I tried adding different things in my .wtf file but nothing helps. I'm running it on a IBM T43 laptop, with a ATI x300 graphics card.

I hope anyone can help me.

---

### Post by Ardrias on 2007-07-16
Installed any addons lately? Perhaps it's one of them acting up after a recent patch or something.

---

### Post by Nkari on 2007-07-16
Something else to check, startup the game and try making a new character.

Does it work fine when you change things like skin colour or hair, but just sort of freezes when you you change something like race or class?

Could be the same problem I am having but with radically different hardware.

---

### Post by neoclaw on 2007-07-17
I tried running WoW with no addons and that won't help.
I also tried crating a new character, and it also crash there.

Btw, I'm using the newest version of wine (0.9.41).

---

### Post by Nkari on 2007-07-17
Damn, going to 0.9.41 from 0.9.40 was the next thing I was going to try and figure out how to do to see if it would help.

---

### Post by xfile087 on 2007-07-17
> **neoclaw said:**
> I don't know if this have been asked before, but when i run World of Warcraft using wine, it crashes right after the loading screen. I think it's when it loads my char, because the system freeze totally after 2-3 seconds right before I can see my char. I tried adding different things in my .wtf file but nothing helps. I'm running it on a IBM T43 laptop, with a ATI x300 graphics card.

I hope anyone can help me.

I get the EXACT same thing. However it DOES work every so often but more often than not it doesn't. I'm sharing the WoW installation with Windows and when I boot into Windows it works perfectly so it's not WoW.

---

### Post by Sandlst on 2007-07-17
Have you tried going here?
[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")
Search for ```
ATI enter game world crash
```
On the site.

---

### Post by SCGhst1 on 2007-07-17
hey kaspy! how ya doin buddy?


anyways...try this out...


worked for me

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

shows you how to correctly getting the ati driver working on any ubuntu version. works great! also...i had the same problem. just do that. your good with UNIX so im sure you can figure it out..

---

### Post by Nkari on 2007-07-17
Probably not going to help me, I'm running Nvidia gear.

---

### Post by Nkari on 2007-07-17
But maybe it is worth a go anyway, I've just been ignoring that because it says it is for ATI. 

Would still be quicker than installing a windows partition just to play WoW if it works, that was pretty much what I had resigned myself to having to do at this point in time to get it going. 

I think I'm going to give it a go when I get home, maybe I can modify it in some way to work and not just kill everything

---

### Post by neoclaw on 2007-07-18
Thanks guys it works now! :D
I just had to add:
[I]Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"[/I]

to my xorg.conf file.

---

