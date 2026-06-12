---
title: "hoe to set framebuffer ibm r31"
date: 2006-01-05
forum: General Help
---

### Post by bags on 2006-01-05
hy!
i've some visual problems when i enter the text-mode (CTRL+ALT+F1) with my ibm r31 laptop. i looked for a solution in google and [i found it here]("http://www.xs4all.nl/~matto/tpr31.html"); i should use a framebuffer and set vga=0x305. how can i do it? whicj file should be edited? 

can someone help me please? :D 
thanks, matteo

---

### Post by owencraig on 2006-04-10
[QUOTE=bags]hi should use a framebuffer and set vga=0x305. how can i do it? whicj file should be edited?
[/QUOTE]

The file you need to edit is /etc/boot/menu.lst, you'll need to have sudo access to edit it, you put that option after the root option of the kernel, e.g. mine is:

```
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 i8042.nomux=1 vga=0x305 ro quiet splash
```

if it is from a fresh install you will only have the root=/dev/hda2 (or something similar, it's the path to the installation)

the ```
i8042.nomux=1
``` part is to stop the erratic mouse movement thta I had from teh battery being polled, I hope this answers your questions.

---

