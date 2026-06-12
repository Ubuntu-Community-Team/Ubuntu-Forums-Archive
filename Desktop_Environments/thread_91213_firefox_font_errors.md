---
title: "firefox font errors"
date: 2005-11-16
forum: Desktop Environments
---

### Post by dninja on 2005-11-16
I'm running an AMD64 but have installed the 32 bit firefox following the howto in the forums. Now whenever I run it up I get the following error repeated whenever I try to paste to or from firefox.
[PHP]
(firefox-bin:11491): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
[/PHP]

I don't know if this is a firefox bug or something to do with the fact I'm running the 32 bit version on a 64bit os.

I've seen another post where somone suggests setting a couple of environment variables for GTK and PANGO but that doesn't work for me.

Can anyone help?

---

### Post by Casey on 2005-11-16
With a 64 bit Firefox/64 bit OS I don't have a problem copying and pasting.  It looks like it might be related to the 32 to 64 bit transition while copying.  I unfortunately don't know how you could fix that without going to all 64.

Do you absolutely need flash (I presume that's why you're using 32 bit firefox?)

Edit: Oh, also I don't think your title is particularly specific.  Perhaps you could change it to (if these forums allow you to edit the title) "Can't Paste To/From 32bit Firefox with 64bit OS."

---

### Post by dninja on 2005-11-17
I need flash as I'm a web developer and my designer likes putting flash things on pages, even though I usually complain about lack of accessibility he never listens!

Anyone else with the same problem? I'll try cross posting this to the AMD64 forum and see if I get an answer from there.

---

### Post by bin on 2005-11-17
Hi 

I may be barking up the wrong tree, but if you run dpkg-reconfigure locales and then re-select the default set, then select Western in Firefox - might help?

in light

bin

---

### Post by dninja on 2005-11-17
I'll give it a try when I get home.

Thanks

---

