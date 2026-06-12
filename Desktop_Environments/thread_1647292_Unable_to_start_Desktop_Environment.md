---
title: "Unable to start Desktop Environment"
date: 2010-12-17
forum: Desktop Environments
---

### Post by proch04 on 2010-12-17
I'm unable to start with a desktop environment - Ubuntu 10.10 - Everything was working fine, then I shutdown my computer for dinner. When I restarted it, it when into a "Ubuntu scree with the logo and the name of the computer"  and I can't get a login.  I get that splash screen with the icon for shutdown and restart on the lower right hand corner. see picture..
[IMG]http://picasaweb.google.com/lh/photo/BZ1y4AT4iCkC35wn4MfVtQ?feat=directlink[/IMG]

After some research online, I got into recovery mode and tried to start the server with 

```
startx
```

Then I got the following result

```
xinit:no such file or directory
```


Now when I run this command

```
sudo startx
``` I can login to root desktop and I notice that the user is root and I have no wireless access.

Somebody Please help,

---

### Post by proch04 on 2010-12-17
Here are additional information:


I ran ```
startx
```from recovery mode

Here is the output

```

startx
xauth:error in locking authority file /home/proch/.Xauthority
xauth:error in locking authority file /home/proch/.Xauthority

blah blab blah......


fatal server error:

xf86OpenConsole: cannot open /dev/tty0 (No such file or directory)


giving up
xinit: No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno 3): Server error
Xauth: error in Locking authority file /home/proch/. Xauthority


```

When I run ```
startx
``` as root, I get the Desktop, but I can't get the wireless connection and can't create any user.

I 've tried reinstalling the desktop environment with the usual command, without any success no success and I don't have networking access. 

My machine: ASUS NETBOOK UL30A, 4GB RAM. No Dual boot. Just Ubuntu 10.10 which I had to reinstall twice for a similar situation


Somebody help! I have a web deadline and I need to meet. Thanks in advance!

---

### Post by Kognit on 2010-12-17
Try to type fsck. But this command should not be executed when the disk is mounted. It is file system check and sometimes it help me but with different problems. I haven't had a problem similar to you two guys but it won't hurt :)

---

### Post by karthick87 on 2010-12-17
Have you updated your system recently..??

---

### Post by proch04 on 2010-12-17
Yes, I have updated my system recently.

---

