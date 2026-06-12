---
title: "Battery indicator red although 1:30h remaining"
date: 2011-09-13
forum: Desktop Environments
---

### Post by gofurygo on 2011-09-13
Hello

Recently I bought an Asus 1018P Eeepc and gave ubuntu ago after I run it without problems on 2 other computers.

One thing I noticed is, that the battery indicator already goes red at about 30% "warning" me that I get low batter... in 1.30 hours or so... See attached screenshot.

I followed this post on launchpad already and went into gconf-editor: 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/743823/comments/1](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/743823/comments/1)

I set the desired percentages under "threshold" and unchecked the "use time for policy"... 

...But its still showing red although there is enough power left... 

Im using the standard ubuntu theme and version 11.04

Any ideas?

Thanks,
Fury

---

### Post by gofurygo on 2011-09-20
Hello again

I did some more testing...

It seems that the battery indicator goes red at exactly 30% of remaining charge although the gconf-editor setting is 15%.

I also tried to set the "time_low" to 600 seconds but nevertheless, it goes red at 30% or about 1:10 to 1:30 hours remaining

In addition, there is no indication like "low battery" or "critical battery" when the battery goes really low, only a red battery indicator, nothing else.

How can I fix this strange behaviour?

On my other Notebook with Ubuntu 10.10 I dont have this problem at all...

---

### Post by gofurygo on 2011-09-26
Bump

Hey guys... really nobody got any clue how to fix the strange battery indicator...? :(

---

### Post by maul9999 on 2011-09-26
> **gofurygo said:**
> Hello again

I did some more testing...

It seems that the battery indicator goes red at exactly 30% of remaining charge although the gconf-editor setting is 15%.

I also tried to set the "time_low" to 600 seconds but nevertheless, it goes red at 30% or about 1:10 to 1:30 hours remaining

In addition, there is no indication like "low battery" or "critical battery" when the battery goes really low, only a red battery indicator, nothing else.

How can I fix this strange behaviour?

On my other Notebook with Ubuntu 10.10 I dont have this problem at all...

At fully charging battery, what battery indicator look like?

---

### Post by Toz on 2011-09-26
It might just be an icon thing - its displaying the icon associated with that battery charge as per the icon theme. I believe the default icon theme for unity is "ubunut-mono-dark". If you look at the contents of **/usr/share/icons/ubuntu-mono-dark/status/24** (or ...status/22), you'll see the icons that are being used. I'm not sure of the logic behind which icon is used when, but if the "battery-020.svg" icon is being used for anything less than 40%, that might explain it. 

You can try switching icon themes to see if there is a difference, or re-coloring the battery-020.svg icon to your liking.

---

