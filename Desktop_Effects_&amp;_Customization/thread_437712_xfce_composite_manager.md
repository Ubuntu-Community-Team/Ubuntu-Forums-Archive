---
title: "xfce composite manager"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by james_027 on 2007-05-09
Hi,

what are the requirements of xfce composite manager in order to work? does it need xgl or aiglx? I am using fesity on ati x1400. I was able to enable the composite feature of xfce but it corrupts my display.:( 

Any advice how to get it to work flawlessly

Thanks

---

### Post by kefir on 2007-05-09
Enable the Composite extension in the X11 config file and make use Xfwm4 is compiled with compositor support (xfwm4 -V).

/etc/xorg.conf

 Section "Extensions"
   Option "Composite" "Enable"
 EndSection

NVidia users also need (well it&#8217;s recommended) this in the device section of the card:

 Option "RenderAccel" "true"
 Option "AllowGLXWithComposite" "true"

Stolen from the xfce wiki =)
[http://wiki.xfce.org/](http://wiki.xfce.org/)

Good luck!

---

### Post by james_027 on 2007-05-09
Hi,

I just found out that ati still has no support for composition, could aiglx or xgl help to enable the composite feature of xfce?:confused: 

Thanks

---

### Post by kefir on 2007-05-09
what does 

xfce4 --version

say?

---

### Post by kefir on 2007-05-09
Ok just tried to get it up and running on my own computer (also have a ATI) card but no luck so it seems like there's a no go with this one...Sucks =(

note-to-self : never again buy a crappy *** ATI card

---

### Post by james_027 on 2007-05-09
> **kefir said:**
> Ok just tried to get it up and running on my own computer (also have a ATI) card but no luck so it seems like there's a no go with this one...Sucks =(

note-to-self : never again buy a crappy *** ATI card

Have you try beryl/compiz with your ati card?

thanks

---

### Post by kefir on 2007-05-10
Hi, yepp i've tried beryl , worked just fine =)

Don't want to use it on a regular basis though, to slow and buggy for me :/

---

