---
title: "Run program in  console at startup"
date: 2011-03-28
forum: Desktop Environments
---

### Post by sakishrist on 2011-03-28
Hello,

I would like to know whether there is a way of running a console program at startup. That means even before user login. My guess was that it would have to be run like a service but this idea comes from my ... "windows" experience.

Thanks a lot!

---

### Post by hictio on 2011-03-28
The "down and dirty" way would be to add the full path to the script (and make sure the script is executable) to the file "/etc/rc.local".

---

### Post by sakishrist on 2011-03-28
Thanks a lot, but just so that I know: "down and dirty" ... does that mean that there is a better way?

EDIT: Also, could you please explain some things from the comments of that file that I do not understand?

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each [COLOR=Red]multiuser runlevel[/COLOR].
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the [COLOR=Red]execution[/COLOR]
# [COLOR=Red]bits[/COLOR].
#
# By default this script [COLOR=Black]does nothing[/COLOR].

I do not know what the [COLOR=Black]multiuser runlevel is. I have never heard of it.
  
Is the execution bit the checkbox in the properties -> permissions tab?
  
Thanks a million!
[/COLOR]

---

### Post by hictio on 2011-03-28
Sorry for the delay.
By down and dirty I mean that it is a trick that will work out of the box, as long as the script you are invoking is executable, that is the script will be invoked, it is up to the script to run properly, etc.
You can write another type of script and create a service, but it is more complex.

Yes, you set the script as executable by ticking the check box.

Make sure you add the full path to the script when you add the entry on the '/etc/rc.local' file, and that you place your line above the "EXIT 0" line.
Multiuser runlevel is the default runlevel on an Ubuntu Desktop box, that is multiuser (any user can login to the system) and with networking enabled.
If I might, what does that script do?

---

### Post by sakishrist on 2011-03-29
Thanks a lot!

Where I live, powercuts are quite common. Plus, I have to travel quite a lot so there is noone to turn it on the PC, login and run the programs needed. I configured it to automaticaly turn on after a powercut but I still had the problem of getting my programs to run. All of them are programs that do not have a gui so I could just run them through the console. 

The programs are utorrent for linux and real vnc.

EDIT: By the way, are the scripts/programs ran as root?

---

### Post by sakishrist on 2011-03-29
I have a problem now and I do not know what the cause is. 

I tried to run utorrent and it seems the script hang there until utorrent exits. I then tried the folowing:

```
mkdir /media/DATA
mount -t ntfs -o umask=0222 /dev/sda2 /media/DATA

exec /home/sakishrist/Downloads/utorrent-server-v3_0/utserver

vncserver

exit 0
```I used exec because that seems to run the program as a different proccess (?) and continue with the rest of the script. 

Well this time the script did nothing at all. Not even the mount.


EDIT:

```
cd /home/sakishrist
mkdir /media/DATA > startup.log
mount -t ntfs -o umask=0222 /dev/sda2 /media/DATA >> startup.log

exec /home/sakishrist/Downloads/utorrent-server-v3_0/utserver >> startup.log

vncserver >> startup.log

exit 0
```
There was no output to the log file either. I have to be doing something teribly wrong here. :confused:

Thanks in advance.

---

### Post by sakishrist on 2011-03-30
Anybody, Please!

---

