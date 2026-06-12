---
title: "Unable to install Ubuntu windows installer"
date: 2011-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tejas19587 on 2011-06-30
Hi Guys,
When i am installing the windows version of ubuntu at the end, afterinstallation is almost completing, it gives an error message:
 
Permission denied, for more information go to c\users\tejas\appdate\local\temp\wubi-11.04-rev211
 
Need your help to get this sorted.
 
Thanks

---

### Post by bcbc on 2011-06-30
You can post the log... or to make it easier just use [this option]("https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F") to install: > ...download both Wubi.exe and the required Desktop ISO from the same location (the release has to match):

For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

Then when you run wubi it will pick up the ISO and install.

If you'd rather figure out the problem, go to the %temp% directory (click START, enter %temp%) and find the log file wubi-11.04-rev211.log.

---

### Post by life in color on 2011-07-01
If push comes to shove and you're unable to install Ubuntu through WUBI you could always just try a LiveCD.

---

### Post by bcbc on 2011-07-01
I just noticed the [lubuntu] tag. You can't install lubuntu with Wubi (not in the current release).

---

### Post by tejas19587 on 2011-07-01
> **bcbc said:**
> You can post the log... or to make it easier just use [this option]("https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F") to install: 
 
Then when you run wubi it will pick up the ISO and install.
 
If you'd rather figure out the problem, go to the %temp% directory (click START, enter %temp%) and find the log file wubi-11.04-rev211.log.
 
I do have the internet connection, so it should work. The solution you recommend, i guess is for those who have no net connection. 
 
I have attached the logs, i cannot make much of it. Let me know if you find anything in it. 
 
I wanted this windows installer to work as i did not want to boot from CD every time i want to use ubuntu.

---

### Post by tejas19587 on 2011-07-01
> **bcbc said:**
> I just noticed the [lubuntu] tag. You can't install lubuntu with Wubi (not in the current release).
 
Sorry for that i am trying ubuntu only. I selected lubuntu in hurry.......

---

### Post by bcbc on 2011-07-01
> **tejas19587 said:**
> I do have the internet connection, so it should work. The solution you recommend, i guess is for those who have no net connection. 
 
I have attached the logs, i cannot make much of it. Let me know if you find anything in it. 
 
I wanted this windows installer to work as i did not want to boot from CD every time i want to use ubuntu.

It says no internet in the guide but it happens to be the best solution with internet as well.

The problem you are having is the bittorrent downloader that wubi uses is being denied access. Either by your windows firewall or another firewall. You have to allow pyrun.exe (python runtime) access to your firewall, or use an alternative method if it's someone elses firewall.

---

### Post by tejas19587 on 2011-07-02
I got a live cd from one of the linux publications, and installed it on my system. 
For now ubuntu loads properly and no issues till now. 
But when on the boot sceen, it shows below three nw entries along with windows:
Ubuntu, with Linux 2.6.38-8-generic
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+,serial console 115200)
Windows 7 (loader) (on /dev/sda2)
 
I am not sure why i see three new entries ? Have i installed the correct copy of ubuntu ?

---

### Post by bcbc on 2011-07-02
> **tejas19587 said:**
> I got a live cd from one of the linux publications, and installed it on my system. 
For now ubuntu loads properly and no issues till now. 
But when on the boot sceen, it shows below three nw entries along with windows:
Ubuntu, with Linux 2.6.38-8-generic
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+,serial console 115200)
Windows 7 (loader) (on /dev/sda2)
 
I am not sure why i see three new entries ? Have i installed the correct copy of ubuntu ?
The first entry is for the 2.6.38-8-generic kernel. The next entry is for the recovery mode comes with each separate kernel and allows to repair problems etc.
Memtest allows you to check for memory problems.
You can customize (or learn more about) these [here]("http://ubuntuforums.org/showthread.php?t=1287602").

---

