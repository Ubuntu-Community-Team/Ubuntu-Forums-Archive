---
title: "CLI cp does not"
date: 2009-03-14
forum: General Help
---

### Post by theocl on 2009-03-14
I'm attempting to copy a file (alsa-base) which is an edited copy of the original from my home directory to the original directory (/etc/modprobe.d) where I have deleted the original file. AFAIK, permissions are OK, and I've tried using the -u option as well. It doesn't copy.
What am I not understanding or doing wrong?!
Thanks.

---

### Post by Dr Small on 2009-03-14
Permission problem?
Try using sudo:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2009-03-14
What command did you use to copy alsa-base from your $HOME to /etc/modprobe.d?

```
sudo cp alsa-base /etc/modprobe.d
ls -la /etc/modprobe.d
```

---

### Post by heindsight on 2009-03-14
As a normal user, you don't have permission to write to /etc/modprobe.d
Use sudo to temporarily get root privileges to write the file to /etc/modprobe.d:
```
sudo cp alsa-base /etc/modprobe.d
```
You'll be asked to enter your password. After you enter your password, the file will be copied.

---

### Post by theocl on 2009-03-14
Thanks for your responses all, but as indicated permissions are OK (set 777 on directories and file to be sure) and used sudo with the command as shown in your responses. The ls -la shows nothing?!
Any other thoughts (I hope)?!

---

### Post by taurus on 2009-03-14
What do you mean it shows nothing?  Type this in and post the whole output here then.

```
ls -la /etc/modprobe.d
```

---

### Post by theocl on 2009-03-14
Taurus - here it is:
theo@theo-desktop:/etc/modprobe.d$ ls -la
total 80
drwxr-xr-x   3 root root  4096 2009-03-13 18:58 .
drwxr-xr-x 118 root root 12288 2009-03-14 14:00 ..
-rw-r--r--   1 root root  4624 2007-10-05 09:41 aliases
drwxr-xr-x   2 root root  4096 2009-03-12 22:39 arch
lrwxrwxrwx   1 root root     9 2009-03-12 22:39 arch-aliases -> arch/i386
-rw-r--r--   1 root root   980 2008-10-06 05:51 blacklist
-rw-r--r--   1 root root   628 2007-10-05 09:41 blacklist-framebuffer
-rw-r--r--   1 root root   156 2007-10-05 07:06 blacklist-modem
lrwxrwxrwx   1 root root    41 2009-03-12 22:40 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root    38 2007-10-05 08:26 blacklist-scanner
-rw-r--r--   1 root root   838 2007-10-05 09:41 blacklist-watchdog
-rw-r--r--   1 root root   343 2007-09-18 17:01 fuse
-rw-r--r--   1 root root   205 2007-10-15 04:41 ipw3945
-rw-r--r--   1 root root   299 2007-10-05 09:41 isapnp
-rw-r--r--   1 root root    38 2008-03-25 10:31 libsane
-rw-r--r--   1 root root   294 2007-10-15 04:41 lrm-video
-rw-r--r--   1 root root    29 2006-10-09 06:33 nvidia-kernel-nkc
-rw-r--r--   1 root root   173 2007-10-05 09:41 options
-rw-r--r--   1 root root    41 2007-09-19 02:50 toshiba_acpi.modprobe

---

### Post by theocl on 2009-03-14
Further on the file list, I've changed the permissions back to original. I did check that they were changed to 777 before attempting the copy.

---

### Post by taurus on 2009-03-14
> **theocl said:**
> Thanks for your responses all, but as indicated permissions are OK (set 777 on directories and file to be sure) and used sudo with the command as shown in your responses. The ls -la shows nothing?!
Any other thoughts (I hope)?!

> **theocl said:**
> Taurus - here it is:
theo@theo-desktop:/etc/modprobe.d$ ls -la
total 80
drwxr-xr-x   3 root root  4096 2009-03-13 18:58 .
drwxr-xr-x 118 root root 12288 2009-03-14 14:00 ..
-rw-r--r--   1 root root  4624 2007-10-05 09:41 aliases
drwxr-xr-x   2 root root  4096 2009-03-12 22:39 arch
lrwxrwxrwx   1 root root     9 2009-03-12 22:39 arch-aliases -> arch/i386
-rw-r--r--   1 root root   980 2008-10-06 05:51 blacklist
-rw-r--r--   1 root root   628 2007-10-05 09:41 blacklist-framebuffer
-rw-r--r--   1 root root   156 2007-10-05 07:06 blacklist-modem
lrwxrwxrwx   1 root root    41 2009-03-12 22:40 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root    38 2007-10-05 08:26 blacklist-scanner
-rw-r--r--   1 root root   838 2007-10-05 09:41 blacklist-watchdog
-rw-r--r--   1 root root   343 2007-09-18 17:01 fuse
-rw-r--r--   1 root root   205 2007-10-15 04:41 ipw3945
-rw-r--r--   1 root root   299 2007-10-05 09:41 isapnp
-rw-r--r--   1 root root    38 2008-03-25 10:31 libsane
-rw-r--r--   1 root root   294 2007-10-15 04:41 lrm-video
-rw-r--r--   1 root root    29 2006-10-09 06:33 nvidia-kernel-nkc
-rw-r--r--   1 root root   173 2007-10-05 09:41 options
-rw-r--r--   1 root root    41 2007-09-19 02:50 toshiba_acpi.modprobe

There is something in there, not empty.  

Where is your alsa-base?  Is it on $HOME or $HOME/Desktop?

```
find ~ -name alsa-base -print
```

---

### Post by theocl on 2009-03-14
I'll be more accurate with terms - sorry.
Here's alsa-base locations:
theo@theo-desktop:/etc/modprobe.d$ find ~ -name alsa-base -print
/home/theo/alsa-base
/home/theo/SoundCard/alsa-base

The one in /home/theo is the copy of the original, the other is the edited copy which includes options for SB AWE and 16 cards.

Not to get off track but so you know the issue, I was trying to get the card working with a SB 16 card (and did temporarily - it did not after a reboot). I also get error "Could not open location; you might not have permission to open the file." from Totem Movie Player 2.22.1 attempting to play a CD on this system.

---

### Post by taurus on 2009-03-14
Do you want to copy the ~/SoundCard/alsa-base to /etc/modprobe.d?

```
sudo cp ~/SoundCard/alsa-base /etc/modprobe.d
ls -la /etc/modprobe.d
```

---

### Post by theocl on 2009-03-14
Yes, that's the command I used (sudo cp alsa-base /etc/mprobe.d), but from /home/theo/SoundCard and not using the "~".
I've tried your command and it works, Thank You! Here's the output from ls:

theo@theo-desktop:/$ ls -la /etc/modprobe.d
total 84
drwxr-xr-x   3 root root  4096 2009-03-14 19:19 .
drwxr-xr-x 118 root root 12288 2009-03-14 14:00 ..
-rw-r--r--   1 root root  4624 2007-10-05 09:41 aliases
-rw-r--r--   1 root root  2375 2009-03-14 19:19 alsa-base
drwxr-xr-x   2 root root  4096 2009-03-12 22:39 arch
lrwxrwxrwx   1 root root     9 2009-03-12 22:39 arch-aliases -> arch/i386
-rw-r--r--   1 root root   980 2008-10-06 05:51 blacklist
-rw-r--r--   1 root root   628 2007-10-05 09:41 blacklist-framebuffer
-rw-r--r--   1 root root   156 2007-10-05 07:06 blacklist-modem
lrwxrwxrwx   1 root root    41 2009-03-12 22:40 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root    38 2007-10-05 08:26 blacklist-scanner
-rw-r--r--   1 root root   838 2007-10-05 09:41 blacklist-watchdog
-rw-r--r--   1 root root   343 2007-09-18 17:01 fuse
-rw-r--r--   1 root root   205 2007-10-15 04:41 ipw3945
-rw-r--r--   1 root root   299 2007-10-05 09:41 isapnp
-rw-r--r--   1 root root    38 2008-03-25 10:31 libsane
-rw-r--r--   1 root root   294 2007-10-15 04:41 lrm-video
-rw-r--r--   1 root root    29 2006-10-09 06:33 nvidia-kernel-nkc
-rw-r--r--   1 root root   173 2007-10-05 09:41 options
-rw-r--r--   1 root root    41 2007-09-19 02:50 toshiba_acpi.modprobe

I'm obviously not using proper command syntax / procedure. Is there a reference you might suggest to help me to learn it?

Again, thanks very much. I'll search the forum on the other issues in case it's already addressed there.

---

### Post by taurus on 2009-03-14
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by heindsight on 2009-03-15
> **theocl said:**
> Thanks for your responses all, but as indicated permissions are OK (set 777 on directories and file to be sure) and used sudo with the command as shown in your responses. The ls -la shows nothing?!
Any other thoughts (I hope)?!

I just thought I should mention, setting the permissions on any directory to 777 (especially important system directories --- like anything under /etc) is definitely a very bad idea. 

There's a very good reason why only root is allowed to write to those directories (otherwise *anyone* can delete or modify important files and break your system). If you need to create or edit files in directories which only root can write in, then use sudo to create or edit the file, don't just change the directory permissions.

---

