---
title: "display server gets down with full disk"
date: 2006-07-29
forum: Desktop Environments
---

### Post by xinelo on 2006-07-29
Hi, 

I'm writing to describe something which has just happened. I managed to solve the problem but I'd like to ask what I can do to prevent it from happening again. 

The thing is that the GDM could not be started apparently because the disk (to be pricese, the / partition) was full:

```
[FONT="Courier New"]xinelo@mypcname:~$ df
Sist. Arq.           1K-blocos      Usad Dispon.   Uso% Montado em
/dev/hda7              8412364   7882176    102864 100% /
varrun                  257836       104    257732   1% /var/run
varlock                 257836         4    257832   1% /var/lock
udev                    257836       160    257676   1% /dev
devshm                  257836         0    257836   0% /dev/shm
lrm                     257836     18856    238980   8% /lib/modules/2.6.15-26-386/volatile
/dev/hda5                67714     53112     10989  83% /boot
/dev/hda2             17566512   3995952  13570560  23% /windows
/dev/sda1            160795424 155231200   5564224  97% /media/SDA1[/FONT]
```

Deleting some files and directories solved the problem. My question is: is there any means of reserving some extra space (or otherwise) to prevent the disk (or the / partition) from running out of space?? 

I'm sending a second post now to explain all the things I did to solve the problem, in case someone is interested, but it shouldn't be too interesting as none of the things below solved the problem (except the last one, which I already mentioned).

---

### Post by xinelo on 2006-07-29
I don't know whether this is relevant or not, but I'll also explain what happened just before the problem. I was playing with k3b and nero in my dual booting system. I just used nero to add a session to a k3b-burnt dvd and rebooted in linux to see if k3b could see the files added with nero. There, the system hung, so I had to reboot by brute force (pressing the on/off button). As I said, I don't know whether this is relevant. 

After that, I rebooted but after logging in, the interface came back to the login manager form. I tried with kde but no luck. I kept trying loging in (every time the login manager reappeared) but suddenly I got into the black console: 

[B]Ubuntu 6.06 LTS mypcname tty1
mypcname login: [/B]

Doing Alt+F7 I could see a message such as:

> **The visualization (display?) server stopped about 6 times in the last 90 seconds. It is likely that something bad is going on. I will wait 2 minuts before trying it again in screen :0. **

which in the original Catalan version was:

> **El servidor de visualització s'ha aturat unes 6 vegades en els últims 90 segons. És probable que passi alguna cosa dolenta. S'esperarà 2 minuts abans de tornar-ho a inventar a la pantalla :0.**

I tried several things, such as: 

[B]$ gdm-restart 
[/B]
or 
[B]
$ gdm-safe-restart [/B]

with no result. I tried then:

**$ sudo /etc/init.d/gdm start **

which had the output: 
[B]
$ * Starting GNOME Display Manager[/B]

but nothing else happened. Then I tried: 

**$ startx **

with the following output in a sort of X window: 

**Xsession: warning: unable to write to /tmp; X session may eit with an error**

I then checked what is wrong with /tmp and I could see that the disk was full. Deleting some files in my home directory got the disk space under 99%. Then I tried a second time to do 

**$ startx **

which started a fresh session. From there I rebooted and everything was fine afterwards.

---

### Post by xinelo on 2006-12-20
Well, well... 

The same thing has happened again today, so much time later.

When I try to log in a pop up window says something like: 

> GDM has not been able to write in your authorization file. That could mean that you've run ouf of space in the disk or that your user directory could not be opened for writing. In any case, it's not possible to log in. Please contact the system's administrator.

I tried to follow the steps that got me sorted last time but it doesn't work this time. When I type $~startx in the command line I get:

```
xauth: error in locking authority file /home/xinelo/.Xauthority
```

I can stay on the console for only 90, it seems... I've tried deleting some files but with no success.

Any ideas?? 

Thank you!! xinelo

---

