---
title: "Im trying to install Nvidia drivers..."
date: 2006-07-26
forum: Desktop Environments
---

### Post by aten on 2006-07-26
I downloaded a file from Nvidia's site named

"NVIDIA-Linux-x86-1.0-8762-pkg1.run"

When I drag it in to the terminal i get this error:

"  ERROR: nvidia-installer must be run as root "

Im sorry but Im a Ubuntu "N00B".


Thanks a LOT.

---

### Post by xyuri on 2006-07-26
to run that command as root you should use "sudo" ...

When running that command, make sure that "sudo " is typed followed by your extra stuff. This will prompt you for the admin password... just type it in and all should go well :)

---

### Post by maddog39 on 2006-07-26
type:
```

sudo [password]

```
Then try to runt he script.

---

### Post by aten on 2006-07-26
So what does it mean as "root" does it mean something like a system admin?

By the way I won't be able to run the script tonigt ill have to wait until im done updating the computer.

But thanks ill post my results!

---

### Post by aysiu on 2006-07-26
If it's on your desktop, change to the desktop directory: ```
cd ~/Desktop
``` Then you should make sure it's executable: ```
sudo chmod +x NVIDIA-Linux-x86-1.0-8762-pkg1.run
``` Then run it as root/administrator: ```
sudo ./NVIDIA-Linux-x86-1.0-8762-pkg1.run
``` Then read the proper way to install applications (i.e., what I just described is not the best way to install NVidia drivers): [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You should also read a bit about permissions:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aten on 2006-07-27
> **aysiu said:**
> If it's on your desktop, change to the desktop directory: ```
cd ~/Desktop
``` Then you should make sure it's executable: ```
sudo chmod +x NVIDIA-Linux-x86-1.0-8762-pkg1.run
``` Then run it as root/administrator: ```
sudo ./NVIDIA-Linux-x86-1.0-8762-pkg1.run
``` Then read the proper way to install applications (i.e., what I just described is not the best way to install NVidia drivers): [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You should also read a bit about permissions:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)


This is the error I get:


 ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.


Thanks for the Help!!!

---

### Post by aysiu on 2006-07-27
> **aten said:**
> This is the error I get:


 ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.


Thanks for the Help!!!
Since you insist on installing it from the .run file instead of using the repositories, you should take comfort in [the fact that that is a common error](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=%22ERROR%3A+Unable+to+find+the+system+utility+%60ld%27%22&btnG=Search) and most sites that have people complaining about that error say that you should just install *binutils*. ```
sudo aptitude update
sudo aptitude install binutils
```

---

### Post by Perfect Storm on 2006-07-27
Any reason why not getting it from the sourcelist?

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
If you have older nvidia card (gforce2, TNT etc) change nvidia-glx to nvidia-glx-legacy.

If it says error on enable nvidia driver, then:
```
sudo nano /etc/X11/xorg.conf
```

Change:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]" (this my card, your will properly looks diffrent)
    Driver         "nv"
EndSection

```

to
```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

```

save and exit. reboot. If it also fails and you end up in non-X. Change back the "nvidia" to "nv".
and:
```
startx
```

If you want to install the one you downloaded check: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=36&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=36&Itemid=63)
It's my quick installation version of tseliot's howto (link are provided if you wanna chack his howto).

---

### Post by azmrb on 2006-07-28
> **aysiu said:**
> Since you insist on installing it from the .run file instead of using the repositories, you should take comfort in [the fact that that is a common error](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=%22ERROR%3A+Unable+to+find+the+system+utility+%60ld%27%22&btnG=Search) and most sites that have people complaining about that error say that you should just install *binutils*. ```
sudo aptitude update
sudo aptitude install binutils
```

The submitter is installing from a terminal because that is what the nvidia instructions say to do.

I have the same problem.  I need to install the nforce driver to make the ethernet work and I can't because binutils aren't installed and I sure aint going to use any repositories with the ethernet working.  Catch22.  I am beginning to thing that ubuntu just isn't ready for prime time.

---

### Post by aysiu on 2006-07-28
> **azmrb said:**
> I am beginning to thing that ubuntu just isn't ready for prime time. Buy a System76 computer and install Windows on it and then say that again.

---

### Post by bensexson on 2006-07-28
You really should try nvidia-glx from the universe repository.

---

### Post by peebly on 2006-07-28
> **aten said:**
> I downloaded a file from Nvidia's site named

"NVIDIA-Linux-x86-1.0-8762-pkg1.run"

When I drag it in to the terminal i get this error:

"  ERROR: nvidia-installer must be run as root "

Im sorry but Im a Ubuntu "N00B".


Thanks a LOT.

have you tried Automatix.

it installed and enabled the nvidia driver for me.

i had no problems at all.

---

### Post by Sambie on 2006-10-01
Im recieving an error 

ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

                                       OK

How can I temp get out of X- server so I can sucessfully install the latest drivers.

---

### Post by Sambie on 2006-10-01
I also just recieved this error


  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

                                       OK

---

### Post by Perfect Storm on 2006-10-01
<ctrl> + <alt> + <F1>

```
sudo /etc/init.d/gdm stop
```
Takes you out of X.

---

