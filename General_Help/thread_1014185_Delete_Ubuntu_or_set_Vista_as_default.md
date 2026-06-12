---
title: "Delete Ubuntu or set Vista as default"
date: 2008-12-17
forum: General Help
---

### Post by bambos22 on 2008-12-17
Hello I am a novice. Please excuse my ignorance

I would wish to either remove UBUNTU from my hard drive or have it as the secondary operating system and have VISTA as default.

I recently intalled Ubuntu on my 500GB hard drive which had VISTA pre installed.

My understanding is that on set up my hard disk was partitioned so that apprix 100GB was devoted to the new operating system leaving 400GB approx to Vista.


On start up Ubunto acts as the default. Is there a way to change this to Vista?

Alternatively how can i remove Ubuntu alltogether?

Harry

---

### Post by Het Irv on 2008-12-17
Setting Vista as default is pretty easy if you know where to look.

```
gksu gedit /boot/grub/menu.lst
```
This code will open up the GRUB menu, I think the first block of code is the section that allows you to change which entry is default.  There are instructions for changing it in that file, but if you need more help don't be afraid to ask.

---

### Post by kanikilu on 2008-12-17
Check out this thread on how to change the default OS in the boot loader. It's as simple as editing one text file.

[http://ubuntuforums.org/showthread.php?t=71915](http://ubuntuforums.org/showthread.php?t=71915)

*EDIT* Too slow ;) Anyways, if you *really* want to remove Ubuntu, check out this page ([http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)) or search some more, but to be honest, it's a bit of work, so, personally I'd give Ubuntu another chance if you can spare the disk space.

---

### Post by TeXtonyx on 2008-12-17
I will assume that you have installed Ubuntu to a separate partition
and are using the grub bootloader menu. If you have Ubuntu by
installing Wubi, then Ubuntu is inside your Windows partition
and you can remove it like any other program. This means you
are using the Vista bootloader now.

Did your computer come with a Vista install cd? Or did it come with
a recovery cd provided by the manufacturer? If you don't have the
Vista install cd, then start the process of getting one here,
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

To fix the problem refer to this website which has pictures first,
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

Then Use the Command Prompt shown in screenshot at this webpage,
(also in the screenshot attached to this post, it's at the bottom)
[http://www.bleepingcomputer.com/tutorials/tutorial147.html](http://www.bleepingcomputer.com/tutorials/tutorial147.html)

Issue the following commands after opening the Command Prompt
C:\bootrec /fixmbr     <enter>
C:\bootrec /fixboot    <enter>
C:\bootrec /rebuildbcd <enter>

This will not delete Ubuntu if it is installed to another partition
(not Wubi inside the Windows partition). But you will not be
able to boot Ubuntu. If you want the choice of booting ubuntu
then download free Easybcd and add ubuntu to the Vista bootloader
menu choices (it will be second) by adding Ubuntu under Linux.

After you make sure you can boot to Vista, and if you want to
get rid of the Ubuntu partition, use the partition editor that
comes with Vista to delete the Ubuntu partition(s) (Swap).

---

### Post by bambos22 on 2008-12-17
> **Het Irv said:**
> Setting Vista as default is pretty easy if you know where to look.

```
gksu gedit /boot/grub/menu.lst
```
This code will open up the GRUB menu, I think the first block of code is the section that allows you to change which entry is default.  There are instructions for changing it in that file, but if you need more help don't be afraid to ask.

Where so i enter this code?

---

### Post by ugm6hr on 2008-12-17
You could consider using EasyBCD / NeoGrub: [http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

---

### Post by bambos22 on 2008-12-17
> **ugm6hr said:**
> You could consider using EasyBCD / NeoGrub: [http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)


I havnt a clue what is going on.

On start up at the BIOS screen it gives me 6 seconds to shoose the operating system. The default is Ubuntu.

How do i make it so that Vista is the defualt?

---

### Post by Robert Bryan on 2008-12-17
The screen where you choose which OS to boot is called the Grub loader. It's just a linux file with OS choices. All you have to do is edit this file and make Vista your first choice. Open a terminal (this is sort of like command line or command prompt in Windows) and follow the instructions from the previous posters. There is a line in the file that reads 'default 0'. I think it's the first line in the file that is not commented out. The zero represents the first OS choice in the file. If you have lets say 4 choices, and you want the third choice in the OS list, just set the default to 2. The OS choices are numbered by the system as 0, 1, 2, 3, 4, etc.... so by editing the file to read 'default 2', you are telling the system to boot the third choice on the list. A previous poster mentioned that there are instructions in the file and there are. Just follow them carefully and you should have no issues. Save the edited file and reboot. If Vista is not the default load, you made a mistake and you need to re-edit the file.

---

### Post by kanikilu on 2008-12-17
> **bambos22 said:**
> Where so i enter this code?
Ok, try following the step-by-step instructions here:

[http://beconfused.com/2008/02/12/how-to-make-windows-vista-boot-first-using-grub-in-ubuntu/](http://beconfused.com/2008/02/12/how-to-make-windows-vista-boot-first-using-grub-in-ubuntu/)

It really can't be presented any clearer than that...

---

### Post by bambos22 on 2008-12-17
> **kanikilu said:**
> Ok, try following the step-by-step instructions here:

[http://beconfused.com/2008/02/12/how-to-make-windows-vista-boot-first-using-grub-in-ubuntu/](http://beconfused.com/2008/02/12/how-to-make-windows-vista-boot-first-using-grub-in-ubuntu/)

It really can't be presented any clearer than that...

Yep very clear

Many thanks

---

### Post by micmak2 on 2011-06-16
right okay so ubuntu is the only installed OS on my system, and i wants it off, i have a vista install disk but it just doesn't work, it says everytime i open the install thingy it says i don't have enough temporary memory... but i have like 200 gb can anyone help this is REALLY annoying me:(:(:(:(:(:(:( thanks in advance

---

### Post by Mark Phelps on 2011-06-16
First of all, you should NOT be resurrecting an old post from 2008.

Second of all, this is NOT a Vista forum (if that is your question).  This is an Ubuntu forum.

Since you're having Vista problems, you would do better posting your concerns to a Vista forum.

---

