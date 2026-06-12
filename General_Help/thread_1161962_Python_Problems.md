---
title: "Python Problems"
date: 2009-05-17
forum: General Help
---

### Post by guiclaw on 2009-05-17
Hey guys,

I've tried googling for the solution to this problem for a good couple of hours now, and i'm at a loose end...

Basically I've got a standard Ubuntu 8.10 (I think - the one thing i've never been able to work out is how to find out which dist i'm currently running!), and I've been running into problems now with python.

Basically, I noticed it when I tried to run mail:

```
peter@server:~$ mail
Fatal Python error: Can't initialize 'type'
Aborted

```

So then I try to run Python:
```
peter@server:~$ python
Fatal Python error: Can't initialize 'type'
Aborted

```

Also trying to run python in verbose mode fails:
```
peter@server:~$ python -v
Fatal Python error: Can't initialize 'type'
Aborted
```

There are similar issues to this on the web, however no problems with this exact message? I thought about reinstalling python - however the apt-get list for remove was massive so I didn't touch that - plus the machine is actually running as a server at my house (I'm at university) and it's going to be a month before I can get physical access to it, so I can't really go breaking my network access!

I hope someone's come across this issue before/can help me fix it!

---

### Post by geirha on 2009-05-17
The following will show what Ubuntu you are running ```
lsb_release -a
```

It does sound like there might be some file missing from the python package, and a reinstall of the python package would be the first thing I'd try. Though, you don't need to remove the package and install it again.

First off, figure out which python versions you have installed:
```
aptitude search '~i ^python[0-9.]+$'
```

Then reinstall each of those packages. If you have python2.6 for instance, do
```
sudo aptitude reinstall python2.6
```

---

### Post by guiclaw on 2009-05-17
Thanks for the quick reply.

Ironically, running lsb_release gives:
```
peter@server:~$ lsb_release -a
Fatal Python error: Can't initialize 'type'
Aborted
```

So I reinstall:
```
peter@server:~$ aptitude search '~i ^python[0-9.]+$'
i   python2.5                            - An interactive high-level object-oriented langu
peter@server:~$ sudo aptitude reinstall python2.5
The following packages will be REINSTALLED:
  python2.5 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 58 not upgraded.
Need to get 3018kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com hardy-updates/main python2.5 2.5.2-2ubuntu4.1 [3018kB]
Fetched 3018kB in 1s (2199kB/s)     
(Reading database ... 149534 files and directories currently installed.)
Preparing to replace python2.5 2.5.2-2ubuntu4.1 (using .../python2.5_2.5.2-2ubuntu4.1_amd64.deb) ...
Unpacking replacement python2.5 ...
Setting up python2.5 (2.5.2-2ubuntu4.1) ...
Fatal Python error: Can't initialize 'type'
Aborted

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
peter@server:~$ mail
Fatal Python error: Can't initialize 'type'
Aborted

```

It seems like something more serious is wrong here :(

---

### Post by geirha on 2009-05-17
Hehe, didn't know lsb_release was a python app. Try with
```
cat /etc/lsb-release
```

Tried to search for that error, and this came up. [http://www.nongnu.org/failmalloc/](http://www.nongnu.org/failmalloc/)

In the examples on that page, python gives that error message when it is fooled to think there is no more memory to be allocated. So it seems malloc is failing for some reason. I assume you have enough memory available? ```
free -m
```

I think a memtest would be in order, but unfortunately, you'll need physical access for that :/

---

### Post by guiclaw on 2009-05-17
Yeah I found that page, but I'm quite sure that the memory isn't bad - the server has been operational without hardware modifications for several months. I can get someone to select memtest on the grub boot screen - I have someone who can do that, just not re-install anything or fix the network.

```
peter@server:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

```

The memory situation:
```
peter@server:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3276       1446       1830          0        293        700
-/+ buffers/cache:        452       2824
Swap:         3153          0       3153

```

---

### Post by geirha on 2009-05-17
Plenty of memory, indeed. The swap partition is unused though. It usually uses a little bit of the swap even though you have plenty of physical RAM available. Try temporarily turning off the swap and see if there's any change.
```

swapon -s    # This will list all swap partitions currently in use.

# Supply the next command with the filename listed in the first column. For instance, if it is /dev/sda5
sudo swapoff /dev/sda5

```

To turn it back on, run ```
sudo swapon -a
```

This is really beyond the scope of my knowledge, so it's all guesswork here. I'm afraid I don't have any other suggestions, or any idea of why python is failing like that :/

---

### Post by guiclaw on 2009-05-17
I've just tried disabling the swap like you suggested and there's been no change...

I've been tailing my syslog for quite a while, and i'm getting this error every 10 minutes:
```
May 17 14:43:49 server sm-mta[26596]: n4HArnkk023229: Warning: program /usr/sbin/sensible-mda unsafe: No such file or directory
May 17 14:43:49 server sm-mta[26596]: n4HArnkk023229: SYSERR(root): Cannot exec /usr/sbin/sensible-mda: No such file or directory
May 17 14:43:49 server sm-mta[26595]: n4HArnkk023229: to=peter, delay=02:50:00, xdelay=00:00:00, mailer=local, pri=1560000, dsn=4.0.0, stat=Operating system error
May 17 14:43:49 server sm-mta[26597]: n4H6nmsw018794: Warning: program /usr/sbin/sensible-mda unsafe: No such file or directory
May 17 14:43:49 server sm-mta[26597]: n4H6nmsw018794: SYSERR(root): Cannot exec /usr/sbin/sensible-mda: No such file or directory
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794: SYSERR(root): putbody: write error: Broken pipe
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   0: fl=0x8000, mode=20666: CHR: dev=0/14, ino=7147, nlink=1, u/gid=0/0, size=0
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   1: fl=0x8001, mode=20666: CHR: dev=0/14, ino=7147, nlink=1, u/gid=0/0, size=0
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   2: fl=0x8001, mode=20666: CHR: dev=0/14, ino=7147, nlink=1, u/gid=0/0, size=0
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   3: fl=0x2, mode=140777: SOCK localhost->[[UNIX: /dev/log]]
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   4: fl=0x8002, mode=100640: dev=8/81, ino=500644, nlink=1, u/gid=0/127, size=1000
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   5: fl=0x8000, mode=100640: dev=8/81, ino=500687, nlink=1, u/gid=0/127, size=160
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   6: fl=0x8000, mode=100640: dev=8/81, ino=500544, nlink=1, u/gid=113/127, size=12288
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   7: fl=0x8000, mode=100640: dev=8/81, ino=500544, nlink=1, u/gid=113/127, size=12288
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:   9: fl=0x1, mode=10600: FIFO: dev=0/5, ino=79909, nlink=1, u/gid=0/127, size=0
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794:  10: fl=0x0, mode=10600: FIFO: dev=0/5, ino=79910, nlink=1, u/gid=0/127, size=0
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794: MCI@0x0: NULL
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794: MCI@0x0: NULL
May 17 14:43:49 server sm-mta[26595]: n4H6nmsw018794: to=peter, ctladdr=<root@*****hostnameremoved******> (0/0), delay=06:54:01, xdelay=00:00:00, mailer=local, pri=3810784, dsn=4.0.0, stat=Operating system error
May 17 14:43:49 server sm-mta[26598]: n4GDxBFc003301: Warning: program /usr/sbin/sensible-mda unsafe: No such file or directory
May 17 14:43:49 server sm-mta[26598]: n4GDxBFc003301: SYSERR(root): Cannot exec /usr/sbin/sensible-mda: No such file or directory
May 17 14:43:49 server sm-mta[26595]: n4GDxBFc003301: to=peter, delay=23:44:36, xdelay=00:00:00, mailer=local, pri=12814426, dsn=4.0.0, stat=Operating system error
```

And there are various other issues that have arisin, such as starting apache2 fails with a SEGFAULT.

I'm not sure if all these are linked however - i'm assuming that sm-mta is something to do with sendmail which I have recently installed..

And also there was a random lockup on the server which I've traced back to smbd crashing during a client connection - however this was in the middle of these problems so I'm not too sure that this crash is linked to anything.

---

### Post by guiclaw on 2009-05-17
Right I've managed to fix my problem.

Basically I got tired of python so I did whereis python and rm -rf'd everything I found.. Drastic I know and yes it borked loads of stuff. Then I did a combination of apt-get remove, dpkg and all sorts forced to remove anything python related.

I tried to compile from source different versions of python, but ubuntu still complained.. so then I had a brainwave.

I installed a new version of 8.04 onto the VMWare server the box is running, and then SCP'd everything with python in the name from that install over, and voila! Everything is running perfectly now! It's even fixed apache (so that must of had some python dependancies???)

Thanks for the help anyway.. though I wouldn't recommend anyone else trying to just force remove python - especially not on ubuntu!

---

### Post by geirha on 2009-05-18
I had strongly recommended against "rm -rf"-ing wildly like that. Very creative and clever way of fixing it again though. You sure got computer skills :)

---

