---
title: "chronometer"
date: 2009-03-01
forum: Desktop Environments
---

### Post by hirohitosan on 2009-03-01
Hi guys.

Anyone know of a chronometer for Ubuntu (Gnome)? A GUI one I mean with a start-stop-reset button.

I tried some buici-clock, alarm-clock, wmclockmon, but I'm not satisfied with them. 

Thank you.

---

### Post by slimx3m on 2009-05-08
you could try this [http://linux.softpedia.com/progDownload/stopWatch-Download-40439.html](http://linux.softpedia.com/progDownload/stopWatch-Download-40439.html).  i think that this is what you are looking for

---

### Post by colau on 2009-05-08
> **slimx3m said:**
> you could try this [http://linux.softpedia.com/progDownload/stopWatch-Download-40439.html](http://linux.softpedia.com/progDownload/stopWatch-Download-40439.html).  i think that this is what you are looking for
I downloaded 87163-stopWatch_v1.tar.gz.
tar vzxf 87163-stopWatch_v1.tar.gz
Going to that directory ./configure does not work.
How to install it?

---

### Post by slimx3m on 2009-05-08
> **colau said:**
> I downloaded 87163-stopWatch_v1.tar.gz.
tar vzxf 87163-stopWatch_v1.tar.gz
Going to that directory ./configure does not work.
How to install it?
all you have to do is to run
```
./stopWatch
```
and that should do the trick.  make sure that you are on the "stopWatch" folder first.

hope that helps

---

### Post by colau on 2009-05-08
> **slimx3m said:**
> all you have to do is to run
```
./stopWatch
```
and that should do the trick.  make sure that you are on the "stopWatch" folder first.

hope that helps
I did this.The result is
```

./stopWatch: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

---

### Post by slimx3m on 2009-05-08
> **colau said:**
> I did this.The result is
```

./stopWatch: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```
it needs this library in order to be able to perform.  you could always get dependicis by going to synaptic package manage and downloading them.

so this is what you will need to do...
in the terminal type the following command
```
sudo apt-get install libqt3-mt
```
or...
1)open synaptic package manage
2)download/install a file called "libqt3-mt"

hope this helps.

---

### Post by KegHead on 2009-05-08
Hi!

What you need is a chronograph.

A chronometer is a precision swiss watch made by various companies.

KegHead

---

### Post by Afanluc on 2010-01-11
There is a program called "stopwatch" in the repository (universe); at least for Ubuntu 9.10, I don't know if for earlier versions. I think that is what you are looking for. You can install it from Synaptic.

It has milliseconds, but you can turn that of.

There is a menu listing in order to start/stop the chronometer, but you can also start/stop it easily by pressing "s" with the keyboard. (There is also a start/stop large button)

---

