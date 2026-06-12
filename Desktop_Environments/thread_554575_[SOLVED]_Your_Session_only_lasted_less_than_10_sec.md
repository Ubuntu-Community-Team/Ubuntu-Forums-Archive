---
title: "[SOLVED] Your Session only lasted less than 10 seconds..."
date: 2007-09-19
forum: Desktop Environments
---

### Post by MotHaiBa on 2007-09-19
Hi all, 

I received this error a few weeks ago and managed to fix it using the command 'sudo apt-get clean' posted by Aysiu.

[http://ubuntuforums.org/showthread.p...ted+10+seconds](http://ubuntuforums.org/showthread.p...ted+10+seconds)

I am now receiving the same error. I tried the above command but this time with no success.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "chau"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device

Could anyone please help?

---

### Post by mjrclark on 2007-09-19
Something similar (not sure it is the same thing though) happened when I ran out of disk space. I solved it by deleting some files in recovery mode to make space, I found some huge (GB or so) log files in /var/log  , the command ls -lh will list the files in a directory and there sizes in kb, mb etc.
Oh, and do not delete the folders, delete files in /var/log or in subdirectories of that- deleting folders there causes problems wiht something I cannot remember.

---

### Post by Whoopie on 2007-09-19
sorry

---

### Post by Beggar on 2007-09-19
The key is this line:

mkdtemp: private socket dir: No space left on device

Your out of space, you are going to need to delete temp files/move stuff of the hdd in order to fix it. The reason clean worked last time, is because it deleted all of the deb packages you had on your system, but now you need to delete actual files. (you could also move these to another hdd)

---

### Post by MotHaiBa on 2007-09-20
Thank you all for your prompt responses.

I am new to Ubuntu so I am not really sure which temp files to delete. Is it safe to delete all temp files.

And could you please advise all the folders temp files may reside in.

Regards

---

### Post by mjrclark on 2007-09-21
It is safe to delete all files in /tmp . I had no problems deleting all the files (but not folders) in /var/log .

sudo apt-get clean may also free some space. Other than that, I am do not know.

---

### Post by Beggar on 2007-09-24
Other then the afore mentioned items, (logs, etc) you need to empty your trash from time to time. There should be a widget on the desktop, otherwise use ```
sudo rm -rf ~/.Trash/*
```.

You can also move large files (like movies, etc) off your system by burning them to dvd, or to another hard drive.

---

### Post by MotHaiBa on 2007-09-24
Thank you all for your help.

---

