---
title: "How do i make Xubuntu more 'XFCE-like'?"
date: 2007-12-09
forum: Desktop Environments
---

### Post by henrypootel on 2007-12-09
Hi
I have recently been using Wolvix Hunter and i love it. the interface is gorgeous, application set is perfect, and the whole system is lightning fast.
Problems cam however, when trying to install other software. i managed to figure out Slapt-Get eventually, but it frankly sucks in comparison to the Debian package management. Thus i came running back into Ubuntu's loving arms(been a user since Warty), this time choosing Xubuntu to get some more of the XFCE goodness.
My problem is, Xubuntu looks pretty much like the standard Gnome version, only blue. There don't seem to be many XFCE specific apps, it's only slightly faster that gnome, and it's just not as great an XFCE experience as Wolvix or Zenwalk. Is there anybody working on making it more XFCE-like at all? or is it just going to be a blue version of the Gnome version, which runs slightly faster on old hardware?

---

### Post by Tenken on 2007-12-09
You could try doing a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") of ubuntu, and install only Xorg and the core xfce desktop instead of the xubuntu-desktop package. Something else to look into would be using Openbox or Fluxbox as your window manager, which is what Wolvix uses.

---

### Post by sstusick on 2007-12-09
I liked XFCE, but it lacks simple configuration tools that Gnome has, so Gnome is what I use.

---

### Post by henrypootel on 2007-12-10
interesting idea. how would i replace the window manager. is it just simply a case of installing fluxbox and if so, how do i tell XFCE that i want it to use fluxbox instead of XFWM?

---

### Post by mali2297 on 2007-12-10
I would try
```

pkill xfwm4 && fluxbox

```

---

### Post by Tenken on 2007-12-10
After installing fluxbox, this should do the trick.
```
fluxbox --replace
```

Also, I would recomment SLiM as an alternative to GDM.

---

### Post by henrypootel on 2007-12-10
wow, that SLIM login is great. i will post my results later.

thanks

---

### Post by henrypootel on 2007-12-13
Hi everyone, here's a screenshot of my XFCE-ified ubuntu gutsy desktop. it fairly cranks on my 700Mhz laptop with 192 megs of RAM. i'm not sure what to call it. maybe Wolbuntu? or UbuntVix?

---

### Post by kpkeerthi on 2007-12-14
> it fairly cranks on my 700Mhz laptop with 192 megs of RAM.
:) Your conky at the background reports you have 504MB of RAM :)

---

### Post by henrypootel on 2007-12-14
ah yes, thats because i took the screenshot on the 'experimentation' VM on my desktop machine.

---

