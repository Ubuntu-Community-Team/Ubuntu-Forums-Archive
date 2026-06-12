---
title: "irq 16 error"
date: 2005-10-27
forum: Desktop Environments
---

### Post by mcrofutt on 2005-10-27
I'm getting an error about 1rq16. I don't have a clue what it means! All that I do know is that the Live CD NOR the install cd will run until I can get past this issue. Any ideas guys/gals?
 A million thanks in advance!

---

### Post by Alexander Kirillov on 2005-10-28
[QUOTE=mcrofutt]I'm getting an error about 1rq16. I don't have a clue what it means! All that I do know is that the Live CD NOR the install cd will run until I can get past this issue. Any ideas guys/gals?
 A million thanks in advance![/QUOTE]
Is it about Hoary (5.04) or Breezy (5.10)? If Breezy, you probalby should repost it to Breezy forum...

It would also help if you gave more detail: what is exact error message? when do you get it? have you already installed Ubuntu, or it appears during installation? what kind of hardware you have (in particular: any unusual devices /boards in your system)?

---

### Post by mcrofutt on 2005-10-28
Thanks for the reply. This pertains to Hoary 5.04. I haven't received my Breezy discs yet and am on dial-up,,, so I'm trying to reinstall grub after purchasing a new pc. I get the error at the usb probe,, I did lsmod and lspci and got the following.

Module                  Size  Used by
nls_iso8859_1           3968  0
udf                    79492  0
parport_pc             30532  1
lp                      8748  0
parport                20032  2 parport_pc,lp
binfmt_misc             8840  1
ipv6                  231296  13
af_packet              16648  0
pcmcia                 16900  0
yenta_socket           17920  0
pcmcia_core            45632  2 pcmcia,yenta_socket
8250                   18180  0
serial_core            18048  1 8250
snd_emu10k1            83716  1
snd_util_mem            3456  1 snd_emu10k1
snd_intel8x0           27200  1
snd_ac97_codec         66936  2 snd_emu10k1,snd_intel8x0
forcedeth              14592  0
snd_opl3_lib            8832  0
snd_sb16_dsp            9600  0
snd_pcm_oss            46112  0
snd_mixer_oss          15872  1 snd_pcm_oss
snd_pcm                77832  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_sb16
_dsp,snd_pcm_oss
snd_timer              20612  3 snd_emu10k1,snd_opl3_lib,snd_pcm
snd_page_alloc          7428  3 snd_emu10k1,snd_intel8x0,snd_pcm
snd_sb16_csp           18048  0
snd_sb_common          13440  2 snd_sb16_dsp,snd_sb16_csp
snd_hwdep               7200  3 snd_emu10k1,snd_opl3_lib,snd_sb16_csp
snd_mpu401_uart         6016  0
snd_rawmidi            19744  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          6924  3 snd_emu10k1,snd_opl3_lib,snd_rawmidi
snd                    45668  19 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_opl
3_lib,snd_sb16_dsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_sb16_csp,snd_
sb_common,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               7264  1 snd
ndiswrapper           114356  0
thermal                11016  0
processor              19764  1 thermal
fan                     3332  0
button                  5136  0
battery                 8324  0
ac                      3588  0
floppy                 52816  0
tsdev                   5696  0
joydev                  8000  0
evdev                   7168  0
usbhid                 28480  0
uhci_hcd               28944  0
ohci_hcd               19080  0
mark@1[~]$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
0000:00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (re
v b2)
0000:00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
0000:00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
0000:00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller(rev c2)
0000:00:05.0 Multimedia audio controller: nVidia Corporation: Unknown device 01b0 (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
0000:00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
0000:01:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:01:01.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

 I've noticed some people on the forums having invidia problems and I cringed when I read the results of those commands........lol
 I'm SURE that someone can give me a hand here and I'll be forever grateful!
 Thanks again,,,,,,,
 Marcus Crofutt

---

### Post by mcrofutt on 2005-10-28
Below is the readout of the stopping point for loading the Live CD.

 IRQ 16: nobody cared (try booting with the "irqpoll" option.
[<c012e4cb>]__report_bad_irq+0x31/0x77
[<c012e59e>]note_interrupt +0x75/0x9b
[<c012df82>]do_IRQ+0xd3/0x111
[<c0104cc5>]d0_IRQ+0x19/0x24
[<c0103966>]common_interrupt+0x1a/0x20
[<c013cf63>]do_mmap_pgoff+0x3dc/0x5f1
[<c0107ff6>]old_mmap+0xab/0xdb
[<c0102ff7>]syscall_call+0x7/0xb

handlers:
[<ee84f671>](usb_hcd_IRQ+0x0/0x4e[usbcore])
[<ee84f671>](usb_hcd_IRQ+0x0/0x4e[usbcore])
Disabling IRQ #16
                         [success]
                         [success]

I hope this helps us help me,,,,,,,,,hehehe
   Marcus

---

