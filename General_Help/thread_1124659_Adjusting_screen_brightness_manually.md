---
title: "Adjusting screen brightness manually"
date: 2009-04-13
forum: General Help
---

### Post by ffahog on 2009-04-13
I have a laptop that I only use on nice days, when I can sit on our back porch and do some work outside. However, in the afternoons there is a lot of sunlight, and it becomes very difficult to see the screen. Unfortunately, this laptop has a function key but no commands that allow me to adjust screen brightness (it seems that most laptops do Fn-1 and Fn-2 or Fn-f5 and Fn-f6, etc., to adjust brightness).

Is there any way that I can manually adjust the brightness on my computer, either by editing a file or through the terminal?

There is a 'brightness' file in /proc/acpi/video/VGA/LCD, but any edits I make in mousepad don't stick.

Any help?

---

### Post by Yvan300 on 2009-04-13
Well i'm not sure if this applies to xubuntu, but there is supposed to be a brightness controller application that you can add to your panel. You can use this to adjust your brightness.

---

### Post by ffahog on 2009-04-13
> **Yvan300 said:**
> Well i'm not sure if this applies to xubuntu, but there is supposed to be a brightness controller application that you can add to your panel. You can use this to adjust your brightness.


There is such an application, but unfortunately it is for Ubuntu/Gnome and is not present in Xubuntu/xfce

---

### Post by ffahog on 2009-04-13
> **ffahog said:**
> I have a laptop that I only use on nice days, when I can sit on our back porch and do some work outside. However, in the afternoons there is a lot of sunlight, and it becomes very difficult to see the screen. Unfortunately, this laptop has a function key but no commands that allow me to adjust screen brightness (it seems that most laptops do Fn-1 and Fn-2 or Fn-f5 and Fn-f6, etc., to adjust brightness).

Is there any way that I can manually adjust the brightness on my computer, either by editing a file or through the terminal?

There is a 'brightness' file in /proc/acpi/video/VGA/LCD, but any edits I make in mousepad don't stick.

Any help?


Terminal commands? 

I have read before that there is a terminal command that goes something along the lines of "echo -n 100 > LOCATION"?

---

### Post by Yvan300 on 2009-04-13
Hey type this :

sudo echo 4 > /proc/acpi/video/GFX0/LCD/brightness

The brightness range is from 1-8 so 4 is medium :)

---

### Post by ffahog on 2009-04-14
> **Yvan300 said:**
> Hey type this :

sudo echo 4 > /proc/acpi/video/GFX0/LCD/brightness

The brightness range is from 1-8 so 4 is medium :)

Thanks. I tried this; however it is giving me a 'PERMISSION DENIED' message. (Even with using the 'su' command.)

Any way around this?

---

### Post by ffahog on 2009-04-14
> **Yvan300 said:**
> Hey type this :

sudo echo 4 > /proc/acpi/video/GFX0/LCD/brightness

The brightness range is from 1-8 so 4 is medium :)

For example, here is what is says:

```
daniel@xubuntu:~$ sudo echo 4 > /proc/acpi/video/VGA/LCD/brightness
bash: /proc/acpi/video/VGA/LCD/brightness: Permission denied

```

---

### Post by ffahog on 2009-04-14
Anyone? A permissions issue seems like a relatively easy fix. Perhaps I should have put this in the Absolute Beginners forum. :)

---

### Post by Yvan300 on 2009-04-14
Why don't you join irc, you would get this fixed easily, you can use xchat, pidgin etc and just join the channel #ubuntu-beginners, we'll be waiting :)

---

