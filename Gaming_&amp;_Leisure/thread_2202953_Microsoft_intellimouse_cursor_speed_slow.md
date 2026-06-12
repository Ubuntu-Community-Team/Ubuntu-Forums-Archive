---
title: "Microsoft intellimouse cursor speed slow"
date: 2014-02-01
forum: Gaming &amp; Leisure
---

### Post by goodbye-windows(tm) on 2014-02-01
Hi all,
   
I've used an old microsoft intellimouse (optical) for years, until I lost the original one. The original one is VERY OLD, from the early days of optical mice.... when optical mice were not the norm and I fell in love with it because I didn't have to take the ball out and clean the dust out of the innards all the time.

I bought 2 replacements recently, both the same model. One of them has a very slow cursor speed, and nothing I can do in the mouse setup makes it scroll anywhere near quick enough. The other unit is very satisfactory in every way-just as my very old original unit was. These are 5 button units, and are still regarded as pretty good performing mice by the gaming types. 

I don't want to go looking for mice from other vendors, would like to keep the intellimouse if I can. 

Are there any adjustments in the software or mods I can do to make the cursor speed more 'typical' in the slower unit? I have experience with hardware and software isn't my thing. If there is a hardware mod, I'd be happy to whip out the 'ole soldering iron as well::>



TIA

Art

---

### Post by tgalati4 on 2014-02-01
Open a terminal:

```
man xset
```

It's possible that one of your mice is defective.  Does it work OK on Windows or on another linux distro?

If you look in your control panel, there are acceleration and sensitivity settings for the mouse through a graphical interface.  I think it just changes the *xset* settings.

---

### Post by goodbye-windows(tm) on 2014-02-02
It works the same on my 6 core AMD desktop and on my I5 Dell laptop. Both (of the mice) were purchased from the same vendor on the same day-I'm stuck. I suppose they might be manufactured with different firmware internelly, but they're the same model.

I'll play with xset later tonight, but with the acceleration and sensitivity settings, it can't be adjusted to make the cursor speed anywhere near what it should be.

GL.

Art

---

### Post by tgalati4 on 2014-02-02
Use *xev* and play with both mice and note any changes in output in the terminal.

---

