---
title: "wierd colors and hangs"
date: 2008-11-06
forum: Desktop Environments
---

### Post by Veratyr9 on 2008-11-06
This just started happening recently (well probably within last month, as election time has made time fly for me (campaigning))
I update ubuntu very regularly.  This probably came from a patch within the last month?

I get to the login screen fine.  once on the desktop i have a good 10 seconds before problems start up.  It seems to get worse if i try moving windows around.  Its kinda like back on the original NES when your game cartridge was dirty, you would get blocks of weird colors and it would hang.

The computer always freezes about 15 seconds into being at the desktop.

I'm a very experienced as a windows user, just venturing into the linux world for my job (network administrator).  So far I really like it, but this is driving me nuts, especially since its like relearning the computer all over again, and I don't know the answer right away.

here is a screenshot taken with my phone.

ever seen this?

---

### Post by Veratyr9 on 2008-11-06
probably should haev put in system specs

mobo is an intel 875p chipset
ati 9800xt agp gfx
1gb ddr
forgot what drivers im using, but they came from ATI, and have never had problems before.

---

### Post by Veratyr9 on 2008-11-06
now this is getting weird.  I got sick of dealing with it and didnt have anything important, so i just did a fresh install of Kubuntu 8.10, and its doing the same thing, except its not hanging.... wtf?

The loading screens display just fine though...

---

### Post by Yashiro on 2008-11-06
Try Ubuntu 8.04 (LiveCD). If you still get problems, it's possible your card is on it's way out.

---

### Post by Veratyr9 on 2008-11-06
nope no problems on the livecd

---

### Post by Yashiro on 2008-11-06
Driver issue then, probably. Look around for some video driver fixes for 8.10 or stick with 8.04.

---

### Post by Veratyr9 on 2008-11-06
was happening on 8.04 too

Here is the odd thing on the fresh install of kubuntu 8.10.  it will sit at the login screen just fine, then I goto log in, and right when the first icon comes up in the loading screen, just beofre the second one, it starts glitching up, and more often than not hangs before it even gets to the desktop

is there a way to force it into vesa mode?

---

### Post by Veratyr9 on 2008-11-07
Just got much weirder.  I just remembered a buddy left his PC here, which also has a 9800xt in it.  I swapped the cards, and it has the same problem.  I then hooked the monitor up to the dvi port with an adapter.  Same thing.

I'm really confused because it displays the live cd just fine.

Just did another fresh install, same thing.  though the definition of insanity is continuing to do the same thing expecting a different result

---

### Post by Veratyr9 on 2009-01-28
SOLVED:
to wrap this thread up for anybody looking at it who's having the same problem

I have 2 identical pc's, or nearly identical (all same parts, just different revisions).  i swapped part for part and turns out that it was a failing power supply.

Looking at the voltages, they were a bit too low for comfort.  what was happening was that the video card was being starved for power.  replaced the psu and problem solved

first time ive ever heard of that, but makes sense if you think about it.

---

