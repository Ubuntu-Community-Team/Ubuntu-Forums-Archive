---
title: "Desktop Effects, won't enable. Other threads haven't solved the problem"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by newb1788 on 2007-10-01
Hi,

I can't get the desktop effects enabled either, I have an onboard VGA, I suppose this may be the problem. I have previously had the cube and wobble effects working but since adding compiz none of this works. I get a message no restricted drivers needed and Envy invidia won't install.

Would be great if someone can help.

---

### Post by BLTicklemonster on 2007-10-01
What video card, and which drivers? Did you install the compiz configuration tool? I'm a random virus magnet, so I can't go looking to see what it's called, sorry, but someone will probably come along and help you find the name for it.

You could search advanced, use compiz and my name to search, and look at any post I made recently that shows up, and you'll most likely find the name of the file to install. 

I hope you get it going.

---

### Post by Howler9443 on 2007-10-01
You can update the file /usr/bin/compiz

Change the line that reads:

T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

to

#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

Be aware, that it acts kinda hokie on my T61 when I enable it. 

I hope this helps.

I kinda of assumed that your integrated graphics were the newer Intel X3100 series. If not, then check the list to see what is listed and make the appropriate changes.

Thanks,
Howler

---

### Post by chronic on 2007-10-01
if you are using an nvidia gfx card then setting up compiz is easy 

just go to system >> administration >> restricted drivers manager 

and enable the nvidia gfx driver

reboot and your done :popcorn:

---

