---
title: "HOWTO: Restore/fix GRUB menu"
date: 2009-05-23
forum: General Help
---

### Post by c/Kr3t on 2009-05-23
I wrote this walkthrough because i recently just experienced the most frustrating problem yet to date with Ubuntu. But I came out of it with more knowledge, which is totally worth it.

Now, I'll be walking through 2 scenarios, both of which I had to deal with.

Scenario 1
You've installed windows on a separate partition and you think everything is all dandy. You reboot to log into ubuntu, and it boots to windows instead, oh noes! ikr? Here's how to fix it.

  Boot into your liveCD

  Start your terminal and type:
```

sudo grub

find /boot/grub/stage1

```
the number you see, probably (hd0,2) is where the grub loader was before.

  type out...
```

root (hd0,2)

setup (hd0)

quit

exit

```
That SHOULD bring it back up..if not continue reading.

If that did not restore your grub menu then do this instead.
(credit goes to Peter Upfold at [http://fosswire.com/post/2009/5/restoring-overwritten-grub/](http://fosswire.com/post/2009/5/restoring-overwritten-grub/))

  Boot to your liveCD

  Open terminal and type:
```

sudo mkdir /mnt/system

sudo mount /dev/<your ROOT partition> /mnt/system

sudo -i

mount -o bind /dev /mnt/system/dev

chroot /mnt/system

grub-install /dev/sda

```
that should take care of the problem.

Scenario 2
You startup your computer and it loads to the grub menu. You press enter to go into your ubuntu partition but it says Error 17: Cannot mount that partition. You pretty much have a heart attack, but worry not for you are reading this thread.

You do most of what Peter Upfold suggested but you detour in the middle.


  Boot to your liveCD

  Open terminal and type:
```

sudo mkdir /mnt/system

sudo mount /dev/<your ROOT partition> /mnt/system

sudo gedit /mnt/system/boot/grub/menu.lst

```

from here you see the coding of your GRUB menu. scroll down till you see ## ## End Default Options ##

right after that is where it shows the text output on your GRUB menu

in each segment there is an option called root and it show (hd0,<whatever>)

in the terminal type 

```

sudo grub

find /boot/grub/stage1

```

and replace whatever number that is in the root option with the number you get with that command.

save, exit and reboot and it should be all good.

---

