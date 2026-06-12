---
title: "desktop size????"
date: 2006-02-20
forum: Desktop Environments
---

### Post by jason.b.c on 2006-02-20
i have a question , in breezy how can you resize your desktop _without_ changing the screen resolution. what i mean is this, say you change your res to 1280-1024 wich is what i use but there is this black border around the actual desktop ( about an inch i would say )so how can you zoom this in _without_  changing the screen resolution or any or all settings on the monitor ( if i change the settings in the monitor it will affect the way that my windows desktop looks ):confused:

---

### Post by Ubuntuud on 2006-02-20
Just to make sure, is 1280-1024 the recommended screen resolution for your monitor?

---

### Post by jason.b.c on 2006-02-20
hey thanks for you quick reply,   well its not so much whats recemended for my monitor, because when i boot up ubuntu defaults to a much higher screen resolution than that ( i think 1600-1280 ) but i don't like it there , so i turn it down a bit , but there is still a black border around the desktop. so thats why i asked if there is a way to zoom or resize to fit to screen better!??;)

---

### Post by tmahmood on 2006-02-20
whats you monitor size? if you are using a 17 inch CRT then recommand resulation would be 1024X768 or 1154X864, for LCD monitor I don't know for sure.. check your manual and then modify your xorg.conf file according to your needs.

---

### Post by jason.b.c on 2006-02-20
it's a 17 inch, an older 17 inch !,  how do you alter the xorg.config file??:confused:

---

### Post by syklitengutt on 2006-02-20
use the buttons on your monitor to strech the screen...
Sorry...
didnt read the last sentence made by you

---

### Post by heimo on 2006-02-20
[quote=jason.b.c]i have a question , in breezy how can you resize your desktop _without_ changing the screen resolution. what i mean is this, say you change your res to 1280-1024 wich is what i use but there is this black border around the actual desktop [/quote] 

EDIT: Oh, just got your last sentence. :) You can use xvidtune to do it. See the link in my signature.

I presume it's CRT, not TFT? Use your monitors menu buttons to adjust geometry. Or alternatively (more complex) you can change the mode, I'd tweak it using xvidtune and add the new modeline to xorg.conf. But geometry settings of your monitor should do the trick - save the settings and it should now work always with this resolution/refresh rate setting.

If it's TFT, you should use its native resolution or if not, find "scaling" or "auto adjustment" setting in its settings menu.

---

### Post by jason.b.c on 2006-02-20
> I presume it's CRT, not TFT? Use your monitors menu buttons to adjust geometry. Or alternatively (more complex) you can change the mode, I'd tweak it using xvidtune and add the new modeline to xorg.conf. But geometry settings of your monitor should do the trick - save the settings and it should now work always with this resolution/refresh rate setting.

If it's TFT, you should use its native resolution or if not, find "scaling" or "auto adjustment" setting in its settings menu.


well i thank you for your quick reply, but as i have already stated if i change the settings on my monitor it will screw up the way my ms windows looks!!!! thus rendering it almost unusable:(     ( it's a crt monitor )!

---

### Post by heimo on 2006-02-20
[quote=jason.b.c]well i thank you for your quick reply, but as i have already stated if i change the settings on my monitor it will screw up the way my ms windows looks!!!! thus rendering it almost unusable:(     ( it's a crt monitor )![/quote]

Yeah, sorry for that. We posted at the same time, see my updated post above.

---

### Post by jason.b.c on 2006-02-20
> see my updated post above.
__________________
HOWTO: Solving resolution/refresh rate problems in Xorg

ok , wow it all looks preaty much like greek to me,,  but i guess i'll eventualy figure it out???:eek:    just wish there was an easier way to do it??   ( *laughing* );)

---

### Post by heimo on 2006-02-20
> **jason.b.c]ok , wow it all looks preaty much like greek to me[/quote]
Nah, it's geek.  said:**
> but i guess i'll eventualy figure it out???:eek:    just wish there was an easier way to do it??   ( *laughing* );)
The only relevant section for you is the How to adjust position of your screen, which instructs using xvidtune and adding the modeline to correct place in /etc/X11/xorg.conf (which is plain text file). If you have any problems, please go ahead and ask, I'll be glad to help as well as I can.

---

