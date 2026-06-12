---
title: "Sound disabled in Ubuntu-11.04"
date: 2011-05-31
forum: Desktop Environments
---

### Post by Kaushik Guha on 2011-05-31
I've installed and updated successfully Ubuntu-11.04(64-bit) onto my system.Everything is working fine,except:-

The sound has become disabled.No sound output from the speakers.All the wires are attached tightly and correctly,with my openSUSE and Mandriva Linux distro on the same machine(at different partitions),the sound seems to be perfectly O.K. and normal.

_The following are from the terminal:_

[B]kgnile11@tabatiti:~$ sudo alsaconf
[sudo] password for kgnile11: 
sudo: alsaconf: command not found
kgnile11@tabatiti:~$ [/B]

All the alsa drivers are successfully loaded.

My system's motherboard is : TA785GE 128M socket AM2+ motherboard from **Biostar**.
Sound system in motherboard is:Realtek ALC662 6-Channel HD Audio

Please help me out.

---

### Post by Copper Bezel on 2011-06-01
Alsaconf doesn't exist in Ubuntu. However, there's [_a bug posted_]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/660293") for your audio card with a workaround.

---

