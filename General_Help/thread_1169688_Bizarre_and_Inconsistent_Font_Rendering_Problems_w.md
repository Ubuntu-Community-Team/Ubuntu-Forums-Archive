---
title: "Bizarre and Inconsistent Font Rendering Problems with Ubuntu 9.04"
date: 2009-05-25
forum: General Help
---

### Post by VCSkier on 2009-05-25
I've got a relatively stock installation of Ubuntu 9.04 on my laptop, and I've been experiencing some unusual problems with the font rendering.  At times, certain characters will be consistently replaced by another character.  The resulting character is usually something unidentifiable (at least to me).  It often seems to be a character from another language set, or sometimes even just a meaningless marking or glyph.  Other times it is just the wrong letter.  For example, when I was just googleing for this problem, all the J's in Google's search results were rendered as S's, resulting in several hits containing references to "Saunty Sackalope."

It sounds humorous, and at first it was, but it seems to get progressively worse.  At first I changed the rendering method on the "Fonts" tab of the "Appearance" preferences, and that helped for a few minutes, but as I navigated around the web, more of these anomalous problems started cropping up again, to the point that nothing on the pages were legible.

Also, it is not just limited to Firefox, I have seen the problem in Terminal, Brasero, and the "Appearance" preferences window.  It doesn't seem to affect the Ubuntu's menu, or the desktop though.  A reboot seems to fix things temporarily.

I checked the RAM with MemTest86, and it showed no problems.  I've got an Intel i855GM integrated chipset, on which I have applied the "optimized" fix on psyke83's "Intel Graphics Performance Guide."  Other than that, it's a stock installation, with the exception of VLC, Picasa3, ubuntu-restricted-extras, and Sun Java 6.

Usually with a problem I would just submit a bug report, but this just seems so bizarre!  I wanted to see if anyone else on the forum was having this problem first.

---

### Post by VCSkier on 2009-05-25
Here's a screenshot of it while it's really bad.  Even as I'm typing now, most of the characters are not rendering properly, so I appologize for any typos.  If anyone has any suggestions, please post them.  My wife and I both use this computer for our coursework, and needless to say, this is quite problematic.

---

### Post by afbase on 2009-05-25
can you give us screen shots of 

System >Preferences > Appearance > Fonts

AND

System >Preferences > Appearance > Fonts > Details

Also what are your settings in Visual Effects (System >Preferences > Appearance > Visual Effects)

I hope you can read this.  If not send smoke signals.

---

### Post by afbase on 2009-05-26
can you give us screen shots of 

System >Preferences > Appearance > Fonts

AND

System >Preferences > Appearance > Fonts > Details

Also what are your settings in Visual Effects (System >Preferences > Appearance > Visual Effects)

I hope you can read this.  If not send smoke signals.

---

### Post by VCSkier on 2009-05-26
This morning, font rendering seems to be behaving properly, at least for now.  Here are the screenshots you requested.  It's interesting, when the rendering is acting up, the text in the example box (abcfgop AO...) is even affected.

Visual effects are set to "normal," which was the default when I installed.  I have tried changing it when I'm having the problem, and it doesn't seem to affect anything.

Regarding the settings in these screenshots, hoping it would fix things, after I started experiencing these problems, I did change the font rendering resolution to "86" (matching the results of "$ xdpyinfo | egrep 'dimensions|resolution'").  It didn't help, but it did make the fonts look nicer when they are displaying properly.  :)

Thanks for your help!

Oh, and I'm using ext4, for the record.

---

### Post by VCSkier on 2009-05-28
It seems that the problem was related to the fix I applied for my Intel graphics.  In the process (using psyke83's guide), I had upgraded to the 2.6.29.3 kernel.  Downgrading to Jaunty's stock kernel seems to have fixed it.  Graphics performance is slightly reduced, but it's worth it.  Maybe an update will be released soon.  For now, I'm going to mark this thread as SOLVED.  Thanks for your help!

---

