---
title: "yEd problem on Xubuntu 11.10"
date: 2012-01-18
forum: Desktop Environments
---

### Post by skywatcher on 2012-01-18
I want to use the yEd graph editor on Xubuntu 11.10, but when I try to install it, I get this error:

> Could not display the GUI. This application needs access to an X Server

Can anyone please tell me how to fix this? I had no problem installing and running yEd on Linux Mint 12.

---

### Post by Toz on 2012-01-18
How are you trying to install the program? Are you running the install command (sudo ./yEd-3.8.sh) from within a terminal window (as opposed to running it in one of the virtual TTYs)?

I just downloaded and installed the program without any problems. Its actually quite a neat Visio-type java app - I'll have to give it a closer look.

---

### Post by skywatcher on 2012-01-19
Yes, I'm using what is called the "Terminal Emulator" on Xubuntu, with sudo ./yEd-3.8.sh.

I get the same message every time.

By the way, could it have something to do with Java?

---

### Post by Toz on 2012-01-19
> **skywatcher said:**
> Yes, I'm using what is called the "Terminal Emulator" on Xubuntu, with sudo ./yEd-3.8.sh.

I get the same message every time.

By the way, could it have something to do with Java?

Possibly. Which java implementation do you have installed? From the terminal window, type in the following command and post back the results:
```
java -version
```

---

### Post by skywatcher on 2012-01-20
This is what I get:

```
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

```

---

### Post by Toz on 2012-01-20
So you're running a 64-bit system. I think thats the problem. According to: [http://yed.yworks.com/support/qa/17/the-yed-linux-installer-aborts-with-error-message-what-can-do]("http://yed.yworks.com/support/qa/17/the-yed-linux-installer-aborts-with-error-message-what-can-do"), the installer can fail on 64-bit systems, because the installer is 32-bit. According to that same link, towards the bottom, there are instructions for manually installing (don't worry about the part about installing the official Oracle versino of Java - it works fine with the java you have installed).

Another option you could try, is to install the 32-bit libraries in your 64-bit install to see if that helps:
```
sudo apt-get install ia32-libs
```

---

### Post by skywatcher on 2012-01-24
Hi Toz

Thanks for the help. I'll give it a try.

---

### Post by gnuts on 2012-02-03
hello I ran into his problem on my 64 bit install and your suggestion worked, after installing ia32-libs the installer ran fine without sun's official java. Thank you!

---

