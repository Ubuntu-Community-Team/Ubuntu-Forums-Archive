---
title: "how to edit x configuration"
date: 2009-05-06
forum: Desktop Environments
---

### Post by torton009 on 2009-05-06
i want to change resolution i use nvidia and i go to xserve display configuration.  
but i can't save xconfigulration  
[COLOR=DarkOrange]/etc/x11/xorg.conf  [/COLOR]  . has in the blank when i press buttom it's show.
[COLOR=DarkOrange]
unable to create new xconfiguration backup
file `/etc/x11/xorg.conf.backup [/COLOR]

and i try to do something wrong way but now i reinstall driver nvidea version 180
but i can't setting in nvidea x server setting  it's tell
[COLOR=DarkOrange]
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/COLOR] 

i want to know how i can do please tell me by step i hope ican  setting new resulution and i can save it don't want to change every time when i log on . i new in ubuntu i don't know more command in terminal . thank you for human beings:)

---

### Post by andrea000 on 2009-05-06
How did you install the driver?Envyng or did you go to hardware
drivers.Did you install nvidia x server setting?There is a place
in the x sever setting to save your x config back.

You can try this i do not know if it still works on 9.04 and i do not know what version of ubuntu your 
running.I would also change the driver back to 177 to start with.I have not heard a lot about 180.

 sudo dpkg-reconfigure -phigh xserver-xorg

This will start a wizard albeit on the console, which will walk you through configuring Xorg server.
Among other things, it will ask you to choose the video driver and the resolution of your monitor 
from a list. Once all the questions are answered, the wizard will make a backup copy of your current 
xorg.conf file and write in the new values. You will have to restart Xorg server for the changes to 
take effect. If you are in graphical mode, you can press the key combination

---

### Post by AlecJ on 2009-05-06
> **andrea000 said:**
> How did you install the driver?Envyng or did you go to hardware 
drivers.Did you install nvidia x server setting?There is a place 
in the x sever setting to save your x config back.

This is how I did it
[http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

---

### Post by andrea000 on 2009-05-06
your running 9.04 on a 64 bit system

---

### Post by torton009 on 2009-05-07
[COLOR=SeaGreen]i use ubuntu 9.04 maybe 32 bit gnome2.26.1  nvidea gforce 7200gs[/COLOR]
 i try to change driver to version 173 and i can go to change resolution at nvidia xserver setting . i back to change driver to version 180 [ recommended ] again i can go to change 
resolution but i can't save like the same time.
i try to use - [COLOR=DarkOrange] sudo dpkg -reconfigure -phigh xserver-xorg[/COLOR]
but it's tell    [COLOR=DarkOrange]xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090507130250

[/COLOR] 
i don't know the way to command. what wrong?
and how to restart [COLOR=SeaGreen]xorgserver ? [/COLOR]
i want to the way to save configuration when change resolution .
please help me again i want to know the way to xorgserver setting where i can go to it?
thank you 000
:)

---

### Post by AlecJ on 2009-05-07
> **andrea000 said:**
> your running 9.04 on a 64 bit system

Yes here the output
```
alec@alec-ubuntu:~$ cat /etc/issue
Ubuntu 9.04 \n \l

alec@alec-ubuntu:~$ uname -a
Linux alec-ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
alec@alec-ubuntu:~$ 



```

---

### Post by torton009 on 2009-05-07
for me 

[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ uname -a
Linux tonjaa-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
tonjaa@tonjaa-desktop:~$ [/COLOR]
and then what can i do ?

---

### Post by AlecJ on 2009-05-07
Ok first you need to update your driver, as the drivers that come with Ubuntu are out of date.

go here and download the binary file  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

then follow the log I did here [http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)

Then you will have full control over your video card

---

### Post by tonjaa on 2009-05-08
o k  now i[COLOR=Red] reinstall ubuntu[/COLOR] it 's can save resolution . but i use    [COLOR=DarkOrange] sudo nvidia-settings[/COLOR]  and restart
at first time i can change resolution. but i don't know i must to update driver again or?
i go to web site that of    nvidia .com/object/unix   i can't find driver match of me.
now i can change resolution i think it o.k. 
or who have a new way can tell me.

---

### Post by goslings on 2009-05-23
> **AlecJ said:**
>  go here and download the binary file  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
then follow the log I did here [http://ubuntuforums.org/showthread.php?t=1142976](http://ubuntuforums.org/showthread.php?t=1142976)


He been looking into this for my GeForce4 Ti 4600 GPU 
under 8.04 I could get the nvidia setting I wanted including using Compiz & AAWN
Now I switch to Ubuntu 9.04 and I can only install NVIDIA 96.43 and not 173.14.18 even if I run the nvidia script 

It worked under 8.04 so why not undet 9.04 

grrrrrr
any ideas appreciated 
thanks 
Ian

---

### Post by AlecJ on 2009-05-23
> **goslings said:**
> He been looking into this for my GeForce4 Ti 4600 GPU 
under 8.04 I could get the nvidia setting I wanted including using Compiz & AAWN
Now I switch to Ubuntu 9.04 and I can only install NVIDIA 96.43 and not 173.14.18 even if I run the nvidia script 

It worked under 8.04 so why not undet 9.04 

grrrrrr
any ideas appreciated 
thanks 
Ian

I think you should remove all nvidia drivers and install (180.53) the last..
and use the file xorg.conf in my log. 
There is code to remove all Nvidia drivers from your machine.

```

sudo apt-get remove nvidia-glx-new   
```

---

### Post by andrea000 on 2009-05-24
There is a great post [here]("http://ubuntuforums.org/showthread.php?t=83973") that may help 9.04 has changed
some stuff and i don't wont to tell you something that is
not right.

---

