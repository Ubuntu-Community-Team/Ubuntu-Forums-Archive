---
title: "Shell/Framebuffer/Bash"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Crooksey on 2006-08-13
Is there any way in which i can change the resolution of the shell, becuase at the moment the text is very large and takes to much space, in some distros i have seen the shell at about 1280x1024, this i think was achived by a line in the grub.conf, but im not sure. 

I have searched the forums and all i find is driver installation threads, so my question is, does anyone know how to make the sheel the 1280x1024 resolution.

---

### Post by kabus on 2006-08-13
You'll have to add the vga parameter to the kernel line in /boot/grub/menu.lst:

```
kernel /boot/vmlinuz26 root=/dev/hda6 ro **vga=xxx**
```

xxx can be one of the following values:

```

#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

```

So for a resolution of 1024x768 @ 256 colours:

```
kernel /boot/vmlinuz26 root=/dev/hda6 ro vga=775
```

---

### Post by Crooksey on 2006-08-13
Thanks, that worked perfectly :)

---

