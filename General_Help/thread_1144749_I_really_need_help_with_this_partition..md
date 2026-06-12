---
title: "I really need help with this partition."
date: 2009-05-01
forum: General Help
---

### Post by Mamsaac on 2009-05-01
I deleted one partition in order to make another one larger, since I needed space for the database and the other partition was not necessary (anymore, at least). 

Other than that, I wanted to make other partitions larger as well, since there was enough space... but this second paragraph is not really important.

So, I used gparted and all seemed fine... but then it moved the partition and when it wanted to check for mistakes it broke.

It recommended using ```
sudo e2fsck -b 8193 /dev/sda7
```, but it is not working.

I disobeyed my usual instinct and didn't back up the database (which was reaching 10gb), since I have used gparted for years and it never gave me any problem (I can no longer say that...)

I wanted to attach the file, but since it's an html file it doesn't let me. Here's a link to it (uploaded in a free webhosting =)): [http://mam.frih.net/gparted_details.htm]("http://mam.frih.net/gparted_details.htm")

I assure you that link is clean (doesn't even have js in it)

When I try ```
sudo e2fsck -b 8193 /dev/sda7
```, it says that there's a bad magic number in the super-block and recommends me to play the very same command.

The command prompt is the following (in Spanish):

```
USER@HOST:~$ sudo e2fsck -b 8193 /dev/sda7
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Bad magic number in super-block mientras se intentaba abrir /dev/sda7

El superbloque podría no ser leido o no describe un sistema de ficheros ext2 correcto.
Si el dispositivo es válido y en verdad contiene un sistema de ficheros ext2 (y no uno 
de intercambio, ufs o algo más), entonces el superbloque está corrompido
y podría intentarse ejecutar el e2fsck con un superbloque alternativo:
   e2fsck -b 8193 <dispositivo>

```

I'm still hoping there's a way to repair the partition.

Note: it's an ext3 partition. The messages e2fsck is throwing display ext2, can that have something to do with it?

Thanks for anyone that is helping me with this problem. Again, I hope something can be done.

EDIT:

I managed to fix the database partition. I'm checking if there are any problems, although I hope there aren't.

---

### Post by jazzgossen on 2009-05-01
> **Mamsaac said:**
> 
I managed to fix the database partition. I'm checking if there are any problems, although I hope there aren't.

Please write how you did it, for future reference. Also, to get English error messages (which may be more useful when posting here) you can type "LANG=C" in the terminal window before entering the other command.

---

