---
title: "Hard drive mounting problems"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Sumint620 on 2006-07-31
hey guys,
ok, well i just installed dapper drake last night (finished in about 20 minutes from LiveCD boot to rebooting into the OS). I set up a dual boot with windows xp on my main hard drive (set as master) and i put ubuntu on my slave drive. dual boot worked great, GRUB detects everything and all goes well. i then looked around to see how to mount (and automatically mount on boot) my windows drive (NTSC) as a read only (all my music is on there) and that worked like a charm. now what i want to do is take an old hard drive (4GB) and use it to share files between ubuntu and XP (i know all about how windows can't read the linux file structure etc.) and i formatted it as FAT32 in windows. i want to be able to mount this drive and have it so i can read and write to the drive. i did get the drive to mount but i can't find out how to write to the drive. if somebody could give me step by step instructions (i can delete the mount point and unmount the drive and start from scratch) that would be really wonderful! i'm somewhat new to linux (use fedora core 5 for a couple weeks) so i would appreciate some help :smile:  . oh one more thing, i'm not really liking that i can't do anything to a lot of files. i installed a firefox theme and wanted to change the chrome.css file to customize it however i can't save the files cause i don't have permission. i also wanted to install a GRUB skin that i found on gnome-look.org and wouldn't let me do that either. i really liked the thing in FC5 that allowed you to be logged in as root without restarting your system or logging out (you just clicked on the app and typed in your pass). anyway, sorry for this being long.

---

### Post by Ziox on 2006-07-31
i can't really help with the mounting thingy, but if you want to have root privilage, then use "sudo"

example:

sudo mkdir /opt

this command would make a directory named opt in /

however any file/folder that's created by sudo is owned by root, not by a user, meaning that you, logged in as user, can't edit the file without either using sudo or gksu/kdesu (GUI for sudo)

hope this helps...

p.s. there is a way that you can log in as root, but Linux, especially Ubuntu, discourage the use of that, because it is unsafe...("with great power comes great responsibilities")

---

### Post by Sumint620 on 2006-07-31
i know how to use sudo and mkdir. thats how i created mount points for the hard drives. i was wondering if there was a way that i could lets say 'log in' as root and edit a file like chrome.css and then log out. it sounds like that gksu is that sort of thing and where would i get that

---

### Post by Ziox on 2006-07-31
you can try gksu nautilus

which would open nautils (file manager for gnome) with root permissions, but always becareful when you are root!!! 

You can never be too careful :)

---

### Post by Sumint620 on 2006-08-02
yup, that gksu nautilus worked perfectly. however i guess this post is a bump for the mounting problems. but thats too for the gksu information!

---

