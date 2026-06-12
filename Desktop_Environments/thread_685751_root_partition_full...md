---
title: "root partition full..?"
date: 2008-02-02
forum: Desktop Environments
---

### Post by machs_fuel42 on 2008-02-02
I recently added a drive to my md0 array, which required me to compile a newer kernel (i end up using 2.6.17.14) so i could resize the array. after ~10 hrs of mdadm reshaping the array it finished; but now i have 100% disk usage on my / partition.  

gnome doesn't like to work when you've got 100% usage on / so     I read a handful of posts which instructed me to removed some older kernels ( i had 4), as well as preforming the apt-get autoclean and apt-get clean tricks.    

I'm down to 95% usage on / but can't help but suspect my recent fooling about has caused something to go awry. 

df -h looks like this
```
machs@electric-monk:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.9G  8.9G  530M  95% /
varrun                506M  164K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  160K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda5              55G   33G   20G  63% /media/download
/dev/md0              895G  452G  444G  51% /media/vector_sigma
/dev/hda1             9.9G  7.6G  1.9G  81% /home

```

```
machs@electric-monk:/$ sudo du --max-depth=1 -h
48K     ./lost+found
1.1G    ./var
484G    ./media
17M     ./etc
4.4M    ./bin
18M     ./boot
176K    ./dev
7.4G    ./home
4.0K    ./initrd
153M    ./lib
12K     ./mnt
74M     ./opt
du: `./proc/6102/task': No such file or directory
du: `./proc/6102/fd': No such file or directory
901M    ./proc
2.6M    ./root
10M     ./sbin
4.0K    ./srv
0       ./sys
68K     ./tmp
4.0G    ./usr
497G    .

```

from du you can see that /proc /usr and /var are looking pretty heavy.  (/home is on a separate partition)

i checked out /var; i've got an dapper installation iso in there for pxe booting so that explains most of that bulk.

/proc is mostly empty except a 900Meg file call kcore, from a quick google search thats normal

I don't know to much about /usr... 
here is what du tells me; 

```
machs@electric-monk:~$ sudo du /usr --max-depth=1 -h
16K     /usr/X11R6
232M    /usr/bin
136M    /usr/games
32M     /usr/include
1.4G    /usr/lib
5.7M    /usr/local
30M     /usr/sbin
1.5G    /usr/share
812M    /usr/src
52K     /usr/etc
76K     /usr/lib64
2.9M    /usr/avr
5.2M    /usr/libexec
4.0G    /usr

```

does any of this look out of place (ie bigger then normal)? or is my install just bloated?

---

### Post by Andrew Stone on 2008-02-07
here is mine (upgraded less then 2 weeks ago, so its pretty clean) for comparison:
40K     /usr/X11R6
12M     /usr/sbin
1.7M    /usr/local
1.1G    /usr/share
54M     /usr/games
63M     /usr/src
1.2G    /usr/lib
119M    /usr/bin
19M     /usr/include
94M     /usr/lib32
2.6G    /usr

---

