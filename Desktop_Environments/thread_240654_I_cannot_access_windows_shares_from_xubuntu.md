---
title: "I cannot access windows shares from xubuntu"
date: 2006-08-21
forum: Desktop Environments
---

### Post by feanor_arcamenel on 2006-08-21
hello everyone, I was using ubuntu with gnome until recently and when using ubuntu, smb://computer_name command of nautilus seemed perfect to connect to a wndows computer.

Now I'm using xubuntu but had some problems about networking. I can access my linux files from a windows computer. That's OK. However, when I try to mount windows shares from xubuntu it asks for a password. But what password is this? I tried everytihng. And I'm using Jags gui to use samba.

---

### Post by TSK on 2006-10-10
Same problem here. I managed to install and configure Samba the right way for the Xubuntu box to be acccessible from the Windows box (thanks to Arnieboy's guide). But from Xubuntu, I simply don't even get how and where to specify the name or IP of the machine I want to reach. 

People write about typing "smb://windows-box-name" and stuff, but where? Thunar sure enough does not allow it on my system. Is Nautilus required? I thought that was for Ubuntu only, not Xubuntu?

---

### Post by dannyboy79 on 2006-10-10
> **TSK said:**
> Same problem here. I managed to install and configure Samba the right way for the Xubuntu box to be acccessible from the Windows box (thanks to Arnieboy's guide). But from Xubuntu, I simply don't even get how and where to specify the name or IP of the machine I want to reach. 

People write about typing "smb://windows-box-name" and stuff, but where? Thunar sure enough does not allow it on my system. Is Nautilus required? I thought that was for Ubuntu only, not Xubuntu?


nautilus is a gtk based program and both ubuntu and xubuntu run gtk type apps. you can install nautilus if you'd like. it sounds like you could use waht the person who posted above you uses, i don't however use any gui, i just use smbmount. check it out, it has helped tons of people! [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by dannyboy79 on 2006-10-10
> **feanor_arcamenel said:**
> hello everyone, I was using ubuntu with gnome until recently and when using ubuntu, smb://computer_name command of nautilus seemed perfect to connect to a wndows computer.

Now I'm using xubuntu but had some problems about networking. I can access my linux files from a windows computer. That's OK. However, when I try to mount windows shares from xubuntu it asks for a password. But what password is this? I tried everytihng. And I'm using Jags gui to use samba.

did you uninstall ubuntu-desktop and then do xubuntu-desktop install or did you do a complete reformat and install of xubuntu? if you did a complete reinstall of xubuntu than you have to configure samba just like you did when you used ubuntu. is your username and password the same on your windows box? if not, you need to specify a username.map file and it's location within you smb.conf file. what does smbtree give you from the terminal? did you add your linux username to smbpasswd. you would type in smbpasswd -a usernamehere then it'll ask you for your password and then you should be good but if your windows username and password are different on linux than you either need to add your win username and password to your linux box and then to smbpasswd or you need to create a username.map file and refer to it in your smb.conf.

found this in gogle:
This username map parameter allows you to map PC style usernames to Linux style usernames. You can specify the location of your username map file with the username map parameters.

Example: username map = /usr/location/samba/lib/username.map

The syntax of the username map file is simple. Each line consists of a Linux style name like manager and a list of possible PC style username like webuser, separated by an equal sign. A sample username map in the username.map file is defined as follows.

Example: manager = webuser

---

### Post by TSK on 2006-10-10
> **dannyboy79 said:**
> nautilus is a gtk based program and both ubuntu and xubuntu run gtk type apps. you can install nautilus if you'd like. it sounds like you could use waht the person who posted above you uses, i don't however use any gui, i just use smbmount. check it out, it has helped tons of people! [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Thanks! The guide at justlinux.com that you linked to was exactly what I needed. I realise Arnieboy had this part in his HOWTO aswell, but very briefly.  Nice also with info on how to make permanent mounts of Windows shares without  putting passwords in the open. Excellent. Now I won't need Nautilus anyway.

---

### Post by dannyboy79 on 2006-10-10
> **TSK said:**
> Thanks! The guide at justlinux.com that you linked to was exactly what I needed. I realise Arnieboy had this part in his HOWTO aswell, but very briefly.  Nice also with info on how to make permanent mounts of Windows shares without  putting passwords in the open. Excellent. Now I won't need Nautilus anyway.

i am glad i could help. i have only been using for about 6 months and i know when i was a newbie I wish people would have helped me out as much as i am NOW. I come onto these forums at least a few times a day, scroll thru and if there is something i know I can help with than i do!

---

### Post by TSK on 2006-10-10
One more note though: The guide at justlinux.com actually had a couple of typos in the code examples (blanks before .smbpasswd), and also missed a few very good tips, such as "sudo mount -a" being a way to test if fstab works, and also "sudo umount /mysharetarget" to unmount a manually mounted share in order to see if fstab does the trick. Also, editing fstab with a new line at the end must be followed by [ENTER] in order to end the file with a new, blank line. Otherwise something goes wrong. I got that error message when doing "sudo mount -a" the first time - and finally solved my problem. 

From another post, I found the following link to Ubuntuguide.org which is what finally got me going, thanks to the details mentioned above:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrit](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrit)

---

### Post by jolito on 2008-05-11
> **feanor_arcamenel said:**
> hello everyone, I was using ubuntu with gnome until recently and when using ubuntu, smb://computer_name command of nautilus seemed perfect to connect to a wndows computer.

Now I'm using xubuntu but had some problems about networking. I can access my linux files from a windows computer. That's OK. However, when I try to mount windows shares from xubuntu it asks for a password. But what password is this? I tried everytihng. And I'm using Jags gui to use samba.


Try this: Alt+F2 and type  nautilus - it opens. From menus: Go -> Location... .In the location field type smb://IP Address. That's it.

---

