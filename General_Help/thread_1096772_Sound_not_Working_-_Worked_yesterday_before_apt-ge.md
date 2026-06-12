---
title: "Sound not Working - Worked yesterday before apt-get dist-upgrade"
date: 2009-03-15
forum: General Help
---

### Post by Deathray on 2009-03-15
Laptop:HP DV6449US
I installed Ubuntu yesterday and remember that the sound worked. Thas was yesterday, in the meantime I have installed a few programs, apt-get dist-upgrade and upgrade. Don't remember exactly what triggered it but the sound definitely doesn't work now. When I double click on the sound icon I receive a popup which says:No volume controle GStreamer plugins and/or devices found. On HP's website under DV6449us specifications it says:Sound: Altec Lansing
How do I get the sound working again? :)
```

**user@user-laptop:~$** uname -a
Linux user-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
**user@user-laptop:~$** aplay -l
aplay: device_list:215: no soundcards found...
**user@user-laptop:~$** lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
**user@user-laptop:~$** cat /proc/asound/card0/codec\#*
Codec: Conexant CX20549 (Venice)
Address: 0
Vendor Id: 0x14f15045
Subsystem Id: 0x103c30b7
Revision Id: 0x100100
Modem Function Group: 0x2
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x27 0x27]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x27 0x27]
  Pincap 0x0000113c: IN OUT HP Detect
    Vref caps: HIZ 80
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=37, enabled=1
  Power: setting=D0, actual=D0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0xab 0xab]
  Pincap 0x0000113c: IN OUT HP Detect
    Vref caps: HIZ 80
  Pin Default 0x40a190f0: [N/A] Mic at Ext N/A
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x19* 0x17
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x22451130: [Jack] SPDIF Out at Sep Front
    Conn = Optical, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001124: IN Detect
    Vref caps: HIZ 80
  Pin Default 0x02a79120: [Jack] Mic at Ext Front
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x06]
Node 0x17 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x14, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-In vals:  [0x10 0x10] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 5
     0x19 0x14 0x12 0x11 0x15
Node 0x18 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x40]: 48000
    bits [0x6]: 16 20
    formats [0x5]: PCM AC3
Node 0x19 [Audio Output] wcaps 0xc11: Stereo R/L
  Converter: stream=0, channel=0
  PCM:
    rates [0x540]: 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x1a [Audio Input] wcaps 0x100d0b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x00, nsteps=0x17, stepsize=0x05, mute=1
  Amp-In vals:  [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Connection: 5
     0x17 0x14* 0x12 0x11 0x15
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
user@user-laptop:~$ 
 
```

---

### Post by Deathray on 2009-03-15
New news - Logging in as ROOT and doing a startx, the sound WORKS!??
What's happening, have I messed up my installation? I have also noticed when logged in as my normal user that in **Adminitration -> Services** everything is grayed out and I don't have the option to select "Unlock".
What do I do?

---

### Post by Deathray on 2009-03-15
I fixed the problem but I don't know why and how it works.
But the cause of the problem was because I deactivated graphical login manager in Services. Once I turned it back on everything went back to normal. But I have a question, the reason I disabled it was because this laptop will be some sort of a "server" and I dont wan't gnome to start automatically. How would this be done the proper way?

---

