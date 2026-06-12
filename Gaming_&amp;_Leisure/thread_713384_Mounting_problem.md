---
title: "Mounting problem"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by Stenudd on 2008-03-02
Okey here we go. 

I've got my game on a .iso file and I want to install it.

In windows its "easy" to mount, just need daemon-tools then the games works fine to install.

In linux it works fine to mount but when I running the setup.exe via wine for example it will fail. On a closer look in the directory i've mount the .iso file in. some files have been renamed. they have got a tilde (~). I know they will do this if the name is longer then 8 characters. 8+3 extension, 11 totally charcters then. 

How is this problem solved? Is there an mount program in Linux like deamon-tools that can handle this files? At this moment Iam mount the files via the mount command and it works fine unless the ~ thing. 

It cant be the .ISO that is broken then not even windows could mount it I've figured out :) I've read the MAN page for mount and found the nojoliet options but it didn't done the trick for me? 

PS. Running Gentoo and have "Microsoft Joliet CDROM extension" built in in the kernel. 

Thanks in advance

/ Stenudd

---

### Post by owbizi on 2008-03-03
Well, take a look at [here](http://ubuntuforums.org/showthread.php?t=87369)!

---

### Post by Stenudd on 2008-03-03
Hmm also I already have these scripts too. downloaded from gnome-look.org I think. It was actually this scripts I use when Iam trying to mount but still the ~.

---

### Post by owbizi on 2008-03-04
Hmm, you can try to get an answer from that topic too. The author possibly is more inclined to know it than me, I'd say, hah. :)

---

### Post by falke on 2008-03-07
> sudo apt-get install gmount-iso

alt+f2  ->   "Gnome-iso"

---

