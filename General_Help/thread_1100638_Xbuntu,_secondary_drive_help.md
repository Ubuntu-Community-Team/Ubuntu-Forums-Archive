---
title: "Xbuntu, secondary drive help??"
date: 2009-03-19
forum: General Help
---

### Post by firebird79 on 2009-03-19
hi, i have installed xubuntu in my computer. Recently my other computer that has XP has gone crazy and it wont boot past the loading screen. Anyways, i've tried to connect the harddrive from my other computer to my xubuntu computer because i want to salvage some of my music. now once i connect the other hardrive it shows up in the BIOS so it is detected, but i cant find it once Xubuntu loads. help???

---

### Post by firebird79 on 2009-03-19
oh by the way, i'm really new at this. :)

---

### Post by ajgreeny on 2009-03-19
Simply open up nautilus and try double clicking on the drive if it is shown in Places in the left hand pane of the window.  If that is no use, with the old drive connected in your machine use the terminal to run the command ```
sudo fdisk -l
``` and either report the output here, or try using one of the commands shown below, depending on the format of the disk (ntfs or fat32).  You will need to change the /dev/sda1 to whatever the output of your first fdisk command was for that drive and will also need to make sure the folder */media/windows* exists with ```
sudo mkdir /media/windows
```Manual mount fat32 windows:-
```
sudo mount /dev/sda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```

Manual mount ntfs windows:-
```
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

---

### Post by firebird79 on 2009-03-19
and this terminal is under, Accesories , am i correct?

---

### Post by ajgreeny on 2009-03-19
It is.  Applications >Accessories >Terminal, then type or copy the commands I gave and enter your password when asked (it will not show on screen) and hit enter.

---

### Post by firebird79 on 2009-03-19
ok, sounds good. unfortunately i am at work right now, but i will try this tonight. if i still cant get it to work i'll post again, but hopefully this works. one more question, i should be able to look into the old HD and copy to my Xubuntu HD some music files correct?


by the way, thanks a lot i really appreciate it. ya have helped me out a lot with my transition to linux. :)

---

### Post by CrusaderAD on 2009-03-19
I'll usually use a flash drive with an operating system on it to boot with. Then I can get my files on other drives. Works eveytime. [http://www.pendrivelinux.com]("http://www.pendrivelinux.com")

---

