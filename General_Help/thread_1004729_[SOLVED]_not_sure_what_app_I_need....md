---
title: "[SOLVED] not sure what app I need..."
date: 2008-12-07
forum: General Help
---

### Post by 2handband on 2008-12-07
/home/gene/Desktop/PacketTracer5_no_tutorials_i386_installer-deb.bin

I'm trying to install the above file on hardy. When I click it it says there is no application installed for this file type. How do I know which application it needs?

---

### Post by taurus on 2008-12-07
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 PacketTracer5_no_tutorials_i386_installer-deb.bin
sudo ./PacketTracer5_no_tutorials_i386_installer-deb.bin
```

---

### Post by 2handband on 2008-12-07
When I pasted the first command I got the following output:

"chmod: cannot access `PacketTracer5_no_tutorials_i386_installer-deb.bin': No such file or directory"

I thought that was a rather odd thing for it to say considering that the file is sitting right in plain sight on my desktop. :lolflag:

---

### Post by taurus on 2008-12-07
> **2handband said:**
> When I pasted the first command I got the following output:

"chmod: cannot access `PacketTracer5_no_tutorials_i386_installer-deb.bin': No such file or directory"

I thought that was a rather odd thing for it to say considering that the file is sitting right in plain sight on my desktop. :lolflag:

The chmod is not the first command.  It's the second command, after the "cd ~/Desktop" command.  In other words, you need to move into Desktop directory first since that file is resided in there, ~/Desktop.

---

### Post by Bölvaður on 2008-12-07
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 PacketTracer5_no_tutorials_i386_installer-deb.bin
sudo ./PacketTracer5_no_tutorials_i386_installer-deb.bin
```

I will elaborate on each part of this so you can adapt it to your situation.

cd ~/Desktop means: change directory to the desktop (/home/username/Desktop).
You should insert the path to the file there like if I Wanted to check my documents

cd /home/bolvadur/Documents


Then chmod 755 PacketTracer5_no_tutorials_i386_installer-deb.bin will give you the rights to run this file as a program (this is an executable installer).

what I would suggest is type:
chmod u+x Packet (then press TAB key to autofinish the word)

u+x means set eXecutable rights for the file, for user (owner of the file)


you should not run installers as root.. so only write:

./Packet  (and then press TAB again for the automatic finish of the word)

using sudo in this situation would be considered security threat by me, but this is exactly how windows deals with installers.

---

### Post by 2handband on 2008-12-07
Okay, I feel a little sheepish for missing that first command. Thanks Taurus! Also thanks to Bölvaður for the explanation... I'm still struggling a bit with command line. The software is now installed and working.

---

