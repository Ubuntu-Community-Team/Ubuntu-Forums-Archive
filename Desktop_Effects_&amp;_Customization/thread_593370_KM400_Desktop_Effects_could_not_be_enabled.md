---
title: "KM400 Desktop Effects could not be enabled"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by deusxechelon on 2007-10-27
I see there are a lot of threads going around similar to my own but all revolve around ATI GFX. I have a VIA KM400 (On-Board) chipset. I am getting the same error "Desktop effects could not be enabled" and this is disappointing, I was looking forward to the fancy graphics..

Any suggestions would be appreciated.

---

### Post by b0rt on 2007-10-27
I hace the exact same trouble, diferent video card(Nvidia GeForce4 420 Go), this is what the terminal says:
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

### Post by deusxechelon on 2007-10-28
I tried the same cmd you did and got this:

```
deusxechelon@deuslinux:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

Im quite sure this means something, Im new to linux, this is all so confusing. Any time I try to research this particular issue all I get is ATI related and its resolutions dont seem to work for me.

---

### Post by h_kerrigan on 2007-10-28
> deusxechelon@deuslinux:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

I have the same problem.
How can I check which is my graphic card?

---

