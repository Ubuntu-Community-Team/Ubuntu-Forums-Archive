---
title: "help!can't run/install matlab on ubuntu!"
date: 2005-03-12
forum: Desktop Environments
---

### Post by lorap on 2005-03-12
installation beginning i get these messages:

/media/usb-cdrom/install: line 1: /lib/libc.so.6: Permission denied
/tmp/6537tmwinstall/install: line 1: /lib/libc.so.6: Permission denied

but installation continues farther.after installing,when i try to run it i get this error:

Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.
Warning: Could not access OpenGL library

< M A T L A B >
Copyright 1984-2004 The MathWorks, Inc.
Version 7.0.0.19901 (R14)
May 06, 2004

??? Undefined function or variable 'matlabrc'.

something interesting else,when i break an installation i get this:

tmp/6537tmwinstall/install: /media/usb-cdrom/install: /bin/sh: bad interpreter: Permission denied
/tmp/6537tmwinstall/install: line 300: /media/usb-cdrom/install: Success

that's all.
if somebody has matlab installed help me please
i'm a student at faculty for applied mathematics,so i can't exist without it,i need it for laboratories.
in microsoft i've it working fine.
thanks
pavel

---

### Post by oVerCaffeinated on 2005-03-12
"Permission denied" comes up when you don't have root access. So try putting sudo before your commands.

---

### Post by lorap on 2005-03-12
hi friend!
that's you again!
yup i alway used "sudo" cause if i didn't i wouldn't install it and i did but it didn't work.
i need this matlab like an air,if you find a way out how to install it let me know please.
thank you very much Friend for you being trying to help people.
this thing has no cost that highcostly it's.
pavel

---

### Post by GilGalad on 2005-03-12
Hi,

I have installed that same version of matlab in hoary without a problem. I got the error of "/lib/libc.so.6 permission denied" but that's because it tries to execute the library. However that error is harmless and matlab loads ok.

TBH, I have not idea why it is failing for you. Did you check out the file install_matlab.out for errors? 

Also, could you post the output of "matlab -n"?

Cheers.

---

### Post by lorap on 2005-03-12
yup :-)
i installed it also but when i try to run it it loads up and closes leaving this error message:

Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.
Warning: Could not access OpenGL library

< M A T L A B >
Copyright 1984-2004 The MathWorks, Inc.
Version 7.0.0.19901 (R14)
May 06, 2004

??? Undefined function or variable 'matlabrc'.

can you say what it's?(or should i say: "can you say what is it",tell me please how is right to say cause english isn't my motherlanguagr)

thanks
pavel

---

### Post by GilGalad on 2005-03-12
Type:

matlab -n

in the terminal and send the output.

P.S. can you say what it is? is the more correct...

---

### Post by lorap on 2005-03-12
i've typed matlab -n and got this:

Warning: Unrecognized MATLAB option "n".
Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.
Warning: Could not access OpenGL library

                              < M A T L A B >
                  Copyright 1984-2004 The MathWorks, Inc.
                         Version 7.0.0.19901 (R14)
                                May 06, 2004

??? Undefined function or variable 'matlabrc'.

can you tell me what should i install esle to get it work?
thanks
pavel

---

### Post by GilGalad on 2005-03-13
It sounds like you are trying to run the matlab binary which is in /usr/local/matlab7/bin/glnx86/MATLAB instead of the script which sets up all the variables and is in /usr/local/matlab7/bin/matlab and usually linked in /usr/local/bin/matlab.

You need to run the matlab shell script. It should be in /usr/local/matlab7/bin/matlab. If it is not you have done something wrong in the installation.

---

### Post by lorap on 2005-03-13
no,i've installed everything here:

/home/lorap(my user name)/usr/matlab

and you're right,to run the matlab i go to the directory:
matlab7/bin/glnx86/MATLAB

you probably already understand what kind of mistake i've done,at least i'm feeling that you do :-)

buddy,help me please i need it like an air.
thank you.
pavel

---

### Post by GilGalad on 2005-03-13
No, to start matlab you have to type:

/home/lorap/usr/matlab/matlab7/bin/matlab

---

### Post by lorap on 2005-03-13
thank you very much friend!
i'll try it as soon as i get home and let you know,
probably you'll need to tell me if it wouldn't work what directories i should install to to have it working.
but anyway,when i run /home/lorap/usr/matlab7/bin/ng86/matlab
it begins to run but falls...
thank you again
pavel

---

### Post by lorap on 2005-03-13
hi again friend!
that's probably a problem cause there's no matlab directory inside bin directory.
this's what it's:

/home/lorap/usr/matlab7/bin/glnx86

/home/lorap/usr/matlab7/bin/mac(macintosh)

and so on but no matlab inside bin

probably i should have choosed another folders view.
let me know what it was in your case.
thanks again.
pavel.

---

### Post by gluon on 2005-03-13
I had problems with Matlab 7 before. The problem I had was that I hadn't installed the program properly.

After you've installed Matlab from CD, go to installation directory $MATLAB and execute install_matlab. That command sets up matlabrc and all other necessary files.

If you want to create a desktop icon or a menu icon for Matlab, use the command ```
matlab setsid $MATLAB/bin -desktop
``` to launch Matlab. Replace $MATLAB with your installation directory.

Hope that helps.

---

### Post by lorap on 2005-03-13
hi friend!
you just don't know how highcostly your solution is for me...
thank you very much,i'll try it just in 2 and 1/2 hour,once i get home.
i've only one question:what way should i run install_matlab script.
do you mean like this?
sudo sh /......../......./matlab/install_matlab
this way?
thank you very much again.
pavel

---

### Post by lorap on 2005-03-13
my dear friends!
you both helped me to solve this problem!
thank you very much!
today i sau "good bye microsoft"!
matlab was the only thing was keeping me there.
i had to run script "install_matlab" afterwhat to go to the "scripts" directory and run "matlab" script.that's all.
thank you very much friends.
pavel

p.s.:
the last one question :-)
how can i make a link to run matlab not from the desktop but from the panel?
thank you again.
pavel

---

### Post by drasko on 2005-03-13
Never tried matlab under linux, but are you considered using Scilab -- it's open source and free.

Regards,
Drasko

---

### Post by lorap on 2005-03-13
hi friend!
it works.
never heard about that product.
i need matlab cause i study mathematics.
that's our laboratory's primary tool :-)
pavel

---

### Post by acorrigan on 2005-03-13
You all helped me too.

I tried installing Ubuntu last week, but had to reinstall windows after I couldn't get matlab installed (I need it for all of my classes except for my writing class)

But now I should be able to fully switch to linux.

Thank you everyone.

---

### Post by lorap on 2005-03-14
hi friend!
you can completely move to linux cause it's possible to do everything windows does and much more.
the only difficulty i've had was to run matlab,but buddies helped me to solve it.now if somebody needs install matlab i would know how to instruct the one installing it.
have you a nice day friend!
pavel

---

### Post by bored2k on 2005-03-14
[QUOTE=lorap]hi friend!
you can completely move to linux cause it's possible to do everything windows does and much more.
the only difficulty i've had was to run matlab,but buddies helped me to solve it.now if somebody needs install matlab i would know how to instruct the one installing it.
have you a nice day friend!
pavel[/QUOTE]
 A how-to maybe?

---

### Post by lorap on 2005-03-14
is there any place called "how to" so i can leave an instruction there?
pavel

---

### Post by bored2k on 2005-03-14
[QUOTE=lorap]is there any place called "how to" so i can leave an instruction there?
pavel[/QUOTE]
 Yep
[Ubuntu FAQs & HOWTOs](http://ubuntuforums.org/forumdisplay.php?f=15)

---

### Post by lorap on 2005-03-14
thanks :-)
i'll go there right now and leave an instruction.
pavel

---

### Post by offby1 on 2005-03-19
I'm looking at this thread and seeing a lot of similarities to my own situation with matlab 7, but the solutions you have proposed do not solve my problem.

I am running (via a symlink) the $MATLAB/bin/matlab script to launch Matlab, and whether I run it as superuser or as my regular user, I get the error
> /usr/local/bin/matlab: line 1: /lib/libc.so.6: Permission denied 
Obviously, this is not good.  Well, not obviously, actually.  For the most part, everything works fine.  I can do most of the pure matlab functions, but when I try to use the symbolic math toolkit, say by doing this:
```

>> syms a b c
>> Fns = [a^2 + 2*b + 3*c*b, 2*a + 3*c, 4 + a + b^3]

```
I get the error message
> 
Unable to load mex file: /opt/matlab/toolbox/symbolic/maplemex.mexglx.
/opt/matlab/bin/glnx86/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
??? Invalid MEX-file '/opt/matlab/toolbox/symbolic/maplemex.mexglx': .

Error in ==> maple at 104
[result,status] = maplemex(statement);

Error in ==> sym.maple at 85
[result,status] = maple(statement);

Error in ==> sym.mpower at 17
   B = maple(A,'^',p);


> 
ls -l /lib/libc.so.6
lrwxrwxrwx    1 root     root           13 2004-12-27 17:22 /lib/libc.so.6 -> libc-2.3.2.so

ls -l /lib/libc-2.3.2.so
-rw-r--r--    1 root     root      1214160 2004-10-27 00:00 /lib/libc-2.3.2.so


How would I go about fixing this?  Is anyone else with Matlab on Ubuntu having this problem?

---

### Post by offby1 on 2005-03-19
Self-reply:

It turns out that Matlab has some weirdness with its JRE linking that requires the environment variable LD_ASSUME_KERNEL=2.4.1 to be set in order to link properly.

So, this works around the problem I was having (though not the "Permission Denied" issue, which appeard to be orthogonal to the mex-file failure -- assistance with that is still quite desirable!)

```
LD_ASSUME_KERNEL=2.4.1 matlab $(opts)
```

---

### Post by nick58b on 2005-04-01
Thanks, the "LD_ASSUME_KERNEL=2.4.1 matlab" fixed the Invalid MEX-file problem for me on hoary RC.  Also, running 

```
sudo chmod 755 /lib/libc-2.3.2.so
``` fixed that startup message (but another one, not causing problems yet, took its place).

Anyway, it appears matlab is working now.  And for the record, I had the exact same problem with Matlab R14 SP1 on Fedora Core 3.

---

### Post by Canuck on 2005-10-16
Hello,

I am having a different problem installing Matlab. I have been following the Wiki guide on how to install it ([https://wiki.ubuntu.com/MATLAB]("https://wiki.ubuntu.com/MATLAB")) and I get the following error when trying to make an image in the temp file.


command used: [COLOR="Blue"]sudo cp -R /media/cdrom1 /tmp/matlab[/COLOR]

Error Received: [COLOR="Red"]cp: reading `/media/cdrom1/win32/help/base/install/pc/mhelp.dat': Input/output error[/COLOR]


Anyone have any suggestions on how to remedy the situation. By the way I am trying to install the student version R14 SP1 and am running Breezy.

Canuck

P.S.  I am very new to Linux so if you have any suggestions on different approaches please keep the instuctions simple.  :)

---

### Post by ssavelan on 2007-02-04
I do have matlab running pretty well in ubuntu......

but, I have:

Warning: Could not query OpenGL.
Warning: OpenGL appears to be installed incorrectly.

when I enter... 

as I am not very good at matlab,  I am unable to tell when I am messing up the code and when it is the OpenGL...

I think anytime you see 'Permission denied' running the same command preceded by sudo is always a good first thing to try.

---

### Post by skywatcher on 2007-02-11
Hi all

Please excuse me for butting in, but I've been following this thread with mounting concern. I installed Ubuntu on my notebook yesterday in the hope of eventually moving away from Windows, but now I'm wondering about the wisdom of this move. I use Matlab extensively, but from this thread (and one or two others) I get the impression that I can expect a lot of trouble trying to use Matlab with Ubuntu. If this is the case, what about other software such as LaTex, Inkscape, Nvu, etc?

---

### Post by ssavelan on 2007-02-12
No need to fret!

My Matlab (for OSX or Linux) actually runs great on Edgy, super even.  I also use the Citrix client to log onto my school's network to use beaucoup proprietary math software with the remote desktop.  So, I can (and do) run two Matlab's at once without a problem.  Many people with windows flounder around with their security level in "Internet Options" trying to run citrix on their XP machines.  I couldn't get it to work on Windows quickly enough to care if it works in Windows (apparently it does).

Of course, as a newly partisan open source lover, I would rather use SAGE/Python and wish that my school facilitated/taught/dealt with this dynamic programming mathematical language project.

[http://modular.math.washington.edu/sage/]("http://modular.math.washington.edu/sage/")

SAGE is a great project,  nipping at the heels if not surpassing Matlab, Maple, Mathematica, etc.....

New version released every few weeks, recently:  very active, very well-supported, intuitive, powerful, dope, tight, phat, etc......  Oh yeah and Ubuntu is Sage's most supported platform next to Mac.:guitar: 

Generally, everything works best for me running Edgy over earlier distros.

---

### Post by ssavelan on 2007-02-12
*running Edgy as opposed to earlier distros*

for those with Breezy, Dapper, etc........

---

### Post by skywatcher on 2007-02-15
Hi

I had a look at Sage. It can never compete with Matlab, unless all you want to do is maths. At present there is nothing to compete with Matlab's great variety of toolboxes and Simulink, all based on the huge set of Matlab functions.

This is why I still hope that someone on the forum can help me get around my problems with installing Matlab R2006b on Ubuntu.

Cheers,

Chris

---

### Post by ssavelan on 2007-02-16
[IMG]/home/biouser/Desktop/tach3.png[/IMG]

---

### Post by ssavelan on 2007-02-16
Darn, I just editted the above post with some great instructions and information and then lost it somehow.

Anyway, in brief, never say never.  Sage interfaces with Octave, yadayada, Matlab is perhaps necessary for engineering, but octave is very similar.  Python and Matlab are both dynamic prog. languages.  I'm vaguely offended... whatever.....

----------------------------------------------------
1.
Is your Matlab for Linux?  The version of Matlab I have was designed to run on Linux or Mac.  The documentation on the CD was good.  We encountered no problems.

2.
Your version of Matlab is not for Linux, but Win:

[http://appdb.winehq.org/appview.php?iAppId=49]("http://appdb.winehq.org/appview.php?iAppId=49")

Wine will run your Matlab in Linux.

3.
Are you affilliated with an institution that will let you log in by remote desktop to Matlab?  I use the Citrix client for linux and run Matlab through my school.  It works perfectly.

So, I run Matlab from within Ubuntu by methods one and three.  You may need to take advantage of method two.

Let me know if that works out.

Good Luck

---

### Post by fletc900 on 2007-03-26
For those using Ubuntu Edgy, the LD_ASSUME_KERNEL=2.4.1 trick does not work. Follow the directions on this link to get the Symbolic Toolbox working again:


[http://remmirath-en.blogspot.com/2006/12/matlab-symbolic-toolbox-on-linux.html](http://remmirath-en.blogspot.com/2006/12/matlab-symbolic-toolbox-on-linux.html)


Cheers

---

### Post by TheTinman on 2007-09-09
> **fletc900 said:**
> 
[http://remmirath-en.blogspot.com/2006/12/matlab-symbolic-toolbox-on-linux.html](http://remmirath-en.blogspot.com/2006/12/matlab-symbolic-toolbox-on-linux.html)


Thanks for the link.  FYI this fix also works for Feisty.

---

### Post by marrabld on 2007-09-19
Have you all tried octave?

I have done most of my undergrad using it and it is nearly %100 syntax compatible! even for image processing

it wont do gui's tho, (inputdlg etc) ... yet.

qtoctave gives you an IDE but is not in the repos yet. (you can find it in the debian repos though)

[www.octave.org](www.octave.org)

```
sudo apt-get install octave octave-forge
```

octave-forge should give you the comunity written *.m files

:guitar:

---

### Post by enavarro on 2007-12-17
Xubuntu 7.10
Matlab 7 R14 (7.0.0.19901)

Solution for "Warning: Could not access OpenGL library"

[http://www.mathworks.com/support/solutions/data/1-18N21.html?solution=1-18N21](http://www.mathworks.com/support/solutions/data/1-18N21.html?solution=1-18N21)

Upon install I got the nasty "could not load OpenGL error"

I tried using my system's libs as suggested in mathworks site. -> warning persisted.

Second, I tried using a combination of 

libGL.so -> /usr/lib/libGL.so.100.14.19 (the one used by the system symlink)
libGLU.so -> original matlab library.

Result -> Success!

Ran smoothly.

---

