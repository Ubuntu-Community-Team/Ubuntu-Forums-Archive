---
title: "Keyboard not working after apt-get dist-upgrade"
date: 2005-09-24
forum: Desktop Environments
---

### Post by jbwiv on 2005-09-24
Guys,

I've been running Hoary for some time now with no problem.  However, last night I did a dist-upgrade and everything seemed fine.  I then installed NVIDIA drivers...again, everything seemed fine.  Now, however, after a reboot this afternoon, the keyboard is no longer working.

The hardware is fine...when I'm in grub before booting the kernel I can use it just fine.  It's only after booting up, *EVEN* in single user mode, that it stops responding.

I can ssh into the box just fine...everything else seems operational.  

Anyone have any suggestions on what I might investigate?

Thanks!

jbwiv

---

### Post by mlomker on 2005-09-24
Well, there's a common X problem with changing the line in your xorg.conf to say **Driver "kbd"**.  That would not explain single-user, though.

---

### Post by jbwiv on 2005-09-24
[QUOTE=mlomker]Well, there's a common X problem with changing the line in your xorg.conf to say **Driver "kbd"**.  That would not explain single-user, though.[/QUOTE]

Yeah, because it doesn't work in single user I wouldn't think that to be the case.  Here's the snippet from xorg.conf:

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver    "keyboard"
  Option    "CoreKeyboard"
  Option    "XkbRules"  "xorg"
  Option    "XkbModel"  "pc104"
  Option    "XkbLayout" "us"
EndSection

---

### Post by jbwiv on 2005-09-24
What's very odd is that when booting the Ubuntu live cd, it doesn't work either.  Works just fine in BIOS settings or in grub, but as soon as it boots, nothing.  Strange...

---

### Post by mlomker on 2005-09-24
>   Driver    "keyboard"
 

You do need to change that, but that'd be easy to do if you could type.   ;-) 

What kind of keyboard?  Laptop?  I heard from someone the other day whose laptop keyboard wouldn't work but an external did.

---

### Post by jbwiv on 2005-09-24
[QUOTE=mlomker]You do need to change that, but that'd be easy to do if you could type.   ;-) 

What kind of keyboard?  Laptop?  I heard from someone the other day whose laptop keyboard wouldn't work but an external did.[/QUOTE]

I can change it by sshing into the box, but it probably won't help since it doesn't even work with the live cd.  If I boot live-expert of the live cd, as soon as I get to the blue screen to change my language it no longer works.  However, back during grub, etc, it works fine.

It's a desktop system with a Asus motherboard. The keyboard is connected through a KVM and works with all other boxes.

Thanks for your help!
jbwiv

---

### Post by mlomker on 2005-09-24
> The keyboard is connected through a KVM and works with all other boxes.


USB or PS/2?  For whatever reason, USB keyboards are touchy.

Connect to your box and do an **lsmod | grep kbd**.  If it doesn't find anything then you could try **modprobe usbkbd**.

---

### Post by jbwiv on 2005-09-24
[QUOTE=mlomker]USB or PS/2?  For whatever reason, USB keyboards are touchy.

Connect to your box and do an **lsmod | grep kbd**.  If it doesn't find anything then you could try **modprobe usbkbd**.[/QUOTE]

PS/2 unfortunately :)

---

### Post by mlomker on 2005-09-24
[QUOTE=jbwiv]PS/2 unfortunately :)[/QUOTE]

That driver is built into the kernel, so I guess I'm out of ideas.  

**dmesg | grep input**?

---

### Post by jbwiv on 2005-09-24
jb@inovate:~$ dmesg | grep input
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
input: PC Speaker

Thanks!
John

---

### Post by mlomker on 2005-09-24
Should be:

```

input: AT Translated Set 2 keyboard on isa0060/serio0

```

Have you tried an **apt-cache search linux-image**?  Maybe that's just a bad kernel and you can try another one.

---

### Post by jbwiv on 2005-09-26
[QUOTE=mlomker]Should be:

```

input: AT Translated Set 2 keyboard on isa0060/serio0

```

Strangely enough...powered down, removed power plug and keyboard, booted back up, nothing.  Removed the 386 kernel image and installed 686 kernel version.  Rebooted...everything was working as it should be again.

I'm at a loss.  Obviously the 386 vs 686 difference is insignificant...perhaps the upgrade I mentioned earlier screwed my existing kernel somehow?

Ugh.

Thanks for all your help!

John

---

