---
title: "two computers, one user"
date: 2006-09-05
forum: Desktop Environments
---

### Post by chinaski on 2006-09-05
hello,

here's my question: I have two machines running Ubuntu (and only that), one desktop one laptop

I both use them for work, so my need is to have two identical environments in order to have any change made on one machine transfered to the other without much pain

how may I achieve this?

thank you :)

---

### Post by taurus on 2006-09-05
If they're both on the network, you can use nfs to mount one /home directory on both machines so your environment is always the same and all your files are available to you no matter which machine you log in!

---

### Post by mssever on 2006-09-05
> **taurus said:**
> If they're both on the network, you can use nfs to mount one /home directory on both machines so your environment is always the same and all your files are available to you no matter which machine you log in!

If you do that, you need to consider what will happen if you take your laptop somewhere. If /home can't be mounted, then you won't be able to log in. This suggests hosting /home on your laptop. Of course, if your laptop is turned off, then you're still up a creek. However, NFS *is* the usual way of doing these kinds of things (although the laptop is a complication).

Another suggestion is to look into Unison. I've never used it, but I've heard that it's mission is to keep files syncronized.

---

### Post by whizbaby on 2006-09-05
Msserver is right. To make your setup comfortable you would need a script which tests if /home can be mounted and tells what to use if not. Another (easier) idea is an external HD with your home on it.

---

### Post by mssever on 2006-09-05
> **whizbaby said:**
> Msserver is right. To make your setup comfortable you would need a script which tests if /home can be mounted and tells what to use if not. Another (easier) idea is an external HD with your home on it.

If you follow this route, you'll need to do a few different things to your fstab. USB device names aren't very predictable, making mounting difficult. But, if you use the ext3 (or ext2) filesystem, you can assign a label using e2label. Then, in fstab put the label where you would normally put the device name; eg ```
LABEL=EXTERNAL_HD /home ext3 defaults 0 2
```

---

### Post by chinaski on 2006-09-06
thank you for your replies ;)

yes the problem is that I carry the notebook around, so I think the script is the best solution

but where could I start to look for how to write a script? I never write/use one before.

anyway, if I got everything right, I have to write/get a script to put on both machines telling them to boot looking for the shared home, and if they can't find it to mount somewhere else.

is that correct?

---

### Post by whizbaby on 2006-09-06
Yes, that's it basically(except I would replace 'somewhere else' by 'something else as home'). There are a lot of ways to do this, perhaps an easier one is to have two users (on the desktop computer), let's call them *netuse*(same password on both computers) and *locuse*. The script should try to mount *netuse*'s home and login as *netuse* when finding it. Otherwise login as *locuse*. The notebook would only need the *netuse* account. To prepare the homedir of *netuse* on the desktop-machine you have to remove all files in there:
**rm -r */home/netuse/****

an entry in */etc/fstab* on the desktop will look similar to this

**laptopsname:/home/netuse /home/netuse nfs defaults,noatime,tcp 0 0**

on the laptop you will have to add something like this to */etc/exports*: 

**/home/netuse desktopsname(rw,no_wdelay,no_root_squash,no_subtree_check,sync)**

to let the computers know each other you'll have to add the name and IP of resp. other computer to */etc/hosts*

e.g. on the laptop (assume desktops IP is 192.168.0.20)

**192.168.0.20             desktopsname**   

If you got this setup right you already can do what you want (if laptop is connected mount the home manually (with **mount -a** if you did a fstab entry) before logging in. If not login as locuse). The script is only for comfort (and should not be too hard to do. Learn scripting by searching for other peoples scipts and try to understand them by using something like [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/))
You can use **cron** to start scripts at boot time.
(another hint: with **ping *computername*** you can verify the presence of *computername* in the net)
(when you see the login screen you can press ctrl-alt-F1 to get to a terminal, and ctrl-alt-F7 to get back to the login screen)

---

### Post by chinaski on 2006-09-06
> **whizbaby said:**
> Yes, that's it basically(except I would replace 'somewhere else' by 'something else as home'). There are a lot of ways to do this, perhaps an easier one is to have two users (on the desktop computer), let's call them *netuse*(same password on both computers) and *locuse*.
ok, and what if I have  same_user same_password different_host_name?

this is my configuration, the same user name might mess things up?

I will study the rest of your post later, thank you very much ;)

---

### Post by whizbaby on 2006-09-06
> **chinaski said:**
> ok, and what if I have  same_user same_password different_host_name?

Read last post, it's exactly for that!

---

### Post by mssever on 2006-09-06
The more I think about this, the more I think that we're making this more difficult than it needs to be. I think that your life would be easier if you did this, instead:
```
sudo apt-get update && sudo apt-get install unison unison-gtk #you need to have the universe repository enabled for this to work
unison -doc tutorial | less # read the instructions
``` There will be an entry for Unison in Applications > Internet. Install Unison on both machines if you plan on using SSH (see below).

If you syncronize your home directory with unison, you'll accomplish the same thing without having to worry about all this NFS stuff.

Then, you have two options for syncronization: SSH and NFS.

To do SSH, do the following on your server (I think that this is the easiest):
```
sudo apt-get install openssh-server
``` 
and on your laptop:
```
sudo apt-get install openssh-client
``` Then, follow the instructions in the unison docs.

To use NFS, export your desktop's home directory and mountit somewhere on your laptop. I use /media/myuser. Then follow the instructions for syncronizing local files (files on the same machine).

---

### Post by chinaski on 2006-09-06
thank you mssever, I think I'll try Unison ;)

@ whizbaby: sorry, I did not read carefully your post, I thought you mean two different user name on each machine

---

