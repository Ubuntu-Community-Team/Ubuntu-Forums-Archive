---
title: "Canon i550 trouble, dont know how to deal with it"
date: 2006-09-07
forum: Desktop Environments
---

### Post by tillsch on 2006-09-07
Hello english-speaking friends :p ,

I'm writing this because I have serious problems with my printer (Canon i550) and because the german forum [www.ubuntuusers.de](www.ubuntuusers.de) wasn't able to help me. I didn't even get an answer, that's frustrating.
There is a guide in the wiki of ubuntuusers.de how to install a Canon printer and I followed all these steps:

1. First I loaded the bjfiltercups-2.2-1.i386.rpm and the bjfilterpixus550i-2.2-1.i386.rpm from a japanese server and converted them with alien to debs.

2. I installed libxml1, libglade0, libpng3 and libtiff4 and after that the files of step 1.

3. Some symbolics must be set up:
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libpng10.so.0.1.0.18 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2s

4. To register the new libraries I typed in the console 'sudo ldconfig'

5. I tested the new configuration with 'bjfilterpixus550i':
BJLSTART
ControlMode=Common
SetTime=20060828211125
BJLEND
 

6. Than I installed the printer. 

And now the virtually problem: whatever I want to print, the printing job gets interrupted and a red exclamation mark appears in the panel. The printer should be alright, he did his job perfectly under Windows and Fedora Core 5 on the same computer (The problem is that I deleted the other partitions and now can not print anymore, but have to :-k ).
Here is the cups error_log, maybe it will help to aproximate to the problem:

tilmann@desktop:/var/log/cups$ cat error_log | tail
E [28/Aug/2006:21:27:00 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:00 +0200] Resume-Printer: Unauthorized
E [28/Aug/2006:21:27:00 +0200] PID 8168 (/usr/lib/cups/backend/canon_parallel) stopped with status 1!
E [28/Aug/2006:21:27:00 +0200] [Job 9] No %%BoundingBox: comment in header!
E [28/Aug/2006:21:27:00 +0200] [Job 9] Unable to open parallel port device file "": No such file or directory
E [28/Aug/2006:21:27:49 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [28/Aug/2006:21:27:59 +0200] cupsdAuthorize: Local authentication certificate not found!

I hope you could help me, this is serious because I need the printer soon. Hope you have some ideas. I'm very grateful to all kind of answers.

regards to all, till

---

### Post by tillsch on 2006-09-07
I got it. 

You have to go in the printer settings -->  connection. There you choose a printer by indicating the port "LPT #1" (no other!). Now the error shouldn't occur anymore.

---

