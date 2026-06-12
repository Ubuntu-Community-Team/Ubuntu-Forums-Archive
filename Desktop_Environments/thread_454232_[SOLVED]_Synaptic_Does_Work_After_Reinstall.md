---
title: "[SOLVED] Synaptic Does Work After Reinstall"
date: 2007-05-25
forum: Desktop Environments
---

### Post by Falcorian on 2007-05-25
I reinstalled Feisty today, and my Synaptic hasn't worked since. I get this error:

```
E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)
```

Now, this error has been discussed on the forum before, but the solutions I've found are to:

```
mkdir /root
etc.. (More stuff here)
```

My problem is, /root exists, but when I do:

```
file /root
/root: broken symbolic link to `libedata-cal-1.2.so.6.0.1'
```


Anyone know what to do? Reinstalling synaptic didn't help, so I'm not sure what to do.

---

### Post by dbott67 on 2007-05-25
Can you post the output of ls -all from the /root directory:
```
dbott@feisty:/root$ [COLOR=Red]**ls -all**[/COLOR]
total 104
drwxr-xr-x 17 root root  4096 2007-05-10 10:43 .
drwxr-xr-x 21 root root  4096 2007-04-22 15:04 ..
-rw-------  1 root root   419 2007-05-13 15:33 .bash_history
-rw-r--r--  1 root root  2227 2006-12-20 10:50 .bashrc
drwx------  3 root root  4096 2007-04-23 23:30 .config
-rw-------  1 root root    33 2007-04-22 16:31 .credentials
drwxr-xr-x  2 root root  4096 2007-04-23 19:30 Desktop
-rw-------  1 root root    16 2007-04-22 15:49 .esd_auth
drwx------  3 root root  4096 2007-05-21 16:29 .gconf
drwx------  2 root root  4096 2007-05-21 16:29 .gconfd
drwxr-xr-x  3 root root  4096 2007-04-23 20:11 .gnome
drwx------  5 root root  4096 2007-05-14 15:24 .gnome2
drwx------  2 root root  4096 2007-04-22 15:49 .gnome2_private
drwx------  2 root root  4096 2007-04-22 15:35 .gnupg
drwx------  3 root root  4096 2007-04-22 21:08 .kde
drwxr-xr-x  3 root root  4096 2007-04-23 19:30 .nautilus
-rw-r--r--  1 root root   141 2006-12-20 10:50 .profile
-rw-r--r--  1 root root 14623 2007-05-10 10:43 .recently-used.xbel
drwx------  2 root root  4096 2007-04-22 21:10 .ssh
drwx------  3 root root  4096 2007-05-21 16:29 .synaptic
drwx------  4 root root  4096 2007-04-23 19:31 .thumbnails
drwxr-xr-x  2 root root  4096 2007-04-22 15:06 .wapi
drwxr-xr-x  2 root root  4096 2007-04-23 19:31 .xine

```Have you tried re-installing libedata... :
```
dbott@feisty:/root$ [COLOR=Red]**sudo apt-cache search libedata**[/COLOR]
Password:
libedata-book1.2-2 - Backend library for evolution address books
libedata-book1.2-dev - Backend library for evolution address books (development files)
[COLOR=Red]libedata-cal1.2-6 - Backend library for evolution calendars[/COLOR]
libedata-cal1.2-dev - Backend library for evolution calendars (development files)
libedataserver1.2-9 - Utility library for evolution data servers
libedataserver1.2-dev - Utility library for evolution data servers (development files)
libedataserverui1.2-8 - GUI utility library for evolution data servers
libedataserverui1.2-dev - GUI utility library for evolution data servers (development files)
```
```
sudo apt-get install libedata-cal1.2-6
```

Is this what you tried when re-creating /root?:
> **vijirajan said:**
> Create the root directory first before creating .synaptic like below:

sudo mkdir /root
sudo mkdir /root/.synaptic

-Dave

---

### Post by Falcorian on 2007-05-25
```
ls -all /root
lrwxrwxrwx 1 root root 25 2007-05-24 11:46 /root -> libedata-cal-1.2.so.6.0.1

```

```
agude@newton:~$ sudo apt-get install libedata-cal1.2-6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libedata-cal1.2-6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

And yes, that was the advice I had found and tried. But since /root exists (but seems horribly messed up), it didn't work. ;) Thanks for helping so quickly though! I'm impressed.

---

### Post by dbott67 on 2007-05-25
Something does seem wrong; my /root directory has lots more stuff.

Try this:
```
sudo mkdir /root/.synaptic
```

Then post the output of:
```
dbott@feisty:/root$ ls -all
total 104
drwxr-xr-x 17 root root  4096 2007-05-10 10:43 .
drwxr-xr-x 21 root root  4096 2007-04-22 15:04 ..
-rw-------  1 root root   419 2007-05-13 15:33 .bash_history
-rw-r--r--  1 root root  2227 2006-12-20 10:50 .bashrc
drwx------  3 root root  4096 2007-04-23 23:30 .config
-rw-------  1 root root    33 2007-04-22 16:31 .credentials
drwxr-xr-x  2 root root  4096 2007-04-23 19:30 Desktop
-rw-------  1 root root    16 2007-04-22 15:49 .esd_auth
drwx------  3 root root  4096 2007-05-21 16:29 .gconf
drwx------  2 root root  4096 2007-05-21 16:29 .gconfd
drwxr-xr-x  3 root root  4096 2007-04-23 20:11 .gnome
drwx------  5 root root  4096 2007-05-14 15:24 .gnome2
drwx------  2 root root  4096 2007-04-22 15:49 .gnome2_private
drwx------  2 root root  4096 2007-04-22 15:35 .gnupg
drwx------  3 root root  4096 2007-04-22 21:08 .kde
drwxr-xr-x  3 root root  4096 2007-04-23 19:30 .nautilus
-rw-r--r--  1 root root   141 2006-12-20 10:50 .profile
-rw-r--r--  1 root root 14623 2007-05-10 10:43 .recently-used.xbel
drwx------  2 root root  4096 2007-04-22 21:10 .ssh
[COLOR=Red]drwx------  3 root root  4096 2007-05-21 16:29 .synaptic[/COLOR]
drwx------  4 root root  4096 2007-04-23 19:31 .thumbnails
drwxr-xr-x  2 root root  4096 2007-04-22 15:06 .wapi
drwxr-xr-x  2 root root  4096 2007-04-23 19:31 .xine

```

---

### Post by Soybean on 2007-05-25
That's not a root directory... it's a link to a .so file. For some reason. That's pretty weird. You say this is a fresh install?

Anyway, I'd delete it. Then follow the instructions to create /root and /root/.synaptic again.

---

### Post by Falcorian on 2007-05-25
> **dbott67 said:**
> Something does seem wrong; my /root directory has lots more stuff.

Try this:
```
sudo mkdir /root/.synaptic
```


```
~$ sudo mkdir /root/.synaptic
mkdir: cannot create directory `/root/.synaptic': No such file or directory

```

:( However, once I removed the folder I was able to create it and it now works... But...

> **Soybean said:**
> That's not a root directory... it's a link to a .so file. For some reason. That's pretty weird. You say this is a fresh install?

Yeah... Although one of my partitions was slightly odd when I installed. The partition with /home on it had a bunch of errors about it's size not being reported correctly or some other. I don't seem to have a log of it, but running fsck fixed it.


> **Soybean said:**
> Anyway, I'd delete it. Then follow the instructions to create /root and /root/.synaptic again.

That fixed it. I'm a little wary though, as it looks like my /root is odd. While the symptom is now gone, I'm not sure the cause of the problem is. Thanks though.

---

### Post by Soybean on 2007-05-25
> **Falcorian said:**
> That fixed it. I'm a little wary though, as it looks like my /root is odd.
I agree. I'd be wary too. You might want to consider reinstalling, now that you've fixed your home partition, to see if it happens again. Even if it does, though, at least you know how to fix it now, right?

My guess (and this is, admittedly, just a wild guess) is that it's just that the install scripts didn't handle that flaky partition very well. Maybe one script sets up the /home and /root directories, and when something went wrong in /home, it just stopped trying and never got around to doing /root. Then some other script wasn't at all prepared to deal with a missing /root, so it just went nuts and did something completely insane. ;)

If I'm right, you should be ok just leaving it, but some things might not be installed quite right. A reinstall would fix it. If I'm wrong... well, a reinstall rarely hurts anything. :)

---

### Post by Falcorian on 2007-05-25
I'm wary of reinstalling as well, since my optical drive is dying, and may very well be the source of the first error... I never know once I've nuked my system if I can actaully get an OS reinstalled, or if the drive is finally going to say "Nope, not reading anything ever again". ;) So as long as nothing else seems wrong, I'm going to give keeping it a shot.


As an interesting note:

```
/root$ ls -alh
total 28K
drwxr-xr-x  7 root root 4.0K 2007-05-25 07:55 .
drwxr-xr-x 22 root root 4.0K 2007-05-25 07:53 ..
drwx------  2 root root 4.0K 2007-05-25 12:32 .gconf
drwx------  2 root root 4.0K 2007-05-25 12:32 .gconfd
drwx------  3 root root 4.0K 2007-05-25 07:55 .gnome2
drwx------  2 root root 4.0K 2007-05-25 07:55 .gnome2_private
drwx------ 3 root root 4.0K 2007-05-25 07:55 .synaptic

```

It seems to be... Rebuilding itself. ;) Maybe a start up script checks to makesure certain files exist...

---

