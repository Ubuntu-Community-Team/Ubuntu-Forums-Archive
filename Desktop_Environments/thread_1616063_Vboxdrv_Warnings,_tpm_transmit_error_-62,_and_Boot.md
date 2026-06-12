---
title: "Vboxdrv Warnings, tpm_transmit error -62, and Booting to Command Line"
date: 2010-11-07
forum: Desktop Environments
---

### Post by SoulMazer on 2010-11-07
Hi, as you can see, I seem to be getting quite a few errors, all of which began upon upgrading to 64 bit Ubuntu 10.10. To be more exact, these are the errors I usually get when I boot: > tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
tpm_tis 00:0b: tpm_transmit: tpm_send: error -62

vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
vboxdrv: counter framework which can generate NMIs is active. You have to prevent the usage of hardware performance counters by        echo 2 > /proc/sys/kernel/perf_counter_paranoid

I also occasionally receive the following: > udevd-work[329]: open /dev/null failed: no such file or directory

Now, let me explain the problems that I am having. Whenever I boot Ubuntu (kernel 2.6.35-22-generic), I am brought to the tty1 screen, and I see the aforementioned errors. I am then allowed to login via the command-line interface and do what I wish. To start X, I have to manually type "startx," and everything seems to go okay. After about one minute, X starts and I go about my normal business, when my screen proceeds to turn completely black and stay that way for about 10 seconds. Then, everything goes back to normal.

If I sit at the tty1 terminal and *don't* type "startx," X usually starts on its own after a minute or so. Right before it starts itself, I see the following error: > tpm_tis 00:0b: tpm_transmit: tpm_send: error -6

Anyways, my questions are as followed: Do I need to worry about the VirtualBox or /dev/null errors, and are they causing my problem? Second of all, how can I make my Ubuntu boot straight into X again?

Thanks in advance.

EDIT: Running 64 bit Ubuntu 10.10 with a GeForce GTS 250 graphics card.

---

