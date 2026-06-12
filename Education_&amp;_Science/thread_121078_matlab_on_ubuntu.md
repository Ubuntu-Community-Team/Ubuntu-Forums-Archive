---
title: "matlab on ubuntu"
date: 2006-01-24
forum: Education &amp; Science
---

### Post by NiTsi on 2006-01-24
i want to install matlab in my ubuntu.can anyone tell me if i can install version 7 on ubuntu. Furthermore i want to know if i can find it for free....

---

### Post by madu on 2006-01-24
You will never get Matlab for free...!!!
I think there is a Linux version of Matlab.. If you want Matlab for free you can try Freemat.. or Scilab (I think..)..

---

### Post by Adrian on 2006-01-24
[QUOTE=madu]If you want Matlab for free you can try Freemat.. or Scilab (I think..)..[/QUOTE]

Or [Octave]("http://www.octave.org/")...

---

### Post by Iesos on 2006-01-24
What I know of, most contries consider it a fellony to "steal" software.
And you won't get it for free without breking some laws (but it is possible, but I dont recomend it).
You should instead install Octave. Its a free software that is just like MATLAB, commands and everything. The only difference is that Octave has some plotting problems.
Take a look at: [http://www.octave.org/](http://www.octave.org/)

---

### Post by Adrian on 2006-01-24
[QUOTE=NiTsi]i want to install matlab in my ubuntu.can anyone tell me if i can install version 7 on ubuntu. Furthermore i want to know if i can find it for free....[/QUOTE]

Yes, you can. If you are a student, there are student versions available for a small amount of money (you have to buy them from your local university/school though).

---

### Post by Adrian on 2006-01-24
[QUOTE=Iesos]The only difference is that Octave has some plotting problems.
Take a look at: [http://www.octave.org/](http://www.octave.org/)[/QUOTE]

There are a lot more differences, especially if you consider all non-free toolboxes that you can buy for Matlab. However, for a lot of users, Octave is more than enough.

---

### Post by ubuntuuser on 2006-01-24
[QUOTE=NiTsi]i want to install matlab in my ubuntu.can anyone tell me if i can install version 7 on ubuntu. Furthermore i want to know if i can find it for free....[/QUOTE]
As the others already said, you won't find it for free...

...unless you are a student and your university has licenses for students. My uni for example has setup a license server, so when I am online (and I always am), Matlab contacts the server and gets a license. Your university software department has to give you an initial license file before you can install it, but after that it's just like installing a program in Windoze, nice graphical installer and stuff. And it works fine, just like the Win version, I use Matlab 7 R14.

---

### Post by NiTsi on 2006-01-29
Thanks guys for your answers.You broke my heart since noone told me a good solution. Octave is not enough and my university doesn't give licenses to students for matlab.Apart from all these i know it is illegal to steal software. Anyway i've heard for cases who put matlab in their linux only by "making"/"changing"/"hacking" the license.

---

### Post by phen on 2006-01-29
try scilab. it is slow compared to matlab, but if you don't need serious number crunching power, it is fast enough by far. it is developed by a french university (i think), and runs just fine. there's even a free simulink add on. maybe you find other toolboxes, too!

---

### Post by mirna on 2006-01-30
Actually the student version costs ~ US $100. I know because I have one. 
I need help on setting matlab mode in emacs.
I got the matlab.el and compiled it into .elc file. I put these into
\usr\share\emacs\site-lisp
directory of my hoary. 
I read on the web that I need to edit .emacs file, but I don't know how to edit it, and I'm not sure if I put the .el and .elc files into the right directory. I compiled .el into .elc inside emacs. I have no knowledge of lisp.
Please, help!!!

Mirna

---

### Post by punchy on 2006-02-14
Hi,

I was in your position exactly. And I do believe I have a good answer: python.

its free, very well supported, and evolving rapidly.

Python has modules which you can load.

One of these is called "numeric", or "scipy". there are tons of other with which you can e.g. plot (e.g. 'biggles').. with the numeric python, you have commands which are matrix oriented, just like in matlab. and many functions for fitting, optimization, solving differential equations or eigenvalue problems are included as well.

google the following: (and this is just a small selection)

scipy
python
vaults of parnassus
 
have fun,
punchy

---

### Post by hizaguchi on 2006-03-29
One possibility is that your department office may have a loaner student copy of Matlab.  Mine did, but it was version 4.0.

Another thing to check for would be to see if your school has a server for running research software remotely via ssh (or ssh -X).  My university has just about everything I could ever need on their servers... even office applications.

But I'm really curious what you're doing that Octave can't handle without a little ingenuity.  Granted, I don't do alot of Matlab type work, but I've actually started to consider Octave to be superior, not just a free alternative.  It supports some useful coding that Matlab does not (or at least, that I don't know how to do in Matlab), and if you upgrade to Dapper you can get kOctave out of the repositories and enjoy a much better editor than what comes with Matlab.  Then there is the documentation, which I have found to be much friendlier.  And most importantly... the "Save and run" button!

---

### Post by [h2o] on 2006-04-25
Matlab Student Version doesn't have to cost much at all, depending on the niceness of your university. My Matlab 7 cost me about 7$. Now I just have to install it on Ubuntu, which proved to be a bit harder than necessary :neutral:

---

### Post by mips on 2006-04-25
[http://www.ubuntuforums.org/showthread.php?t=29919](http://www.ubuntuforums.org/showthread.php?t=29919)
[http://www.ubuntuforums.org/showthread.php?t=142557](http://www.ubuntuforums.org/showthread.php?t=142557)
[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)
[https://wiki.ubuntu.com/MATLAB](https://wiki.ubuntu.com/MATLAB)

---

### Post by leeyee on 2006-05-11
I was in your position too! But now I have decided to use Scilab as an alternative, I have MATLAB CDs here, but they are pirated! I won't use it anymore. Under linux, you can use many thing for free, and freedom.
Actually, Scilab is a really good software, and it has some useful toolboxes such as Signal Processing etc. My major is Information Engineering, so it's enough for me. To be honest, I don't like Octave and don't recommend you to use it either. It has some problems when plotting curves and it has no GUI under GNOME (There is one for KDE if i recall). What's more, It has no changes these monthes actually.

---

### Post by u04f061 on 2006-05-31
[QUOTE=leeyee]I was in your position too! But now I have decided to use Scilab as an alternative, I have MATLAB CDs here, but they are pirated! I won't use it anymore. Under linux, you can use many thing for free, and freedom.
Actually, Scilab is a really good software, and it has some useful toolboxes such as Signal Processing etc. My major is Information Engineering, so it's enough for me. To be honest, I don't like Octave and don't recommend you to use it either. It has some problems when plotting curves and it has no GUI under GNOME (There is one for KDE if i recall). What's more, It has no changes these monthes actually.[/QUOTE]

problem with me in using scilab is that i can't read the font it offers.can u tell me how can i change the font of main command line of scilab?

do u use the same unreadable font or have changed?

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE='[h2o]']Matlab Student Version doesn't have to cost much at all, depending on the niceness of your university. My Matlab 7 cost me about 7$. Now I just have to install it on Ubuntu, which proved to be a bit harder than necessary :neutral:[/QUOTE]
Can you (or anybody else) tell me if you got it working under Ubuntu 6.06? I haven't managed it yet - I'm still stuck on the error where it says

*** glibc detected *** malloc(): memory corruption: 0x000000000059b770 ***
Aborted

when you try to run it. This is with an AMD64 install of Dapper, if it makes any difference.

---

### Post by girishsasikumar on 2008-05-04
Well I am an old user of matlab and a fairly new user of Ubuntu, and the sticky part of ubuntu was that I could not run matlab. And for people doing work on EEE or DSP or Control system projects matlab is a life line........i spent quiet a lot of time searching and working to get matlab running on ubuntu....
So here it is 
I have used Ubuntu Hardy Heron final release with wine and Java Virtual machine Installed in wine......
Well I used matlab 6.1 installed in my windows drives.......dunno about newer ones.....but should work........

[LIST=1]
[*]Open 'Applications\Wine\Browse C:\drive'
[*]Copy 'C:\program files\matlab' or wherever else the matlab installation is in windows
[*]Paste it to wine\c_drive\program files
[*]open '\....\matlab\bin\win32\license.dat' with a text editor
[*]You will see a line something like this 
INCREMENT Optimization_Toolbox MLM 12 01-jan-0000 uncounted \ 	2B90825F7119 HOSTID=DISK_SERIAL_NUM=[COLOR="Red"]8b856f8[/COLOR] PLATFORMS=i86_n \
[*]copy the disk serial number eg 8b856f8
[*]open 'Applications\Wine\configure wine'
[*]in the 'Applications tab' choose 'Add application'
[*]browse and select '\....\wine\c_drive\program files\matlab\bin\win32\matlab.exe'
[*]choose windows xp as the operating system
[*]in the 'drivers' tab select 'show advanced'
[*]in the drive c label and serial number, set to 'manual assign'
[*]paste the drive serial number you copied from license.dat into the 'serial' field and click apply
[*]now if u run the matlab.exe file in \wine\c_drive\programfiles\matlab\bin\win32 it should work
[/LIST]

well it worked for me..........
I tested out quiet a few matlab commands and MPC tool boxes in simulink, they worked very well, actually faster than in my windows install

now for the useless part of the discussion.........

u could add matlab to the applications tab, by adding a custom application launcher to your applications tab, and change the icon of the launcher to the cool matlab icon we all like and love from \wine\c_drive\program files\matlab\bin\win32\matlab.ico

hope u like this solution !!!!

and a cool foto of matlab in ubuntu..........

[IMG]http://picasaweb.google.com/girishsasikumar/Ubuntu/photo#5196465951775072962[/IMG]

well i cant upload the foto.......

so here is the link
[http://picasaweb.google.com/girishsasikumar/Ubuntu/photo#5196465951775072962](http://picasaweb.google.com/girishsasikumar/Ubuntu/photo#5196465951775072962)

---

### Post by anaGP on 2008-05-27
HELP ME!!!!
I have installed matlab 7 on linux. Use the distribution kubuntu (Ubuntu 8,04 kernel 2.6.24 - 16 - generic).
Matlab does not recognize mex - setup (it gives a license error -2). But in line of command of linux yes works well mex -setup.
Also when I want to use guide, it does not work (it gives license error -2).
I followed the installation passages that I found in forums and I do not see differences with which I did  Somebody can give some suggestion me?  Will be that I need some license?
 Somebody has the license of the Matlab 7 R14 that can command to me by mail? 
Thank you very much
AnaGP

---

### Post by linuxnovice on 2008-06-09
One more possibility is that if you know Python, you could use the extentions Scipy and Numpy. [http://www.scipy.org](http://www.scipy.org).

---

### Post by Buzzdee on 2008-06-12
I installed Matlab 7 (R14 if I recall correctly) without issues on Gutsy x86 64-bit using the graphical installer and the procedure in the instructions. Works like a charm.

---

### Post by aumi_khan on 2008-06-13
hi,
i know it is not good but sometime we need to do this kind of things.
you can download the latest version of MATLAB from torrent. 
i am an engineering student and i need to use MATLAB because in my university, they use MATLAB and some commands are not same on MATLAB, Octave or Scilab.

---

### Post by fmonjaraz on 2008-06-25
Torrentz!!!!!!!!! Matlab 2008 works great under hardy..much better than any open software..

---

