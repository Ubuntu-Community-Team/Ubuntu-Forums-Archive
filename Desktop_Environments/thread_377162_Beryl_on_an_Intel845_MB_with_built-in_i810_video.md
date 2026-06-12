---
title: "Beryl on an Intel845 MB with built-in i810 video"
date: 2007-03-05
forum: Desktop Environments
---

### Post by sconnell on 2007-03-05
I have an Intel 845 motherboard with a built-in i810 video card. Has anyone had success getting this type of configuration to work?

I suspect the reason why Beryl refuses to change to the Beryl desktop is because of this:
glxinfo | grep direct
direct rendering: No

Also, diagnostics passes for everything but:
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

--------------------------------------------------------------------------

Any ideas before I give up?  I really wanted this to work because I have a friend, who is bragging about how great Vista is, coming to visit on the weekend. I would really like to make this work without having to resort to disabling the on board video and purchasing an ATI card.

Thanks a million!

---

### Post by derekguy on 2007-03-05
I have an Intel 915 chipset motherboard but it also uses the i810 video driver. I am using Edgy and Beryl works fine but it did not when using Dapper, perhaps you could try upgrading and see it that works...

---

### Post by sconnell on 2007-03-05
Thank you for your reply. Perhaps I should have also indicated that I have Ubuntu Edgy distro installed as well.

I think my problem may be related to the direct rendering problem.

I have been careful to do all available (that I know of) updates.

---

### Post by sconnell on 2007-03-07
No tips from anyone? :-) :popcorn:

---

### Post by richrosa on 2007-03-30
bump. same problem.

---

### Post by hikaricore on 2007-03-30
Sorry, I don't have much time today to give a walkthru of what
to check, so probably your best bet is to search the forums for:

> i810 direct rendering

Dozens of people have had similar issues, and most have solved them.

Good luck,

--Aaron

---

### Post by richrosa on 2007-04-03
I've researched this far and wide, and found many false leads. If you have a moment and can give us all a good answer, I promise to write up a HOW-TO based on it.

---

### Post by kikke on 2007-04-22
You must set video-ram's size when configuring dpkg-reconfigure xserver-xorg.
Set this to 32768kB.

---

