---
title: "Lame encoder ?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-17
Hi I am using audacity and I am trying to export as mp3 and it tells me i need the LAME encoder and I looked on the audacity website and I am unable to find a linux version of LAME.  Can someone tell me where I can get it so I can export a file as MP3?

Thanks

---

### Post by mgor on 2006-08-17
make sure you have the multiverse repos in /etc/apt/sources.list,
```
deb http://se.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper multiverse
```

```
apt-get update
apt-get install liblame0
```

---

### Post by Magiczero on 2006-08-17
I ran that stuff and I get this

tanner@ubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
tanner@ubuntu:~$ gedit source.list
apt-get update
...
apt-cache search liblame
apt-cache search liblame
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
tanner@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
tanner@ubuntu:~$ ...
bash: ...: command not found
tanner@ubuntu:~$ apt-cache search liblame
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
tanner@ubuntu:~$ apt-cache search liblame
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
tanner@ubuntu:~$ liblame-dev - LAME Ain't an MP3 Encoder
> liblame0 - LAME Ain't an MP3 Encoder
bash: liblame-dev: command not found
tanner@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
tanner@ubuntu:~$ ...
bash: ...: command not found
tanner@ubuntu:~$ apt-cache search liblame
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
tanner@ubuntu:~$ apt-cache search liblame
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder
tanner@ubuntu:~$ liblame-dev - LAME Ain't an MP3 Encoder
> liblame0 - LAME Ain't an MP3 Encoder
bash: liblame-dev: command not found
tanner@ubuntu:~$
What now?

---

### Post by ajgreeny on 2006-08-17
You need to edit the sources.list file as root, so either open synaptic as usual (using your password, so as root by default) and then go to settings>repositories where you can chose to enable universe and multiverse repos.  All should then work either in *synaptic,* *aptitude* or using [I]sudo apt-get.

[/I]You can also edit sources.list by typin in a terminal:-
gksudo gedit /etc/apt/sources.list
and then editing manually.

---

