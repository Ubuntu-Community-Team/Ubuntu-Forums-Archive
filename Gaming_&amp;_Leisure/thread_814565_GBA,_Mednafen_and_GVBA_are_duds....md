---
title: "GBA, Mednafen and GVBA are duds..."
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by dracule on 2008-05-31
I am trying to make this work, but this simply isnt letting me emulate a darn thing.

I installed mednafen 8.8 from the repositories listed on mednafen.sourceforge.net

it lets me play my pokemon game for about 5-10 min, then crashes and says "segmentation fault. Have a fluffy day"
a search on google for "segmentation fault have a fluffy day mednafen" (w/o the quotes) gives 4 links. 

so i do not know where the error is.



Also, i do not know if GVBA will work (eg not crash), but i cannot map the buttons to my Xbox 360 controller (yes i have the drivers installed and use it all the time in zsnes), but i cannot find a site that shows how to set up the controllers for use with GVBA.

---

### Post by acoustibop on 2008-05-31
Try this [.deb for Mednafen 0.8.8]("http://ubuntuforums.org/showpost.php?p=4655351&postcount=26") posted by FranMichaels, dracule.  Works perfectly for me.

---

### Post by dracule on 2008-05-31
> **acoustibop said:**
> Try this [.deb for Mednafen 0.8.8]("http://ubuntuforums.org/showpost.php?p=4655351&postcount=26") posted by FranMichaels, dracule.  Works perfectly for me.

now that i installed that deb, i get an error saying something about

libcdio.so.7: cannot open shared object file: No such file or directory

---

### Post by acoustibop on 2008-05-31
Then you need to install libcdio7 (in the repositories), dracule.  If that doesn't fix it, install the -dev package, as well.

---

### Post by dracule on 2008-05-31
nope, didnt do it. crashed with "segmentation fault (core dumped"


EDIT: tried it in windowed mode, still crashes...

"Signal 11 has been caught and dealt with"

---

### Post by dracule on 2008-05-31
no$gba provides full speed emulation through WINE, so i think ill use that.

im pretty impressed with wine now that ive seen this...

---

### Post by dracule on 2008-05-31
lol, sorry for the triple post, but that doesnt seem to cut it... (that crashed too) 

Dang. I tried a couple more roms and they all crash.



but does anyone know how to config a gamepad to GVBA?

---

### Post by acoustibop on 2008-06-01
Are you using a 32bit or a 64bit OS, dracule, and which version (assuming you're using Ubuntu)?

---

### Post by dracule on 2008-06-01
> **acoustibop said:**
> Are you using a 32bit or a 64bit OS, dracule, and which version (assuming you're using Ubuntu)?

I was running 7.10, when i started this thread. but i decided hey, why not go to 8.04 since mednafen is crashing all the time on 7.10

so i installed 8.04 32bit

then i installed 8.7 from the repos. 

this time it went for a LONG time. i thought i had finally fixed the problem by upgrading. but then... BAM!

segmentation fault.




so a segmentation fault still happens on a fresh install (not upgade)...

i am very sad because it went for a good 20 min before it crashed, causing me to get my hopes up and think that there might be a chance. :(

---

