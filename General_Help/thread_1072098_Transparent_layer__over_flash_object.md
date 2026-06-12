---
title: "Transparent layer  over flash object"
date: 2009-02-17
forum: General Help
---

### Post by gopan on 2009-02-17
Hi
I am trying to setup a transparent gif image over a flash object .
I tried adding wmode = trnsparent to the object tag and param tag.
it works fine in windows.
But in kubuntu the image goes beneath the flash. (i was checking firefox)

Also i tried putting an iframe as suggested [here]("http://blog.marcoos.com/2006/07/21/html-div-above-a-flash-animation-on-linux-its-possible/") 

I could place a div over the flash using this method; but the flash behind the div became tranparent.

I also tried using swfobject but same results

Can someone help me out of this?

Regards
Gopan

---

### Post by rharriso on 2009-02-17
Don't beat your head in over it. Damn near nothing works in linux's flash player
my company does a lot with the flash pano player, and we never check to make sure anything is working in linux. 
Gay i know, but it's only because flash player for linux is garbage. adobe needs to fix that pronto.

In linux flash is the top layer in any webpage. There is no way to get it to work. Check out:
hulu.com
mlb.com
those dudes couldn't do it, and they are pros.

---

### Post by mcduck on 2009-02-17
That's a know bug in the Linux version of flash plugin. It always plays on top of everything else.

There's nothing you can do about it, and since it has been like this for ages it doesn't really seem like Adobe is going to fix it either..

---

### Post by simon@vg on 2009-12-18
If you can live with the extra tag you can put an iframe in the stack above the flash movie and it layers correctly:

[http://piast.pertus.com.pl/~marcoos/flashlinux/](http://piast.pertus.com.pl/~marcoos/flashlinux/)

Worked for me.

---

