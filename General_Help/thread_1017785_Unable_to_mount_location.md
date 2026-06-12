---
title: "Unable to mount location"
date: 2008-12-21
forum: General Help
---

### Post by JoeneU on 2008-12-21
Hi all,

I'm trying to fix windows with Ubuntu. Someone gave me [this](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/) link. I need to copy pci.sys, or make an back-up.

The problem is that I can't open my hard drive. I typed (like in the link I gave) the "code" for a forced connection. But after that, i'll get this message:

> DBus error org.freedesktop.DBus.error.noreply: did not receive a reply. possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply time out expired, or the network connection was broken

How can i fix this? I need to get in my hard drive to copy pci.sys or make an back-up.


Thanks, Joene

---

### Post by blackgr on 2008-12-21
First locate the windows drive in /dev. Lets say its /dev/sdx
Now download a tool called ddrescue. 
```
sudo apt-get install ddrescue
```
and copy with this tool the whole disk to a single file:

```
cd ~
dd_rescue /dev/sdx backup.bin
```

After you do it. Try to mount the backup.bin:

```
sudo mount -t auto backup.bin /mnt -o loop
cd /mnt
```

And try to retrieve your files.

---

### Post by JoeneU on 2008-12-21
> **blackgr said:**
> First locate the windows drive in /dev. Lets say its /dev/sdx
Now download a tool called ddrescue. 
```
sudo apt-get install ddrescue
```

I've got an error, but the problem is that my language is Dutch so i don't think it is usefull to copy/paste it here.

But it's kinda like this:
```
Packagelists getting read... Ready
Tree of requirements is building
The status information is reading... Ready
E: Could not find package ddrescue
```

---

### Post by blackgr on 2008-12-21
> **JoeneU said:**
> I've got an error, but the problem is that my language is Dutch so i don't think it is usefull to copy/paste it here.

But it's kinda like this:
```
Packagelists getting read... Ready
Tree of requirements is building
The status information is reading... Ready
E: Could not find package ddrescue
```

You have to enable universe packets

System>Administration>Software sources

enable both multivese and universe and click close. Then  refresh and try again.

---

### Post by JoeneU on 2008-12-21
> **blackgr said:**
> You have to enable universe packets

System>Administration>Software sources

enable both multivese and universe and click close. Then  refresh and try again.

Still the same error, maybe because i haven't got internet?
I've got now all 5 selected, but i cant refresh.

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could't find package ddrescue

---

### Post by blackgr on 2008-12-21
> **JoeneU said:**
> Still the same error, maybe because i haven't got internet?
I've got now all 5 selected, but i cant refresh.

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could't find package ddrescue

Just get the packet from here
[http://packages.ubuntu.com/search?keywords=ddrescue](http://packages.ubuntu.com/search?keywords=ddrescue)

---

### Post by JoeneU on 2008-12-21
Oke, can I download it here and tranfers it by USB-Stick?

And which one should i download, i see 6:
# dapper
# feisty
# gutsy
# hardy
# intrepid 
# jaunty

And when i click one, i need to choose: 

Architecture....Package Size......Installed Size.....Files 
amd64..............17.2 kB............76 kB.........[list of files]  
i386...................17.1 kB............76 kB.........[list of files]  
powerpc............20.9 kB............84 kB.........[list of files]  


And when i have it on the PC, what for "code" should I enter in the Terminal screen? The same?

---

