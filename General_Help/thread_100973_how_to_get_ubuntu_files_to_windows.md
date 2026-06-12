---
title: "how to get ubuntu files to windows"
date: 2005-12-08
forum: General Help
---

### Post by Fittersman on 2005-12-08
i need help tonight to get my test from ubuntu to windows, the file is too large to use a floppy and i dont have a cd burner my windows partition (hda2) doesnt allow me to write to it, if i could create a new partition to use with windows and ubuntu that'd be great but i need any way to get my file there asap!!

---

### Post by Bachstelze on 2005-12-08
As I told you a billion times, you can't write on NTFS partitions with Linux. If your Windows partition is FAT32 you can.

---

### Post by Fittersman on 2005-12-08
thats the first time you said that adn how do i change it to fat then?

---

### Post by Bachstelze on 2005-12-08
You can't, if you want to convert it you have to format. Do you have any FAT32 partitions you could use ? Post the results of

```
sudo fdisk -l
```

---

### Post by Fittersman on 2005-12-08
no only windows (ntfs) and ubnutu (whatever) and another one that ive never seen before so im not about to play with it

---

### Post by syncme on 2005-12-08
I've seen someone work around this....
The person created a 4 gig fat32 partition and used that to move files back and forth. 
4 Gig might be a bit big but it's a solution. 

Syncme

---

### Post by Fittersman on 2005-12-08
tell me how tell me how!!!! :D lol

---

### Post by Qrk on 2005-12-08
You can use the live CD to resize either Linux or Windows. Gparted will allow you to change whichever one you want. I sometimes use the paritioning part of the install CD, but it doesn't matter.

Reduce your Ubuntu size by 500MB, and format the free space as Fat32. Move the file to the Fat 32 partition from Ubuntu, then boot into windows, and look for  your Fat32 partition in My Computer.

---

### Post by MichaelM on 2005-12-08
An easier solution (no partioning or formatting): [Explore2fs]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm") lets you browse EXT2 or 3 file systems from Windows. If you went with the defaults in installation, that is what you have.

---

### Post by Bachstelze on 2005-12-08
The other one must be the swap space... You could use that space for a fat32 partition since it is not ABSOLUTELY required for Ubuntu to boot. Oh btw I perhaps found a solution for your modem : 

Download this : [http://membres.lyos.fr/mafiaboy03/ubuntu/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb](http://membres.lyos.fr/mafiaboy03/ubuntu/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb)

Put it on a floppy disk and copy it in your home diretory in ubuntu. Then open a terminal and run

```
sudo dpkg -i sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb
```

(you can use the name completion with the TAB key so you don't have to type the whole name. Then see if wvdialconf detects your modem.

EDIT : thanks for this MM, it might be useful.

---

### Post by Grey on 2005-12-08
There's also the option of using a Windows tool to read the Linux partition.  That's what I do in the rare case that I need something in Windows.  I use [this tool here](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) for the job.

---

### Post by Fittersman on 2005-12-08
thanks alot micheal!! i got my test out and thank you

---

### Post by MichaelM on 2005-12-08
[QUOTE=Fittersman]thanks alot micheal!! i got my test out and thank you[/QUOTE]
Glad to help!
I see Grey had the same solution. :)

---

