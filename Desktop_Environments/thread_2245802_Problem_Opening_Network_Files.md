---
title: "Problem Opening Network Files"
date: 2014-09-26
forum: Desktop Environments
---

### Post by oakridge on 2014-09-26
When opening files from with a program the 'Open Fie' window does not list network sources.  This is not too bad for programs like LibreOffice where files can be opened from the Home Folder but at present I am making considerable use of FSlint where it is not possible.  

Am I missing something?

Thank you.

Malcolm

---

### Post by andrew102 on 2014-09-26
Are you mounting the drives to /media/MyDrive ?
That would probably make it easier

---

### Post by deadflowr on 2014-09-26
Maybe i'm missing something, and I would not be surprised if I was, but the network folder needs to be mounted first, in order for any program to see it.

You could set the network shares to be auto-mounted, so that they are mounted upon boot/login, is that something you'd want?

Or is this going into a totally misguided direction?

---

### Post by tgalati4 on 2014-09-26
You can put permanent network mounts in [/etc/fstab]("https://help.ubuntu.com/community/Fstab") and they show up like local mounts.

Some programs can see advertised/published network shares, some can't.  For the programs that can't, use /etc/fstab.

---

### Post by oakridge on 2014-09-27
Thank you all very much.  It is seven years since I retired and was using the command prompt all the time and I am getting very rusty. The machine I am connecting to is dual boot Linux/Windows 7 and the connection seems to work better with Windows.

Windows and Linux do have there own strengths.  I am currently cataloguing a collection of of about 30K documents, some in surname, some in first-name and some in title and they must all be in surname.  It will keep me busy for quite a while.

---

