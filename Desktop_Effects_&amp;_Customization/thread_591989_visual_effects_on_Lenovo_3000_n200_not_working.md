---
title: "visual effects on Lenovo 3000 n200 not working"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by thatwouldbeme on 2007-10-26
When I try to select 'normal' or 'extra' visual effects in the appearance manager I get an error saying 'desktop effects could not be enabled'

What do I need to do to get them to work?

sincerely,
thatwouldbeme

---

### Post by thatwouldbeme on 2007-10-26
update:  apparently xgl server is not installed but when I install it I am logged back off immediately after logging in.  any ideas?

---

### Post by staib on 2007-12-09
Hi - has ANYONE got desktop effects on this Lenovo laptop working - my version only has the intel graphics chip (which runs Vista Aero fine) but I also want my 7.10 desktop effects to be good so I can show it off at work :-)

Nick

---

### Post by Ub1476 on 2007-12-09
Graphic controller?

```
lspci | grep VGA
```

---

### Post by staib on 2007-12-15
Hi - sorry I missed that reply ](*,)

The graphic controller (lspci | grep VGA) is:

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Any further help from you or others greatly appreciated - I even got the sound working now, so this is all looking good...

Nick

---

### Post by gryzzly on 2007-12-17
> **staib said:**
> Hi - has ANYONE got desktop effects on this Lenovo laptop working - my version only has the intel graphics chip (which runs Vista Aero fine) but I also want my 7.10 desktop effects to be good so I can show it off at work :-)

Nick

Hi, running COMPIZ on the same mashine fine (this thing that is responsible for visual effects)
(but video card is nVidia 7300 go, not intel-on-board;)

---

### Post by monkeyking on 2007-12-22
funky graphics work out of the box for me.
That is after I installed the restricted driver.

---

### Post by staib on 2007-12-23
I finally got the desktop effects working (with a restricted driver) but now find that the sound has completely gone again - aarghh!  Everything (sound, fingerprint reader, camera etc) works fine in Vista - apart from the clutzy OS itself, of course!

---

### Post by monkeyking on 2007-12-23
I havn't got the fingerprint stuff working yet.
Well I have never had a computer with fingerprint reader, so I don't really know what I'm missing.

But I had very few problems with the lenovo.
I spend a few hours before finding out, that motherboard modem needs to be enabled in bios,
otherwise sound won't work.

---

