---
title: "Feisty Compiz Success"
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by silex on 2007-04-17
Just wanted to give a huge thank you for any passing by devs from the desktop effects team.  My Radeon 9800 worked "out of the box" with the ati driver in the Feisty Beta.  Enabled desktop effects and I've got wobbly windows and everything; the only thing that took any time was looking up the gnome-compiz-manager package to configure some of the options.

In Edgy, getting fglrx/xgl/beryl going was a bit of a hassle (beryl's always a little broken, anyway) but now I've got all the effects I want/need with zero hassle!

---

### Post by guv on 2007-04-20
Likewise, desktop effects and compiz worked out of the box with my Ati 850XT using the "ati" driver. Previously I've tried Fedora Core and Ubuntu Edgy, and in both instances couldn't get desktop effects working with either using the ati, radeon or fglrx drivers.

So yeah, big thanks to the Feisty devs from me too. :)

---

### Post by el_itur on 2007-04-20
Seems like I'm the only one that follow the book and din't get the desktop effects work with nvidia fx 5200.

[code]
gandalf-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[code]

mi xorg-conf seems to be right (although It wasn't needed right?)

any one else with this problem?

---

### Post by derrekito on 2007-04-21
Anyway we can do this running the proprietary drivers?

---

### Post by The Pinny Parlour on 2007-04-21
Nice when it works. :)

---

### Post by derrekito on 2007-04-21
> **The Pinny Parlour said:**
> Nice when it works. :)

I wish I could say the same thing :(

---

### Post by Stelakis1 on 2007-04-21
I have an hp nx5000 and everything worked out perfectly after the fresh install...
But when I did the first update the cube stopped working...:(

---

### Post by orange2k on 2007-04-21
Yeah the same happened to me but I enabled it againg by going to the console and typing:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

and then:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

---

### Post by derrekito on 2007-04-21
> **Stelakis1 said:**
> I have an hp nx5000 and everything worked out perfectly after the fresh install...
But when I did the first update the cube stopped working...:(

Is that an ATI card?  If so, are you using the open source drivers or the fglrx drivers?

> **orange2k said:**
> Yeah the same happened to me but I enabled it again by going to the console and typing:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

and then:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

I'm afraid of going and just typing crap out, so I'll ask:  What does that do?

---

### Post by orange2k on 2007-04-21
It enables the cube...

---

### Post by derrekito on 2007-04-21
> **orange2k said:**
> It enables the cube...

Opps... lol okay thnx, I suppose I should read more carefully.

---

### Post by orange2k on 2007-04-21
> **derrekito said:**
> Opps... lol okay thnx, I suppose I should read more carefully.

No problem, hope it work for you...

---

### Post by Stelakis1 on 2007-04-21
Its an Intel 82852GM intergrated graphics card... Anyway thanks Orange2k but I already formated the partition for the 2nd time and now everything works fine... untill the next ugrade... Then I will try your way...

---

### Post by lbe on 2007-04-26
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

Worked perfect for me, thanks alot! :)

---

