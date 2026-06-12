---
title: "how do you use su or sudo"
date: 2005-04-05
forum: Desktop Environments
---

### Post by dcast on 2005-04-05
I've tried to use su and sudo but sudo nothing happenns in the terminal and with su it asks for a password and when i type nothing happens?

---

### Post by Xian on 2005-04-05
What command are you using with sudo? For example,

$ sudo gedit

---

### Post by dcast on 2005-04-06
well that may  solve my problem i was under the impression the su and sudo just made you root for all of the apps and not a selected one

---

### Post by dcast on 2005-04-07
I tried your example and basically the same thing happened but now it says that it couldn't find the domain name for my computer? is this happening because it isn't connected to the internet??

---

### Post by carlc on 2005-04-08
What is the full command that you are typing in terminal?

sudo ????

---

### Post by bored2k on 2005-04-08
[QUOTE=carlc]What is the full command that you are typing in terminal?

sudo ????[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RootSudo/](http://www.ubuntulinux.org/wiki/RootSudo/)

---

### Post by carlc on 2005-04-08
My post probably was not that clear. I was tyring to figure out what dcast was typing to get a message regarding not finding the domain name for his pc.

---

### Post by dcast on 2005-04-09
At first i was simply typing in $ su and $ sudo. when i use su it just asks for a password and then nothing happens when I type. When i use sudo it says:
 
sudo: unable to lookup debian via gethostbyname ()
usage: sudo -V l  -h l  -L l -L  l  -v  l  -k  l  -K  l  [-H]  [-P] [-S]  [-b] [-p prompt]
                           [-u username/#uid]  -s  <command>

what does this mean?? i also tried the example of $ sudo gedit but then it said

sudo: unable to lookup debian via gethostbyname ()
password:

then nothing happens when i type??? ](*,)

---

### Post by carlc on 2005-04-09
When you type sudo, follow it with the command of what you are trying to do (e.g. open a program, copy a file, change user permissions).

Example:

sudo mkdir /usr/java

---

### Post by dcast on 2005-04-09
so say i wanted to opend synaptic what would i use there?

---

### Post by carlc on 2005-04-09
just type: 

sudo synaptic

---

### Post by dcast on 2005-04-09
i've tried that and basically the same thing happens...nothing. I can't even get synaptic to run when I click on it nothing happens the computer doesn't do anything?

---

### Post by carlc on 2005-04-09
Sorry, but if synaptic will not run from the terminal or gnome menu then I am not sure what is going on or how to get it to work. If you have a specific program that you are trying to install, have you tried just using apt-get? (sudo apt-get install name of program here)

---

### Post by slunk on 2005-04-09
I am having the exact same issue after a fresh install.  I can neither pull up the root terminal nor Synaptic.  I get the same domain error when using sudo, also.  And, I just want to mount a partition.

---

### Post by Mr_THX on 2005-04-10
I am having the same problem.  I cant do anything with sudo.  

I was just trying to mount an ntfs partition and I couldnt even use mkdir with sudo.

---

### Post by slunk on 2005-04-10
[QUOTE=Mr_THX]I am having the same problem.  I cant do anything with sudo.  

I was just trying to mount an ntfs partition and I couldnt even use mkdir with sudo.[/QUOTE]
 Anyone have a solution?  I also get an error message when I first login stating...

"could not look up internet addres for "host name."  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding "host name" to the file /etc/hosts."

I then choose "log in anyway"

---

### Post by Leif on 2005-04-10
For those who can't get synaptic working, what happens when you type "sudo apt-get install synaptic" ? If it installs it, now "sudo synaptic" should work.

As for not being able to create a folder on an NTFS drive, you can't (at least not by the usual mount method). Writing to NTFS isn't quite there yet, AFAIK.

---

### Post by slunk on 2005-04-10
I, at least, get the same kind of error.  It reads...

(user)@(host):~$ sudo apt-get install synaptic
sudo: unable to lookup (host) via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or directory

By the way, I am typing these message from another system than what this is occuring on.

---

### Post by slunk on 2005-04-10
:-D  The smiley above should be interpreted!

---

### Post by dcast on 2005-04-10
last night i did a complete reinstall and now it works fine... strangest thing. But i still get the login error that was posted by slunk when i log in.

---

### Post by dcast on 2005-04-10
i don't really understand why gnome supposedly won't work properly without an internet connection. Couldi correct the problem by removing my network card??

---

