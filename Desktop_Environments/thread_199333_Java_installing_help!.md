---
title: "Java installing help!"
date: 2006-06-18
forum: Desktop Environments
---

### Post by SuperCow on 2006-06-18
ubuntu@ubuntu:~$ sudo cd /usr/java/
sudo: cd: command not found
ubuntu@ubuntu:~$ sudo /usr/java/
sudo: /usr/java/: command not found
ubuntu@ubuntu:~$ chmod a+x jre-1_5_0-linux-i586.bin
chmod: cannot access `jre-1_5_0-linux-i586.bin': No such file or directory
ubuntu@ubuntu:~$ sudo chmod a+x jre-1_5_0_07-linux-i586.bin
chmod: cannot access `jre-1_5_0_07-linux-i586.bin': No such file or directory
ubuntu@ubuntu:~$ sudo chmod a+x /home/ubuntu/Desktop/untitled folder/jre-1_5_0_07-linux-i586.bin
chmod: cannot access `/home/ubuntu/Desktop/untitled': No such file or directory
chmod: cannot access `folder/jre-1_5_0_07-linux-i586.bin': No such file or directory
ubuntu@ubuntu:~$ sudo chmod a+x /home/ubuntu/Desktop/JAVA/jre-1_5_0_07-linux-i586.bin
ubuntu@ubuntu:~$ sudo chmod a+x /home/ubuntu/Desktop/JAVA/jre-1_5_0_07-linux-i586.bin
ubuntu@ubuntu:~$ ls -l
total 0
drwxr-xr-x 3 ubuntu ubuntu 120 2006-06-18 20:06 Desktop
ubuntu@ubuntu:~$ ./jre-1_5_0_07-linux-i586.bin
bash: ./jre-1_5_0_07-linux-i586.bin: No such file or directory
ubuntu@ubuntu:~$
](*,)  thats what i was trying to do and it doesn't work :(

---

### Post by bruce89 on 2006-06-18
That's not how you install java anymore ```
sudo aptitude install sun-java5-jre
``` but the multiverse repo has to be enabled first.

---

### Post by SuperCow on 2006-06-18
multiverse repo?

---

### Post by meng on 2006-06-18
[https://wiki.ubuntu.com/Repositories/Ubuntu?action=show&redirect=AddingRepositoriesHowto](https://wiki.ubuntu.com/Repositories/Ubuntu?action=show&redirect=AddingRepositoriesHowto)

---

### Post by SuperCow on 2006-06-18
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/rt.jar': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on sun-java5-bin (= 1.5.0-06-1) | ia32-sun-java5-bin (= 1.5.0-06-1); however:
  Package sun-java5-bin is not installed.
  Package ia32-sun-java5-bin is not installed.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-jre
Errors!

---

### Post by meng on 2006-06-18
So you're going to try something different than advised? That's cool. If you want to do it your way, download .deb files for sun-java5-bin and ia32-sun-java5-bin and then install them (but they may have other dependencies also). Otherwise, if you want to go with the advice given in this thread, you could try using synaptic or apt-get.

---

### Post by beameup on 2006-06-19
I used Add/Remove to add it.

---

