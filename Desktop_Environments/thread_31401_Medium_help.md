---
title: "Medium help"
date: 2005-05-03
forum: Desktop Environments
---

### Post by Redby on 2005-05-03
Hello, can anybody help me please. When i insert DVD-ROM with data or movie into my DVD-ROM DRIVE, nautilus say me that´s empty medium and open CD/DVD burner window. I am sure it isn´t empty medium.

 I tried more options in FSTAB like udf,iso9660 or auto for filesystem, but no result.

 Thank you for your replies

---

### Post by nemin on 2005-05-03
[QUOTE=Redby]Hello, can anybody help me please. When i insert DVD-ROM with data or movie into my DVD-ROM DRIVE, nautilus say me that´s empty medium and open CD/DVD burner window. I am sure it isn´t empty medium.[/QUOTE]
Are you sure the drive works corectly? Have you ever tried it under windows?

---

### Post by Redby on 2005-05-03
Yes, drive is ok. I used it on Mandrake and everything was OK. 

Thankx for replies

---

### Post by StacyWebb on 2005-05-03
pretty simple fix is to go in to the mount directory and make a folder cdrom0
cd /media
sudo mkdir cdrom0

also you may need to make one in the /mnt directory also
cd /mnt
sudo mkdir cdrom0

Try that and let us know if it works.

---

### Post by Redby on 2005-05-03
I made it, but with the same result. I allready had cdrom0 and cdrom1 in /media. When i mount manualy from console i got second icon on my desktop named DVD-ROM (2) and this one is ok with correct data. I don't understand why first one from automount is withou data.

 Thanx for replies

---

### Post by StacyWebb on 2005-05-03
Does this happen with only Burned DVD's? Or does it happen with pressed ones also?

---

### Post by Redby on 2005-05-03
All kind of DVD's data and movies. CD's are ok.

---

