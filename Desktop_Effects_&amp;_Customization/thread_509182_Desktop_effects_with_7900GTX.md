---
title: "Desktop effects with 7900GTX?"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by napster2500 on 2007-07-25
hello all! this is my first post here!:)
i would like to know if it is wise to change my video card. i have a powercolor X1900XT 512 MBit and i cant enable my desktop effects in ubuntu 7.04 (in fact i didn't manage to enable the compiz and beryl themes either):(
i'm tired to try hundred of methods to make this things work and i've heard that the nvidia cards have better support on ubuntu.
so i've come here to ask the real specialists what should i do. please help me!

regards

---

### Post by Haegin on 2007-07-25
If you want desktop effects have you tried installing the fglrx driver ([guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")) and then installing XGL to get it going ([guide]("https://help.ubuntu.com/community/CompositeManager/Xgl"))

That should let you run compiz fusion fine I would think. ([guide]("https://help.ubuntu.com/community/CompositeManager/CompizFusion"))

Good luck.

P.S. I always buy nvidia if I can but my laptop has a pretty pathetic ATI Xpress 1100 and this method worked for me. I am 99% certain you can get compiz (aka desktop effects) working with your current card.

---

### Post by shavenlunatic on 2007-07-25
it'll all change when ati opensource and/or improve their drivers :)  i kept hold of my ATI just incase

---

### Post by napster2500 on 2007-07-25
> **Human Prototype said:**
> If you want desktop effects have you tried installing the fglrx driver ([guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")) and then installing XGL to get it going ([guide]("https://help.ubuntu.com/community/CompositeManager/Xgl"))

That should let you run compiz fusion fine I would think. ([guide]("https://help.ubuntu.com/community/CompositeManager/CompizFusion"))

Good luck.

P.S. I always buy nvidia if I can but my laptop has a pretty pathetic ATI Xpress 1100 and this method worked for me. I am 99% certain you can get compiz (aka desktop effects) working with your current card.

i dont know what happened... i've installed all like in the manuals but i cannot see the titlebars with the minimize &co. buttons..
for the moment i have re-enabled the metacity... please help!

---

### Post by Haegin on 2007-07-25
Install emerald
```
sudo apt-get install emerald emerald-themes
```

Use the following compiz command to start desktop effects:
```
compiz --replace -c emerald
```

---

### Post by napster2500 on 2007-07-25
i've found this list and it sais that the x1900 series is unsupported...

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

why should i try to do something impossible?

PS: are all the nvidia boards supported? all of them??

---

### Post by Espreon on 2007-07-25
I think that just means that your card for the opensource driver is unsupported, but should work with fglrx. Fglrx works fine for me and I have an X1400 and I can do all of the effects like the cube,water,snow,lightning,fire,transparency,fish and everything else. Eventhough you have no window bars can you produce a cube by doing this:

Press CTRL+ALT mouse click and hold?

And I don't think "all" of them are supported. But from what I seen most.

---

### Post by shavenlunatic on 2007-07-25
> **napster2500 said:**
> i've found this list and it sais that the x1900 series is unsupported...

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

why should i try to do something impossible?

I would still try the above advice from Human Prototype...

> PS: are all the nvidia boards supported? all of them??

It's a chip... and pretty much yeah, still always wise to have a check before you buy though

---

### Post by shavenlunatic on 2007-07-25
also.. if your drivers aren't installing correctly (although I'm not sure that is your problem) have you tried Envy, made by alberto milano (sp?)

---

