---
title: "compile and install plain 2.6.14 kernel"
date: 2005-12-24
forum: General Help
---

### Post by rohrbold on 2005-12-24
Hello together,

recently I tried to code a little bit in one of the kernel's subsystems and now I'd like to see if my changes work as expected. Therefore I need to compile a plain 2.6.14 kernel and install it properly. I don't want to use the Debian/Ubuntu special way as I have to test the patch with other distributions later, too. Unfortunately I get a kernel panic at the moment so that I need some advise :-)
What did I do?
[LIST]
[*]I extracted the kernel archive in [FONT="Courier New"]~/kernel/[/FONT]
[*]I applied the latest subsystem's patch and my own (no errors)
[*]Edited the Makefile for the entry »[FONT="Courier New"]EXTRAVERSION = -mr[/FONT]«
[*]Copied the currently used configuration from [FONT="Courier New"]/boot/config-2.6.12-10-386[/FONT] to [FONT="Courier New"].config[/FONT] and used [FONT="Courier New"]make old_config[/FONT] to adjust it
[*]Let [FONT="Courier New"]make[/FONT] run (no errors)
[*]as root: [FONT="Courier New"]make modules_install[/FONT] 
[*][FONT="Courier New"]cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.14-mr[/FONT]
[*][FONT="Courier New"]cp System.map /boot/System.map-2.6.14-mr[/FONT]
[*]Added an entry in [FONT="Courier New"]/boot/grub/menu.lst[/FONT] (I have another SuSE system on my harddrive and do not use update-grub for that reason)
[/LIST]
Now I already noticed that I don't have an initrd.img anywhere ... Maybe that's the only thing that is missing. Is there anything I should do different? Am I close to where I would like to be?

Martin

---

