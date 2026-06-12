---
title: "Make a shared partition for Windows/Linux"
date: 2009-01-03
forum: General Help
---

### Post by miocene on 2009-01-03
I would like to partition one of my disks so I can store files and access them from Windows and Ubuntu.

This is, for example, so I can put my music and video files in it and play them in both OS's.

Is this possible and what's the best way of doing it without screwing up my system.

*btw, vista is installed on a RAID array of 2x160GB and Ubuntu on a separate (internal) 80GB drive*

---

### Post by Shpongle on 2009-01-03
its possible to access the windows files from ubuntu im not sure about getting at files on ubuntu through windows tho, a friend of mine has his laptop setup with both on the same disk and he just accesses his windows directories by typing the path in the terminal, as far as i can remember he just installed from the live cd with vista already on the disk and he was able to access his files,:D

hope this helps

---

### Post by miocene on 2009-01-03
OK, so how do I know what the path to my windows directory is?

---

### Post by Shpongle on 2009-01-03
as far as i know its like  "windowspartitiondisk \ username \Documents\ Music" for example


i cant remember it exactly tho, id have to ask my friend, i don't wanna be tellin you the wrong stuff. .you know but you can definately access windows files from ubuntu:D

---

### Post by miocene on 2009-01-03
OK I did some searching on how to access my windows files and it says I need to mount the windows partition into ubuntu.

I followed the  instructions and installed gparted to identify the windows partition but it just recognises my 2 160GB disks as "unallocated space" when I know they are formatted as ntfs as a RAID array.

As a result it cant mount it.

How do I mount a raid array?

---

### Post by fjgaude on 2009-01-03
You mount an NTFS array using a program called **dmraid**. You install it using:

```
sudo apt-get install dmraid
```

Then you make a mountpoint:

```
sudo mkdir /home/raid
```

or anything you wish the point to be.

Then you issue this command:

```
sudo dmraid -ay
```

You mount using the array name given as something like /dev/mapper_sbcabcdefghij

```
sudo mount -t ntfs /dev/mapper_sbcabcdefghij /home/raid
```

After all that works successfully then you can place a line in your **/etc/fstab** file so all this is automatic on bootup.

You might wish to read the **man** pages for dmraid to see what it does and how.

Let us know how you are doing.

---

### Post by miocene on 2009-01-03
Thanks for the reply.
I installed dmraid and made the directory but having trouble mounting

Here is the output from the dmraid thing

```
harry@harry-desktop:~$ sudo dmraid -ay
RAID set "isw_bgdjcgdacf_ARRAY" already active
RAID set "isw_bgdjcgdacf_ARRAY1" already active
RAID set "isw_bgdjcgdacf_ARRAY2" already active
RAID set "isw_bgdjcgdacf_ARRAY3" already active
```

What do I use for '/dev/mapper_sbcabcdefghij'?

---

### Post by fjgaude on 2009-01-03
Okay, try using /dev/mapper/isw_bgdjcgdacf_ARRAY. If it doesn't work add a 1 to the ARRAY word and see what happens. Then 2... one of the four should mount.

---

### Post by miocene on 2009-01-04
Success! (I think). I have managed to mount it but still cannot access my docs.

I get this when I open my "raid" folder after mounting:
[IMG]http://i19.photobucket.com/albums/b169/miocene/Screenshot.png?t=1231074656[/IMG]

But I can't find my folder under "users".
The only users are "public" and "default"

How do I find my docs?
And thanks for the help so far.:)

---

### Post by miocene on 2009-01-05
Sorry can I bump this - still cant find my files

---

