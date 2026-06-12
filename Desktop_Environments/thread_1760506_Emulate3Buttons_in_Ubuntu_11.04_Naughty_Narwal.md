---
title: "Emulate3Buttons in Ubuntu 11.04 Naughty Narwal"
date: 2011-05-17
forum: Desktop Environments
---

### Post by lpe on 2011-05-17
Hi,

I've just upgraded from 10.10 to 11.04 and sorted out the mess that came along, now there's just one thing left and I'm all set.

I have always used Emulate3Buttons and had it working on 10.10 earlier as well but now I can't seem to get it going.

I've edited my xorg.conf like this:

```

Section "InputDevice"
  # generated from default
  Identifier "Mouse0"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/input/mouse0"
  Option "Emulate3Buttons" "yes"
  Option "ZAxisMapping" "4 5"
EndSection

```

Nothing happens if I write "yes" or "no" (or true/false).
I've searched for similar conf in HAL as well but to no avail, anyone got a clue?

Best Regards

---

### Post by lpe on 2011-05-17
Apparently, I can't paste using the scrollwheel either, so I suspect there's something else wrong then just the xorg.conf

---

### Post by wildmanne39 on 2011-05-17
> **lpe said:**
> Apparently, I can't paste using the scrollwheel either, so I suspect there's something else wrong then just the xorg.conf

Hi, a lot of people including myself had had problems upgrading to natty, so I did a fresh install and it fixed my problems.

---

### Post by Copper Bezel on 2011-05-17
Have you tried setting these two properties through gpointing-device-settings ?

---

### Post by lpe on 2011-05-17
> **Copper Bezel said:**
> Have you tried setting these two properties through gpointing-device-settings ?

Worked instantly, many many thanks!

---

### Post by Copper Bezel on 2011-05-17
Excellent. = ) Just mark the thread as solved, if you would, in Thread Tools at the upper right. = )

---

