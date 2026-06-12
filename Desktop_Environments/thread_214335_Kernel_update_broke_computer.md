---
title: "Kernel update broke computer"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Trelo on 2006-07-12
I just installed today's updates and my ubuntu installation broke.  Is not that I'm really pissed off but I wonder how can an official update brake my installation just like that.  I get some kernel panic error at boot so I guess I will have to do a clean install isnt it?

---

### Post by Appolusionist on 2006-07-12
> **Trelo said:**
> I just installed today's updates and my ubuntu installation broke.  Is not that I'm really pissed off but I wonder how can an official update brake my installation just like that.  I get some kernel panic error at boot so I guess I will have to do a clean install isnt it?

You can probably avoid a clean install. Shortly after you turn your computer on you should have a message like "loading grub press esc to exit" or something like that. You have to catch it quick because it is counting down. Press ESC and you should have a list of previous kernels. Choose the one prior to your latest and it will try to load using that kernel instead.

---

### Post by Trelo on 2006-07-12
Thanks a lot that worked for me! :D

How do I make it default to boot with the old kernel though?  And what happens with the new one?

Thanks again :)

---

### Post by Appolusionist on 2006-07-12
> **Trelo said:**
> Thanks a lot that worked for me! :D

How do I make it default to boot with the old kernel though?  And what happens with the new one?

Thanks again :)

The new one is still installed, but you can bypass by changing your grub default. You can follow the link below for the how-to on that. Of course you can always try with the new kernel uninstall,reinstall, and do some research to see what happened. :) 

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by philippe_carlo on 2006-07-12
You probably have nvidia or ati proprietary drivers installed, right. If that is the case, then you have to remove/install them again. The reason for this is that they need to be compiled against the new kernel (from the update). If you do this after booting with the new kernel in text mode, you should be able to use the new kernel without problems.

---

### Post by philippe_carlo on 2006-07-12
PS: there are similar threads below. Look for them.

---

### Post by Trelo on 2006-07-12
Cheers guys much appreciated :)

---

### Post by Trelo on 2006-07-12
Btw any directions on how to safely remove Ati drivers?

---

