---
title: "Gentoo-like boot up"
date: 2009-12-15
forum: Desktop Environments
---

### Post by Dr. Oddbio on 2009-12-15
I really like the gentoo boot-up, text and all.
I couldn't find a screenshot of what it looked like online so I used the install cd, and took a picture with my phone:
[GentooBoot Pic]("http://img15.imageshack.us/img15/2477/gentooboot.jpg")

I love how there is a little picture of TUX in the top left corner of the screen and the output is more colorful. It would be really cool if I could duplicate that in Ubuntu, or maybe with the Ubuntu logo.

But even if I can't get that picture (as it seems like it would be pretty hard to do) It's in the kernel isn't it?? If it's a part of the kernel then I think I'd stay away from that.

But, even without the little logo in the corner, I would very much like to see a lot of output during boot time instead of the graphics.
I removed splash from the boot line, and I managed to disable GDM so that I login from the shell, and guess how many lines I see on the screen total?  only about 15, including the login line.


Of course this is all not too important, I just think it would be sweet if I could get at least one of those things.

Thanks!

---

### Post by lewisforlife on 2009-12-15
In your boot loader, get rid of the work "splash" in your Kernel options.

---

### Post by Dr. Oddbio on 2009-12-15
> **lewisforlife said:**
> In your boot loader, get rid of the work "splash" in your Kernel options.

Thanks for replying..

But as I stated in my post I've already done that.

---

### Post by lewisforlife on 2009-12-15
Oh sorry, guess I didn't read your whole post.  That's weird that you only see about 15 lines, I see double that at least.

---

### Post by MentalNotes on 2009-12-16
You're right, the kernel has to be recompiled to show a logo. You can increase the resolution on boot to show some more messages. If you're using GRUB 1, add vga=791 to the GRUB command line for a 1024x768 boot screen.
If you're using GRUB 2, change #GRUB_GFXMODE=640x480 to GRUB_GFXMODE=1024x768 in /etc/boot/grub.cfg and run sudo update-grub. As for the coloured messages, I'm guessing Gentoo has it's own boot script which sets that up.

---

### Post by Dr. Oddbio on 2009-12-16
> **MentalNotes said:**
> You're right, the kernel has to be recompiled to show a logo. You can increase the resolution on boot to show some more messages. If you're using GRUB 1, add vga=791 to the GRUB command line for a 1024x768 boot screen.
If you're using GRUB 2, change #GRUB_GFXMODE=640x480 to GRUB_GFXMODE=1024x768 in /etc/boot/grub.cfg and run sudo update-grub. As for the coloured messages, I'm guessing Gentoo has it's own boot script which sets that up.


My resolution is good, and there is tons of room left for more information to be printed...
but ya, for some reason it just prints a handfull (always 15) messages only.

Im using Ubuntu 9.10

ALSO, perhaps a reason is that I've disabled GDM, so there might be a few less messages due to all of that stuff not loading.

---

