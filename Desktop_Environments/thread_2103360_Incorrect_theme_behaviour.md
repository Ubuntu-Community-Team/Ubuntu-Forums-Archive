---
title: "Incorrect theme behaviour"
date: 2013-01-10
forum: Desktop Environments
---

### Post by ThrashManiac on 2013-01-10
Hi everyone! 

I'd like to ask you how to tweak installed theme. 

I have 'greybird-gtk' and it's all nice, except for this one: 
[[img]http://s1.postimage.org/go4qd9szv/20130109_234324.jpg[/img]](http://postimage.org/image/go4qd9szv/)
As you can see - the background of selected day is incorrect. After I put mice pointer on it - it receives the correct color. 

Could you please help me out with this one? ):P

---

### Post by morgengenuss on 2013-01-10
Well first of all I need a bit of information:
 * what version of Ubuntu/Gtk3 are you using?
 * what version of Greybird are you using?

What parts did you modify exactly (usually the top panel should be dark iirc, although I personally don't use Unity).

---

### Post by ThrashManiac on 2013-01-10
You are right: 
```
$ dpkg -l libgtk[0-9]* | grep ^i
ii  libgtk2-perl                           2:1.223-1build3                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                            2.24.10-0ubuntu6                        GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.24.10-0ubuntu6                        programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                       2.24.10-0ubuntu6                        common files for the GTK+ graphical user interface library
```
Latest Greybird, sorry, I don't know how to get it's version. 

Not modified. Ubuntu 12.04 with compiz effects on.

Does it help?

---

### Post by morgengenuss on 2013-01-10
Well it doesn't help too much. First of all, "latest" isn't clear because it depends on where you got the "latest" from. If it's the main Ubuntu repository, then you might wanna pull Greybird from git instead (use the gtk3.4 branch if you're on 12.04).

What panel are you using there exactly? Unity?

---

### Post by ThrashManiac on 2013-01-11
> **morgengenuss said:**
> Well it doesn't help too much. First of all, "latest" isn't clear because it depends on where you got the "latest" from. If it's the main Ubuntu repository, then you might wanna pull Greybird from git instead (use the gtk3.4 branch if you're on 12.04).

What panel are you using there exactly? Unity?

Okay, I've used this one: 
```
sudo su
add-apt-repository ppa:shimmerproject/ppa
apt-get update
apt-get install shimmer-themes-greybird
```
...and , yes, I use the Unity desktop.

---

### Post by Frogs Hair on 2013-01-11
I installed via the same PPA and have just tested the theme in Unity and XFCE and can't reproduce the problem. If you just changed the theme log out and back in. I notice that on occasion I have to do this to get certain themes to display properly. If that doesn't work I have no idea what the problem is.

---

### Post by morgengenuss on 2013-01-11
> if you just changed the theme log out and back in. I notice that on occasion i have to do this to get certain themes to display properly.
+1

---

### Post by ThrashManiac on 2013-01-11
> **Frogs Hair said:**
> I installed via the same PPA and have just tested the theme in Unity and XFCE and can't reproduce the problem. If you just changed the theme log out and back in. I notice that on occasion I have to do this to get certain themes to display properly. If that doesn't work I have no idea what the problem is.
I have logged in and out about 20 times before I have written this topic. Try pressing on the calendar opener multiple times.

---

### Post by morgengenuss on 2013-01-13
Have you tried using the latest version from our github repository?
You can download the version for Gtk3.4 here: [https://github.com/shimmerproject/Greybird/archive/gtk3.4.zip](https://github.com/shimmerproject/Greybird/archive/gtk3.4.zip)

---

### Post by ThrashManiac on 2013-01-14
> **morgengenuss said:**
> Have you tried using the latest version from our github repository?
You can download the version for Gtk3.4 here: [https://github.com/shimmerproject/Greybird/archive/gtk3.4.zip](https://github.com/shimmerproject/Greybird/archive/gtk3.4.zip)

Thanks, I'll try it today.

---

### Post by satya164 on 2013-01-16
Sorry for the delay. It will be fixed soon.

---

