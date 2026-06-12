---
title: "Resolution unavailable"
date: 2009-02-19
forum: General Help
---

### Post by stoneage on 2009-02-19
I just did a fresh install of Intrepid on 64 bit, and the appropriate resolution for the monitor is not on the list of options. 

1152 x 864 is the highest on Preferences -> Screen Resolution.
Administration -> Nvidia X Server Settings offers 1360 x 768 but the screen is shifted upwards so that most of the top panel is obscured.

I need 1440 x 900. I use the machine for graphics and 3D rendering and the distortion is making life very difficult. (Also text is difficult to read)

Can anyone cure it ?

---

### Post by dcstar on 2009-02-19
> **stoneage said:**
> I just did a fresh install of Intrepid on 64 bit, and the appropriate resolution for the monitor is not on the list of options. 

1152 x 864 is the highest on Preferences -> Screen Resolution.
Administration -> Nvidia X Server Settings offers 1360 x 768 but the screen is shifted upwards so that most of the top panel is obscured.

I need 1440 x 900. I use the machine for graphics and 3D rendering and the distortion is making life very difficult. (Also text is difficult to read)

Can anyone cure it ?

There are a number of people that I have seen report similar issues, you can try and search out those posts and see if there is a fix for you.

One thing you may want to try is installing a different version (like 8.04) that may identify you particular hardware better, all it will cost you is the download of a Live CD to boot up and see what it does.

---

### Post by stoneage on 2009-02-19
> **dcstar said:**
> There are a number of people that I have seen report similar issues, you can try and search out those posts and see if there is a fix for you.

One thing you may want to try is installing a different version (like 8.04) that may identify you particular hardware better, all it will cost you is the download of a Live CD to boot up and see what it does.

Thanks for the reply.

I have been doing that, but no luck yet. I just traded up from 8.04 because it only allowed 800x600. 
I had been using Hardy since April, but it turned bad two days ago and even with a fresh install it won't use the graphics driver, so here I am. 

I think I need to discover how to add a modeline to the xorg.conf, unless someone happens to know better - I would have thought 1440 was a fairly common resolution nowadays.

Any and all help appreciated.

---

### Post by stoneage on 2009-02-21
The xorg.0.log can be found here:-
[http://pasteall.org/4363](http://pasteall.org/4363)

---

### Post by stoneage on 2009-02-22
I found a solution with the help of some people at [http://blenderartists.org/forum/showthread.php?t=148775](http://blenderartists.org/forum/showthread.php?t=148775)

I used gtr to generate a modeline, and Nvidia X Server Settings to generate an xorg.conf and edited the two together along with information on the monitor's HorizSync and VertRefresh rate.

The resulting xorg.conf can be viewed here:-
[http://pasteall.org/4382](http://pasteall.org/4382)

---

