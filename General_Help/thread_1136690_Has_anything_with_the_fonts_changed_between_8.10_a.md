---
title: "Has anything with the fonts changed between 8.10 and 9.04?"
date: 2009-04-25
forum: General Help
---

### Post by Tmi on 2009-04-25
As in the topic, my question is whether there has been any changes that has to do with fonts between 8.10 and 9.04.

The reason that I ask is that I usually get tired eyes pretty fast with bad fonts. In Arch for example I use fluxbox and have done no font setup whatsoever, and my eyes get tired really fast.

In Ubuntu 8.10 me eyes lasted a lot longer and it was much nicer to browse the web and read stuff on the computer. Now after an 9.04 install I'm starting to feel tired quite quickly again, and thus my question.

Since I wiped my harddrive I can't check how the options (system -> preferences -> appearance -> fonts) were there. Anyone know if there are any changes in these options between the versions that might affect the fonts?

I might add that I have installed the mscorefonts, and that as far as I know they are working as they should. Does the gnome fonts options affect the fonts I see in Firefox after installing the mscorefonts?

---

### Post by kpkeerthi on 2009-04-25
Do you use LCD? You might want to set Subpixel hinting to medium or full under system -> preferences -> appearance -> fonts

---

### Post by ACMiller on 2009-04-25
Also, the fonts in firefox may appear different if you don't have the microsoft core fonts package installed. These fonts are used to display many webpages. You could try installing them, I'm sure they're under add/remove programs. Otherwise it sounds like fiddling with your fonts settings mentioned above could do the trick

---

### Post by Tmi on 2009-04-25
Thank you for your answers. It's actually a CRT monitor I use, and I have the ms-fonts installed which seem to work as they should.

After fiddling about with the options it looks to me like the font options I set in Gnome has no effect at all on my browser fonts. This is of course reasonable since webpages chose there own fonts and I guess Firefox takes care of the rendering (or whatever you call it :P) without caring for any Gnome options. Is that correct? If so my problem is probably somewhere else and not in the actual fonts.

---

### Post by Tmi on 2009-04-26
I've checked on a Hardy live cd, and the default fonts there are the same as on my current 9.04 install (same fonts, size, shading and smoothing). Thus fonts seem not to be the problem.

I'm pretty much running out of ideas now for what else might cause eye strain. My refresh rate is fine (85 Hz), the resolution is also what it should be (1024x768), I've checked the horizsync and vertrefresh values and they are also correct.

Anyone else have any ideas what might be causing this? What does 9.04 and Arch w/ fluxbox have or lack that 8.10 and 8.04 does not that might cause eye strain?

---

### Post by ubuntu27 on 2009-04-26
I don't know what problems does it have.


You can try to use [F.lux]("http://www.stereopsis.com/flux/").

See Also:

[http://ubuntuforums.org/showpost.php?p=6827918&postcount=1517](http://ubuntuforums.org/showpost.php?p=6827918&postcount=1517)


If you speak Spanish:

[http://ubuntuforums.org/showpost.php?p=6861390&postcount=1](http://ubuntuforums.org/showpost.php?p=6861390&postcount=1)

---

### Post by Tmi on 2009-04-27
Well, I've reinstalled 8.10 and my eyes feel better again. I've kept 9.04 for testing purposes, and there is a definite difference between the two when it comes to straining my eyes.

Right now I don't know what to do really. The fonts are the same in the two, the monitors refresh rate is the same, both xorg.conf's look essentially the same, both uses nvidia drivers.

My guess is that it is something with the newer xorg since both 9.04 and Arch uses it, while 8.10 uses an older version. Oh well, I'm out of ideas to test so I guess I'll just stick to 8.01 and hope my eyes feel better after another update.

---

