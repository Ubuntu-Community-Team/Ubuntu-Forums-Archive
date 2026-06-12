---
title: "Am I able to do this?"
date: 2006-01-19
forum: General Help
---

### Post by shafer5 on 2006-01-19
Okay, I have ubuntu installed on my current HD (40 gig). I was wondering if it were possible to take the HD out of my other computer and put it in the desktop I am using now and install windows xp for those who don't know how to use ubuntu at my house? If so can someone do a step by step for me or point me to a link that will?

thanks

---

### Post by MacV on 2006-01-19
[QUOTE=shafer5]Okay, I have ubuntu installed on my current HD (40 gig). I was wondering if it were possible to take the HD out of my other computer and put it in the desktop I am using now and install windows xp for those who don't know how to use ubuntu at my house? If so can someone do a step by step for me or point me to a link that will?

thanks[/QUOTE]

I;m not sure if that would work or not. Maybe if you made the new hard drive a slave drive and kept the Ubutnu one as master, but if anything, it should be done like as if you were doing a Dual boot system. Good luck!

---

### Post by slux on 2006-01-19
You are and it's even easier than dual booting with a single hard drive. Just plug it in (making it slave as the previous poster suggested will be less work) and install XP on it. After that you'll have to add an entry to your /boot/grub/menu.lst for booting from the second drive and you're done.

I find that it's very hard to switch if you rely on a dual-boot setup though. People usually boot into their normal OS by habit or at the sight of the first problem, no matter how slight. :P

---

### Post by lha on 2006-01-19
This is possible. But please, do not make your additional hd slave and install Windows on it. I'm not sure if it's possible to install Windows to a slave and even if it is, grub will be overwritten making you unable to boot Ubuntu.

Here's the way I'd do it.
1) Plug out your Ubuntu drive. There's no need for it during Windows install. If it's not in your computer, Windows installer can't hose it.

2) Make your new drive primary master and install Windows on it just like it would be the only os on your computer.

3) When your done with Windows, make Windows drive primary slave and Ubuntu drive primary master. Boot Ubuntu.

4) Make a backup of menu.lst and edit it.
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Add following lines to the end of menu.lst:
```
title Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1
```

5) Reboot.

---

### Post by shafer5 on 2006-01-19
do i go about doing this in the terminal?

---

### Post by dvensy on 2006-01-19
i 'm new on unbuntu , i want to install bind on unbuntu ,i don't know how to do that

---

### Post by Sef on 2006-01-19
> do i go about doing this in the terminal?

Do this from the terminal:

> 4) Make a backup of menu.lst and edit it.

Code:

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

The other you will do from gedit (a text editor) that will come up.

dvensy: please start a new post for your problem.  Thank you.

---

### Post by shafer5 on 2006-01-19
When i type

> 4) Make a backup of menu.lst and edit it.

Code:

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

it says command not found

---

### Post by Sef on 2006-01-19
I just checked and they work.  They are three separate commands.  

A) ```
cd /boot/grub
```

This changes you to this submenu.

B) ```
sudo cp menu.lst menu.lst_backup
```

This makes a backup copy of your menu.lst.

C) ```
sudo gedit menu.lst
```

This brings up gedit.

What one do you have problem with?  If you even add an extra space, you could get a command not found error.  Just try again.  It does take some time to learn the command line, but it is worth it.

The other option could be that you did it right, but there is a problem with your system.  But retype the commands and see what happens.

---

### Post by shafer5 on 2006-01-19
ahh..shit..lol  

i was typing sudo cp menu.lst_backup instead of sudo cp menu.lst menu.lst_backup

sweet
thanks for you help, its greatly appreciated as i try to find my way through ubuntu.

---

### Post by shafer5 on 2006-01-19
do i add

code:
> title Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1

after it says ### end debian automagic kernels list?

or just before that? if anyone knows i need to know quickly

---

### Post by lha on 2006-01-19
[QUOTE=shafer5]do i add

code:


after it says ### end debian automagic kernels list?

or just before that? if anyone knows i need to know quickly[/QUOTE]

After that line. If you are interested in what happens if you add it before those lines, see [this thread.]("http://ubuntuforums.org/showthread.php?p=669651")

---

### Post by shafer5 on 2006-01-19
[QUOTE=lha]After that line. If you are interested in what happens if you add it before those lines, see [this thread.]("http://ubuntuforums.org/showthread.php?p=669651")[/QUOTE]

man am i glad i asked before i went ahead and did it. i was going to put it before it said the whole end debian thing..thanks again..you have been a bunch of help

---

### Post by shafer5 on 2006-01-19
sweet..everything works.

so when i start my computer i have to push the esc key to get the list right? and select from that list?

if so then everything is good to go!! this site is so freakin awesome...

---

### Post by lha on 2006-01-19
[QUOTE=shafer5]sweet..everything works.

so when i start my computer i have to push the esc key to get the list right? and select from that list?

if so then everything is good to go!! this site is so freakin awesome...[/QUOTE]

If a menu doesn't appear automatically, you need to press esc. Then select Windows or Ubuntu from list.

---

