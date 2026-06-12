---
title: "ubuntu desktop crashing"
date: 2005-09-17
forum: Desktop Environments
---

### Post by duan on 2005-09-17
Hi excuse if this is not the right forum to post...

Ubuntu crashed/halted three times already on me in three weeks, the last two times I t happened while using firefox.

Everthing just dies, leaving only the mouse cursor working but it doesn change when moving over a link and I can't click anything.

ALT+CTRL+Backspace won't kill X.
ALT+CTRL+F-keys wont bring up a virtual terminal.

I know it's not completely dead because if I plug my MMC card reader in, I see the light burning twice, the second time like it normally does when mounting it.

Essentiallly the entire desktop environment is dead (so I posted here...)

Please, how can I discover what causes the problem? I'd be interested to figure out where I can get a log or output to read next time I log in...

Oh, everything is updated, and the only thing I installed NOT FROM the hoary universe repository is the lame mp3 encoder, so there are no funny experimental libraries installed.

Many thanks.
Duan

---

### Post by neighborlee on 2005-09-17
[QUOTE=duan]Hi excuse if this is not the right forum to post...

Ubuntu crashed/halted three times already on me in three weeks, the last two times I t happened while using firefox.

Everthing just dies, leaving only the mouse cursor working but it doesn change when moving over a link and I can't click anything.

ALT+CTRL+Backspace won't kill X.
ALT+CTRL+F-keys wont bring up a virtual terminal.

I know it's not completely dead because if I plug my MMC card reader in, I see the light burning twice, the second time like it normally does when mounting it.

Essentiallly the entire desktop environment is dead (so I posted here...)

Please, how can I discover what causes the problem? I'd be interested to figure out where I can get a log or output to read next time I log in...

Oh, everything is updated, and the only thing I installed NOT FROM the hoary universe repository is the lame mp3 encoder, so there are no funny experimental libraries installed.

Many thanks.
Duan[/QUOTE]


Instability can be caused by many things, but I can share how I ( so far anyway) fixed mine.  I had similar problems as little as a few days ago, and simply fixed it by patching my kernrel with the 'badram' patch, which can be had by googling for 'badram'.

The history of this is simply my crashing led me to ( Windows was very rarely   displaying this behavior but thats another kettle as we know ) reboot and try the 'memtest' option, and sure enough I had badram.

I am not saying this is your fixall, but if indeed it comes back showing that you have bad ram, then this might just fix you up.

If thats at least part of your problem, you of course download the patch and then procede to patch the kernel ( of course you need the source , which you just download from synaptic, ( but make sure to get the 2.6.10 one ) and then just move over the one from /boot to /usr/src/linux-source-2.6.10 renaming it just 'config' as you do so..

Dont make any signifficant changes unlesss you know what you're doing as it can cause a kernel to be unbootable of course.

in /usr/src/linux-source-2.6.10 run: make kpkg kernel-image --initrd

That will add line you need to /boot/grub/menu.lst ( BUT will add a bunch of unnecesssary lines to to too which you can sort out by editing ).

That will also plop down a kernel-image-2.6.10_10.00.Custom_i386.deb , in /usr/src which you can install with:  sudo dpkg -i kernel*.deb

OF COURSE this is all assuming its bad ram causing your grief, but so far given the memtest results I had, and given that so far I'm not seeing any crashing, I feel it was very worth it.

Good luck and I hope this helps.

cheers
nl

---

### Post by duan on 2005-09-17
I'll give this a try, thanks!

I was wondering how long I would go before recompiling a kernel.

The first time it crashed, my boot hanged about 1 minute on the BIOS NVRAM testing, but i enabled the RAM test now and I see it is the very next thing it does after checking the NVRAM. There were one or two other times it did so but it disappeared. Maybe the ram is defective, or the contacts are rusty... the pc is gettin about 4 years old...

OK, lets see about this kernel.. (I've backed up the important data...)

Duan

---

### Post by duan on 2005-09-26
I did the memtest but after 7 hours it came back flawless. only when I selected adress range > BIOS all did I get errors at 4066 and 4097 bytes. I do not know what these are, they don't come up when I check with the BIOS std options. Also checking my two DIMMS one at a time, in any slot I get the exact same results.

Figured it was maybe not the RAM when the memtest program crashed...

Then figured it was maybe the CPU, it was running at 52 degrees. However a friend said that normally on new(cheap) motherboards the voltage regulators and caps go, with similar effects to the PC. Opening the case normally lowers the ambient temparature in the box sufficiently to make a flakey regulator hold on a little longer. I opened the box and with the pc running groped around for hot chips, two parts were hotter than the rest but no other visible issues.

However the pc did die soon. So I opened the power supply fan big time (it is a quiet kit with adjustable fan speed on the power supply and the pc was running, until I got bored a few days later and rebuilt the whole thing in a plastic box and I placed the fans so that a LOT of air gets sucked in from the same side and foreced over the mobo, and out the other end. 

It is running a lot cooler now and has been on for running 3d graphics and everything for 24 hours.

Maybe there is life in the board yet.

thanks for all the help.
Duan

---

