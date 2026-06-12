---
title: "Im a noob"
date: 2005-05-04
forum: Desktop Environments
---

### Post by Fraggy on 2005-05-04
Right, ive just installed Ubuntu on me system.  This is the first Linux distro I have had on my comp. I have no idea on how to install applications and stuff like that, i love the look and feel of the system, and just want to know a couple of things, here goes:

1 - How would i got about installing applications. I just download amsn and dont know how to install it, i downloaded the debian version, is that right?

2 - How do I look at my windows partitions, cause i want to get some stuff and put it in my ununtu partition so that i can do my work on it and also listen to my mp3s.

Thanks in advance guys and gals!!! \\:D/

---

### Post by Joeb on 2005-05-04
The easiest way to install software is to use the synaptic package manager (under System-->Administration).  You probably need to enable two other repositories (places on the internet where packages/programs are located).  To do that, in synaptic, go to the Settings--->Repositories menu, click on "Add" and click the Community maintained and Non Free checkboxes.  Once you exit all of that, your packages you want will probably be in the list and Ubuntu will download and install them for you by clicking on them to select them and then clicking the apply button.  If something you want still isn't listed, then you will need to install it manually by downloading it and following the directions given by the author.

Your second question of seeing your windows partition is pretty straight forward.  You need to add a line to your /etc/fstab file.  The easiest way is to open a terminal window and type:  sudo nano /etc/fstab

Then add to the bottom of the stuff listed:  /dev/hda1   /mnt/windows    auto   rw,user,auto  0  0

This is assuming that your windows partition is the first one on the first hard drive, if not that hda1 will have to be changed.

After saving and exiting, you need to create the mount point.  Still in the terminal window enter:  sudo  mkdir /mnt/windows

And that should do it.  BTW, you don't have to call it /mnt/windows, but whatever you call it in the /etc/fstab file needs to be the same as the directory you created or it won't work.

Hope that helps and welcome to Ubuntu!

ps.  The forum you posted in is not really for asking questions.  It would be better to use one of the other support forums.

---

### Post by vassie on 2005-05-04
[QUOTE=Fraggy]Right, ive just installed Ubuntu on me system.  This is the first Linux distro I have had on my comp. I have no idea on how to install applications and stuff like that, i love the look and feel of the system, and just want to know a couple of things, here goes:

1 - How would i got about installing applications. I just download amsn and dont know how to install it, i downloaded the debian version, is that right?

2 - How do I look at my windows partitions, cause i want to get some stuff and put it in my ununtu partition so that i can do my work on it and also listen to my mp3s.

Thanks in advance guys and gals!!! \\:D/[/QUOTE]

Hello

Firstly, this is not the place to ask questions
Secondly, [this](http://ubuntuguide.org/) should answer all your questions

Have fun :)

Ben

---

### Post by Fraggy on 2005-05-04
ooops, sorry guys, but thanks for the help, i wont be making any more mistakes again, cheers.

---

