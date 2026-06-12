---
title: "Please help me this is driving me insane."
date: 2009-01-15
forum: General Help
---

### Post by Soludus on 2009-01-15
Hi,

Im on the brink of saying **** it and going back to Vista, sometimes like I'd say 60-70% of the time when I try to restart, it stops after the ubuntu loading screen and goes to a black screen. Please help me this is so annoying, I have to reboot twice to just restart.

---

### Post by Soludus on 2009-01-15
It's an HP Dv5t-1000 with a Nvidia GeForce 9600m GT. 32 bit ubuntu but have duo core intel centrino 64 bit processor. 4GB RAM.

---

### Post by Drubie on 2009-01-15
> **Soludus said:**
> Hi,

Im on the brink of saying **** it and going back to Vista

NOOOOOOOO!

to tell you the truth, I'm not a guru, but dont give up so easilly.

If you still like the rest of ubuntu, consider dual-booting (even I can do it)

I bet in about 3 minutes, someone (who knows what they are doing) will help

---

### Post by albinootje on 2009-01-15
> **Soludus said:**
> It's an HP Dv5t-1000 with a Nvidia GeForce 9600m GT. 32 bit ubuntu but have duo core intel centrino 64 bit processor. 4GB RAM.

Can you please post the output of :
```

dmesg
lspci

```

---

### Post by u-slayer on 2009-01-15
Ctrl+Alt+F8 should show you a log of what's happening on boot. If you want to start GDM manually you can do this

```

Ctrl+Alt+F1
Login

sudo killall gdm
sudo gdm

```

---

### Post by todak on 2009-01-15
How long does the display stay at a black screen? Look at your hard drive activity indicator. Sometimes after a restart, newly installed software will be configuring and it will take a few minutes to finish and then you will get a login screen. Or perhaps the drive is being checked for errors.

---

