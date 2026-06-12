---
title: "my grub stopped booting!!!"
date: 2009-06-23
forum: General Help
---

### Post by maddie_gielow on 2009-06-23
so after i installed ubuntu and made another user account, i went to windows to do some things. needless to say, ubuntu is still installed, but my computer boots directly to windows xp!

no options or anything at bootup

how can i fix this? i tried auto super grub but it gave me an error and didn't work...

any other easy fixes for this or should i just reinstall?

thankies!:KS

---

### Post by ~sHyLoCk~ on 2009-06-23
> **maddie_gielow said:**
> so after i installed ubuntu and made another user account, i went to windows to do some things. needless to say, ubuntu is still installed, but my computer boots directly to windows xp!

no options or anything at bootup

how can i fix this? i tried auto super grub but it gave me an error and didn't work...

any other easy fixes for this or should i just reinstall?

thankies!:KS

No need to reinstall, I'm sure we can fix this! Does the boot screen menu option [where you choose betwen Xp or ubuntu] shows? I think your tiomeout is set very low and you can't see it! Try booting gain and when it says "Grub loading" press Escape and  see if you get that menu.

---

### Post by maddie_gielow on 2009-06-23
no grub loading message or options to pick ^^
just simply does my normal bios messages, then goes straight to windows

---

### Post by lindsay7 on 2009-06-23
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


Thanks to Presence1960 for the write up

---

### Post by maddie_gielow on 2009-06-23
> **lindsay7 said:**
> Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


Thanks to Presence1960 for the write up

i'll try that out in a second and let you know how it works. thanks!

---

### Post by Wiebelhaus on 2009-06-23
> **maddie_gielow said:**
> so after i installed ubuntu and made another user account, i went to windows to do some things. needless to say, ubuntu is still installed, but my computer boots directly to windows xp!

no options or anything at bootup

how can i fix this? i tried auto super grub but it gave me an error and didn't work...

any other easy fixes for this or should i just reinstall?

thankies!:KS

Press the escape key to initialize the grub menu , once you but into Ubuntu [change you grub display time to like 5 or ten seconds]("http://www.gnu.org/software/grub/manual/grub.html").

---

### Post by maddie_gielow on 2009-06-23
i'm posting this from my old ubuntu setup. (:
it worked out well! i thought something went corrupt after i tried everything i could in auto super grub and it still didn't work XD!

but thanks again! :KS

---

