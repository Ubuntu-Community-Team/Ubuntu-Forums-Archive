---
title: "enable write on windows partition to play mp3s?"
date: 2005-10-24
forum: Desktop Environments
---

### Post by elementary on 2005-10-24
I am trying to play mp3s on rhythmbox. I have the codecs, but when I play them off my windows partition, I get an error 'Could not open resource for writing'. Does this mean I need to enable write for my windows partition? [and if so, what do I edit?] cheers

---

### Post by VR6Pete on 2005-10-24
Sounds more like your missing a codec, do they play ok in XMMS?

---

### Post by elementary on 2005-10-24
yep. no problem in XMMS (but i dont really like that program)
I did apt-get install gstreamer0.8-mad
is there something else i need?

---

### Post by jeffreyvergara.NET on 2005-10-24
if you are using FAT32 filesystem it will be easier to make it read/write, I heard that it's NTFS is not yet fullt supported under linux?

anyways, you must edit your fstab "sudo gedit /etc/fstab", I recommend you visit [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by elementary on 2005-10-24
It's NTFS filesystem. Ubuntuguide doesn't say how to enable write for that...can it be done?

---

### Post by Kyral on 2005-10-24
Technically it can be done, but its VERY VERY VERY Experimental. You stand a better chance of destroying your Windows Partition then it actually working

---

### Post by elementary on 2005-10-24
hmmm, pass

---

