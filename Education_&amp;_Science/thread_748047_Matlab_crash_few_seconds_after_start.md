---
title: "Matlab crash few seconds after start"
date: 2008-04-07
forum: Education &amp; Science
---

### Post by mulpac on 2008-04-07
Hello,

Matlab installed fine and when starting first the splash screen comes up and then the matlab window is visible for a few seconds saying "Initiallizing" on the status line at the bottom, but then it crashes.
It crashes the same way even with -nodisplay:

 matlab -nodisplay

                                                    Version 7.6.0.324 (R2008a)
                                                   
terminate called after throwing an instance of 'MathWorks::System::SimpleException'
(SIGABRT) (core dumped)

Version R2007a crashes in a similar way, but the message is a little bit different:
terminate called after throwing an instance of 'MathWorks::System::_utException'

The computer is running 32-bit kubuntu 7.10 Gutsy Gibbon on an AMD64 BE2400 (dual core). I have googled a lot, but so far I have only found troubles related to Simulink and Java and Compiz (which I am not running). Any ideas on how to solve this problem?

---

### Post by kbless7 on 2008-04-10
have you tried reinstalling?

---

### Post by twistadias on 2008-04-11
same thing happens to me. It opens up fine if you start it from the terminal
```
matlabroot/bin/matlab
```
but the terminal window remains open at the same time. is there any way to hide this??

found this on the matlab homepage  [http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/unix/f0-43815.html&http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=KMF&q=matlab+2008+unix+guide&btnG=Search&meta=](http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/unix/f0-43815.html&http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=KMF&q=matlab+2008+unix+guide&btnG=Search&meta=)

seems that we have to start the license manager.
the how to says that we have to go to the matlabroot/etc directory
but there isn't an etc directory in the matlab folder

---

### Post by kbless7 on 2008-04-11
launch by using
```
matlab/bin/matlab -desktop
```
this causes it to launch without the shell of a terminal

---

### Post by dimamali on 2008-05-26
My case now :-D
I have Matlab7.1 installed on Hardy and Wine.
I still get that frozen matlab spalsh screen and my cpu goes to 100% but that's all.
I tried to run Matlab from the shell but i get an error. I think it has to do with JVM.
Any suggestions?

Thanx in advance!

---

### Post by ahmatti on 2008-05-26
> **dimamali said:**
> My case now :-D
I have Matlab7.1 installed on Hardy and Wine.
I still get that frozen matlab spalsh screen and my cpu goes to 100% but that's all.
I tried to run Matlab from the shell but i get an error. I think it has to do with JVM.
Any suggestions?


I suggest you get the native linux version of Matlab if possible. I have no experience in running Matlab under wine, but the native version runs nicely.

---

### Post by aimran on 2008-05-26
Are you guys running AMD64s? That could  be the problem as described here: [http://unitstep.net/blog/2006/08/21/getting-matlab-to-run-on-a-newer-athlon-64-x2-cpu/](http://unitstep.net/blog/2006/08/21/getting-matlab-to-run-on-a-newer-athlon-64-x2-cpu/)

Even though it's on the windows version I feel the problem is similar. I had it on my xp install too.

---

### Post by 00marcvs on 2008-08-26
I just had this very same problem on a xen virtual machine.

The reason for this is the missing /dev/pts directory and the missing mount.

This can be fixed by adding these two lines to /etc/rc.local

 mkdir /dev/pts
 mount -t devpts devpts /dev/pts

Good Luck, 
M.

---

### Post by Proton Soup on 2008-08-26
> **twistadias said:**
> same thing happens to me. It opens up fine if you start it from the terminal
```
matlabroot/bin/matlab
```
but the terminal window remains open at the same time. is there any way to hide this??

found this on the matlab homepage  [http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/unix/f0-43815.html&http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=KMF&q=matlab+2008+unix+guide&btnG=Search&meta=](http://www.mathworks.com/access/helpdesk/help/base/install/index.html?/access/helpdesk/help/base/install/unix/f0-43815.html&http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=KMF&q=matlab+2008+unix+guide&btnG=Search&meta=)

seems that we have to start the license manager.
the how to says that we have to go to the matlabroot/etc directory
but there isn't an etc directory in the matlab folder

it's been about 12 years since i used Matlab, and not on Linux, so take this for what it's worth, but i suspect that 'matlabroot' is a system variable within Matlab itself and holds the path of Matlab's root directory on your system.  that might be C:\Program Files\Matlab on a winders box, but in linux maybe something else, like root root.

and i assume the rest of you are using a student version, because as much as a Matlab license costs for professionals, i'd think they'd deal with you personally to get you going here.

---

### Post by Crafty Kisses on 2008-08-26
Post the results of > top

When the program is open.

---

### Post by zainmsud on 2008-09-22
Try this:

[http://unitstep.net/blog/2006/08/21/getting-matlab-to-run-on-a-newer-athlon-64-x2-cpu/](http://unitstep.net/blog/2006/08/21/getting-matlab-to-run-on-a-newer-athlon-64-x2-cpu/)

[http://www.codecomments.com/archive381-2005-5-505181.html](http://www.codecomments.com/archive381-2005-5-505181.html)

---

### Post by trigoman05 on 2009-02-11
Following this : [http://phchshow.blogspot.com/2008/10/matlab-error.html](http://phchshow.blogspot.com/2008/10/matlab-error.html)

Solved my problem

Hope it helps.

---

### Post by Timmmm on 2009-06-01
I also had this problem (Ubuntu 64 bit on AMD Opterons). Worked fine from a terminal but from a shortcut or the run dialog it just shows the splash for a second then exits.

Using 'matlab -desktop' fixed this.

Thanks!

---

