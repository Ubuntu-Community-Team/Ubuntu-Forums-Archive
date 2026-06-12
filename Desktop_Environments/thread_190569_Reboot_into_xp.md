---
title: "Reboot into xp"
date: 2006-06-06
forum: Desktop Environments
---

### Post by bohboh on 2006-06-06
I have a dual boot system with ubuntu and xp.

At the mo' i have ubuntu as the default OS to boot into. When i am in ubuntu, and need to reboot into xp, is it possible to restart and for it to boot into xp instead without me having to sit there and wait for the OS menu (grub) to appear after it has restarted.

Basically,  can i say "restart my computer and instead of booting into ubuntu, boot into xp instead".

---

### Post by Ramses de Norre on 2006-06-06
I've heard of no other way as changing the defaults line in /boot/grub/menu.lst.
You could write a script to change that easily though. (be sure to backup the file!)

---

### Post by adwait on 2006-06-06
In the grub folder, @ /boot/grub/menu.lst, make a copy of this file and name it alt.menu.lst. Now open the file and make XP the default OS in it (ask if you aren't sure howto)

Now make a text file containg
```

mv /boot/grub/menu.lst /boot/grub/alt2.menu.lst
mv /boot/grub/alt.menu.lst /boot/grub/menu.lst
mv /boot/grub/alt2.menu.lst /boot/grub/alt.menu.lst
reboot

```

Now use
```
chmod +x <filename>
```

This will make the file executable. Now every time you want to boot to XP, run this file with
```
sudo ./<filename
```

Note: You need to run with sudo. Also, once you run this the efauly OS will be XP, so when you want to boot to Ubuntu. you will need to sit there and select Ubuntu. When you boot to ubuntu you have to chage it back. You can write a script to do this as well, same as the above code just skipping the last line.

---

### Post by irv on 2006-06-06
[QUOTE=bohboh]I have a dual boot system with ubuntu and xp.

At the mo' i have ubuntu as the default OS to boot into. When i am in ubuntu, and need to reboot into xp, is it possible to restart and for it to boot into xp instead without me having to sit there and wait for the OS menu (grub) to appear after it has restarted.

Basically,  can i say "restart my computer and instead of booting into ubuntu, boot into xp instead".[/QUOTE]
When you installed Ubuntu it setup grub for the boot order and other things. You can edit the menu.lst file in /boot/grub, but you have to do it as super user. If you do this, then it will boot into xp first everytime. To get it to boot back into ubuntu you would have to change the default boot again. I don't think this is what you want to do. Be careful when manually editing the menu.lst file or any system file. You could screw-up your system. On rare occations I need to boot into xp, and I just wait it out. I use ubuntu 99% of the time so it is not a big deal for me.

---

### Post by bohboh on 2006-06-06
Thanks everyone.

The idea of making the alt menu files will only work if i want to make xp default. Which will mean that i will have to change it back to make ubuntu the default (as you mentioned).

Ok, no worries. TBH, i am 3 days into ubuntu and need xp to make the transition easier. Have lots of work etc and so need to be able to boot into xp as and when i need to do any work whilst i try and find linux equivalents, and so far, xp's days are numbered! Ubuntu is brilliant!! :p

---

