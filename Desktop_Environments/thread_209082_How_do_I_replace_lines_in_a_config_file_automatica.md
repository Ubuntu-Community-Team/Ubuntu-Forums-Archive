---
title: "How do I replace lines in a config file automatically using script?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by PryGuy on 2006-07-04
Hello, everybody!
I've got a question to ask. The problem is pretty common, I have downloaded some packages but I have no possibility to download them every time I want to install Ubuntu. So I decided to make an installation script that would dpkg -i all the files. It works fine except for one thing: I've got an nvidia-glx package with the other files and I want my to make my script modify the /etc/X11/xorg.conf file and replace the line```
	Driver		"nv"
```with the line```
	Driver		"nvidia"
```so it could start the original nVidia driver after the gdm restart. I'm sure it is possible with all the Linux command line power. Please help! Thanks in advance!;)

---

### Post by PryGuy on 2006-07-05
Anybody??? Is that so hard?:(

---

### Post by Thund3rstruck on 2006-07-05
you'll use the sed tool. 

something like 
```

sed s/nv/nvidia filename

```

however, you'll need to loop the file to find the line to change. I don't have a UNIX machine at my disposal here or I'd whip it up for you. Perhaps someone here can help

---

### Post by wrtrdood on 2006-07-05
sed 's/nv/nvidia/' xorg.conf >new-xorg.conf

---

### Post by duff on 2006-07-05
sed also has a -i parameter which can be used to edit the file directly.

sed -i 's/nv/nvidia' xorg.conf

---

### Post by PryGuy on 2006-07-05
thanks friends... it really helped!=D> 
I'm writing an unattended postinstall script...

---

