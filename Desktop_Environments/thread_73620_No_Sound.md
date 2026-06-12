---
title: "No Sound?"
date: 2005-10-09
forum: Desktop Environments
---

### Post by xMikey on 2005-10-09
I'm a complete n00b to Linux, and I just installed Ubuntu about a week ago!  How come there is no sound?  Do I need to do something to activate the sound or something?  Please help! lol

---

### Post by karuptdata on 2005-10-09
It could be that its not configured yet or improperly could you post more information like type of soundcard please??

---

### Post by xMikey on 2005-10-15
I haven't configured it yet!

When I go to Applications > Sound & Video > Volume Control

i get a popup that says "No Volume Control Elements and/or Devices Found."

Do I need to install a sound driver or something?

I get this when I open an mp3- "Couldn't open audio!

Please Check That:
Your Soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard"

I have no idea on how to configure the soundcard

---

### Post by xMikey on 2005-10-22
Heres my soundcard info stuff-

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 22)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
0000:00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device 4310
0000:00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
0000:00:0b.2 Input device controller: Rockwell International: Unknown device 4312
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
```

Found that out by typing "lspci" in the gnome terminal thing

---

### Post by Ranime on 2005-10-22
[QUOTE=xMikey]Heres my soundcard info stuff-

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 22)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
0000:00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
[b]0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device 4310
0000:00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
0000:00:0b.2 Input device controller: Rockwell International: Unknown device 4312[/b]
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
```

Found that out by typing "lspci" in the gnome terminal thing[/QUOTE]

It seems like your "simpel communications controller" (modem) is hogging your bus.

The "Unknown device 4310" is probebly a sound-out of some kind or a duplex (flex) sounddevice of your modem.
The "Unknown device 4312" is probebly the sound-in or mic of your modem.

Conclusion from this list:
- If you have onboard sound, is is disabled or defective.
- If you have a pci / usb soundcard, it is either devective or their might be something else wrong...

What kind of soundcard do you think you have?

---

### Post by cricketr on 2005-10-22
[QUOTE=xMikey]I'm a complete n00b to Linux, and I just installed Ubuntu about a week ago!  How come there is no sound?  Do I need to do something to activate the sound or something?  Please help! lol[/QUOTE]
Hey xMikey: Go to the wiki and go to user documentation.  Bring up the Unofficial Ubuntu Guide. It has tips to reconfigure your sound in Gnome. It works on my box now. Hope this helps.

Criketr

---

### Post by xMikey on 2005-10-28
[QUOTE=Ranime]It seems like your "simpel communications controller" (modem) is hogging your bus.

The "Unknown device 4310" is probebly a sound-out of some kind or a duplex (flex) sounddevice of your modem.
The "Unknown device 4312" is probebly the sound-in or mic of your modem.

Conclusion from this list:
- If you have onboard sound, is is disabled or defective.
- If you have a pci / usb soundcard, it is either devective or their might be something else wrong...

What kind of soundcard do you think you have?[/QUOTE]
I have no clue..! :mad: :( 
is there a way to find out without physically looking?  like a command in the terminal or something?

---

### Post by CompleteNewb on 2005-11-13
hey i have ran into the same problem buddy, if you have a hp, which im assuming you do, then you most likely have a rockwell chameleon combo card, which means itis a combo modem and sound card, the only way to know what kind of card you have is to go to the hp website and find out your hardware specifics. hope this helps, if it is what i think it is though, you will probably have a hard time getting a module for it. im in the same situation

---

### Post by beerorkid on 2005-11-15
from user ampersand: Right click somewhere in the xmms main window, and go to properties, change the output to something else (usually ALSA) and try again.

from here: [http://www.ubuntuforums.org/showthread.php?t=86588&highlight=correct+output+plugin+selected](http://www.ubuntuforums.org/showthread.php?t=86588&highlight=correct+output+plugin+selected)

---

