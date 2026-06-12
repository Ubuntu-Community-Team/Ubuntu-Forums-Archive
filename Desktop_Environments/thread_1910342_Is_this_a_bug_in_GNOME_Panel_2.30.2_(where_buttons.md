---
title: "Is this a bug in GNOME Panel 2.30.2 (where buttons go blind on the sides)?"
date: 2012-01-17
forum: Desktop Environments
---

### Post by rocksockdoc on 2012-01-17
I think I'm running into a Ubuntu 10.04 Lucid Lynx bug in the GNOME Panel 2.30.2 where the panel buttons instantly become blind when the panel is displayed to the sides.

[LIST]
[*]When Gnome panels are oriented on top or bottom, they work fine
[*]But when they're oriented on either side, they instantly go blind
[/LIST]
   Is this a known bug? Is there a known workaround? Can't even an icon or program name be displayed?

These blind icons (which convey absolutely no information) are especially frustrating because, from a practical standpoint, vertical (up:down) screen space is at a premium on any laptop ... therefore all menus and program indicators are best placed on the (less critical) horizontal area (side:side) area.

To illustrate the problem, here is my laptop screen with four programs running (plus the Gnome panel properties form) with the only difference between the two screenshots being the Gnome panel placement.

[SIZE=3]**Notice that the buttons convey information when the Gnome panel is on the top or bottom:**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210997&stc=1&d=1326776544[/IMG]

[SIZE=3]**As soon as we set the Gnome panels to the sides (either side), the buttons go blind!**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210998&stc=1&d=1326776544[/IMG]

The user will note this happens with any number of buttons. That is, even with a single button, (with or without autohide), the panel buttons instantly go blind when the Gnome panels are placed on the sides. 

The questions are:
Q1: Is this an already-reported bug?
Q2: What is the known workaround?
Q3: Is there any way to get ANY information out of the buttons when they're on the side? (an icon? a program name?)

---

### Post by Krytarik on 2012-01-17
That's because you've the Panel's "Size" to a value lower than 24 px (thanks for including the Properties window in your screenshots!).

> **rocksockdoc said:**
> Q1: Is this an already-reported bug?
I didn't find one at the first glance, but you may search for yourself:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel](https://bugs.launchpad.net/ubuntu/+source/gnome-panel)

> **rocksockdoc said:**
> Q2: What is the known workaround?
Q3: Is there any way to get ANY information out of the buttons when they're on the side? (an icon? a program name?)
Set the Panel's "Size" to any value equal or higher than 24 px; it would start with an icon.

Regards.

---

### Post by rocksockdoc on 2012-01-17
You were right! It really 'was' that simple. It's not a bug at all. It's user error! Thanks!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211023&stc=1&d=1326826060[/IMG]

---

### Post by Krytarik on 2012-01-17
> **rocksockdoc said:**
> It's not a bug at all. It's user error!
Well, I would *indeed* deem that a bug, since if the Panel is oriented horizontally, the icons *don't* disappear, no matter what "Size" you set. And reg. the 'break-even' value for "Size"; apparently that depends on what theme you are using.

---

### Post by mcduck on 2012-01-17
...on the other hand filing a bug about that wouldn't be likely to accomplish anything; from Ubuntu developer's point-of-view it's an upstream bug, and the upstream (Gnome project) has already moved on to working with Gnome 3 so it's very unlikely they'd start redesigning the window list applet for the old gnome-panel any more.

---

### Post by Krytarik on 2012-01-17
> **mcduck said:**
> ...on the other hand filing a bug about that wouldn't be likely to accomplish anything; from Ubuntu developer's point-of-view it's an upstream bug, and the upstream (Gnome project) has already moved on to working with Gnome 3 so it's very unlikely they'd start redesigning the window list applet for the old gnome-panel any more.
Yeah, of course; just saying. :D

---

### Post by rocksockdoc on 2012-01-17
> **Krytarik said:**
> if the Panel is oriented horizontally, the icons *don't* disappear

This is true. And easy to replicate.

> **Krytarik said:**
> regarding the 'break-even' value for "Size"; apparently that depends on what theme you are using.

I change nothing unless the change imparts some kind of advantage.

So, when I first installed Ubuntu, I simply chose the "clearlooks" theme, which closest matched the ingrained Windoze intuitiveness - and left it at that.

I can't speak for any other theme ... but if someone is to use the Clearlooks theme (which closest matches Windoze as far as I can tell), I'd list the default "clearlooks" theme as enforcing a 30-pixel minimum size on Gnome side panels as shown below ... 

For me, that's all I needed. Thanks for the advice. I can't believe the solution/workaround was so simple! 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211038&stc=1&d=1326837231[/IMG]

---

