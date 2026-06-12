---
title: "Fuz2y_Desktop_Theme_v1.2.tar.gz; can't install"
date: 2008-02-10
forum: Desktop Environments
---

### Post by bumanie on 2008-02-10
Trying to install the above desktop theme. I have followed the instructions as best I can, but am obviously doing something wrong or am missing something. Can someone please help. 
Here are the instructions (everything else has ## at the beginning)

## To install simply extract all files (as root user) to your Home folder: 

## Code:

cp Fuz2y_Desktop_Theme_v1.2.tar.gz ~/
cd ~/
sudo tar -zxvf Fuz2y_Desktop_Theme_v1.2.tar.gz

Here is the output from terminal when I input codes as per the instructions after unpacking.

ubuntu@ubuntu:~/Desktop$ cp Fuz2y_Desktop_Theme_v1.2.tar.gz ~/
cp: cannot stat `Fuz2y_Desktop_Theme_v1.2.tar.gz': No such file or directory
ubuntu@ubuntu:~/Desktop$ cd ~/
ubuntu@ubuntu:~$ sudo tar -zxvf Fuz2y_Desktop_Theme_v1.2.tar.gz
Password:
tar: Fuz2y_Desktop_Theme_v1.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Thanks to anyone who can help. I have installed emerald theme manager (at least my preferences list says so).

---

