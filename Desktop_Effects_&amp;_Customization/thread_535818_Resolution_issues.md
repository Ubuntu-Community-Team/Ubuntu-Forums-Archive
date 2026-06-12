---
title: "Resolution issues"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by ragrim on 2007-08-27
Ok im running a Acer Travelmate 4230 Laptop with a 7300 go and im using a benq T91W 19" widescreen.

Ive just installed gutsy 7.10 tribe 4 and everything is working fine except i cant run 1440x900 res, ive had this problem with fiesty 7.04 and i just modified my xorg.conf, but this time it no work. below is a screenshot of what i see when i run 1440x900 res.

[IMG]http://img.photobucket.com/albums/v321/ragrim/Screenshot-1.png[/IMG]

ive tried various combinations of xorg configurations and still no luck, any help would be muchly appreciated.

---

### Post by zoobave on 2007-08-27
try 

**# X -configure**

---

### Post by ragrim on 2007-08-27
unfortunatly didnt help, it created a new xorg.conf for ne and i tested it and all i get when X starts is a mouse pointer thats an X and the screen is just a blank with a whole lot of lines on it.

---

### Post by ragrim on 2007-08-27
Got it fixed.... worked out after doing that configure the test i done didnt display what i expected it to, but i copied the new xorg.conf that the X -configure created and now im running 1440x900 res no worries.

Thanks!

---

