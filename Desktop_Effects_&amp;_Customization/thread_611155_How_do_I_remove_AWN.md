---
title: "How do I remove AWN?"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by tyraeon on 2007-11-12
In an attempt to make my Ubuntu laptop look like a Mac, I changed all my desktop environments to the Leopard / OS X Themes. Now, it seems, I like everything I have except for the AWN Window Navigator at the bottom of my screen. Only problem is that I can't remove it.

I tried 'sudo apt-get remove avant-window-navigator' but it tells me that it wasn't installed to begin with. I followed a Linux-Mac Conversion tutorial on this forum (can't find link, sorry). The method I used to install it was that I edited /etc/apt/sources.list and I did one or two other minor things...

My question is, is there an easy way to remove this? Or should I go into /etc/apt/sources.list and look for what I added and just take it out. I'm only hesitant to do the latter because I'm afraid of ruining something. Any ideas?

---

### Post by tyraeon on 2007-11-12
EDIT: Fixed it myself. If anyone's wondering, I just deleted the two lines I added in /etc/apt/sources.list then ran 'sudo apt-get remove avant-window-navigator' then rebooted.

:]

---

