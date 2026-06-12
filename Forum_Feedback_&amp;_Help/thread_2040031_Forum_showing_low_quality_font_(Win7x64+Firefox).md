---
title: "Forum showing low quality font (Win7x64+Firefox)"
date: 2012-08-10
forum: Forum Feedback &amp; Help
---

### Post by erupter on 2012-08-10
Hi.
I've been having a problem recently with my laptop: the ubuntu forums look ugly!
This does not happen on my desktop pc which has the same software config (Win7x64+Firefox).

Following is a picture of the problem
[IMG]http://web.tiscali.it/img/ubuntuforumsproblem.jpg[/IMG][IMG]http://web.tiscali.it/erupter/img/ubuntuforumsproblem.jpg[/IMG]

It happens only on the ubuntu forums, never seen any such thing on any other page.

Any advice?

---

### Post by coffeecat on 2012-08-10
As with your desktop, ubuntuforums in my laptop with Win7 + Firefox looks just fine. Two thoughts:

Check your cleartype settings. Has cleartype been turned off? However, the font rendering in your screenshot is far worse than when I switch off cleartype.

With your laptop, what is the font rendering like for ubuntuforums in another browser such as Internet Explorer or Chrome?

---

### Post by erupter on 2012-08-10
IE9 is ok, cleartype is off (neverliked it) but so is on the desktop which doesn't show the problem.

---

### Post by steeldriver on 2012-08-11
I've been struggling with this (well, similar - in my case it's fine on a Xubuntu laptop and a Win XP 32-bit laptop - but horrible on my Windows 7 x64 desktop - all Firefox)

It does seem to be a Firefox issue - the best results I've got so far is by going to about:config in the address bar, then finding the entry

```
gfx.downloadable_fonts.enabled         true
```and toggling it to 

```
gfx.downloadable_fonts.enabled         false
```I then re-enabled cleartype

FWIW the desktop is a Core i5 with integrated Intel graphics - depending on your H/W you might want to play with all the gfx settings and see if anything works for you

[http://support.mozilla.org/en-US/questions/791489](http://support.mozilla.org/en-US/questions/791489)

---

### Post by CharlesA on 2012-08-12
When I tested it last time, the text appeared like in the OP when Cleartype was off. Windows 7 defaults it to on. Windows XP defaults it to off.

---

