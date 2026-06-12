---
title: "No Sound...No Detection"
date: 2005-08-01
forum: Desktop Environments
---

### Post by DJC-ZA on 2005-08-01
Hi There, I am Absolutely new to Linux and the whole DIY with OS so, any help will be appreciated.... I have a AMD Sempron 1.5Ghz, 200Gb SATA Seagate HDD, nVidia GeForce4 256Mb AGP Card, Onboard Sound. Via 6 Channel....

Everything works 100% but my sound doesn't even detect... If anyone outhere can talk baby language to me and assist me in this regard, I will appreciate it very much...

Regards

"NEWBIE"

---

### Post by Shiven on 2005-08-01
depends on the soundcard honestly...

if its a nforce2 soundcard (or motherboard), sis or intel, you'll need to run modprobe snd-intel8x0.

if its a via soundcard, you'll need to run modprobe snd-via2xx i think it is (you might want to search around for that module name...)

if its a creative product (and god please let it be creative ^-^) run modprobe emul (can't remember the end piece, you might want to search for that too...)

to find out what type you have, sudo lsmod -v | grep audio.

if its an nforce2 soundcard, there are some extra things you'll want to do, so if so, drop a line here and i'll paste some things that come in handy...

one last thing- when you have run "modprobe <module-name>" as above, you might want to run '/etc/init.d/hotplug restart' (without the quotes), as that should make it so your sound starts on boot and you never have to do this again ^-^

hope that helps!

---

### Post by heimo on 2005-08-01
Open terminal (Applications->System Tools->Terminal [or something like that]) and type these commands
 ```
lspci
lsmod | grep snd

``` 
and copy-paste the outputs on this forum to give us some more information. Thanks!

---

