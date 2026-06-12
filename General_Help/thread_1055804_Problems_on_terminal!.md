---
title: "Problems on terminal!"
date: 2009-01-31
forum: General Help
---

### Post by azmo35 on 2009-01-31
Hi,i found something useful for me,this software called SmartCam i know i have to compile the kernel because mine is latest on Ubuntu 8.04.1, this is mi start on learn more thins on Linux so i used this two [http://www.simplehelp.net/2008/11/19/how-to-use-your-nokia-n95-as-a-wireless-webcam/](http://www.simplehelp.net/2008/11/19/how-to-use-your-nokia-n95-as-a-wireless-webcam/)
and
[http://www.noeman.org/gsm/symbian-os-9-1-applications/56377-smartcam-smart-phone-web-camera-update-5-8-08-a.html](http://www.noeman.org/gsm/symbian-os-9-1-applications/56377-smartcam-smart-phone-web-camera-update-5-8-08-a.html)
when on terminal i run [cd] command and return [HTML]azmo@azmo-laptop:~$ cd documents
bash: cd: documents: No such file or directory
azmo@azmo-laptop:~$ documents
bash: documents: command not found
azmo@azmo-laptop:~$ ~/ documents
bash: /home/azmo/: is a directory
azmo@azmo-laptop:~$ cd /documents
bash: cd: /documents: No such file or directory
azmo@azmo-laptop:~$ cd documents
[/HTML]
What i'm doing wrong? 
Any help on to compile this[because i'm still a new to linux but i wanted learn] will be appreciate thanks in advance,azmo.

---

### Post by binbash on 2009-01-31
There is no directory called documents under your home.Try cd Documents since d and D is different at linux

---

### Post by azmo35 on 2009-01-31
Thanks, i'm so idiot, now i will try folow the toturial.

---

### Post by x33a on 2009-01-31
always try ls -la to see which files and folders (including hidden ones) are present under the current directory.

---

