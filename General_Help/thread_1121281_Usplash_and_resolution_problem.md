---
title: "Usplash and resolution problem"
date: 2009-04-09
forum: General Help
---

### Post by letmekilluplz on 2009-04-09
I am trying to install a new Usplash but startup manager dosent offer my res which is 1280x800 Any help?

Also how do I find out which color setting I need (8,16,24)?

And my splash screens colors are messed up can anyone tell me why?

---

### Post by letmekilluplz on 2009-04-10
Its been 15 hours now.. so bump

---

### Post by aniruddha on 2009-04-16
Hello all. I have been having this problem as well. I had recompiled the "ubuntu-sunrise" theme, chnaged my menu.lst file to the vga value using hwinfo to match the 1280x800, 8-bit value and edited usplash.conf to x=1280 and y=800. My startupmanager is configured to 640x480, 8 bits. 

I am still however, seeing the usplash not being centered properly (and thus showing up as two images side by side and both cropped strangely) and strange colour distortions on shutdown. Essentially the colours are corrupted so it looks as if someone has thrown neon paint onto my precious usplash theme. Sighs. 

I am using Intrepid on a Lenovo Ideapad Y530 with a Nvidia 9500M G (the latest 180 drivers). Compiz is enabled. 

Any suggestions?

edit: the vga value I got from hwinfo and am using in menu.lst is 0x0361

---

### Post by aniruddha on 2009-04-17
Help me, ubuntuforums, you're my only hope...

---

