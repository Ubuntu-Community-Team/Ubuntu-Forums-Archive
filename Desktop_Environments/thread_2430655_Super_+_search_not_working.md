---
title: "Super + search not working"
date: 2019-11-05
forum: Desktop Environments
---

### Post by robwilson.laptop on 2019-11-05
(New user, first ever question, please be gentle)

  When I hit Super and start typing the name of a bit of  software, nothing whatsoever comes up in the search below the search  box, but if I know the exact name of what I'm trying to open and I type  it in full, it opens.

  If, say, I want GIMP and I do <super>GI, I used to get search results for "GI...", now I get a blank screen underneath the search box.  If I do <super>GIMP<return>, it opens GIMP.

Happening since I upgraded to 19.10 yesterday.   Logouts and reboots have made no difference.

---

### Post by TheFu on 2019-11-05
Ubuntu 19.10 changed many things. Canonical decided to try out lots of things that might not be ready for general use.  If you want an OS that is stable, stick with an LTS release like 18.04.

Reasonable question. Asked pretty well.  With GUI questions, it is best to lead with the exact release and DE being used so nobody has to guess.  For example, I'm running: 
```
$ more /etc/lsb-release
...
Ubuntu **16.04.6** LTS
```

And my DE is:
```
$ inxi -F
System:    Host: posc Kernel: 4.15.0-66-generic x86_64 (64 bit)
           Desktop: **FVWM 2.6.5** Distro: Ubuntu 16.04 xenial

```
The solution for my DE is different than the solution for whatever DE you happen to be running.

---

### Post by deadflowr on 2019-11-05
Which desktop session?
I know in unity (Ubuntu's old desktop) it removes the lens packages upon upgrade ( or it did, maybe they fixed that),
so you need to reinstall those
```
sudo apt install unity-lens-files unity-lens-applications
```
If gnome desktop (Ubuntu 's new default desktop), try disabling any added extensions.

---

### Post by robwilson.laptop on 2019-11-06
Desktop: Gnome 3.34.1
Distro: Ubuntu 19.10 (Eoan Ermine) 

I've disabled every gnome tweak extension in turn, no effect on my issue.

---

### Post by robwilson.laptop on 2019-11-07
Issue solved with -

sudo apt-get --reinstall install yaru-theme-gnome-shell

---

