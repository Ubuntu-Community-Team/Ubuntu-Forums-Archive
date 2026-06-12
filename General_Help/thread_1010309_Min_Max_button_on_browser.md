---
title: "Min Max button on browser"
date: 2008-12-13
forum: General Help
---

### Post by LE CHARBON on 2008-12-13
Lost my min max button on swiftweasel. The same for firefox as well. I am refering to the buttons on the top right hand corner of the browser. Any ideas? I just upgraded to 8.10.:confused:

---

### Post by fooman on 2008-12-13
in firefox (maybe same for swiftweasel)...try this:


press f11 to go to fullscreen, then f11 again to get to a normal size.  that *should* fix it...if it comes back again when you restart firefox, then try this:

do the f11 thing twice and when you get to the normal size screen...unmaximize the screen (not minimize).

then close firefox and reopen it.

maximize firefox and you should be good.

---

### Post by LE CHARBON on 2008-12-13
I tried multiple versions of that with no avail. Anyone with other ideas?

---

### Post by fooman on 2008-12-13
how about a screenshot?

---

### Post by LE CHARBON on 2008-12-13
/home/weston/Desktop/screen

---

### Post by LE CHARBON on 2008-12-13
No screen shot.

---

### Post by fooman on 2008-12-13
do the buttons come back when you disable visual effects?

try going to system > preferences > appearance > visual effects > try setting to "none"

---

### Post by rswoody2000 on 2008-12-13
Does that only happen in those 2 programs or does it happen in any window?

---

### Post by LE CHARBON on 2008-12-13
> **fooman said:**
> do the buttons come back when you disable visual effects?

try going to system > preferences > appearance > visual effects > try setting to "none"

That was it. Visual effects must have some kind of bug.

---

### Post by -kg- on 2008-12-13
I found another thing that worked for me, at least with the problem concerning Firefox buttons.  From the last post [[COLOR="Blue"]_on my thread:_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=958945&page=2")

> I found while doing the F11 trick does work, on some machines i have seen this happen way too much as is such not an acceptable solution.

Don't fret though! I did find a solution. You need to fire up Compiz Settings Manager (need to install it), and under Utility -> Workarounds, disable Legacy Fullscreen Support.

This has fixed it up for every machine i have see the issue with.

While the F-11 trick does work, I was having trouble with the problem re-occurring, necessitating repeating the F-11 thing.  Once I followed the above procedure I have had no more problems with it whatsoever.

---

### Post by LE CHARBON on 2008-12-13
> **-kg- said:**
> I found another thing that worked for me, at least with the problem concerning Firefox buttons.  From the last post [[COLOR="Blue"]_on my thread:_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=958945&page=2")



While the F-11 trick does work, I was having trouble with the problem re-occurring, necessitating repeating the F-11 thing.  Once I followed the above procedure I have had no more problems with it whatsoever.


Itried all that and it does not work for me. Is it a driver issue or bug?

---

### Post by -kg- on 2008-12-14
I'm not real sure.  I'm using Hardy for both my installs (32 bit on my laptop and AMD64 on my desktop), and disabling the Legacy setting in Compiz worked for both of them.  But I have no experience yet with Intrepid.

I don't think it's driver related, but I don't know that it's a bug, either.  Considering that a "Legacy" setting (for Hardy, at least), I would think that it was just an issue of the software having issues with newer OSes without good legacy support (I suppose you could call that a bug).

Earlier you said:

> [QUOTE] Originally Posted by fooman  View Post
do the buttons come back when you disable visual effects?

try going to system > preferences > appearance > visual effects > try setting to "none"
That was it. Visual effects must have some kind of bug.[/QUOTE]

This confuses me.  My technique deals with "Visual Effects" (via Compiz) as well, though no setting of Visual Effects had any effect at all...only disabling Legacy.

I don't know.  Though I'm hardly new to computers (started in the early '80s), I'm relatively new to Linux.  I'm continually studying, but I'm not quite there yet.

---

