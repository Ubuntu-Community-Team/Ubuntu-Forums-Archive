---
title: "jaunty hangs and restarts"
date: 2009-04-28
forum: General Help
---

### Post by montini on 2009-04-28
I don't understand what's happening, but sadly I must admit that I find ubuntu 9.04 unstable - it suddenly hangs and restarts with no visible reasons! f.e. this time it hung when I was downloading some .pdf while browsing. Here is the messages log at the hang/restart time:

```

Apr 28 18:51:27 insecticide kernel: [  319.446928] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 28 18:52:31 insecticide kernel: [  383.275012] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
Apr 28 18:52:32 insecticide kernel: [  384.285185] Echoaudio Indigo DJ 0000:16:00.0: PCI INT A disabled
Apr 28 18:54:03 insecticide kernel: [  474.968106] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
Apr 28 18:54:03 insecticide kernel: [  474.968579] Echoaudio Indigo DJ 0000:16:00.0: enabling device (0000 -> 0002)
Apr 28 18:54:03 insecticide kernel: [  474.968597] Echoaudio Indigo DJ 0000:16:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 28 18:54:03 insecticide kernel: [  474.968753] Echoaudio Indigo DJ 0000:16:00.0: firmware: requesting ea/indigo_dj_dsp.fw
Apr 28 18:54:03 insecticide kernel: [  474.997070] Echoaudio Indigo DJ 0000:16:00.0: firmware: requesting ea/loader_dsp.fw
Apr 28 18:54:03 insecticide kernel: [  475.019026] Card registered: Indigo DJ rev.0 (DSP56361) at 0x88000000 irq 16
Apr 28 18:54:03 insecticide pulseaudio[4357]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Apr 28 18:58:15 insecticide kernel: [  727.920046] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 28 18:58:30 insecticide kernel: [  742.322257] CE: hpet increasing min_delta_ns to 33750 nsec
Apr 28 18:58:30 insecticide kernel: [  742.325776] CE: hpet increasing min_delta_ns to 50624 nsec
Apr 28 19:03:14 insecticide syslogd 1.5.0#5ubuntu3: restart.

```

I think first lines are not important - as I am already used to pull out/stick back my Echo Indigo DJ PCMCIA card after system resume from suspend (a bug I suppose, anyway - but it was like that in ubuntu 8.10 too). But the lines stating "CE: hpet increasing ...." - what's that? because just after that the system hangs.

it is very sad to stumble upon such behaviour - i mean, hey c'mon....linux never hangs...does it?

---

### Post by happyhamster on 2009-04-30
- Hpet is a hardware timer. You could try disabling it (which will force another clocksource). So, try booting with the parameter:

hpet=disable

- Or (only on 32 bit systems I believe):

clocksource=pit

- Or (64 bits too):

clocksource=tsc

- Safest way of testing that is appending the parameter manually during the boot process. Boot into the Grub menu and select the first line (Ubuntu 9.04, kernel ........) and press e to edit. Select the second line (kernel /boot/vmlinuz.........) and press e again.
You should see the current kernel-parameters used (in my case: ro quiet splash). Just add the parameter you want to test to the end of that line and press enter.
Then press b to continue the boot process.

This procedure is pretty safe, because the parameter will be gone after a reboot. (To make a permanent change you would have to edit /boot/grub/menu.lst)


- Another thing you could look into: does the crash happen with or without the sound card inserted? For example, with sound card connected, take a look at:

cat /proc/interrupts

- to see if the card shares an interrupt with something else. It's possible there's a conflict there.

Anyway, good luck, and keep us informed.

---

### Post by ubuser_7 on 2009-05-05
Check this out: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

I am having similar problems. Curious to know what hardware are using?

---

### Post by montini on 2009-05-13
> **ubuser_7 said:**
> Check this out: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

I am having similar problems. Curious to know what hardware are using?

if you's interested in my config then it's lenovo thinkpad R61: CPU intel Core2 duo T7100 @ 1.80GHz, 2GB RAM, nvidia Quadro NVS 140M, kernel 2.6.28-11-generic, partition "/" - ext4, patition "/home" - ext3.

---

