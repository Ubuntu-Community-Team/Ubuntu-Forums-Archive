---
title: "Got a Ubuntu cd but........"
date: 2009-04-04
forum: General Help
---

### Post by alcav on 2009-04-04
Hi,

I got myself a Ubuntu cd rom which I managed to get to boot, but unfortunatly my mouse will not work.

My mouse is a usb wireless type.Any ideas anyone?.

I just wanted to work from the cd for the time being,I have 2gig of ram btw.

Alan

---

### Post by Therion on 2009-04-04
USB to PS2 adapters are about $2 where I am.  That or beg, borrow or steal a wired mouse long enough to get updates and hope your wireless mouse gets picked up once you get the updates and such installed.

What brand/model of wireless mouse do you have?  And what version of Ubuntu are you using?  I haven't had that particular issue since... Feisty, I think.

---

### Post by rhcm123 on 2009-04-04
> **alcav said:**
> 
My mouse is a usb wireless type.Any ideas anyone?.


Time for basic tech support:
1. Are batteries good?
2. Is mouse plugged in?
3. Is mouse on/connected?

Now, if that isnt the problem, can you hit alt-F2, then run lsusb?

---

### Post by theozzlives on 2009-04-04
Did you hit the button on the receiver til the light flashes, then the button on the bottom of the mouse?

---

### Post by alcav on 2009-04-04
Hi all ,
It's a "creative" mouse,works fine on xp on same comp.Batteries brand new,it is ubuntu version 8.What updates would I be looking for?.

Thanks for your replies.....Alan

---

### Post by Ben Crisford on 2009-04-04
> **alcav said:**
> Hi all ,
It's a "creative" mouse,works fine on xp on same comp.Batteries brand new,it is ubuntu version 8.What updates would I be looking for?.

Thanks for your replies.....Alan

Do:

*Alt+F2> Isusb*

---

### Post by tjwoosta on 2009-04-04
> **Ben Crisford said:**
> Do:

*Alt+F2> Isusb*

umm.. im pretty sure thats not going to do anything

i think you meant to say

press alt-f2 then in the box that pops up type

```
gnome-terminal
```

then in the terminal type

```
lsusb
```

---

### Post by alcav on 2009-04-05
Thanks for all your replies guys,sadly tho nothing worked.
I even tried a wired mouse to no avail,but the usb and wired mice are ok on XP.

Can't really assess Ubuntu without a mouse,although I like what I have seen so far.

Alan

---

### Post by rhcm123 on 2009-04-05
> **alcav said:**
> Thanks for all your replies guys,sadly tho nothing worked.
I even tried a wired mouse to no avail,but the usb and wired mice are ok on XP.

Can't really assess Ubuntu without a mouse,although I like what I have seen so far.

Alan

consider filing a launchpad bug, mice are one of the few things that always work for me with ubuntu

---

