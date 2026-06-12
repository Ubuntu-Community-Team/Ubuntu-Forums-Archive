---
title: "Trying to install Hardy on Dell Optiplex Gx1"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OneMixDJ on 2009-05-07
Ok,

I thought this would be straight forward, but obviously it's not. ;)

I'm trying to convert my Optiplex Gx1 from XP to Ubuntu.

I tried using a known working CD which was successfully used on my Compaq and Gateway desktops in the past, and it's now being "ignored".

My boot sequence is verified for CD-Rom first.
The iso CD is ignored and then Windows starts...

If I remove the HD from the boot sequence (to force it solely) on CD), the iso is not being read for some reason.

Meanwhile if I try the iso CD on another machine I have (Gateway), it works...

Is this a stupid Dell thing I'm dealing with here?

I want to replace Windows with Hardy, then upgrade to Ubuntu Studio.

Any help is appreciated...Thanks!

---

### Post by coffeeaddict22 on 2009-05-07
On My Dell you've got to go into the boot options menu each time you want to boot off the CD.  I'm assuming you mean you've gone into the BIOS and OK'ed the CD as a Boot option from what you've said...

---

### Post by OneMixDJ on 2009-05-07
> **coffeeaddict22 said:**
> On My Dell you've got to go into the boot options menu each time you want to boot off the CD.  I'm assuming you mean you've gone into the BIOS and OK'ed the CD as a Boot option from what you've said...

Yes,

I have the CD-Rom as the first boot option; and have tried this with and without the HD in the picking order. It seems to me that the iso just refuses to be read.

---

### Post by coffeeaddict22 on 2009-05-07
There's two options when it first starts; one gets you into the BIOS, one you select what you're booting from.  (It's F12 on my machine)... have you tried that?

---

### Post by lykwydchykyn on 2009-05-07
Are you sure the CD drive is any good?  Optical drives are one of the first things to go bad on most machines, in my experience.   A machine that old is bound to have a problematic drive.

I used to have a GX1 in my office, but I got rid of it last year; so I can't remember if it will boot to USB but I don't think it did.  Any chance you can plug a different CD drive into it?

---

### Post by OneMixDJ on 2009-05-07
I just tried the F12 option, it doesn't work on my machine.

Here's something even wackier; check this out:

I have a complete set of RH 7.2 that I tried to install via boot from (just to see what happens), and like Ubuntu, the CD is once again ignored and Windows just boots up. 

My CD drive works in Windows, so I don't know what the deal is... *LOL*

---

### Post by OneMixDJ on 2009-05-07
> **lykwydchykyn said:**
> Are you sure the CD drive is any good?  Optical drives are one of the first things to go bad on most machines, in my experience.   A machine that old is bound to have a problematic drive.

I used to have a GX1 in my office, but I got rid of it last year; so I can't remember if it will boot to USB but I don't think it did.  Any chance you can plug a different CD drive into it?

Well, the CD drive does work in Windows because it was how I installed XP in the first place. However, I guess I'll try changing the CD drive and see if that does anything.

---

### Post by coffeeaddict22 on 2009-05-07
What I think we're all saying is it aint Dell, or Linux.  The CD is your most likely problem, although it should be at least trying to spin up if you've properly selected it. 

If it doesn't spin up, you're not selecting the CD to boot from.  You may be changing things in your BIOS but not selecting the right key combination to save it; you may be locked out from starting off the CD if it's an ex-work PC or something like that.  Both my Dell machines have two selections when you get offered the BIOS menu notice after the POST; it's possible the key to use is different on your machine, so watch the upper right corner of the screen to see if it is an option.

If it does try to spin up: knowing the interaction of CD's and little people in _my_ house, any CD 6 months old is most likely in need of recutting because of all the scratches.

---

### Post by OneMixDJ on 2009-05-07
Guys,

I changed the CD-Rom from one of the other machines and now the iso is being read.

*"Ohhh, Happy DAY!!!"*
 \\:D/\\:D/\\:D/

I guess the one that was in there, although functioning, was likely too old to read the iso CD.

Thanks very much for your help! 
=D>=D>=D>


I am now moving forward with my install!

Thanks!

---

