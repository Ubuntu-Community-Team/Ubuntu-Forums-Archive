---
title: "Urgent Help"
date: 2006-07-07
forum: Desktop Environments
---

### Post by mishranurag on 2006-07-07
Hi!

I cannot login to my system now.It's extremely frustrating. I have tried to get help in this thread 

[http://ubuntuforums.org/showthread.php?t=210164](http://ubuntuforums.org/showthread.php?t=210164)

Basically, the my KUBUNTU is not letting me login and throwing the following error  "XSession: warning: unable to write to /tmp. Xsession may exit with an error". I have cleaned the /tmp cirectory by logging into terminal. 

Please help as I cannot access my system.

Regards,
Anurag

---

### Post by Ctrl+Alt+Del on 2006-07-07
try 'apt-get clean' and/or the output of df -h

---

### Post by mishranurag on 2006-07-07
Thanks a lot, it did work. I realized I am using about 97% of my root partition, although I have a partition of 8 Gb. How can I find out useless stuff in it and delete it? How can I make sure that it doesn't happen again?

Thanks
Anurag

---

### Post by [S|G] on 2006-07-07
Use adept to uninstall packages you do not use/need

---

### Post by mishranurag on 2006-07-07
Yes, I can do that, but still 8 Gb? Isn't it too much? I thought UBUNTU is pretty light. I haven't installed any obscene amount of softwares.

---

### Post by llamakc on 2006-07-07
In a terminal:

cd /

sudo du -h --max-depth=1

In that output you'll see which toplevel directories have the most stuff.

Here's mine:

```

ken@dothan:/$ sudo du -h --max-depth=1
Password:
48K     ./lost+found
32G     ./home
15M     ./etc
12K     ./media
787M    ./var
266M    ./lib
1.8G    ./usr
4.2M    ./bin
27M     ./boot
228K    ./dev
4.0K    ./mnt
899M    ./proc
1.7M    ./root
8.7M    ./sbin
56K     ./tmp
0       ./sys
4.0K    ./srv
4.0K    ./opt
4.0K    ./initrd
36G     .

```

So minus my absurdly large /home directory (which is on a diff. partition anyways) of 32G I have about 4G of stuff installed with almost two G in /usr. 

If your /home directory is on the same partition don't forget to remove stuff from ~/.Trash to free up space also.

---

### Post by mishranurag on 2006-07-08
This is the result of 
sudo du -h --max-depth=1

48K     ./lost+found
4.7G    ./var
3.8G    ./home
222G    ./media
13M     ./etc
4.4M    ./bin
19M     ./boot
136K    ./dev
4.0K    ./initrd
188M    ./lib
4.0K    ./mnt
79M     ./opt
899M    ./proc
4.1M    ./root
11M     ./sbin
4.0K    ./srv
0       ./sys
88K     ./tmp
2.1G    ./usr
80K     ./.bzr
234G    .

My /home is mounted on a 30 G partition.
/media contains other partitions as well. My /var and /usr are eating too much space. But isn't it bad?? Shouldn't UBUNTU be light?

Anurag

---

### Post by RAOF on 2006-07-08
The /var looks suspiciously large.  Check out /var/log - I had a similar problem where mythtv would continually write to its logfile until the entire partition was full.  4gb logfiles aren't good :)

Also, it looks strange that your entire filesystem is a bzr repository (the /.bzr directory) :)

---

### Post by mishranurag on 2006-07-08
Thanks for the hint. My following folder is 4.5Gb big.
/var/tmp/kdecache-anmishra/krun

It is due to couple of very big movie files I was trying to unzip and it temporarilly stored at this folder. Now my ./var is less than 120 M.

Thanks for help.
Anurag

---

### Post by mishranurag on 2006-07-17
A related question. How can I configure rar to open compressed file in some folder rather than /temp ??
Thanks
Anurag

---

