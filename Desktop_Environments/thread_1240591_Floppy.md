---
title: "Floppy?"
date: 2009-08-14
forum: Desktop Environments
---

### Post by iwant2 on 2009-08-14
I just installed unbuntu on a Compaq descktop.  How do I get it to read a floppy?

---

### Post by jm2 on 2009-08-14
Put your floppy in the drive.

If you are using the graphic display, At the top Applications, Places, System. Look at Places, if your floppy drive isn't listed, then go under computer, and see if it's there.
If you find it, just click on it, and it should show you what the contents of the floppy is.

If it isn't found above, then Goto Applications, Accessories, Terminal.
At the $  type

mount /dev/fd0 /mnt/floppy
then press the enter key

(What this is saying is computer load the contents of /dev/fd0 (your floppy drive) into /mnt/floppy (area on the linux computer).)

You might need to set the type of the floppy if the above doesn't work. 
See man mount

You can also search the forum for floppy drive.

I hope this will point you in the right direction

---

### Post by iwant2 on 2009-08-15
Typed
mount /dev/fd0 /mnt/floppy

then I pressed the enter key

Got
No such file or directory

Where does one see man mount?:confused:

---

### Post by iwant2 on 2009-08-15
> **jm2 said:**
> Put your floppy in the drive.

If you are using the graphic display, At the top Applications, Places, System. Look at Places, if your floppy drive isn't listed, then go under computer, and see if it's there.
If you find it, just click on it, and it should show you what the contents of the floppy is.

If it isn't found above, then Goto Applications, Accessories, Terminal.
At the $  type

mount /dev/fd0 /mnt/floppy
then press the enter key

(What this is saying is computer load the contents of /dev/fd0 (your floppy drive) into /mnt/floppy (area on the linux computer).)

You might need to set the type of the floppy if the above doesn't work. 
See man mount

You can also search the forum for floppy drive.

I hope this will point you in the right direction

I give up.  What might some types of floppy drives be and is the command something like this:
mount /dev/fd0/mount/floppy/typeshere?

All I really want to do is to run a file from a floppy.  Why is that so difficult?

---

### Post by iwant2 on 2009-08-15
With the amount of time I have spent unsuccessfully on the floppy & internet connection for 
Ubuntu, I would have had a more profitable use my time by simply purchasing Windows XP instead.  

I could actually be using my other computer instead of trying to make it work.](*,)

---

### Post by lisati on 2009-08-15
> **iwant2 said:**
> Typed
"mount /dev/fd0 /mnt/floppy
then press the enter key"

Got
"No such file or directory"

Where does one see man mount?:confused:

Don't type the quotes, and don't type in the "then press the enter key" bit.

Put your floppy in the drive and then type the following in on the command line:
```
mount /dev/fd0 /mnt/floppy
```

---

### Post by iwant2 on 2009-08-15
Typed
mount /dev/fd0 /mnt/floppy

then I pressed the enter key

Got
mount: only root can do that

---

### Post by Marlonsm on 2009-08-15
When you need root, just put a "sudo" in front of the command:
```
sudo mount /dev/fd0 /mnt/floppy
```
it'll ask you the password, so type it and press Enter.

> **iwant2 said:**
> With the amount of time I have spent unsuccessfully on the floppy & internet connection for 
Ubuntu, I would have had a more profitable use my time by simply purchasing Windows XP instead.  

I could actually be using my other computer instead of trying to make it work.](*,)

Sometimes it is easier to do certain things in Windows, and sometimes it's easier in Ubuntu. I've once gone back to Windows for a few weeks, just then I realized how much better it was in Ubuntu for me.
But maybe that's not your case, there is not such a thing like the ultimate OS that is the best for everybody, so some will be better in Windows, some in Ubuntu/Linux, some in OSX...

---

### Post by iwant2 on 2009-08-16
> **Marlonsm said:**
> When you need root, just put a "sudo" in front of the command:
```
sudo mount /dev/fd0 /mnt/floppy
```it'll ask you the password, so type it and press Enter.

Did that.
Got:
mount: mount point /mnt/floppy does not exist

:rolleyes:

---

### Post by iwant2 on 2009-08-16
My floppy will be able to read files in a few days.  I'll also be able to hook up a midi hassle- free.

**[SIZE=3]I just won XP off of ebay![/SIZE]**  :)

---

### Post by cmapesjr on 2009-08-16
Glad you got it sorted out. :)

---

### Post by bwallum on 2009-11-01
> **cmapesjr said:**
> Glad you got it sorted out. :)

Not too sure this thread ended at all well. I've got a similar headache with the floppy drives on three machines, two AMD64 and a i386.

How exactly do you get a floppy drive to work in Karmic please?

---

