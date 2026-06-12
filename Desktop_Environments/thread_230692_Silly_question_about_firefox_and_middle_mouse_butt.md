---
title: "Silly question about firefox and middle mouse button"
date: 2006-08-06
forum: Desktop Environments
---

### Post by rogeriovinhal on 2006-08-06
In Firefox everytime I accidentaly press the middle mouse button and miss a link, firefox goes to a random page (mostly of the times it is a page that I have never and would never visit).

What is this page?

---

### Post by glotz on 2006-08-06
Try this. Type about:config to location bar and hit enter. Find middlemouse.openNewWindow and doubleclick true > false. That's it.
(the page opened is determined by your clipboard content)

---

### Post by rogeriovinhal on 2006-08-06
Actually, this one seems more like it:
middlemouse.contentLoadURL

Based on my clipboard contents? But how come it show pages that I have never seen before?

---

### Post by glotz on 2006-08-06
Oh, you're right about that. [http://kb.mozillazine.org/Middlemouse.contentLoadURL](http://kb.mozillazine.org/Middlemouse.contentLoadURL)

You're seeing strange pages because of how Firefox handles non-URL input in location bar; it makes a google's "i'm feeling lucky" search with the input.

---

### Post by rogeriovinhal on 2006-08-06
Oh, that explains a lot. :) 
Damn you "I'm feeling lucky"! :D

---

