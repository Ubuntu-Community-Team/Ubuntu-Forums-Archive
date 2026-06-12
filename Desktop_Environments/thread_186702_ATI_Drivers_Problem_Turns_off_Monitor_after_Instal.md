---
title: "ATI Drivers Problem: Turns off Monitor after Install"
date: 2006-06-02
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-02
Hey,

I've tried 6 times now ( each with fresh install's of 6.06 ) and I can NOT get my ATI drivers to install. Here is my PC Spec:

AMD 64 X2 3800
DFI Lanparty UT Ultra-D
ATI X800XT
1GB Corsair PC3200

I'm running the 32bit version of 6.06. Every time I follow the offical guide and the one in this forum my drivers just do not work. 

When I restart my PC after installing the drivers, it gets the login screen and shows a very distorted image of the screen - at that point it then goes black and turns my monitor off ( well, as if no signal is going to it )

Please will someone help me to install my ATI Drivers? Will I have to format and install 6.06 32bit again? ( about the 9th install of it now, in < 24 hours :D  )

Thanks ](*,) ](*,)

---

### Post by zAo on 2006-06-02
Can you reach a TTY with Cntrl + F1 ?
Then edit your /etc/X11/xorg.conf and change the vsync and hsync. Restart.

---

### Post by v8YKxgHe on 2006-06-02
Erm, I don't know what you mean by TTY

But that's the thing - I can't see ANYTHING, even if I tried ctrl+al+F1 or ctrl+F1 - no signal is going to my monitor, I think.

---

### Post by v8YKxgHe on 2006-06-03
Any one?

EDIT: I've reinstalled 6.06 and have it set up how I want now - but with no ATI drivers. Would someone help me to make sure when I install the ATI drivers now, that it does not go wrong?

---

