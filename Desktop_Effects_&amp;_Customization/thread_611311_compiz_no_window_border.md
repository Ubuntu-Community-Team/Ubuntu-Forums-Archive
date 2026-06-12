---
title: "compiz no window border"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by Word on 2007-11-12
I upgraded from 7.04 to 7.10 when i go to appearance and turn on effects I lost my title bar. I have read through the forums no solution. The effects seem to work I have an nvidia card no other problems

---

### Post by Word on 2007-11-12
I installed xserver-xgl restarted and it worked. Dont ask me how

---

### Post by rundee_f on 2007-11-12
Try this : System>Preferences>Advanced Desktop Effects, find Window Decorations.. In the Command line, type **emerald** (for emerald user) or **gtk-window-decoration** (for non-emerald user)..

tell me if this help...

---

### Post by FuturePilot on 2007-11-12
> **Word said:**
> I upgraded from 7.04 to 7.10 when i go to appearance and turn on effects I lost my title bar. I have read through the forums no solution. The effects seem to work I have an nvidia card no other problems

Did you previously have Trevino's Compiz Fusion installed on Feisty?

---

### Post by epidemiks on 2008-03-08
> **rundee_f said:**
> Try this : System>Preferences>Advanced Desktop Effects, find Window Decorations.. In the Command line, type **emerald** (for emerald user) or **gtk-window-decoration** (for non-emerald user)..

tell me if this help...

I've just setup compiz on gutsy after installing a snazzy new 22" wide screen and a nice nvidia graphics card, and I've got the same issue, typing emerald at the command get the window borders back,  but stops working when i quit the command prompt... how do you get this to stay? fanks!

---

### Post by bwang on 2008-03-08
Alt+F2

Type emerald --replace

---

