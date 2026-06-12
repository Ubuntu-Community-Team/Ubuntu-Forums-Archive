---
title: "Wont run program"
date: 2009-01-24
forum: General Help
---

### Post by claesnl on 2009-01-24
Hello there

I am trying to install 2 programs, Maple12 and eclipse, both of which needs a working java installation to function. But when i doubleclick the "installMapleLinux" nothing happends. When i try to run it in terminal it says:

cd: 30: can't cd to Linux/Disk1/InstData/VM
sh: Can't open ./Maple12Linux32Installer.bin

I have both programs installed on my laptop, but here on my stationary, it is not working.

I have java installed for firefox (i can go and use java sites) but apparently it is not working on the PC?

Thx in advance
 - Claes

---

### Post by Procuro on 2009-01-24
Hmm... try moving the bin off the disk to your desktop. Then cd to your desktop and try: chmod 777 Maple12Linux32Installer.bin  if its permission issues that's the problem. Hopefully if you do that it'll install when you try ./

Isn't eclipse already in the ubuntu respository? The synaptic package manager should install all the java stuff for you.

This might help: [http://ubuntuforums.org/archive/index.php/t-907702.html](http://ubuntuforums.org/archive/index.php/t-907702.html)

---

### Post by claesnl on 2009-01-24
That doesnt change anything im afraid.

eclipse is "installed", since its just a packacke that needs to be extracted, but it wont run the eclipse file to start to program either.

Claes

---

### Post by claesnl on 2009-01-25
New development...

I have tried extracting eclipse to another folder than /usr/local/ and now it runs fine. So the first part is "fixed".

But maple installer still wont run.

---

