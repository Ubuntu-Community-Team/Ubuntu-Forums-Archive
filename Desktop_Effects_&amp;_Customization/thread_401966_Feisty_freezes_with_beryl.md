---
title: "Feisty freezes with beryl"
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by mshale on 2007-04-05
I just installed beryl after doing a clean install of 7.04  all works great except i get discolored sections around the windows, and until I go to close a window.  When i click close, actually before i get to, feisty freezes, and there is nothing i can do but restart.  i can still move the mouse, but cannot click anything.

when i load beryl manager in a terminal, i get a warning that says "... claims to not support..."  I can't quite remember what what those elipses contain, but after i get off of work, i can go and check and edit the post.  

Thanks guys and gals for your help!!

---

### Post by jrock2004 on 2007-04-05
What is your vid card and is it setup

---

### Post by mshale on 2007-04-05
> **jrock2004 said:**
> What is your vid card and is it setup

I'm in no way sure.  all I know is that i have a toshiba satellite m45-s331.  Is there a way to find out?

---

### Post by jrock2004 on 2007-04-05
inside settings should be a device manager and it should show you what hardware it has the other thing you could do is look into your xorg.conf and look at video section and see what it is set as

---

### Post by TrusigheR on 2007-04-05
> all works great except i get discolored sections around the windows

I had that problem too, you have to disable the blur for the windows and it works fine..at least it did for me =\

As for your video card..

> 
Video

    * Graphics Processor / Vendor
    * Intel GMA 900

    * Video Memory
    * Dynamic Video Memory Technology 3.0 - 64 MB 
[http://reviews.cnet.com/Toshiba_Satellite_M45_S331/4507-3121_7-31263273.html?tag=sub](http://reviews.cnet.com/Toshiba_Satellite_M45_S331/4507-3121_7-31263273.html?tag=sub)

No clue if that is supported, you might have to play around a little bit.

---

