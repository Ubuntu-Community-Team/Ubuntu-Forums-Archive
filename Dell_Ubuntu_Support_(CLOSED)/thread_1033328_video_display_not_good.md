---
title: "video display not good"
date: 2009-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Broady on 2009-01-07
Hi
I am a newbie to linux .got ubuntu installed just a few days ago.

My video quality is really bad.i think my graphics card is not configured properly.
specs 
Dell inspiron 1520
2 Gb ram
ubuntu 8.04 
nvidia 8400 graphics card 128mb dedicated

how do i know what driver to install for my graphics card .
by the way i have access to a repository.
i also have vista on my comp.no issues of display in that.
Can somebody help me out....

Broady

---

### Post by theinnercityhippy on 2009-01-07
It is probable that the driver is already installed but not yet activated as it is not maintained by Ubuntu but by NVidia themselves, as they are quite good at supporting their products for use in Linux, releasing a driver called NV

In the panel at the top go to

System > Administration > Hardware Drivers

You will have to put in your user password as you are making changes to your system. In the window that opens, you will probably see thatthe driver NV is listed but with a red button next to it, showing it is not enabled, and there will be an option to enable it. Click on this, reboot and you should be good to go.

If this doesn't work I will try to help you further

-JimDog*-

---

### Post by WSmart on 2009-01-07
It should load automatically.  Have you done your updates and rebooted?  You can check in System>Administration>Hardware drivers.  The Nvidia control panel, xserver settings, should be in System>Admin too.  Check it out.

What I always recommend anyone moving to Linux for the first time is using a KVM switch and building a new machine for Linux, unless this is the first computer.  Dual boot with Windows sucks.  I found a cheap KVM that works on eBay last January and I've been live with *Ubuntu for a year now.  Not a problem.

Be real, be sober.

---

### Post by Broady on 2009-01-07
Hi
As said i went 
System > Administration > Hardware Drivers

but it showed 

no proprietary drivers are in use on this system.

there are no options at all .the list is blank.

Broady

---

### Post by armandh on 2009-01-07
what version of ubuntu have you installed?
oops found it 8.04
you may have to activate 3rd party softeare sources

---

### Post by theinnercityhippy on 2009-01-07
> **Broady said:**
> Hi
As said i went 
System > Administration > Hardware Drivers

but it showed 

no proprietary drivers are in use on this system.

there are no options at all .the list is blank.

Broady

try opening a terminal in Applications > Accessories > Terminal and issuing the following command
```

user@ubuntu:~$ sudo apt-get install nvidia-
```

When this is complete, reboot and go back to hardware drivers where hopefully it will be. You can then issue the following at the command line.

```
user@ubuntu:~$ nvidia-detector
```

To check your card is found correctly
```

user@ubuntu:~$ sudo nvidia-settings 
```

to configure it

This is the way to manually load the nvidia driver. If you are using an older version of Ubuntu issue the following command if you want to automatically upgrade your system. I reccommend backing up any important files first, which is good practice anyway :-)

```
user@ubuntu:~$ sudo apt-get update
user@ubuntu:~$ sudo apt-get dist-upgrade
```

---

### Post by Broady on 2009-01-07
Hi
how do you activate 3rd party software sources?
(by the way i got the repository connection to work with the help of another guy)
Broady

---

### Post by theinnercityhippy on 2009-01-07
Go to 

System > Administration > Software Sources and enter your password.

In the box that opens, click the Third Party Software tab and check the boxes. Sorry, should have mentioned that from the off, hehe some expert I am ;)

Reboot and try going to hardware drivers again and hopefully you'll find it there

-JimDog-

---

### Post by Broady on 2009-01-27
Hi,
Now as i go to System->admin->hardware drivers->
i find the nvidia driver being listed.(earlier this itself did not come).
So i clicked and enabled it .needed me to restart and i did that.But then as it reboots it reaches a place where (before the username is asked)the _screen goes white and there is a thick black line_ in the middle.Restarting any no of times is of no use.But i can hear the login window music and if i carefully type the name and password it reaches the desktop though i cannot see it.
Then i went to recovery mode and did 'try to fix Xserver'.Then it overwrote config files.now i can get back to my desktop as earlier and as usual video display is bad.

---

### Post by WSmart on 2009-01-27
Try and reset the CMOS/BIOS.  It's amazing how many issue that can cause.

Also, why did you use 8.04 rather then 8.10?  That's a newer graphics card and you want the latest Ubuntu has to offer for that puppy.

---

### Post by Broady on 2009-01-30
Hi 
I finally got it working.
there were similar problems posted and just followed it to get it corrected.
the link is
[http://ubuntuforums.org/showthread.php?t=814838](http://ubuntuforums.org/showthread.php?t=814838)
follow the instructions and it ll work.
Thanks to all of you for replying to my problems.

Broady

---

### Post by Broady on 2009-01-30
Hi
i finally got the problem sorted out.
the link has the solution..
[http://ubuntuforums.org/showthread.php?t=814838](http://ubuntuforums.org/showthread.php?t=814838)

i just followed it and now it is working.
Thanks to all of you for your help.

Broady

---

