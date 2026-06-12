---
title: "persian language in ubuntu ?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by m.h.shams on 2006-06-16
dear friends,

can i use persian true type fonts in ubuntu 6.06 ?

when i try to add these fonts to ubuntu fonts, i got no result, 

?????

regards.
shams

---

### Post by Pooya Farshim on 2006-06-18
Hi

To view pages like [www.bbc.co.uk/persian](www.bbc.co.uk/persian) correctly, install the package msttcorefonts.

Pooya

---

### Post by m.h.shams on 2006-06-18
[QUOTE=Pooya Farshim]Hi

To view pages like [www.bbc.co.uk/persian](www.bbc.co.uk/persian) correctly, install the package msttcorefonts.

Pooya[/QUOTE]

Dear Pooya, 

web pages is'nt my problem

i want to install some True Type Persian Font in Ubuntu 6.06,
i want to write persian docs in open office or other text editors.


thanks again
Shams

---

### Post by majed on 2006-06-18
Hi Shams,

I think I got the solution for you :)

I faced issues with Arabic in XFCE and found a solution and I hope it will work with you as well...

To test it, do run this command in a terminal:

```
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ir & 
```

Then press both SHIFT keys at the same time (SHIFT+SHIFT) to toggle your keyboard between English and Farsi.

If it works then you just need to have this line executed everytime you login (for example have it in a script that will be run in your profile or in your Autorun) :)

Good luck!

Majed

PS: more of this in my previous post about it here: [http://ubuntuforums.org/showthread.php?t=82213](http://ubuntuforums.org/showthread.php?t=82213)

---

### Post by m.h.shams on 2006-06-18
[QUOTE=majed]Hi Shams,

I think I got the solution for you :)

I faced issues with Arabic in XFCE and found a solution and I hope it will work with you as well...

To test it, do run this command in a terminal:

```
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ir & 
```

Then press both SHIFT keys at the same time (SHIFT+SHIFT) to toggle your keyboard between English and Farsi.

If it works then you just need to have this line executed everytime you login (for example have it in a script that will be run in your profile or in your Autorun) :)

Good luck!

Majed

PS: more of this in my previous post about it here: [http://ubuntuforums.org/showthread.php?t=82213](http://ubuntuforums.org/showthread.php?t=82213)[/QUOTE]

dear majed,

i read in ubuntu documents that "to add True Type Fonts in Ubuntu, just drag and drop TTF fonts to Fonts Window" but i can't do this.

my real problem is adding Persian TTF fonts to ubuntu.


thanks, for ur kindly helps.
shams

---

### Post by h.mehdi on 2006-06-19
Hi m.h.shams,

Have a look at this guide 
[http://wiki.hezardastan.org/DapperPersianSupport](http://wiki.hezardastan.org/DapperPersianSupport)

Hope this solves your problem... let me know if you need more help :)

---

### Post by yamca on 2006-06-19
Hi
I think i saw pictures of a persian ubuntu at flickr.com

---

### Post by Pooya Farshim on 2006-06-19
Hi,

Cannot you just intsall TT fonts from the packagae manager?

Enable universe or multiverse and serach for Farsi or Persian or Iran. Could also search for Arabic...

Think there is also a Font manager pckager.

Pooya

---

### Post by majed on 2006-06-19
hummm..

i did the Arabic TT fonts by putting them in /home/<user>/.fonts and then rebuilding the fonts cache.

Good luck!

---

### Post by m.h.shams on 2006-06-19
thanks all, i got it.

---

