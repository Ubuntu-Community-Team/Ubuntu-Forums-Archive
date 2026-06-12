---
title: "System getting shut down abruptly in ubuntu 11.10"
date: 2012-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cyclokar on 2012-03-25
Hello,
       I recently partitioned my hard drive and used around 55 GB of my D drive for Ubuntu 11.10 , i am also running windows 7 in my system.(Dual) Whenever i use ubuntu my system get shut down suddenly after half an hour or so , abruptly! irrespective of the processes I am running. And if I try to boot immediately it never happens , as in I dont even reach the OS loader page where I usually get to choose between Windows or Ubuntu , system again shuts down well before that. But I dont see any such problems when using Windows 7 .I am not sure if it is a hardware related issue cause the problem is only with  Ubuntu. Using a dell inspiron 4gb
Could anyone please help me out with the issue.

---

### Post by gordintoronto on 2012-03-25
Please describe your hardware: laptop or desktop? CPU? Video? Memory?

One of the things which might cause this problem is overheating. To see the temperatures, install lm-sensors, then open a Terminal (command line) and run this command: sensors-detect
Say yes to everything, reboot, and the command: sensors
will show you as many temperatures as your chips will produce.

There are some things you can do to reduce the temperatures, but they generally depend on what hardware is in your computer.

Then again, the shutdowns might have nothing to do with overheating.

---

### Post by cyclokar on 2012-03-25
> **gordintoronto said:**
> Please describe your hardware: laptop or desktop? CPU? Video? Memory?

One of the things which might cause this problem is overheating. To see the temperatures, install lm-sensors, then open a Terminal (command line) and run this command: sensors-detect
Say yes to everything, reboot, and the command: sensors
will show you as many temperatures as your chips will produce.

There are some things you can do to reduce the temperatures, but they generally depend on what hardware is in your computer.

Then again, the shutdowns might have nothing to do with overheating.

Regarding my hardware-
Dell Inspiron N5010 laptop
core i5 processor
4gb memory (2.27 Ghz)
320 gb hard drive
How does one reduce the temperature, other than by some external means? installing sensors will just tell me my systems situation .. is there any package that i can run that controls the internal fans .. turning it faster or running it for a longer time etc

---

### Post by gordintoronto on 2012-03-25
Yes, there are ways. For example, 10 seconds in Google found this:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)

I think there are more ways. I don't think that writeup talks about the fans at all.

But first, find out if that's the problem.

---

### Post by cyclokar on 2012-03-26
> **gordintoronto said:**
> Yes, there are ways. For example, 10 seconds in Google found this:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)

I think there are more ways. I don't think that writeup talks about the fans at all.

But first, find out if that's the problem.

Yeah, i dont know if overheating is the real issue here , thanks anyway!

---

