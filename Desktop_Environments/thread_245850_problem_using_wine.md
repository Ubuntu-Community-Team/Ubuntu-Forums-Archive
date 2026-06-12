---
title: "problem using wine"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Abadon on 2006-08-28
Hi there,

I was really excited when I found out that I could use windows aplications on my ubuntu using wine.  When I installed DVD Decrypter that program opens properly but does not recognize any of my dvd drives it says devise not found. Before I installed that program I made sure that dma is on, so evrything should have worked properly. The other thing is how do I remove apications which are installed via wine. For any sugestions thanks a lot.

---

### Post by chuckyp on 2006-08-28
Well you probably need to check with wine's appdb if you go to winehq.com you can search the appdb and make sure that dvd decrypter works with wine.  All programs installed with wine should be in the following directory structure.

$home/.wine/c_drive/program files/ etc......

---

### Post by reacocard on 2006-08-28
open a terminal and type
```
winecfg
```
on the devices tab, tell it to autodetect.

for uninstall, just use the program's uninstaller.

---

### Post by Anonii on 2006-08-28
> **Abadon said:**
> Hi there,

I was really excited when I found out that I could use windows aplications on my ubuntu using wine.  When I installed DVD Decrypter that program opens properly but does not recognize any of my dvd drives it says devise not found. Before I installed that program I made sure that dma is on, so evrything should have worked properly. The other thing is how do I remove apications which are installed via wine. For any sugestions thanks a lot.

First of all, does _WINE_ recognise any of your drives?
Open "winecfg" from the terminal ,and go to the drives section, are they listed? Is D: the place your CD-rom is mounted? 

You can simply uninstall programs that you installed with wine using:
rm -r ~/.wine/..../<program_directory>
AFAIK this is the default uninstall of a wine program , dunno about the registry... (There is a possibility that the default uninstaller of the game/program located in the program/game directory will work, but it didnt for me, most times)

Also, you can get IRC support from:
Server: irc.freenode.net
Channel: #winehq

Good luck.

---

### Post by Abadon on 2006-08-28
Hi there,

Thanks a lot for the sugestions. When I opened my terminal and got wine configuration which is nice, then I've noticed it says windows 2000 default settings!!!!!!!!!! no idea why, anyway I followed your sugestion and use autodetect. It did detect drive D which is my dvd/cd rom but also comes as an error:err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0. How do I get that information. Please if you can post a simple instruction since I'm still  new in ubuntu.

---

