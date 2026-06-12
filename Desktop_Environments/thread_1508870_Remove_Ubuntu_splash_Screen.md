---
title: "Remove Ubuntu splash Screen"
date: 2010-06-13
forum: Desktop Environments
---

### Post by Ravernomina on 2010-06-13
As the Tops Says how would i go about doing this?? I Do enjoy seeing the text fly by to see whats going on. Plus it makes me feel more nerdy when taking my computer to star bucks :P. So could some one please fill me in? TY!

i Did find a Google searches of this. But _**BUT!!!!!!!**_ They all modify the bootloader.... and well that was for GRUB 1.... so assist :3

---

### Post by quixote on 2010-06-14
Are you using Maverick?  ("Ubuntu Dev Release" it says over on the left there :))  All that nice text flies by when there's any sort of warning generated during the boot process.  I just installed Maverick alpha1 in virtualbox yesterday, and I'm pretty sure I had text flying by too.  (I wasn't paying attention to that.)  I think at this point it's just at such an early stage, text is normal.  

If you want to turn it off in any version using grub2, then change this line in /etc/default/grub: ```
GRUB_CMDLINE_LINUX_DEFAULT="**quiet** splash"
```"quiet" means no text, "splash" means show the default splash screen.  Then run "sudo update-grub" (without quotes).

---

