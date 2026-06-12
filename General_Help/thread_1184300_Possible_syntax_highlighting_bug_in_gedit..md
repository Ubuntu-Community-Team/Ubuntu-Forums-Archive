---
title: "Possible syntax highlighting bug in gedit."
date: 2009-06-11
forum: General Help
---

### Post by lavinog on 2009-06-11
I was looking at some init.d scripts and noticed that the syntax highlighting doesn't work right with /etc/init.d/checkroot.sh
Everything past line 72: ```
	DEV="$(findfs "$DEV")"
``` is treated as a string.
if I change the line to ```
	DEV="$(findfs "$DEV ")"
``` everything looks fine (except the enclosed space now)

I tried to recreate the issue on a new file, and I can't seem to get it to do it.

My main question is if this is just me, or does it do this for other users?

---

