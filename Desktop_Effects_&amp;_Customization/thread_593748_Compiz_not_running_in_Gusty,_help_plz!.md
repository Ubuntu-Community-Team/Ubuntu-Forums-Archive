---
title: "Compiz not running in Gusty, help plz!"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by b0rt on 2007-10-27
Hey guys, sorry to bother but i have troubles with my compiz con Gusty. I have alredy install the restricted drivers for mi Nvidia Geforce4 420 Go, but when I type compiz on the terminal, it doesnts work
```
bort@Leviathan:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

``` 
Can Anyone Help me? any help will be apreciatted.

---

### Post by FuturePilot on 2007-10-27
You won't be able to use Compiz. They put a restriction for a minimum amount of video RAM (64MB) due to the black window bug. Your card appears to have less than 64MB.
However you can work around this, but it's not recommended as it will likely cause problems such as black windows.
```
SKIP_CHECK=yes compiz
```

---

### Post by b0rt on 2007-10-27
Thx, i haven't tougth about the fact it may had a minimun video Ramm request, any ways i tried the "SKIP_CHECK=yes compiz", and i got this:
```
bort@Leviathan:~$ SKIP_CHECK=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```
And still nothing, is there anything i can do? Thx.

---

### Post by b0rt on 2007-10-27
Im asking this, because i had ir runing on Feisty, with some troubles (window borders disappears), but except for that, it ran fine, it was not slow or anything, that's why im thinking there may be a way to run it under Gusty

---

