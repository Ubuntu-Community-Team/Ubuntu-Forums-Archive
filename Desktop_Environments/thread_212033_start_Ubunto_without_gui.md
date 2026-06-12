---
title: "start Ubunto without gui"
date: 2006-07-09
forum: Desktop Environments
---

### Post by tonym2 on 2006-07-09
Hi,

Long time windows user, Linux n00b trying to make the switch,

Weird question: is it possible to boot Ubuntu to a pure command line environ emnt but, if I want to, start the Gnome gui environment when I want to?

2nd question: Since I am so used to the Windows way of doing things in the file system, I am having a hard time getting used to NOT seeing drive letters. How do I mount then refer to a 2nd hard drive in my system. (I haven't installed it yet, but plan on attaching an external USB hard drive)

Thanks!

Tony

---

### Post by ShiningHolden on 2006-07-09
Thank you for switching to Linux.
Thank you for not running back to Windows with questions/differences.

It is possible, but why?
You could always just
```

CTRL+ALT+F1

```
To get yourself in a terminal, and switching back into a GUI by
```

CTRL+ALT+F7

```
The GUI would still be there...

I don't know of a way to booting directly into, a non GUI because you cant remove GDM from start up....

To your second question:
Heh. Just tihnk of it like this:
```

C:/ = /
Program Files = /usr/bin
Documents and Settings = /home/USERNAME (Or, for more tehcinal use, $HOME)

```

As for mounting a 2nd hard drive... Upon connection and detection (Which for hard drives is like, pouring gasoline in a fire and it will raise, connect it, it's there)

It will then be there, you can right click, mount... To my knoweldge, it is in
```

Places > Computer

```

You can just double click it, and, there it is.

**TIP:** Make sure it is formated to a Linux file system. It isnt required...

I just remembered... 
```

sudo mkdir /filesystem2 
mount /dev/hd(I cant tell you what your device will be) /filesystem2

```

That makes a directory, named filesystem2, and the device/partiton is mounted into that folder.

---

### Post by FredB on 2006-07-09
hda = first hard drive
hdb = second hard drive

After you have partitions.

A usb drive ? I think that gnome / kde will handle flawlessly.

Program files can also be /usr/local/bin too !

The best thing to do, is to buy a "linux for dummies" book. It will help a lot understanding the un*x way to organize things.

---

### Post by mlind on 2006-07-09
> **tonym2 said:**
> 
Weird question: is it possible to boot Ubuntu to a pure command line environ emnt but, if I want to, start the Gnome gui environment when I want to?



Yes, you'll just remove gdm from startup script so it won't launch.

Be aware of the risks before executing this command. Read **man update-rc.d**.
```

sudo update-rc.d -f gdm remove

```

---

### Post by sooqing on 2006-07-09
i havent try this, but in fedora, changing the runlevel to init 3 should work? ubuntu follows a different runlevel though..

---

### Post by ShiningHolden on 2006-07-09
> **sooqing said:**
> i havent try this, but in fedora, changing the runlevel to init 3 should work? ubuntu follows a different runlevel though..

The default, GUI based run level for Debian, is 2.
3 is a run level that run's without a GUI, but it would be just as easy as
```

CTRL+ALT+F1

```
and having your GUI-Less terminal right there.

---

### Post by tonym2 on 2006-07-09
Thanks, Guys!

I knew about the ctrl + alt + F1 thingy, I'll just use that. : )

Also, thanks for the mini course in the file system. I do have a "dummies" book here called "Linux in Easy Steps" It's older and geared toward Mandrake and kde but I think I cna adapt. :)

Thanks again!

Tony

---

### Post by ingvildr on 2006-07-09
wouldn't booting into recovery mode from grub do what you want, or from the session menu on gdm there should be a terminal session.

---

### Post by Wolki on 2006-07-09
You can just use the services tool (system -> settings -> services -> uncheck "graphical login screen")

Afterwards, "startx" should start your gnome.

As for the hard drives, it's not that difficult. You basically choose which names you want your hard drives to have (usually /media/somename/ or /mnt/somename/). It's like drive letters, only better since they are less likely to get confused (add a hard drive, and suddely everything jumps a letter and stuff like that).

---

