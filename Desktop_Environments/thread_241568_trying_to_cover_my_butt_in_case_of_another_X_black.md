---
title: "trying to cover my butt in case of another X blackout!"
date: 2006-08-22
forum: Desktop Environments
---

### Post by randell6564 on 2006-08-22
Hey folks!

This is probably a stupid question.  Since I can for example, open my /etc/fstab by doing a 'sudo gedit /etc/fstab' I figured that I could do the same thing with a text file that I created, but it's not working.

I use Hdb1 (/vault) as a storage drive. On that drive, I have a folder named 'MyManPages'. It is several text files containing commands and fixes that folks have provided to me since I started using ubuntu. I want to add the xserver-xorg-core fix that jlx provided to us yesterday.

I will need to be able to read these files from the text console if I experience another X blackout again. How do I pull a text file that I created up on my console?

I cd'd to the MyManPages directory and tryed to open one of my files by doing a 'sudo gedit name of file' but all it pulls up is a blank text file.

Any ideas?  Here is a screen shot of my terminal. maybe it will help.  the list in green is all text files.  Thanks!

---

### Post by Ramses de Norre on 2006-08-22
Gedit wont work when X is broken, it's a graphical program..
You'll want to use "less": ```
less name of file
```
If you need to edit it you'll need to use vi or nano instead of less (I prefer vi, but it's not the easiest editor in the beginning..).
The most easy thing to cover yourself up is writing scripts, I wrote a script for easy recovering X in case I encountered the update hell: ```
#!/bin/sh
#Downgrade the xorg server, temporarly needed due to a bug in the dapper repo

if wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
then
        if wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
        then    echo "downloading completed"
        fi
fi

if sudo dpkg -i xserver-xorg-core*.deb
then    echo "installing completed"
fi

if rm xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
then
        if rm xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
        then    echo "removal of packages completed"
                echo "Restart X"
        fi
fi

```
It's written fast but should work..

---

### Post by randell6564 on 2006-08-22
> **Ramses de Norre said:**
> Gedit wont work when X is broken, it's a graphical program..
You'll want to use "less": ```
less name of file
```
If you need to edit it you'll need to use vi or nano instead of less (I prefer vi, but it's not the easiest editor in the beginning..).
The most easy thing to cover yourself up is writing scripts, I wrote a script for easy recovering X in case I encountered the update hell: ```
#!/bin/sh
#Downgrade the xorg server, temporarly needed due to a bug in the dapper repo

if wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
then
        if wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
        then    echo "downloading completed"
        fi
fi

if sudo dpkg -i xserver-xorg-core*.deb
then    echo "installing completed"
fi

if rm xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
then
        if rm xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
        then    echo "removal of packages completed"
                echo "Restart X"
        fi
fi

```
It's written fast but should work..

Well, it's taken me 15 damn minutes to get to your reply!  This forum is really starting to suck.  it's taking forever to load!

Anyway, Thanks my friend!  All I will need to be able to do is read these files. But I even tryed to open them from the terminal on my desktop and could'nt. I used gedit for that and just got a blank file.

I would not know how to run this script.  can ya give me some instructions or point me to some tutorials on running scripts?  Thanks!

---

