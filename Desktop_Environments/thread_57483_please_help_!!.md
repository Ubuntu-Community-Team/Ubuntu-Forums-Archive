---
title: "please help !!"
date: 2005-08-16
forum: Desktop Environments
---

### Post by ceborame on 2005-08-16
I am a complete linux newbie.

Can someone please tell me IN DETAIL how  I do step 4 of this ( its to install flash player )

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s)

The file is unpacked and is displayed on my desktop

Kind regards

Mick

---

### Post by krusbjorn on 2005-08-16
Click your gnome menu (top left corner of the screen), go to system tools and then click Terminal. Navigate to the directory by typing "cd ~/Desktop/install_flash_player_7_linux". Now, type "./flashplayer-installer". If you get permission errors, you will have to  write "sudo ./flashplayer-installer" instead.

Good luck!

---

### Post by ceborame on 2005-08-16
aw thanks ; i use kde tho ! but i would assume its the same

---

### Post by ceborame on 2005-08-16
did that and got this

michael@ubuntu:~$ cd ~/Desktop/install_flash_player_7_linux
michael@ubuntu:~/Desktop/install_flash_player_7_linux$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
michael@ubuntu:~/Desktop/install_flash_player_7_linux$

---

### Post by krusbjorn on 2005-08-16
Type "ls" to see what files there is. There probably is a file named installer-something. Remember that it's case sensetive.

EDIT: Did you see this, btw?

[http://ubuntuguide.org/#flash-mozilla](http://ubuntuguide.org/#flash-mozilla)

---

### Post by ceborame on 2005-08-16
phew done it thanks

I deleted the unpacked installer and extracted it again except I chose extract to and NOT extract to install_flash_player_7_linux

I told it to extract to desktop and your instructions where good then

Thanks 

MIck

---

