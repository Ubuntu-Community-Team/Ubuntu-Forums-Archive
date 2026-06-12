---
title: "xubuntu manage volume with keyboard"
date: 2006-08-20
forum: Desktop Environments
---

### Post by progster on 2006-08-20
Hey there,

I have just installed the latest version of xubuntu after running ubuntu for about 2 years. I was quite used to managing the volume with my [logitech internet pro keyboard](http://www.logitech.com/index.cfm/partners/details/US/EN,CRID=1970,parentCRID=925,SCRID=925,CONTENTID=9534), which always worked out of the box. Not so for xubuntu unfortunatly... it was probably taken care of by some gnome service I think. Can anyone point me in the right direction to get it working under xfce? 

A search on these forums didn't show up anything usefull, so either it's so obvious I should have seen it or I'm the first one asking :)

---

### Post by progster on 2006-08-20
Ok, I found it. For other people having this issue:

* [download](http://keytouch.sourceforge.net/dl-keytouch.html) the ubuntu package of [keytouch](http://keytouch.sourceforge.net/index.html).
* Install it (using dpkg or by double clicking the .deb in ubuntu dapper)
* Run it (you will find it under System->Keytouch on xubuntu)
* Select your keyboard type
* Apply settings and your done 

btw the similar threads feature of this forum is amazing!

---

### Post by NJC on 2007-06-25
progster;

Thanks!! I tried the xmodmap route and was apparently too daft to figure it out. But I did get it working using KeyTouch in Dapper 6.06 (XFCE desktop) with a HP SK-2511A keyboard.

---

### Post by ugm6hr on 2007-07-02
Keytouch (and a keyboard editor for it - so you can add any keyboard) are in the Fesity repositories.

---

### Post by NJC on 2007-07-31
Keytouch was so laggy and horrid to use that I eventually canned it, along with XFCE desktop too. Back to Gnome - slow, but reliable, at least on my old machine.

---

### Post by ugm6hr on 2007-07-31
> **NJC said:**
> Keytouch was so laggy and horrid to use that I eventually canned it, along with XFCE desktop too. Back to Gnome - slow, but reliable, at least on my old machine.

I found KeyTouch annoying too.  But managed to configure volume shortcuts with the built-in XFCE Keyboard Settings:
[http://ubuntuforums.org/showpost.php?p=2998469&postcount=2](http://ubuntuforums.org/showpost.php?p=2998469&postcount=2)

Does the same thing, just without the visual representation on-screen.  You do need to work out which* amixer* volume control to use though (I think most use *PCM*, whereas I chose *Surround* for my laptop).

Just a thought if you're not fixed on GNOME...

---

