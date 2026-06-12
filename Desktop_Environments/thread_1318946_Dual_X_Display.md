---
title: "Dual X Display"
date: 2009-11-08
forum: Desktop Environments
---

### Post by RedSingularity on 2009-11-08
Im not sure if anything can be done about this but i figured i would ask.  

Problem is when i set my monitors to use 2 separate X screens.  Both monitors load but one is unusable.  It stays in a "frozen" like state.  The mouse moves onto it but i cannot click or type anything on that monitor.  Anyone know of any fixes??

---

### Post by AlphaLexman on 2009-11-08
I have two monitors, but only one X session. 'Nvidia X Server Settings' should pick up on that and give you options to what you are looking for.

I would try unplugging the secondary monitor, reboot, login and 'hot-plug' the second monitor. If you have the latest Nvidia drivers that should work.

If not, try:
```
nvidia-xconfig
```

---

### Post by RedSingularity on 2009-11-08
Thats what i did originally but no dice.  I have googled twin x displpays and see that its not that popular.  Maybe i will have to stick with twinview.

---

### Post by SuperSonic4 on 2009-11-08
What's wrong with Twinview? I have it enabled and my two screens are independent of one another - they're not clones or anything and it's not stretched. In essence it's what I wanted from separate displays

---

### Post by RedSingularity on 2009-11-08
Well twinview stretches the monitor across 2 screens for me.  How can i set it up like you did?

---

