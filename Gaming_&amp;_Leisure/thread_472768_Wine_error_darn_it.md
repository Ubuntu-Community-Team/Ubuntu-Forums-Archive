---
title: "Wine error darn it"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by burt_57 on 2007-06-13
robert@robert-desktop:~$ wine /patchtocrom/install.exe
wine: creating configuration directory '/home/robert/.wine'...
wine: '/home/robert/.wine' created successfully.
wine: cannot find '/patchtocrom/install.exe'

---

### Post by hikaricore on 2007-06-13
Are you literally typing: *"/patchtocrom/install.exe"*

Because I'm going to guess more likely correct than not, that you are and that location does not exist.

I can also only imagine that you've gotten this from some howto, and you think they mean to really type: pathtocdrom.
When you should be finding out/typing the REAL _path_ to your cdrom drive.

---

### Post by Majorix on 2007-06-13
You could go to the cd's mount directory and run
```
sudo wine ./install.exe
```
from there. I think that should work.

---

### Post by hikaricore on 2007-06-13
> **Majorix said:**
> ```
wine install.exe
```

^^ fixed

---

### Post by cogadh on 2007-06-13
> **Majorix said:**
> You could go to the cd's mount directory and run
```
sudo wine ./install.exe
```
from there. I think that should work.
FYI - Never "sudo" a wine command, especially installations. It's also a bad idea to navigate to the CD, then run the command, it can cause problems if you have to eject and swap the CD. A better method would be:
```
wine /media/cdrom/install.exe
```
Type out the full path to the install executable (wherever it may be).

---

### Post by burt_57 on 2007-06-13
> **cogadh said:**
> FYI - Never "sudo" a wine command, especially installations. It's also a bad idea to navigate to the CD, then run the command, it can cause problems if you have to eject and swap the CD. A better method would be:
```
wine /media/cdrom/install.exe
```
Type out the full path to the install executable (wherever it may be).

wine /media/cdrom0/install.exe is what I type because my CD rom is CDrom0;
and the othe one is CDrom1
wine /media/cdrom/install.exe <---------- that does not work for me , why I do not know.

---

### Post by hikaricore on 2007-06-13
...And did this give you any new results?

What exactly are you trying to install?

---

### Post by cogadh on 2007-06-13
I believe you may be taking our sample instructions too literally. Since we don't know what you are installing and don't know exactly how your system is setup, we have to give answers in a somewhat generic form and assume that you know to adjust what we say to match your system and circumstances. When I suggest using "wine /media/cdrom/install.exe" I'm assuming that you will adjust that line to match your needs; i.e. change the path to your correct drive path, change the executable name to the correct name, etc.

That does bring up an interesting question. Is the installation executable actually named "install.exe" or does it have a different name like "setup.exe"?

---

### Post by burt_57 on 2007-06-13
I am trying to setup Max Payne the first version.
The setup with wine goes well.
Wine put it in somewhere like call c:\Program File\Max Payne.
I can see the installation and all file when I type wine file.
Did all what I have read about it ...how to ect...
Apply patch 1.5 , name it I did all .
Anyway thank you all for your advise.
oh do not forget I have been a user of Ubuntu for 5 weeks.
I sooooooooooo green.
Will not give up.
Was a Windows user ;)

---

