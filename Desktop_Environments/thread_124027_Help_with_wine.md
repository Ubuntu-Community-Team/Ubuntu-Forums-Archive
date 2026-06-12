---
title: "Help with wine"
date: 2006-01-31
forum: Desktop Environments
---

### Post by nami on 2006-01-31
Hi

I want to run a windows program on ubuntu and am guessing Wine is the approach to take.

It's a 3D Chat program.

Can anyone help with the installation, configuration, and how to use Wine?

nami

---

### Post by Mickey1 on 2006-01-31
in terminal type 
```

sudo apt-get install wine

```

when you downloaded your setup.exe  open with wine :-)

---

### Post by nami on 2006-02-01
Thanks.

How do I open it with Wine if I have already downloaded it onto my desktop?

---

### Post by nami on 2006-02-01
I tried that and it didn't work.  Here are the installation screenshots.  You can see the error in the last screenshot:

[[IMG]http://img217.imageshack.us/img217/7612/screenshot1pa.th.png[/IMG]](http://img217.imageshack.us/img217/7612/screenshot1pa.png)

[[IMG]http://img88.imageshack.us/img88/5622/screenshot16lj.th.png[/IMG]](http://img88.imageshack.us/img88/5622/screenshot16lj.png)

[[IMG]http://img55.imageshack.us/img55/2530/screenshot26gf.th.png[/IMG]](http://img55.imageshack.us/img55/2530/screenshot26gf.png)

[[IMG]http://img86.imageshack.us/img86/2223/screenshot39az.th.png[/IMG]](http://img86.imageshack.us/img86/2223/screenshot39az.png)

[[IMG]http://img85.imageshack.us/img85/5096/screenshot45te.th.png[/IMG]](http://img85.imageshack.us/img85/5096/screenshot45te.png)

---

### Post by geekphreak on 2006-02-01
This error might have been caused by missing Windows dll files or something like that. Your wine installation is most likely fine.

---

### Post by nami on 2006-02-01
So does that mean it can't be run on breezy?

---

### Post by geekphreak on 2006-02-01
Check the application database on wine's homepage to see whether anyone's done it successfully. Generally, if some files are missing, without the missing files you will not be able to run it, but you might copy those from somewhere and tweak things to make it work.

---

### Post by nami on 2006-02-01
Doesn't look to promising.  Can't find it in the list.  The program is called There.com.

---

### Post by Sutekh on 2006-02-01
After installing wine, you should run 'winecfg' from a terminal or Alt+F2.

You may need to set some settings, including the version of Windows that wine will mimic the behaviour of, or to choose how wine implements windows libraries (.dlls).

Check out the wine guide for a better explanation and maybesome tips for you to get this working.
[WineHQ- Wine User Guide]("http://www.winehq.com/site/docs/wineusr-guide/index")

---

### Post by nami on 2006-05-20
I've seen a website where some was able to get IMVU (another windows 3d chat) working on linux.  Has no one been able to get There.com working yet.  It needs Internet Explorer to work!

How do I install internet explorer and then use wine to start both internet explorer and there.com?

---

