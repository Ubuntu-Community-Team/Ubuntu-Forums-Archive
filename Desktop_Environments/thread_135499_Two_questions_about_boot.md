---
title: "Two questions about boot"
date: 2006-02-24
forum: Desktop Environments
---

### Post by pixelnate on 2006-02-24
1) Is there any way to reduce the size of the text that scrolls on boot? On SuSE the font is tiny on boot. What can I say, I just think it looks nice.

2) When booting, I get the nice Ubuntu/Kubuntu graphic, but it hangs then goes back to regular verbose mode. Is something broken here? How can I fix it so that the text scrolls under that logo like it is supposed to?

Thx.

---

### Post by Xian on 2006-02-24
[QUOTE=pixelnate]1) Is there any way to reduce the size of the text that scrolls on boot? On SuSE the font is tiny on boot. What can I say, I just think it looks nice.[/quote]

If you want it like SuSE you'll need to install & configure bootsplash. If you want smaller text you can disable usplash and then set the font size on your kernel line via your grub config. Adjusting your monitor hardware settings may also help since usplash seems to stetch the type somewhat.

[QUOTE=pixelnate]2) When booting, I get the nice Ubuntu/Kubuntu graphic, but it hangs then goes back to regular verbose mode. Is something broken here? How can I fix it so that the text scrolls under that logo like it is supposed to?[/quote]

It should only go verbose if:
1. There is a delay in activating a module/service.
2. There is a detected error.

Either of these true??

---

### Post by az on 2006-02-24
Add the vga=771 for 1024x768 console display.  Change the line in grub to:

# kopt=root=/dev/hda1 ro vga=771


and then run sudo update-grub...

---

### Post by kurup on 2006-08-08
Hi..where can I add the vga parameter? Could you clear that one for me? 

I too love the small lines rather than the big bulky text. Also is there any way I can change the font type?

---

