---
title: "How do I access Windows stuff"
date: 2005-04-09
forum: Desktop Environments
---

### Post by LinuxHawk on 2005-04-09
How do I access Windows stuff while in KUbuntu Live session?

I need to burn some Windows stuff with K3B, and need to access the C: Drive.

With Mepis, SuSE, and Knoppix I can do this, but I cannot seem to find where Ubuntu hides the Windows stuff. It looks as if it can only see Linux. It is NTFS but all I need is to read the stuff I bring to the Windows drive.

How can this be done in UBUNTU?

Thanks in advance...

---

### Post by lao_V on 2005-04-09
Are you using Ubuntu or Kubuntu?

In Ubuntu you should find your NTFS drive under Places -> Filesystem

In Kubuntu this should be under System -> Storage media

---

### Post by humanity_to_others on 2005-04-09
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by LinuxHawk on 2005-04-09
I am trying out KUbuntu (the KDE version)

The storage lists a Floppy Drive and a single Hard drive.
Which is what I have, however when I click on the Hard Drive I get a 
<cannot mount device ; cannot find hda-1>

This is an older Dell and if it is to be used it needs to co-exist with Windows.

Any other suggestions...

Again thanks in advance for your help and input.

---

### Post by digby on 2005-04-09
Ubuntu doesn't mount NTFS partitions by default, but you can do it yourself with only a couple of simple commands in the terminal.  First we have to make a directory where you can mount the drive.
```
$sudo mkdir /c
```
You won't ever have to repeat this step.

Now we actually mount the drive.  To do this, I have to make some simply assumptions about your system, but it should work without your changing anything.  I'm assuming that your windows partition is the first on your drive and that your harddrive is the master on IDE 1.
```
$sudo mount /dev/hda1 /c -t ntfs
```
They way this works is you tell it to mount something (in this case /dev/hda1 -  the first partition on hda) in a certain spot (/c) and that it has a certain filesystem type (-t ntfs).

Hope this helps.  If you have trouble, let me know.

---

### Post by LinuxHawk on 2005-04-09
Thank you

---

### Post by serioussam on 2005-07-29
[QUOTE=digby]Ubuntu doesn't mount NTFS partitions by default, but you can do it yourself with only a couple of simple commands in the terminal.  First we have to make a directory where you can mount the drive.
```
$sudo mkdir /c
```
You won't ever have to repeat this step.

Now we actually mount the drive.  To do this, I have to make some simply assumptions about your system, but it should work without your changing anything.  I'm assuming that your windows partition is the first on your drive and that your harddrive is the master on IDE 1.
```
$sudo mount /dev/hda1 /c -t ntfs
```
They way this works is you tell it to mount something (in this case /dev/hda1 -  the first partition on hda) in a certain spot (/c) and that it has a certain filesystem type (-t ntfs).

Hope this helps.  If you have trouble, let me know.[/QUOTE]
 Hello y it gives permisison denied even though i m logged in as root :(

---

### Post by dasnk on 2006-06-16
thanks digby, Seems a strange decision not to have the NTFS drive mounted by default, After all it was detected and added to the boot manager during installation.

---

