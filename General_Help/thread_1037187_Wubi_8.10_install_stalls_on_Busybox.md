---
title: "Wubi 8.10 install stalls on Busybox"
date: 2009-01-11
forum: General Help
---

### Post by endrit10 on 2009-01-11
Hey, I am BRAND NEW to Linux, infact, its the first Time I am using and Liking another OS other than Windows, Ok, so I tried it as a Live CD, its ******* immence, easy to ease etc etc, but the Install WAS HORRIBLE, It comes up with some /DEV/SBA ****, i have NO idea what the hell that is, and I tried installing Ubuntu normally it WIPED my HDD and could not boot unbutu (it gave me some GRUB error 21)

So I reinstalled Windows Vista, and decided to give Wubi a go.
Everything worked out fine till it told me to remove my DVD and reboot, so I did.

I saw that Ubuntu was added to the boot manager so i selected it and pressed enter, it then came up with the nice looking ubuntu splash screen and I was thinking "goodbye windows" until i get this annoying ******* error:

BusyBox (some stuff here)
Enter 'help' for a list of commands

(initramfs)

And it just stays like that, I tried rebooting and trying other install methods like Safe-graphic mode and verbose mode but all of them send me to this. 

I tried googling for this problem and it lead me to this forum and I saw someone say :

"Hey Buddy,

There is a simple but great solution...

edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!

Enjoy..."

Well my problem is, there is no file in c:\ubuntu\disks\boot\grub\ its an EMPTY FOLDER, 
i do however have a menu.lst in C:\ubuntu\winboot and another different one in C:\ubuntu\install\boot\grub

i tried reinstalling wubi, and even redownloading an iso and burning, still same problem, I dont know what the hell is going on.

HELP!

P.S I posted this in the Wubi forum, but noone is alive in there, and I really need help urgently.

---

