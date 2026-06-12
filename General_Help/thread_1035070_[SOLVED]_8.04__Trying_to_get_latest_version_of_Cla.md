---
title: "[SOLVED] 8.04  Trying to get latest version of Clamav"
date: 2009-01-09
forum: General Help
---

### Post by thelugnut on 2009-01-09
I am trying to install the latest version of "Clamav" (0.94.2)

I downloaded the file to desktop.

Then made the following entries in the terminal:

> james@home:~/Desktop/clamav-0.94.2$ make
make: *** No targets specified and no makefile found.  Stop.
james@home:~/Desktop/clamav-0.94.2$ sudo make install
make: *** No rule to make target `install'.  Stop.
james@home:~/Desktop/clamav-0.94.2$ make launcher
make: *** No rule to make target `launcher'.  Stop.
james@home:~/Desktop/clamav-0.94.2$ 

I really am not familiar with using "tar" so any suggestions?:confused:

---

### Post by tuxxy on 2009-01-09
You can install the ClamAV including in the repos much easier, search for clamav in Synaptic or enter in the terminal

```
sudo apt-get install clamav
```

If you really want to install the latest version did you run /configure before make?

---

### Post by thelugnut on 2009-01-09
thanks for the reply.
I did install Clamav using Synaptic, but when I run the "freshclam", I get the following printout:
> james@home:~$ sudo freshclam
[sudo] password for james:xxxxxxxxxx 
ClamAV update process started at Fri Jan  9 16:58:47 2009
WARNING: Can't query current.cvd.clamav.net
WARNING: Invalid DNS reply. Falling back to HTTP mode.
Reading CVD header (main.cvd): OK (IMS)
main.cvd is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
Reading CVD header (daily.cvd): OK
daily.inc is up to date (version: 8848, sigs: 49299, f-level: 38, builder: ccordes)
WARNING: Current functionality level = 26, recommended = 38
Please check if ClamAV tools are linked against the proper version of libclamav

The version number is 0.92.1 and I assumed I needed the latest version 0.94.2. 
I know I went awry somewhere but don't know how to get back on track.:confused:

---

### Post by Thanh-BKK on 2009-01-29
Hello.

I am facing the exact same problem. I am completely unable to get updated signatures, using ClamAV 0.92.1 and ClamTK 4.08, sitting on virus definitions from 11. February 2008. 

My system is Hardy 8.04.1

My terminal messages are exactly like the OP's except mine recommends 35 as "functionality level".

When i attempt to do it through the GUI (sudo clamtk) i get a terminal output "I don't have any paths!"

Please help us out.... thanks in advance.

Kind regards......

Thanh

---

