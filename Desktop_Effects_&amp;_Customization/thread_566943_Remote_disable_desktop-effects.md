---
title: "Remote disable desktop-effects"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by _Phil on 2007-10-04
Hi all

Question:
Is there a way to disable desktop-effects via SSH?

Situation:
I'm currently at work and want to go on my home pc using vnc.
But desktop-effects are enabled on my home pc and there is a bug in vnc/X11/compiz or whatever using desktop-effects..
So i simply want to disable them.

cheers
phil

---

### Post by eentonig on 2007-10-04
Under Kubuntu, you could try the command 

> kwin --replace

For Ubuntu there's a similar command, but I can't find it for the moment.

---

### Post by _Phil on 2007-10-04
Can't do this by:
> metacity --replace

(metacity is gnome's standard windows manager)

because I have to run this from X.

---

### Post by _Phil on 2007-10-05
Solved it another way, not very nice but it's all I wanted.

I change the driver of X11 to "nv" from "nvidia"  because this one can't load desktop effects due to no support for 3D. Then restart X.

And if I am at home i change the driver back to "nvidia".

cheers
phil

---

