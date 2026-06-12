---
title: "Virtualbox error"
date: 2009-08-02
forum: Desktop Environments
---

### Post by asai on 2009-08-02
Hi,
I have a problem with the Virtualbox. I have used it for some time now, but after a upgrade it doesn't work any more.
I get this error when I try to start any of my Virtual machines:
[IMG]http://asai.dyndns.org/images/vbox_error.png[/IMG]
I have installed the package DKMS, but when i run the command sudo /etc/init.d/vboxdrv setup I get command not found

Any suggestions?

---

### Post by asai on 2009-08-02
OK, so I solved it myself. :D

Here is my solution:

 1. I completely removed the application.
 2. sudo nano /etc/apt/sources.list
 3. Added deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) jaunty non-free
 4. wget [http://virtualbox.org/debian/sun_vbox.asc](http://virtualbox.org/debian/sun_vbox.asc)
 5. sudo apt-key add sun_vbox.asc
 6. sudo apt-get update
 7. sudo apt-get upgrade
 8. sudo apt-get install virtualbox-3.0

Now, when I open Virtualbox, all my Virtualmachines are in place, and running. :)

---

### Post by 67GTA on 2009-08-02
You don't have to go through all of that trouble. Just run the command the error message gave you in a terminal to recompile the Vbox drivers into the kernel. 

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by asai on 2009-08-02
I know that command but:
> **asai said:**
> I have installed the package DKMS, but when i run the command sudo /etc/init.d/vboxdrv setup I get command not found

So, *all* that trouble only took a few minutes and the important thing is that the problem is solved. :)

---

### Post by Cal27 on 2009-08-12
I was getting 'command not found' as well, so I tried asai's solution but it still didn't work. I decided to check in my init.d directory and found 'vboxdrv.dpkg-bak'. I ran that and everything works now.

---

### Post by can8dnSix on 2009-08-16
Had the same issue and tried all the posted fixes, until I read the one right above (by Cal27) my response. Nonetheless, everything works now. 

```
bash:/etc/init.d$ sudo ./vboxdrv.dpkg-bak setup
 * Stopping VirtualBox kernel module *  done.
 * Removing old VirtualBox netadp kernel *  done.
 * Removing old VirtualBox netflt kernel *  done.
 * Removing old VirtualBox kernel *  done.
 * Recompiling VirtualBox kernel *  done.
 * Starting VirtualBox kernel *  done.
bash:/usr/binS ./VirtualBox

```

Everything works now! 
Thanks,
Can8dnSix

---

### Post by leehach on 2009-08-24
Had the same problem on upgrade to kernel 2.6.24-24.59 last week. Want to reiterate what asai said, upgrade to VirtualBox 3.0 solved the problem. DKMS did not work (as it had for several previous kernel updates), sudo /etc/init.d/vboxdrv setup did not work, and my init.d directory did not have vboxdrv.dpkg-bak.

Thanks, asai!

---

### Post by PiHalf on 2009-10-30
Hi all,
I got the same error message on newly installed Kubuntu 9.10. 
Installing DKMS and runnin' setup with
```
sudo /etc/init.d/vboxdrv setup
```didn't work, cause there was no "vboxdrv" ...

But there was a "virtualbox-ose" ...

After running
```
sudo /etc/init.d/virtualbox-ose start
```everything just worked fine for me :D !
Thx for the hints!

---

### Post by khughitt on 2009-10-30
```
sudo /etc/init.d/virtualbox-ose start
```

Worked for me as well! (Running Ubuntu 9.10 2.6.31-14-generic-pae). I just loaded up [BUM]("http://www.marzocca.net/linux/bum.html"), and checked the box for "virtualbox-ose", so hopefully it should start automatically from now on :)

---

### Post by propan0 on 2010-03-08
> **PiHalf said:**
> Hi all,
I got the same error message on newly installed Kubuntu 9.10. 
Installing DKMS and runnin' setup with
```
sudo /etc/init.d/vboxdrv setup
```didn't work, cause there was no "vboxdrv" ...

But there was a "virtualbox-ose" ...

After running
```
sudo /etc/init.d/virtualbox-ose start
```everything just worked fine for me :D !
Thx for the hints!

Same here, no vboxdrv, just runing virtualbox-ose it seemed to solve the problem:
```
/etc/init.d$ sudo ./virtualbox-ose start
* Starting VirtualBox kernel modules
* Disabling the hardware performance counter framework         [ OK ]
```

Thanks everyone!

---

### Post by bilalsultan86 on 2010-03-11
Hi:

I have faces this error twice and two different solutions worked for me.

Initially, running virtual-box as root. 'gksudo virtualbox'

and this time 

sudo /etc/init.d/virtualbox-ose start

Thankyou:):)

---

### Post by asus-user on 2012-03-23
ubuntu 10.04 and this worked for me thanx [asai]("http://ubuntuforums.org/member.php?u=413066")

---

### Post by ranger1021994 on 2012-03-23
> **asai said:**
> OK, so I solved it myself. :D

Here is my solution:

 1. I completely removed the application.
 2. sudo nano /etc/apt/sources.list
 3. Added deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) jaunty non-free
 4. wget [http://virtualbox.org/debian/sun_vbox.asc](http://virtualbox.org/debian/sun_vbox.asc)
 5. sudo apt-key add sun_vbox.asc
 6. sudo apt-get update
 7. sudo apt-get upgrade
 8. sudo apt-get install virtualbox-3.0

Now, when I open Virtualbox, all my Virtualmachines are in place, and running. :)
  Thnxx man..!!! :) :)

---

### Post by oldos2er on 2013-04-29
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

