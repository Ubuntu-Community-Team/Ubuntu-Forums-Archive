---
title: "Xorg vs XFree86"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by chaok on 2005-10-21
What is the difference between these 2?  I currently just use Xorg.  I see that Cedega require XFree86.

Thanks

---

### Post by arcanistherogue on 2005-10-21
I don't really know much, but I remember my friend telling me that Xorg has more documentations and stuff.  He said its all the X window system, but they are just like different distrobutions of it.  note that this probably isnt a good analogy though.

Anyway, when it refers to Xfree86, Xorg can be used also.  It just means you need the X window system installed, and I use cedega frequently on this computer with Xorg.

---

### Post by chaok on 2005-10-21
ok very cool.

Thanks.  Now to get my OpenGL working ;)

---

### Post by joneall on 2005-10-23
Why *does *Ubuntu use Xorg instead of XFree86?  I thought the latter was the Debian standard.  My Debian "Bible" explains it, not Xorg.

---

### Post by Zeroedout on 2005-10-23
[quote=joneall]Why *does *Ubuntu use Xorg instead of XFree86? I thought the latter was the Debian standard. My Debian "Bible" explains it, not Xorg.[/quote]

because Xfree86 switched to a license that is not gpl and i belive it wasn't free software friendly. So what happened is people forked the code and called it x.org. They are essentially the same thing, however xorg is free, xfree86 is not. Both are beer free, just xorg is freedom free as well.

---

### Post by Burgundavia on 2005-10-23
Ok, time to clear out the fog here.

Xorg is a fork of XFree86. The straw that broke the camels back to create the fork was a relicensing of XFree86 to have an annoying advertising clause.

What does this mean for you, the humble gamer? Good things, because the recent development with Xorg makes it easier to ship new 3D drivers seperate from the mainline tree, as well as new completely open-source drivers, such as those supporting the r300 series of ATI cards (Radeon 9200+ and PCIE)

Hope that clears up the air.

Corey

---

### Post by Biased turkey on 2005-10-23
[QUOTE=Burgundavia]Ok, time to clear out the fog here.

Xorg is a fork of XFree86. The straw that broke the camels back to create the fork was a relicensing of XFree86 to have an annoying advertising clause.

What does this mean for you, the humble gamer? Good things, because the recent development with Xorg makes it easier to ship new 3D drivers seperate from the mainline tree, as well as new completely open-source drivers, such as those supporting the r300 series of ATI cards (Radeon 9200+ and PCIE)

Hope that clears up the air.

Corey[/QUOTE]

Xfree86 is dead, long live Xorg

---

### Post by joneall on 2005-10-24
Very clear.  Thank you.  John

---

### Post by clparker on 2005-10-24
I dont know if any of you guys remember the good ol' grumpy groundhog ubuntu, the one released last year, 4.10, It used XFree 86, and It sucked, While the conversion to Xorg was somewhat rocky come hoary six months later, it was well worth it, i was there, i suffered for all of you, allot of us did.

---

### Post by Reiver_Fluffi on 2005-10-24
[quote=joneall]Why *does *Ubuntu use Xorg instead of XFree86? I thought the latter was the Debian standard. My Debian "Bible" explains it, not Xorg.[/quote]

I believe the Debian guys are working towards using Xorg as of the next stable release, AFAIK!

---

### Post by ygarl on 2005-10-24
So, Cedega just happily works with XOrg instead of xfree86 then?

---

### Post by Brinstar on 2005-12-31
In a similar vein, i'd like to know if the drivers that Intel supply for the 855GM chipset will 'just work' with Xorg. The current ones claim to be for Xfree86.

---

### Post by rikai on 2005-12-31
[QUOTE=ygarl]So, Cedega just happily works with XOrg instead of xfree86 then?[/QUOTE]

100% correct.

[QUOTE=Brinstar]In a similar vein, i'd like to know if the drivers that Intel supply for the 855GM chipset will 'just work' with Xorg. The current ones claim to be for Xfree86.[/QUOTE]

All intel chipseets are able to be used on x.org I believe without compiling the drivers from intel, at least with x.org...

Do us a favor and post up your xorg.conf in a set of quote tags(personal preference, easier on my eyes)?

---

### Post by AthlonMDK on 2006-01-01
So as we know now Xorg is a fork of XFree86, but not just a fork. 
Advantages (Xorg -> XFree86)
- Xorg 7.0 will be modular especially nice for LFS / GENTOO, not having to compile the whole Xorg.
- Xfree86 had slow progress while XORG has a faster development.
- XORG = GPL :KS 
- Faster bugfixes in XORG

---

### Post by leech on 2006-01-01
Another clarification of this, besides the licensing, XFree86 was also forked because of it's extremely slow development.  X.org has had several releases since the fork, and I think XFree86 has really only had one.  

And Yes, the next release of Debian will have X.org in it.  In fact the Testing and Unstable already do use X.org.

Leech

---

