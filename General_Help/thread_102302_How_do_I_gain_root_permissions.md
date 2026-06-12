---
title: "How do I gain root permissions?"
date: 2005-12-11
forum: General Help
---

### Post by PheonixRising on 2005-12-11
I'd like to store some files from my Linux Partition onto my Win XP one. However, whenever I try to copy a file over, it tells me that I need "root" permissions because thats the owner. HELP!

---

### Post by aysiu on 2005-12-11
Two problems here:

1. Windows XP is probably formatted as NTFS, which means no write permissions from Linux.
The safest way to transfer some of these files is to get an intermediary (external hard drive, MP3 player, floppy disk, whatever) to copy them to, boot up into Windows, and copy them back.

2. You're unable to move the file because you're not root. To temporarily gain root privileges, hit Alt-F2 and type ```
gksudo nautilus
```

---

### Post by codejunkie on 2005-12-11
[quote=PheonixRising]I'd like to store some files from my Linux Partition onto my Win XP one. However, whenever I try to copy a file over, it tells me that I need "root" permissions because thats the owner. HELP![/quote]
you can't, if your windows xp install is using a ntfs partition, because linux can't write to a ntfs file system it can only read it.

---

### Post by DarkOra on 2005-12-11
Your best option is a external file storage system, or if you want to get a online FTP server but for a good one you may have to dish out some cash.

---

### Post by gw90se on 2005-12-11
You mentioned your Windows "partition", so I assume that you are dual-booting. If so, there is a windpws program that you can install that will show your linux partition as a drive under Windows Explorer. I forget the name, but you should be able to Google it. I installed it at work, so I could dual boot ther. It works fine.

---

### Post by mherring on 2005-12-11
I recommend a separate drive for data---formatted FAT32.  Both Linux and Windows will read/write just fine.  From each OS, you can link this disk in wherever you want.

I did not see anyone address the root issue.....I prefer to have a root account, rather that Ubuntu's own unique sudo thing.
In a terminal, I think the command is sudo passwd root, and a new (root) password at the prompt.  You can then simply type "su" whenever you want god-like powers---saves a lot of repeated typing of sudo.
When you want to return to normal:  su <username>

---

### Post by drogoh on 2005-12-11
[QUOTE=mherring]
I did not see anyone address the root issue.....I prefer to have a root account, rather that Ubuntu's own unique sudo thing.
[/QUOTE]

There are 8^532546543254235 threads about su versus sudo discussing the very same thing.  That's why nobody addressed the "issue".  There are benefits and drawbacks of using su versus sudo and vice versa, all addressed within the multitude of threads on the subject(s).

---

### Post by Aiden on 2005-12-11
I was actually wondering how I can login as root with terminal and other things, whenever I try to mount my ntfs drive to /mnt/win (or even create that folder) I get permission denied. I do su username enter password: pass but it still does nothing, I even do su root enter password: pass and it says denied, I have only set one pass and that was for my user, ron, during install, but I cant login to root with anything.

Help?

---

### Post by psusi on 2005-12-11
You should not set a root password, and not use su.  If do use su, you return to your normal user with the exit command, not by nesting another su.  If you don't want to prefix several commands with sudo, then issue sudo -s to get a root shell, do what you need to do, then exit back to normal user.  

[QUOTE=mherring]I recommend a separate drive for data---formatted FAT32.  Both Linux and Windows will read/write just fine.  From each OS, you can link this disk in wherever you want.

I did not see anyone address the root issue.....I prefer to have a root account, rather that Ubuntu's own unique sudo thing.
In a terminal, I think the command is sudo passwd root, and a new (root) password at the prompt.  You can then simply type "su" whenever you want god-like powers---saves a lot of repeated typing of sudo.
When you want to return to normal:  su <username>[/QUOTE]

---

### Post by Aiden on 2005-12-11
But I want to have root always when I login to my machine, I know it breaks alot of its security but the machine will barely be online, and when it is the hub is only giving it port 8080 for the external proxy to browse the web (and thats it).

Any way to just have root enabled when I login with my default user?

---

### Post by RAOF on 2005-12-11
No.  Although, if you set a root password you should be able to login as root.  I think there's a GDM setting somewhere about allowing root to login, but I don't do it, and it's a bad idea.

I don't think there's a way to give your normal user root privs.

---

### Post by aysiu on 2005-12-11
[QUOTE=Aiden]I was actually wondering how I can login as root with terminal and other things, whenever I try to mount my ntfs drive to /mnt/win (or even create that folder) I get permission denied. I do su username enter password: pass but it still does nothing, I even do su root enter password: pass and it says denied, I have only set one pass and that was for my user, ron, during install, but I cant login to root with anything.

Help?[/QUOTE] Follow these instructions to get access to your NTFS drive:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Aiden on 2005-12-12
I got the NTFS part down (have done it plenty in the past, upgraded to 5.10 decided to reinstall).

I have looked around everywhere in Ubuntu and on the web but I cant find how to enable root to logon. It is a bad idea I know but as I said, the system will barely be online and when it will be it will be on a http only proxy and Ill probably be not even using the browser, just filetransfers from my windows machines. I just really want to enable root to be default login or to have my normal user have root abilities.

---

### Post by aysiu on 2005-12-12
You can enable a root login, but things get tricky because Ubuntu's set up to use sudo, so if you're trying to perform an administrative task, it asks you for the sudo password, not the root one. As for how, at the bottom of this link, there's an explanation (I'd encourage you to read the entire page, though): [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Also, what's wrong with just creating a launcher (or even a keyboard shortcut) for the command ```
gksudo nautilus
```?

---

### Post by tsugaguy on 2006-01-07
how do you make a launcher? i am new 2 ubuntu and especially to linux in general. sounds like a windows shortcut...?:confused:

---

### Post by aysiu on 2006-01-07
[QUOTE=tsugaguy]how do you make a launcher? i am new 2 ubuntu and especially to linux in general. sounds like a windows shortcut...?:confused:[/QUOTE] Right-click on the panel and select "Add to Panel." Then select "Custom Application Launcher." For the command, type ```
gksudo nautilus
```. You can put whatever description or icon on it that you like.

---

