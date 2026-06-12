---
title: "help, i lost my desktop!"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by benner on 2007-03-21
i have been messing around with all of the different instructions i have found here to try to get beryl running on my machine.  i am running edgy 64 bit on an amd 4200+ dual core machine with a video card manufactured by ASUS with an ATI x550 chipset and 256 onboard.  ubuntu called the card 'unknown' and then something about sapphire 370 something or other.  sorry i can't tell you more.  i can't see anything.  after a number of attempts with various scripts and trying to get xgl running, i gave up.  each time, it just fell back into gnome.  the beryl gem appeared on the taskbar. if i tried to go back into beryl-manager and selected the beryl theme, the screen would flicker and then it would go back to gnome and all was well.  i gave up for a while.  then, today, i thought i would give it another shot.  i followed this guy's instructions...

 [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

where people with similar cards had had luck.

i typed 

wget -P ~/ [http://koti.mbnet.fi/waappu/download/ati-aiglx-beryl.sh](http://koti.mbnet.fi/waappu/download/ati-aiglx-beryl.sh) 

then

sudo sh ~/ati-aiglx-beryl.sh 

and as i already had beryl installed, it didn't take long.  i downloaded a few updates that suddenly appeared.  they all had to do with xorg 7.2 and beryl.  then i rebooted the computer and there was no desktop.  just a big, blank, brown screen (that is, ll the taskbars and my icons were missing).

i rebooted a few more times, tried gnome failsafe.  nothing.  i wouldn't know where to begin with a command line login without help from you kind folks, so here i am, once again...

can someone help me out?

p.s. do you think i will have any more luck with beryl or compiz on feisty?  i'm the only linux user that i know in the flesh.  i'd like to show off a bit and see if i can win a few people over...

---

### Post by benner on 2007-03-21
well, i got back to where i started with 

sudo aptitude remove --purge beryl emerald
sudo sh ~/.sysreset.sh

still no beryl though

---

### Post by Waappu on 2007-03-21
Hi

Could you please post your xorg.conf and output of ```
lspci
```

---

