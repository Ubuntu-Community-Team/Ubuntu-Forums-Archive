---
title: "GRUB menu doesn't start automaticly although it could be started manually"
date: 2009-04-22
forum: General Help
---

### Post by BigBonsai on 2009-04-22
I got a strange GRUB glitch here. I had to reinstall Windows so I had to reinstall GRUB.

Like recommended several times here I used "sudo grub" to start the GRUB (ver. 0.97) console. Following are the commands I used to reinstall GRUB to the MBR and the output of GRUB: ```
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /grub/stage1
find /grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/grub/stage2 /grub/menu.lst"... succeeded
Done.
```So far so good. On the next reboot GRUB is there. But the "/grub/menu.lst" configuration file is not used. Instead I get the GRUB command line interface. From there I can start the menu with
```
configfile /grub/menu.lst
``` as well as ```
configfile (hd0,5)/grub/menu.lst
``` (just to be sure that the device map the time I set up GRUB was correct)

I am confused. At installation time GRUB tells me that /grub/menu.lst will be used as default configfile. But on boot time I have to start it on my own.
Does anybody have a clue why menu.lst doesn't come up on its own? Thanks in advance.

---

