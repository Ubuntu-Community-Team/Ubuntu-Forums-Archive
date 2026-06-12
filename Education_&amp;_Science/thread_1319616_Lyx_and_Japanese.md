---
title: "Lyx and Japanese"
date: 2009-11-08
forum: Education &amp; Science
---

### Post by Kulgan on 2009-11-08
Hi all,

I've been using Lyx for a while now, and I'm very pleased with it. Glad to see the back of OpenOffice's formula tools. However, now that I've got iBus working correctly with Japanese input I would also like to be able to use this in Lyx. This should be relevant to all users of CJK out there. 

Now that Lyx comes with Unicode support built in, this should not be a problem. Yet it remains an unsolved issue. 

I have tried following guidelines from [http://wiki.lyx.org/LyX/Unicode](http://wiki.lyx.org/LyX/Unicode) to no avail. I have installed all the fonts I can find that look promising from the repositories and I have changed the Language/Encoding without improvement. 

If anyone has any ideas/success stories I would love to hear them!

Thanks,
~ K

---

### Post by antony_css on 2009-12-20
I have the same problem using ibus in lyx - Ctrl+Space cannot trigger the input engine.

I found similar issue from this link:
[http://code.google.com/p/ibus/issues/detail?id=84]("http://code.google.com/p/ibus/issues/detail?id=84")
It is said that this issue affects all qt applications, and so "ibus" should be replaced with "xim" in qt environment.

---

### Post by Kulgan on 2009-12-20
That's odd. I have no problem switching to kana input with Ctrl-Space. Everything appears correctly in Lyx, but it doesn't export correctly.

The attachment is taken with the encoding set to "Unicode (CJK)".

Good luck :/

---

### Post by kleeman on 2009-12-20
Try asking here:

[news://news.gmane.org:119/gmane.editors.lyx.general](news://news.gmane.org:119/gmane.editors.lyx.general)

The devs hang out there and here:

[news://news.gmane.org:119/gmane.editors.lyx.devel](news://news.gmane.org:119/gmane.editors.lyx.devel)

---

