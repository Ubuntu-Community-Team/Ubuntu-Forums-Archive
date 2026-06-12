---
title: "Unreal Tournament sound problem"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by Moneymail on 2008-05-17
Hello everybody, I'm new here on ubuntu forums.
I'm writing this cause I have a problem with Unreal Tournament (the fist), on ubuntu. I installed it with the loki installer, everything went fine except that I have no sound at all in the game. I don't know what to do considering I'm quite new with Linux world.
Help would be appreciated, thanks.

---

### Post by FrozenFox on 2008-05-17
I'm really not sure if this will help you, but it's worth a shot. If it doesn't help, please run unreal tournament from the terminal/console and give us the output, which will probably tell us what's wrong with the sound.

[http://www.fingel.com/ut/howtos/utonlinux.html](http://www.fingel.com/ut/howtos/utonlinux.html)

When it says install aoss, use synaptic.

---

### Post by Moneymail on 2008-05-18
Thanks for your reply. I followed what is written on this site, except that I don't understand that line:
**Now you need to launch UT using the aoss wrapper. In the command prompt, type ./aoss ut and the game should run. Your sound problems should be solved now.**

What is command prompt? If I type ./aoss ut in a terminal, it tells me the file doesn't exist, though it's in my home.
I don't understand that. Could you help me please? Thanks a lot!

---

### Post by FrozenFox on 2008-05-18
I think that line may be a typo. In any case, my apologies for not being directly able to help you here without the following steps, as I don't have my ut cd with me to tell you exactly where stuff is, and I am not using ubuntu atm.

If you installed aoss as the tutorial said, say via synaptic.. In /usr/bin there is probably an "aoss" binary. You can check this via ls /usr/bin | grep oss in the terminal or go there in nautilus/konqueror or your favorite file browser/manager.

You also need to check where your ut launcher is. Is it in /home/yourname? Or is it in /usr/bin/, like /usr/bin/ut? Im on the assumption that you will find it in /home/yourname or /home/yourname/ut/ut or something. 

For the sake of simplicity, let us assume that aoss is in /usr/bin and ut is in /home/yourname/. The command you should use, then, is

/usr/bin/aoss /home/yourname/ut

Or, since ubuntu automatically assumes you refer to a select several folders for binaries unless otherwise specified,

aoss /home/yourname/ut   will also work.

---

