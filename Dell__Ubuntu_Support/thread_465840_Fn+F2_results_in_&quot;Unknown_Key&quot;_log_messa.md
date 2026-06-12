---
title: "Fn+F2 results in &quot;Unknown Key&quot; log message"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by lostunicorn on 2007-06-06
Hi,

I have a Dell Inspiron 9400 laptop with the next-gen intel wireless card (4965AGN).
There are no Linux drivers for that wireless card yet, but it is supported by ndiswrapper.

I have installed ndiswrapper and could install the 64-bit Windows driver for the card without problems.
However, after loading ndiswrapper (through modprobe), the wlan0 interface does not appear (not in iwconfig and not in ifconfig (-a) ).
ndiswrapper reports that the device has been found though:

```
sudo ndiswrapper -l
netw6v64 : driver installed
         device (8086:4229) present
```

I suspect the wireless card is simply turned off at the moment...
However, when I try to turn on the card with the Fn+F2 key combo, nothing happens.
I only get an entry in /var/log/messages:

```
Jun  6 10:54:15 LoneWolf kernel: [  188.795826] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Jun  6 10:54:15 LoneWolf kernel: [  188.795835] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.

```

It's strange that this keycode is not recognized, because the audio-related Fn combo's worked right from the start.

It is my understanding that any key combination is actually linked to a command? If anyone could provide the command, that would already be a big help... I could then manually enable/disable the device (linking the keycode to the command is then my next problem)

Greets,

Unicorn

---

### Post by angryfirelord on 2007-06-20
DId you remember to load the module? Find out what steps you're missing: [http://ubuntuforums.org/showthread.php?t=471794]("http://ubuntuforums.org/showthread.php?t=471794")

I'm not sure about the key combination, but all that error message is saying is it doesn't understand Fn+F2.

---

### Post by kgr132 on 2007-06-21
Have you tried going into the BIOS settings at boot time and making sure the wireless card is enabled and the radio is on from there? Just a thought.
-K-

---

### Post by Tethtibis on 2007-06-27
I've had this same problem, you have to load the driver into the NDIS wrapper in root mode. this can be accomplished not by sudo commands,but with pressing cntl+alt+ F1 at login screen, but it's all bash code, so watch out!

---

