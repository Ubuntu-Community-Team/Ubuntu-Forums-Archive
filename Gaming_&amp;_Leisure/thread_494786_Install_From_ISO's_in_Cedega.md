---
title: "Install From ISO's in Cedega"
date: 2007-07-07
forum: Gaming &amp; Leisure
---

### Post by Vendetta_NZ on 2007-07-07
Is it possible to install a game in Cedega using an ISO? I have no discs to burn it to, (its C&C3). I have tried to extract the iso using the archive manager, then selecting the setup.exe file in Cedega, however it just seems to hang and nothing comes up. Has anyone successfully managed to install a game in Cedega using a .iso? If so can you please explain?

---

### Post by nereid on 2007-07-07
Just mount your ISO to your cd-rom folder and install it using Cedega as you would with any other cd-rom.

```

mount -t iso9660 -o loop /path/to/iso /path/to/cd-rom/folder

```

---

### Post by Vendetta_NZ on 2007-07-07
How would you use this? Path to Iso I understand, but path to cdrom folder?

---

### Post by Vendetta_NZ on 2007-07-07
EDIT: I have managed to mount it as cdrom0 in Computer. It does not work however. Cedega still looks for the setup files in the F:/ Drive in which a disc does not exist.

---

### Post by Vendetta_NZ on 2007-07-07
Also, how will I unmount it?

---

### Post by nereid on 2007-07-07
Use umount to unmount the image, just like you would do with a regular cd-rom. Take a look at your Cedega options. To which folder does f:/ link? Note that folder down and use that one in the mount command.

---

### Post by Haz13r on 2007-07-07
Back when i had Windows, i had this program called PowerISO.  That works really well but i will try with Ubuntu.  
Btw, never get MagicISO.  If you want you should get Alcohol 120 from a Torrent Downloader.  I love that.

---

### Post by hikaricore on 2007-07-07
You can't use windows software to mount ISOs under Linux...

---

### Post by Vendetta_NZ on 2007-07-07
Does anyone know of a program available under linux that does a similar thing to Alcohol 120%? I have already posted in the Gutsy Gibbon Idea Pool stating that Gutsy should include an ISO Mounting feature. Its so needed.

---

### Post by Vendetta_NZ on 2007-07-08
When I right click on my CD Drive (physical) in Computer, it says its location is Computer:/// is that what I should mount it to? I've tried that, it says its not a directory.

---

### Post by IanW on 2007-07-08
/path/to/cdrom/folder = /media/cdrom (for me anyway)

---

### Post by Vendetta_NZ on 2007-07-08
Yeah I figured that. Lemmie try something out, i'll post my method and result if it works.

---

### Post by Ninja duck on 2010-02-21
Gmount-iso is a small Gui tool that mounts iso's for you

---

