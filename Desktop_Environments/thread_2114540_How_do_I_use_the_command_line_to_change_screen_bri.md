---
title: "How do I use the command line to change screen brightness?"
date: 2013-02-10
forum: Desktop Environments
---

### Post by Tom6153 on 2013-02-10
simple question
how do i use the command line to change screen brightness? and how do i get it to fix that brightness permanently?
I'm just trying to figure out how to do things without using the gui
thanks

---

### Post by pqwoerituytrueiwoq on 2013-02-10
install [xbacklight]("apt:xbacklight") and/or [backlightx]("http://pastebin.com/HzzHrS2g") 
then run [FONT=Courier New]backlightx --help[/FONT] and/or [FONT=Courier New]xbacklight --help[/FONT] depending on which or both you install

scripts install manually go in [FONT=Courier New]/usr/local/bin[/FONT] you will need to [FONT=Courier New]chmod +x[/FONT] it also

---

### Post by schragge on 2013-02-10
There used to be package *ddccontrol*. Don't know if it's still there in newer Ubuntu releases.

---

### Post by steeldriver on 2013-02-10
On my laptop, I can write a value direct to the acpi brightness file, e.g.

```
$ echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

I don't know the naming convention of the acpi_video0 file - you would need to check if that file exists for you. I can see the max value in /sys/class/backlight/acpi_video0/max_brightness. If that works for you, you could set the desired value in rc.local

---

