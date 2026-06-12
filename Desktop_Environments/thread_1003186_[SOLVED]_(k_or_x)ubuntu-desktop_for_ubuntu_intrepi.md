---
title: "[SOLVED] (k or x)ubuntu-desktop for ubuntu intrepid 64bit"
date: 2008-12-05
forum: Desktop Environments
---

### Post by sheishkabob on 2008-12-05
I recently researched several versions of Linux to find one i liked. I originally went away from ubuntu, because i wanted more than 1 single desktop environment. While playing with ubuntu in virtualBox, i found a way to get all three ubuntu (gnome), Kubuntu (KDE), and Xubuntu (XFCE)on one partition, one could simply choose the environment at login.

I did this with synaptic. I chose to install the kubuntu-desktop and xubuntu-desktop packages. (this was i386 mode)

I liked that feature and installed it on my empty partition and now that i have it installed (64bit) the (x and k)ubuntu-desktop packages are not there. I imagine it's simply that the source isn't in my source list, and i've searched and i can't find the source locations to add for intrepid (i've found like 50 for gutsy). I'm also wondering if 64bit is the reason.

So my question is: can someone tell me the source (or even better, where to find it) and also, is the linux kernal the 64-bit part? Will installing Kubuntu-desktop the same way as before, still be 64-bit or do i have to specify that i wan't 64bit?

---

### Post by taurus on 2008-12-05
What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```
Otherwise, you can post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Zorael on 2008-12-05
I'm not sure I understand.

Pretty much all packages have 64-bit equavilents, so there's no reason you shouldn't be able to install all three alongside eachother like you did in virtualbox. The repositories are the same so you don't need to find any special 64-bit repo.

As for kernels, just get -generic or -rt or -xen or whatever you want; there's no -amd64 kernel image anymore. You'll do just fine with -generic.


And use aptitude, not apt-get! :3
```
$ sudo aptitude update
$ sudo aptitude install kubuntu-desktop xubuntu-desktop
```

---

### Post by sheishkabob on 2008-12-05
Thanks.  That's working so far (it's running still). I knew of that command, but I just assumed it wouldn't work if synaptic didn't list it. (obviously I'm kinda new to Linux) I'll know better next time.

---

### Post by sheishkabob on 2008-12-05
What's the difference in apt-get and aptitude? Apt-get is what i used, (since i started before you did in posting). Is aptitude better for 64bit?

---

### Post by Zorael on 2008-12-05
If you use 'apt-get **autoremove**' when removing packages (instead of just 'apt-get **remove**'), the difference is minimal. Aptitude is slower and a bit more zealous with installing recommended packages, but it's *worlds* better at resolving broken dependencies.

See [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude).

---

### Post by taurus on 2008-12-05
[http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/](http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/)

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

