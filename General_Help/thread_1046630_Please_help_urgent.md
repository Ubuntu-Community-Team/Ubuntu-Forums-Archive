---
title: "Please help urgent"
date: 2009-01-21
forum: General Help
---

### Post by Super_Samio on 2009-01-21
Ok, so I had dual boot with Vista and Ubuntu, but I never really used Ubuntu, being that I'm an idiot and whatnot, so I read a thread online about uninstalling it, that basically said "Delete the Ubuntu partition, then boot using your vista disk and put blah blah blah command in to get rid of the grub / boot to vista each time"

Fine and dandy I thought, but no, I del'd the partition and then went to boot my vista CD. and all the recovery disk does, that i got with my PC is say 'loading windows files' then it does that, and then basically just blue screens on me....


wat do?

---

### Post by ajgreeny on 2009-01-21
RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
Code:

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

Then you should be able to boot directly into Windows again if all goes well.

---

### Post by Super_Samio on 2009-01-21
I'll what you suggested now, and edit back with the results. thanks.

---

### Post by 2hot6ft2 on 2009-01-21
This is for xp but should be the same for vista.
> **Monotoko said:**
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

---

### Post by donkyhotay on 2009-01-21
Not really relevant at this point but if you aren't familiar with partitioning it's a good idea to install ubuntu with wubi so that it doesn't affect windows at all. Getting rid of it as simple as uninstalling any other program through the control panel.

---

### Post by Super_Samio on 2009-01-21
> **ajgreeny said:**
> RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
Code:

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

Then you should be able to boot directly into Windows again if all goes well.


MY GOD, I LOVE YOU. THANK YOU, SO, SO MUCH. 

Ok... Now thats all sorted, all I have to do now is format my storage drive that ubuntu is on... and then extend my windows parition like I wanted to in the first place...

Does anyone know of a good free program for formatting/extending partitions etc?

---

### Post by oldos2er on 2009-01-21
"Does anyone know of a good free program for formatting/extending partitions etc?"

 gparted. It's on the Ubuntu LiveCD, or from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

