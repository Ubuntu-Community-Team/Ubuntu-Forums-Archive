---
title: "Xorg hangs during ddc check."
date: 2006-06-04
forum: Desktop Environments
---

### Post by bb002 on 2006-06-04
I have a really old box that I put back into use (300Mhz amd k6-2 w/ 128MB RAM) with an equally old monitor (maybe even older, not really sure. monitor supports 5bnc and vga cables). Anyways, 50% of the time when I boot the machine instead of xorg showing up i will have a black screen and a locked up keyboard.

The only thing I can do is ssh into the box from another computer. "top" says Xorg is using 99.8% of the cpu with "top" and "sshd" using the last .2%. if i do a quick "cat /var/log/Xorg.0.log" the last three lines are: 
```

(II) S3VIRGE(0): VESA VBE DDC supported
(II) S3VIRGE(0): VESA VBE DDC Level none
(II) S3VIRGE(0): VESA VBE DDC transfer in appr. 0 sec.

```

Since this box/monitor combo did the exact same thing with windows i learned a little work around. By unpluging the power from the monitor everything will start working again and i can plug the monitor in again. After unpluging the monitor these lines show up in the log:
```

(II) S3VIRGE(0): VESA VBE DDC read successfully
(--) S3VIRGE(0): No DDC signal

```
if the computer boots fine without me having to unplug, the xorg log will only have one ddc line:
```

(II) S3VIRGE(0): VESA VBE DDC unsupported

```

In windows I couldn't disable ddc making it a pain on every boot, while i don't know how in linux. I've looked around for awhile and have found references that you can do it but no actual how to. My guess is on an option i add to the video card section of xorg.conf. 

Hopefully someone knows what to do?

---

