---
title: "Need help!!"
date: 2006-02-12
forum: Desktop Environments
---

### Post by naveents on 2006-02-12
I am new 2 linux!! Can any1 plz tell me how 2 transfer data from linux 2 windows and vice versa?? I am having Xp!! I have many Mp3 and other stuff which i need 2 copy to Linux!! I am a beginner,so,i would be happy if someone can explain it in simple way!! Mailing me is als OK...my mail id is [email]naveentsnts@gmail.com[/email]

---

### Post by simon_is_learning on 2006-02-12
The usual answer to this question is installing samba. I however still havn't managed to figure out how to use it on a winME. (still working though). 
So when I have to transfer files I use FTP.

On the Ubuntu:
Sudo apt-get install proftpd
(use Standalone in server type)

On the windows machine:
download smartftp [www.smartftp.com](www.smartftp.com)

connect to the Ubuntu IP (ifconfig in ubuntu-terminal) use your ubuntu username and password.

When I did it it worked on the first try ;)

good luck

---

### Post by Irony on 2006-02-12
See here for mounting Windows in Linux; [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

Basically the instructions tell you to make a folder and then mount it. You can also do it so the created folder mounts Windows on boot-up.

To access Linux from Windows use; [http://www.fs-driver.org/](http://www.fs-driver.org/) or this which is very simple and easy [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by Irony on 2006-02-12
I think simon_is_learning is referring to networking rather than accessing partitions on the same machine.

---

### Post by simon_is_learning on 2006-02-12
Is the problem that you have two different computers or is it that you have a linux partition and a windows partition?

becouse Me and Irony is talking of different problem/solutions. 
And i'm not ironic =)

---

### Post by alfotis on 2006-02-12
See [Paragon Mount Everything]("http://www.mount-everything.com/"), but my advise is to mount your linux partition as read only (at least for start, just to make sure that the program works fine - remember, it runs on Windoze...  ) in order to access your linux partition from Windows

---

### Post by atoponce on 2006-02-12
More information on the setup of you machine(s) and exactly how you want to transfer the files would be helpful.

---

### Post by naveents on 2006-02-13
I am having windows and linux in same computer.....I have partitioned it...

---

