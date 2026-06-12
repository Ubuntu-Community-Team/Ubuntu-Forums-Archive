---
title: "Several doubts about Ubuntu 5.04"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Peter Alien on 2005-05-10
Hello,

can someone take me some doubts:

Can i access WinXP Pro FAT32 partitions with Ubuntu 5.04 ?

I wanted to install a new pack of cursors in Ubuntu and i read that i have to install them in /.icons , but this directory doesnt appear to me. What the . before the name of the directory means ? It's a hidden directory ?

What is the difference between the Terminal ans the Konsole ?

can someone tell me if Knemo exists for Ubuntu 5.04 ?


Many many thanks guys  :smile:

---

### Post by Xian on 2005-05-10
1. Yes, you can access FAT partitions.

2. The /.icons folder is hidden, you are correct. To access it open the file browser (nautilus) and select 'View' from the main menu then choose 'Show Hidden Files'. You can then see the folder in your /home directory.

3. The terminal is a generic name for konsole type applications. Konsole is just a particular type of terminal.

4. Knemo 0.3.1 is in Ubuntu 5.04.

---

### Post by petehall on 2005-05-10
[QUOTE=Peter Alien]Hello,

can someone take me some doubts:

Can i access WinXP Pro FAT32 partitions with Ubuntu 5.04 ?[/QUOTE]

Yes. You can read from and write to FAT32, and you can read from NTFS.

[QUOTE=Peter Alien]I wanted to install a new pack of cursors in Ubuntu and i read that i have to install them in /.icons , but this directory doesnt appear to me. What the . before the name of the directory means ? It's a hidden directory ?[/QUOTE]

Yes, it will be hidden. If you type the .icons bit into your Nautilus Location field, it will navigate to that directory. If it doesn't, you need to create the directory too.

[QUOTE=Peter Alien]What is the difference between the Terminal ans the Konsole ?[/QUOTE]

I haven't used KDE for a while, but it sounds like they are fundamentally both the same thing.

---

### Post by az on 2005-05-10
"Can i access WinXP Pro FAT32 partitions with Ubuntu 5.04 ?"

Yes.  You must create a mount point and then mount the partition yourself, since the installer does not do that for you.


"I wanted to install a new pack of cursors in Ubuntu and i read that i have to install them in /.icons , but this directory doesnt appear to me. What the . before the name of the directory means ? It's a hidden directory ?"

Yes, . means it is hidden.  That folder should be created in your home directory.



"What is the difference between the Terminal ans the Konsole ?"

Konsole in a terminal.  So is Gnome-terminal, xterm, Eterm, ...  There are manyto chose from.


"can someone tell me if Knemo exists for Ubuntu 5.04 ?"

Look in

packages.ubuntu.com

---

### Post by railz68 on 2005-05-10
also ".hidden" directory(s) are created (if not already there), for custom settings, saves,..... for Applications, games....

They are hidden so users don't accidently delete them. But you can access the easily when you need to, as others have told you.

Once a application or game is launched for the 1st time, most will create a hidden directory for itself. Anything customized, or saved, will be saved in these hidden directorys.

---

### Post by Peter Alien on 2005-05-10
You&#341;e all Great

Many many thanks for your posts

Im still a n00b in Linux  :???: 

 :)

---

### Post by Stormy Eyes on 2005-05-10
[QUOTE=Peter Alien]Im still a n00b in Linux  :???: [/QUOTE]

Don't worry about it. Keep asking questions, keep hacking, and keep learning. You won't be a newbie for long.

---

