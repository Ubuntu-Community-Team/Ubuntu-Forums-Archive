---
title: "ubuntu doesnt start on boot up"
date: 2009-05-08
forum: General Help
---

### Post by kvs on 2009-05-08
hey,
whenever i boot up ubuntu, the login screen doesnt appear. the cursor that is supposed to be present at login screen appears with a busy sign, but the screen is black. i pressed alt+ctr+F4 and could login to text mode. please, could anyone tell me how to login to the graphical mode?

---

### Post by Peter09 on 2009-05-08
Use recovery mode (press escape at the Grub prompt) and get to a command shell.

If this was a working config check your disk space with 
```
df -h
```

You can try startx at the command prompt.

---

### Post by argail1980 on 2009-05-08
Hi,

you can also get to the text mode and try

```
sudo /etc/init.d/gdm restart
```

This should restart the graphical login-manager in case it's stuck. Please post what happens after that.

You should also have a look at the X-server Logfile

```
less /var/log/Xorg.0.log
```

look for lines starting with "(EE)", these are errors

---

### Post by kvs on 2009-05-08
i tried startx. its says 'unrecognized command'

---

### Post by Peter09 on 2009-05-08
What version of ubuntu are you using?

---

### Post by argail1980 on 2009-05-08
try the other method... I don't know if the startx script even exists any more.

---

### Post by kvs on 2009-05-08
i tried restarting the gdm, but it showed the same thing (the busy cursor and the blank screen). 
in the other file, the line with EE was:
(EE) acceleration initialization failed

---

### Post by Peter09 on 2009-05-08
:confused: Whoops - wrong thread

---

### Post by kvs on 2009-05-08
i have ubuntu 8.10

---

### Post by Peter09 on 2009-05-08
Has this configuration ever worked?

---

### Post by kvs on 2009-05-08
yes, it was working fine. this problem only started today. its been working properly for over a month

---

### Post by argail1980 on 2009-05-08
Hi,

could you post the contents of the file:

```
/etc/X11/xorg.conf
```

And you can check if gdm is even running with

```
ps aux|grep gdm
```

the output should look like:

```
root      5934  0.0  0.1  14400  1784 ?        Ss   10:53   0:00 /usr/sbin/gdm
root      5940  0.0  0.4  19668  4892 ?        S    10:53   0:00 /usr/sbin/gdm
root      5959  1.5  5.2  72992 53772 tty7     Ss+  10:53   0:48 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      6137  0.0  5.2  72992 53772 tty7     S+   10:53   0:00 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
argail     10406  0.0  0.0   3248   816 pts/0    S+   11:46   0:00 grep gdm

```

---

### Post by kvs on 2009-05-08
[FONT=monospace]ps aux|grep gdm displays:
root 10079 0.0 0.0 14516  1849 ?     Ss 15:00 0:00 /usr/sbin/gdm
root 10081 3.1 2.8 71668 58656 ?     S  15:00 0:37 /usr/sbin/gdm
root 10087 0.1 0.6 18744 12488 tty7  Ss+ 15:00 0:02 /usr/X11R6/bin/X: 0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
karan 28880 0.0 0.0 3296 772 tty1 R+ 15:20 0:00 grep gdm

karan is my login name
[/FONT]

---

### Post by kvs on 2009-05-08
[FONT=monospace]/etc/X11/xorg.conf shows:
Section "device"
         Identifier  "configured video device"
Endsection

Section "monitor"  
        identifier      "configured monitor"
endsection

section "screen"
          identifier       "default screen"
          monitor           "configured monitor"
          device            "configured video device"
endsection
        
[/FONT]

---

### Post by argail1980 on 2009-05-08
ok, that look good so far.... if this problem is new, maybe it is solved by an update. you can do that from the text console with
```
sudo apt-get update
sudo apt-get upgrade
```

Your xorg.conf looks ok too... hmm.. I have to think

---

### Post by kvs on 2009-05-08
could this be a hardware problem? for a few days, iv been having a problem: my laptop keeps getting swicthed off on its own in between. could this have a connection?

---

### Post by argail1980 on 2009-05-08
another idea:

make a backup copy of your xorg.conf```
cp /etc/X11/xorg.conf ~/
```

and then try

```
dpkg-reconfigure xserver-xorg
```

what kind of graphics card do you have?

Another idea:

What is the output of ```
df -h
``` you didn't post it when Peter suggested that

---

### Post by Peter09 on 2009-05-08
Check your disk with 

```
df -h
```

and 
```
fsck
```

---

### Post by kvs on 2009-05-08
all the drives have use% of a maximum of 39%. another one has 33%.rest are either 0 or 1%
i used  ati radeon graphics card

---

### Post by kvs on 2009-05-08
when i ran fsck, it says warning: running e2fsck on a mounted filesystem may cause severe filesystem damage.

---

### Post by argail1980 on 2009-05-08
> could this be a hardware problem? for a few days, iv been having a problem: my laptop keeps getting swicthed off on its own in between. could this have a connection?

I had the same thing. With me it was a heat problem (actually, it still is..) could you have fried your graphics card?

```
sudo lshw
```

should give you the hardware installed on your system. And any funny crashes are usually recorded in ```
/var/log/messages
```

---

### Post by kvs on 2009-05-08
it shows a LOT of recent crashes.

---

### Post by kvs on 2009-05-08
should i just reinstall ubuntu? how do i create a backup?

---

### Post by kvs on 2009-05-08
btw , you have the heat problem too? so even your laptop keeps getting switched off? what can be done about it?

---

### Post by Peter09 on 2009-05-08
Re: Heat problem

Java has had an issue where it runs at 100% cpu after you have finished browsing, might be worth using HTOP to see if that is the problem.

---

### Post by argail1980 on 2009-05-08
> btw , you have the heat problem too? so even your laptop keeps getting switched off? what can be done about it? 

I have no idea. Right now I'm keeping an eye on the temperature and reduce the load when it gets too high. I think about upgrading to 9.04. 7.10 didn't seem to have that heat problem, but I want a current ubuntu version.


could you post the latest crash and a few lines above? Maybe we can learn something from that.

did the reconfiguring the xserver work out?


btw: what happens if you enter```
sudo /etc/init.d/gdm stop
```

---

### Post by kvs on 2009-05-08
after reconfiguring the server, the screen became black and white, and still didnt show the login screen. thankfully i had made a backup file. i think that overheating problem is because i used to put my laptop on the bed all the time. i need to put it on a hard surface to allow airflow

---

### Post by kvs on 2009-05-08
it says "stopping gnome display manager              :  OK  " on executing that command

---

### Post by kvs on 2009-05-08
also, my Xorg.0.log file has the following error:
(EE) Radeon (0) : Acceleration initialization failed

---

### Post by kvs on 2009-05-09
guys .. please help me out.. im sort of freaking out...

---

### Post by DeMus on 2009-05-09
> **kvs said:**
> all the drives have use% of a maximum of 39%. another one has 33%.rest are either 0 or 1%
i used  ati radeon graphics card

When using the instruction:
```
df- h
```
you answer a drive has 39% free space, one has 33% and the rest either 0 or 1%.

Please use the instruction again and this time copy - paste the outcome in your answer.
You can copy text from a terminal by using ctrl-shift-c (instead of ctrl-c).

When it is really true you have 1 or 0% free space then it's obvious where the error lies.
So, please copy-paste the outcome in your next answer.

---

### Post by kvs on 2009-05-10
Filesystem                                Size    Used    Avail      Use%  Mounted on
/host/ubuntu/disks/root.disk       27G      8.3G  18G        33%    /
tmpfs                                     1011M     0       1011M      0%   /lib/init/rw
varrun                                    1011M  100K   1011M       1%  /var/run
varlock                                   1011M     0     1011M        0%  /var/lock
udev                                       1011M   2.9M  1008M       1%   /dev
tmpfs                                      1011M     0     1011M       0%   /dev/shm
/dev/sda2                                   77G    30G     47G       39%  /host
lrm                                         1011M    2.0M  1009M       1%  /lib/modules/2.6.27-11-generic/volatile

The problem with copying from the terminal is that right now im on a different machine. the machine on which i have ubuntu is not starting the graphical mode, so i have to use a different machine. i have to sort of write the whole thing all over again, i cannot copy or paste :(

---

### Post by Peter09 on 2009-05-10
I am running out of ideas here.

As an aside, with a terminal command if you follow up with a > 'filename' the output will go to a file.

so

```
df -h > file.txt
```

will give you a file called file.txt with the output in it. Makes it easier to transfer to a different machine.

---

### Post by kvs on 2009-05-10
but i don't really know how to transfer that file to another machine. i could try using a pendrive, but the problem is, i can't access the pendrive in text mode. in graphical mode, my pendrive would be in the /media/disk directory. now, whenever i go to /media, and type ls, it displays only 2 directories: cdrom and cdrom0. im not able to access the pendrive

---

### Post by kvs on 2009-05-10
also, i have another drive which contains all my windows stuff. it was also there in /media/disk. in text mode, i just cannot access that directory

---

### Post by Malvank on 2009-05-16
I was uninstallting and reinstalling OpenOffice and i think i messed up and removed something that broke Gnome.

After that i got the black screen problem. I you change the session to Genom and get an error that genom installation can't be found, then this solves the problem.


re-install gnome:

sudo apt-get install --reinstall ubuntu-desktop

Hope this helps if anything else fails.

---

### Post by argail1980 on 2009-05-19
I think it is a graphics-card driver problem. d'you know what ati radeon you have? i.e. I have a X1400 in my laptop.

My guess is that the problem comes from the Xserver

> (EE) Radeon (0) : Acceleration initialization failed 

Another idea:

!! backup your /etc/X11/xorg.conf again and then try:

```
sudo aticonfig
```

if that doesn't work, try to install the correct driver with "envy" that is a program that looks for the fitting driver for ati or nvidia cards

```
sudo apt-get install envyng-gtk
```

and then start the program... propably with ```
sudo envy
``` or something similar

> it says "stopping gnome display manager : OK " on executing that command 
this tells me that the gdm is running.. but I don't really know what to make out of that

---

### Post by kvs on 2009-05-23
ok, problem solved. i backed up my data and upgraded to ubuntu 9.04. and it works all right , till now

---

### Post by argail1980 on 2009-05-25
well, that's also a possibility :-)

---

