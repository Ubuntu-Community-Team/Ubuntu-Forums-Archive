---
title: "Hi, My first post and already a Q..."
date: 2005-12-19
forum: General Help
---

### Post by IT_Geek on 2005-12-19
Hi All,

I have Ubuntu installed on my old computer and i am now looking into changing it into my new computer... can i just move the hard drive???

It is installed on my slave drive i was running 2 drives... 
Primary Windows,
slave Ubuntu...
so grub was loaded on my windows drive...


When i put the ubuntu drive in a newly built pc, i get nothing... the pc switches on but i dont get any screen... in fact the screen just stays blank... and the power saving goes on thus the screen switches itself off...

Any help would be awesome as am sure its something solvable but i have no clue...

Geek

ps: i would prefer not to have to fromat this drive as it has some of my settings for Ubuntu....

---

### Post by manicka on 2005-12-19
You could try changing the switches on the drive to make it the master and then configuring grub using this method.

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by kairu0 on 2005-12-19
In your new PC, the Ubuntu drive is the master or the slave?

In either case, you will have to install Grub to the MBR of the master drive to get it working.

---

### Post by IT_Geek on 2005-12-19
[QUOTE=kairu0]In your new PC, the Ubuntu drive is the master or the slave?

In either case, you will have to install Grub to the MBR of the master drive to get it working.[/QUOTE]

My Ubuntu drive will be the Master but it doesnt even boot up, the screen stays blank so there is no way i can even boot from CD???

Anyone know how to install computers at home??? could help me on this...?

---

### Post by manicka on 2005-12-19
Sounds to me like you have hardware issues with the way your drives are setup. You need to set the boot order of your drives in the BIOS so that it looks for the cd before a hard drive.

 Once these are sorted you should be able to boot into a breezy cd, then fix the mbr.

---

