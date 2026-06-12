---
title: "Typing &quot;TM&quot; shows a symbol"
date: 2009-10-08
forum: Desktop Environments
---

### Post by LannyRipple on 2009-10-08
Anyone know why typing "TM" in text entry areas displays a symbol that looks like a face instead of the letters?  More importantly does anyone know how to get it to stop.

By text entry I mean just about anywhere associated with the desktop.  For instance typing in the title of this post it happened but in the message body here it doesn't.

  -ljr

---

### Post by NinjaNumberNine on 2009-10-08
TM is the symbol for trademark and appears as the letters "TM". Not really sure how to turn it off, as I don't have that problem. I'll check, though. I use KDE, are you using GNOME?
[IMG]http://t2.gstatic.com/images?q=tbn:-lB24LlbQf51FM:http://www.summitsoftlogodesign.com/graphics/LogoDictionary/Symbol1.png[/IMG][IMG]http://t2.gstatic.com/images?q=tbn:wW4SD7NHp2TGQM:http://www.trademarkquery.com/images/Symbol%2520trademark.jpg[/IMG]

---

### Post by Joeb454 on 2009-10-08
It does indeed sound like it's showing the TM logo, though from what I recall, TM isn't in a circle, it's simply &#8482;

Can you provide a screenshot (or confirm that's the symbol you see) at all? :)

---

### Post by NinjaNumberNine on 2009-10-08
> **Joeb454 said:**
> From what I recall, TM isn't in a circle, it's simply ™
? :)
Yeah, you're right, edited my first post,  guess I had remembered the circle on the [IMG]http://t2.gstatic.com/images?q=tbn:1BtSek3WbDmmjM:http://z.about.com/d/inventors/1/G/N/U/RT.GIF[/IMG] :)

---

### Post by andrea000 on 2009-10-08
it will show what your talking about if you
have libtm-perl installed I'm not sure why
libtm is there from what i can see it doesn't
do anything it may have something to do with
the trademark.

---

### Post by LannyRipple on 2009-10-08
I've attached a screenshot.  I'm aware that TM is short for trademark.  What I don't understand is why my system insists on translating it.  I'm running Linux Mint 7 (Ubuntu 9.04 w/ Gnome).  It's almost impossible to google for the problem since TM is often used (to mean trademark of course).  The one reference I ever found to it was a user asking a #ubuntu channel why it happened to him.  Unfortunately he didn't get a response.  (Nor did I when I tried the #gnome and #linuxmint channels recommended by their respective websites.  :/

Specifically if I type TM in uppercase then as soon as the 'M' is typed the TM changes into a symbol.  This occurs even in the middle of a work (e.g., HTML) or for text being presented by the system.  As an example of that last on the editor for these forums on the toolbar on the far right are a pair of angle brackets.  Hovering over them displays the tooltip: "Wrap [H@L] tags around the selected text.'  (Where @ is not the "at" sign but whatever the system is translating TM as.

  -ljr

PS - libtm-perl is for querying and building topic maps.  Additionally I don't have it installed.

---

### Post by LannyRipple on 2009-10-09
Mostly solved anyway.  This seems to be a consequence of using Purisa as my system font.  When I switch to Sans the behavior goes away.  Still not sure of the why of it since I really like the look of Purisa but at least I have a workaround.

  -ljr

---

