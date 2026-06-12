---
title: "would dell change my video card without too much hassle?"
date: 2007-11-04
forum: Dell  Ubuntu Support
---

### Post by jack handy on 2007-11-04
i initially got the ATI card because i used to be a windows guy and i didnt think much about it..  but now that i've switched over completely to ubuntu, i've found my multimedia experience slightly lacking.  

i've got ubuntu running on my desktop and the graphics on there are amazing with the nvidia drivers.

so the question is:  do you think dell would put up much of a fight if i asked them to switch my video card to an nvidia card?  (i'm still under my Complete Care package)

---

### Post by jack handy on 2007-11-04
i think my case for getting them to change my card has improved since i just confirmed what i started suspecting when i first installed linux: the video card only has 128MB of memory instead of the 256MB that was advertised (and present in my invoice).

at first, i thought maybe it had something about the crappy linux driver not giving me correct information about the hardware... but i was checking something in the BIOS, and the video memory says 128MB there too.

so screw you dell, you're replacing it with an nVidia card for my troubles.

---

### Post by dward526 on 2007-11-04
Right On.  I think your strongest case is in the fact that they did not provide the 256 card advertised.  This will be an even stronger case if it is one you requested.

---

### Post by gbrainin on 2007-11-05
Some video cards advertise a memory capacity that is only partly on board.  For example, the 256MB card may have 128MB on board and another 128MB of "shared" (that is, regular system) memory.  Check the advertised specs for your model card carefully.

---

### Post by jack handy on 2007-11-05
frack, i didnt know that video cards were integrated on laptops.  dammit.

so i'm stuck with the crappy ATI card.  :(

---

### Post by Dellfan on 2007-11-05
They are not entirely integrated on Dell notebooks, but on most models there are differences on the motherboard, with the end result being a paired motherboard / graphics card daughterboard. Definitely the case on the 1505/6400, so you can't just change out the graphics daughterboard.

Regarding the ram specs, on many cards the spec is "amount of ram" that particular model supports. Typically have some dedicated "onboard" ram, and some shared system ram. Often the only difference between versions of the card is that higher end versions support more ram, with the actual hardware being the same. Yes it is silly and artificial but most marketing is. This is further complicated by configuration rules that many allow different amounts of system ram to be used depending on how much system ram you have. The really high end cards have only onboard ram, but they are not typically found in notebooks.

---

### Post by sciurus on 2007-11-06
Are you using ATI's proprietary driver?

---

### Post by jack handy on 2007-11-06
i just installed the latest driver from ATI and it does seem like my initial freakout was a little pre-mature..  i'm afraid of trying to install World of Warcraft again, though.

---

### Post by aldenhg on 2007-11-07
Give it some time. AMD (nee ATi) have opened up their drivers a bit and really seem to be kicking in house development of the binary driver into high gear. Things will get better. I promise.

---

