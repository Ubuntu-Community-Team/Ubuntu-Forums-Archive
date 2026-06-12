---
title: "Wubi 8.10 install stalls on Busybox"
date: 2009-01-11
forum: General Help
---

### Post by endrit10 on 2009-01-11
Hey, I am BRAND NEW to Linux, infact, its the first Time I am using and Liking another OS other than Windows, Ok, so I tried it as a Live CD, its ******* immence, easy to ease etc etc, but the Install WAS HORRIBLE, It comes up with some /DEV/SBA ****, i have  NO idea what the hell that is, and I tried installing Ubuntu normally it WIPED my HDD and could not boot unbutu (it gave me some GRUB error 21)

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

---

### Post by endrit10 on 2009-01-11
Ok, I know this is rude, but its been 5 hours and nothing, are these forums dead?

Seriously, I'm about to ******* throw this computer out the windows, I have NO IDEA what is ******* up, so much for Linux being ready for mainstream use, it doesn't even install.

---

### Post by Yashiro on 2009-01-12
Run a disk check on your Vista install.

- Open a command prompt and type *chkdsk /f*, reply *y* to the prompt.
- Reboot into Windows
- Chkdsk will run
- Once at the desktop reboot into Windows again
- Now reboot into Ubuntu (the wubi install that was added to the windows bootloader)
- Learn to relax, it's only a computer.

---

### Post by 60hbe16es52 on 2009-01-12
is [runescape gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) site safe?

---

### Post by endrit10 on 2009-01-12
Didn't work.
I tried reinstalling in safe mode, didn't work.
ffs its dead here, i give up

---

### Post by abn91c on 2009-01-12
that usually happens when you do a hard reset with Wubi and the drives fail to mount. To fix it restart normally to windows first then reboot back to ubuntu, DONOT power off or use reset button. Just for kicks defrag windows first.

---

### Post by endrit10 on 2009-01-14
Didn't work.

---

### Post by endrit10 on 2009-01-15
Is this the official Wubi forum?
If so, this is ludicorously bad service.
Call me rude, call me arrogant, but it is.

---

### Post by Yashiro on 2009-01-15
Serivce? Hehe. Linux is a free OS, everyone here is user just like yourself.

I'd try the 8.04 release.

---

### Post by endrit10 on 2009-01-16
I didn't mean customer service, I meant, User Service, I tried 8.04, same thing.
I've tried reinstalling Vista, I've tried whipping my HD and installing Ubuntu on its own, and I STILL get this.

---

### Post by Yashiro on 2009-01-16
Re-installing Windows isn't going to help anything, so stop doing it.

So, *running Ubuntu from the LiveCD works?*
*What motherboard do you have?*

---

### Post by endrit10 on 2009-01-16
Yes running from LiveCD works, but the partioner is probably the worst peice of programming (not trying to be difficult, i am seriou :D) i have EVER used.
It does not work.
It simply does not work at all.
If it tries to make a new parition, it says error, if it tries to take the whole disk it whips all my stuff and then when i restart i get busybox, sometimes i get  GRUB Error 21 aswell... if ubuntu is going to move forward, GRUB needs to die.

Grub is the worst loader ever contemplated, the amount of complaints and problems with it are unacceptable and it should be banned from existantce and from memory, i read that there is a alternative loader called LiLO which i would use if i EVER got ubuntu to work...

Its seriously pissing me off.

Here are my specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00717671&lc=en&dlc=en&cc=us&lang=en&product=3214122](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00717671&lc=en&dlc=en&cc=us&lang=en&product=3214122)

---

### Post by thezood on 2009-01-17
[QUOTE=endrit10]
Grub is the worst loader ever contemplated, the amount of complaints and problems with it are unacceptable and it should be banned from existantce and from memory, i read that there is a alternative loader called LiLO which i would use if i EVER got ubuntu to work...
[/quote]

This is a community of volunteers. Waiting a couple of hours is normal. People doesn't work here and noone is getting paid to service you. And the ruder you are, the less people are going to want to help you. 

I've had my share of problems and I've always gotten help and I've had - and solved - the Error 21 issue. Grub works perfectly. What you are experiencing are configuration problems. Error 21 means Grub can't find its configuration file. If you have formatted your hard drive and reinstalled Windows, the configuration file for Grub has been deleted, which is what causes this error. 

You need to calm down and explain exactly what the situation is right now. Have you managed to install Ubuntu now? Are you using Wubi? Do you have a working Windows installation? How many hard drives do you have and how many partitions on each hard drive?

If you ONLY have Windows now and only WANT Windows, you can repair the hard drive with a tool on the Windows CD (google is your friend here).

If you want to run Ubuntu and want to get Grub working, you need to reinstall Grub and tell it where it can find its configuration file. This will happen automatically when Ubuntu gets installed. In some cases, Grub is configured so that it looks for its configuration file on the wrong partition, causing Error 21. So it could be that you have a working Ubuntu that you can't boot right now. This can easily be fixed but it all depends on what you want right now and on what the status of your Ubuntu/Windows/Wubi installations is right now.

Please provide all that info and I'm sure you can fix this.

---

