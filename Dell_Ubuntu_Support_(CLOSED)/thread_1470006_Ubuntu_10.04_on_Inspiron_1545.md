---
title: "Ubuntu 10.04 on Inspiron 1545"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BabaBlackSheep on 2010-05-02
The good news is 10.04 installs fine (Except for some sort of IO error at the end of the installation, but then it boots right in.) Internet works, sound works, etc.

The problem comes in when after X amount of time of use the system basically undergoes a catastrophic failure of sorts. This is what I did both times to get the same results:

1.Using the GUI programs tool, I install some basic applications (Pidgin, ZSNES, Compiz Config, nothing too outlandish).
2. I get the dependencies for MPD (Music Player Daemon) which includes glib. Glib requires gettext. I install gettext via aptitude and I compile the latest glib from source and install it.
3. I install MPD and begin to try and configure it some.

It is at the end of that third step when my system fails catastrophically. Applications fail to execute, the system refuses to shut down properly, and once forced off Ubuntu refuses to boot. I typically note that the system is in this failed state has stopped working when I attempt to run gedit from the terminal. It gives me some error which I can't recall correctly, but it did mention symlinks in it. Aside from that I don't install or change any other files. Just bringing this to the Ubuntu community's attention.

Also note, this problem never happened in Ubuntu 9.04 or .10

edit: For the record, I did this from a clean install twice.

---

### Post by Jimtheplanner on 2010-05-03
Hi i'm happy it went well for you. I have a couple of issues with my 1545.

1) Every so often I get a flash across my screen like the it's refreshing and freezes for a split second - very annoying this did not happen with 9.10.

2) My hard drive area just under the left hand palm rest can get very hot!!

Normally I use Mandriva gnome and KDE - the gnome runs warmer however its cool compared to 10.04.

Does the above happen for you?????

Jim

---

### Post by Black Jack on 2010-05-03
hello.

I use ubuntu on dell inspiron 1545 but i need drivers for the intgarted webcam and for the intgrated microphone. any one can help me please

B.R.

---

### Post by Jimtheplanner on 2010-05-03
BR,

Sorry I dont have any of the integrated stuff I use a plug in Logitech webcam for sight and sound...

Jim

---

### Post by Jimtheplanner on 2010-05-03
Ok Folks,

From a previous post for heat problems by chaosz911:-

```
$ sudo apt-get install cpufrequtils lm-sensors
$ sudo sensors-detect
```

then 

(answer yes to all questions with sensors-detect, this will add the proper modules to /etc/modules)

```
$ sudo cpufreq-set -g ondemand
```

(This will lower your cpu speed if you do not use it and thus make things even more cool)

And to test if it all went we

```
$ cpufreq-info
$ sensors
```

For me so far so good - and a bonus my screen flicker has stopped!!!

So far....

Jim

---

