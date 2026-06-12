---
title: "ABAQUS: finite element analysis"
date: 2007-10-21
forum: Education &amp; Science
---

### Post by neoflight on 2007-10-21
Anyone here using ABAQUS?  i am using it for my research. I have to learn python to do the scripting now. just wondering if anyone experienced with ABAQUS here could help with some questions...

thnks

---

### Post by ro314 on 2007-10-22
I am working on PhD Thesis using ABAQUS. Scripting is explained in the "ABAQUS Scripting User's Manual". 
In case you are not familiar with Python - it is not necessary to learn all the details of the python language to be able to write ABAQUS scripts...
Any specific questions?
greetings,
Robert

---

### Post by cherry316316 on 2007-10-28
> **ro314 said:**
> I am working on PhD Thesis using ABAQUS. Scripting is explained in the "ABAQUS Scripting User's Manual". 
In case you are not familiar with Python - it is not necessary to learn all the details of the python language to be able to write ABAQUS scripts...
Any specific questions?
greetings,
Robert

how did u install Abaqus on ubuntu
i am trying to install Abaqus 6.7 on Ubuntu 7.10
but no success so far, 
also the setup file in abaqus folder dont run

it says :
```
bash: setup: command not found 
```

then I went into the folder which has "install.bin
and used the following command
```
 chmod a+x install.bin
./install.bin 
```
this went till some step , but in the end, it was not able to verify the installation and exit with error
:(

pls pls help me

---

### Post by ro314 on 2007-10-29
> **cherry316316 said:**
> how did u install Abaqus on ubuntu
i am trying to install Abaqus 6.7 on Ubuntu 7.10
but no success so far, 
also the setup file in abaqus folder dont run


hi!
unfortunately i have never installed abaqus myself - our system administrator is doing these things. i can not even ask him - he is on holiday. i remember he once said that installing abaqus in ubuntu (which is not officially suported) is quite tricky. 
good luck,
robert

---

### Post by cherry316316 on 2007-10-31
> **ro314 said:**
> hi!
unfortunately i have never installed abaqus myself - our system administrator is doing these things. i can not even ask him - he is on holiday. i remember he once said that installing abaqus in ubuntu (which is not officially suported) is quite tricky. 
good luck,
robert

well , Thanks

in case you come to know something then do let me know

cherry

---

### Post by cherry316316 on 2007-11-07
> **ro314 said:**
> hi!
unfortunately i have never installed abaqus myself - our system administrator is doing these things. i can not even ask him - he is on holiday. i remember he once said that installing abaqus in ubuntu (which is not officially suported) is quite tricky. 
good luck,
robert

I want to install Abaqus on my computer Ubuntu 7.10 gusty.

I am trying from many days, but no success so far.

I also installed MESA separately but when i run "/media/cdrom0/setuo -sysinfo" it gives me following output
if you have success of installing or running Abaqus so far, then please let me know. I am using Abaqus 6.7, but I also have
cd for Abaqus 6.6

I have also installed FORTRAN , g++ , sun-java6 and mesa , but it refuses to verify.

when i tried to run abaqus installer according to the command given on your blog
"/media/cdrom0/setup -nosystemchecks -jre /usr/lib/jvm/java-6-sun/jre/  -console"
because when i write  "-jre system" it says VM not found and stuff.

so with the above command, it do runs and install the Abaqus, but when I run Abaqus after installation,
it runs in full transparent mode, which I dont know how to fix. I have also attach the screen shot of the
Abaqus when i run after this installation.
 [IMG]http://www.its.caltech.edu/~dev/Screenshot.png [/IMG]



my output from```
 "/media/cdrom0/setup -sysinfo" 
```:


```

root@cherry-laptop:/home/cherry# /media/cdrom0/setup -sysinfo

A scratch directory is required for the execution of the
Abaqus installation procedure.

TMPDIR is not defined on this system.  Provide the full path
to the scratch directory.

Scratch directory is: /tmp

Checking system requirements for Abaqus.  This will
take just a moment...
Checking for GNU Lib C version 2.3.2 or newer.
Pass - Found GNU Lib C Version 2.6.1.
WARNING: Unknown Linux distribution type found on this system just setting base
         kernel version information.

Running system configuration checks for Linux/x86-32.
Please wait until all the needed information has been gathered...

Current system configuration is:

Hostname:             cherry-laptop
Username:             root
Date:                 Wed Nov  7 00:36:31 2007
Processor:            Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
Number of CPUs:       2
Linux Distribution:   Unable to determine Linux Distribution.
Memory:               3545 Mb
Graphics Card:        nVidia Corporation unknown chipset (0x0407) rev 161
X11 Version:          Unable to determine X11 Version.
OpenGL Version:       Unable to determine OpenGL version.
X Server:
                      server glx version string: 1.4
                      client glx version string: 1.4
                      GLX version: 1.3
                      OpenGL version string: 2.1.1 NVIDIA 100.14.19


System requirement status is:

Requirement:          SuSE 9.3, 10.0 or 10.1, SuSE Enterprise Linux 9.0 or
                      10.0, SuSE Enterprise Desktop 10, Red Hat Enterprise 3.0
                      or 4.0
Products:             All Abaqus Products
Status:               Fail - Unable to determine Linux Distribution.

Requirement:          GNU Lib C 2.3.2 or greater
Products:             All Abaqus Products
Status:               Pass - Found GNU Lib C 2.6.1.

Requirement:          Linux Kernel 2.4.20 or newer
Products:             All Abaqus Products
Status:               Pass - Found Linux Kernel 2.6.22-14-generic.

Requirement:          GNU Compiler Suite 3.2 or later
Products:             Abaqus make utility with C++ and Abaqus make utility with
                      Fortran and Abaqus with user subroutines
Status:               Pass - Found gcc version 4.1.3

Requirement:          Intel 32-bits C++ Compiler 9.1
Products:             Abaqus make utility with C++
Status:               Fail - Unable to locate and/or determine the version of a
                      C++ compiler on this system.

Requirement:          Intel 32-bits Fortran Compiler 9.1
Products:             Abaqus make utility with Fortran and Abaqus with user
                      subroutines
Status:               Fail - Unable to locate and/or determine the version of a
                      Fortran compiler on this system.

Requirement:          HP-MPI 02.02.05.00
Products:             Abaqus analyses using MPI-based parallelization
Status:               Fail - Unable to locate a supported MPI implementation on
                      this system. For more information on the MPI-based
                      parallel functionality, see the section 'Parallel
                      processing modes in Abaqus' in the Abaqus Analysis User's
                      Manual.

Requirement:          Mesa 4.3.0 or greater
Products:             Abaqus/CAE and Abaqus/Viewer
Status:               Fail - Unable to determine Mesa version.

Requirement:          XFree86 or Xorg server must be configured to load the glx
                      module
Products:             Abaqus/CAE and Abaqus/Viewer
Status:               Pass

Requirement:          Netscape 7.0, Mozilla 1.2, Firefox 1.0.1, or greater
Products:             Abaqus Documentation
Status:               Pass - Found Firefox 2.0.0.8

Not all requirement checks succeeded.



...finished.
```

---

### Post by dandelo on 2007-11-25
It's a compiz problem.

Insert this before "abaqus cae" command:

XLIB_SKIP_ARGB_VISUALS=1

ex: XLIB_SKIP_ARGB_VISUALS=1 */abaqus_dir*/abaqus cae

Or you have to disable desktop effects

---

### Post by cherry316316 on 2007-11-25
Dear Dandelo,

Thanks a million.

I tried many things from many days, I was in the impression, that there is problem in installation , or may be java etc etc . but nothing helped.

Thanks again 

cherry :)

---

### Post by cherry316316 on 2007-11-25
:)

---

### Post by AlexVader on 2008-01-19
Hi cherry316316

I have been following this topic with interest... sinc I am an engineer who wishes to shift completely from MScrap to Linux...

The problem is that most of my productivity software tools are oriented to WinBlowze...

Anyway, i am using a Laptop, ASUS F3Jr, and i have narrowed my distro search to three candidates:

CentOS 5.1, Ubuntu 7.10, and Suse Linux 10.0.

My choices are rather restrictive, i look for a distro that will "fit into" my hardware with the least tweaking possible (Ubuntu is the clear winner... :-) ) AND will support the software that i use at work...

So far i have managed to install CFD analysis codes in Ubuntu, CAD tools (pro/Engineer ), and i want to proceed to FEA multiphysics tools;

I have two of them, one is ANSYS Multiphysics 10.0, and the other is Abaqus 6.7.

As far as i know, simulia does not support Gutsy, so...

I had tp convert the rpm of termcap w/ alien so as to extract the libtermcap package to /lib, so that the documentation install would not complain.

Since Ubuntu is not supported, i installed the Abaqus product w/ the option /media/cdrom0/setup --nosystemcheck...

Install went allright, started licence server, configured the product... ok.

The only issue is that when i start /usr/local/abaqus/command/abaqus cae,
the app states that there is an abaqus CAE kernel error, if i start it w/o the gui... like in /usr/local/abaqus/command/abaqus, i can run any job i want.

Could you please give me a hint on what am i missing here? maybe some packege, or lib...  ?

So far i have only installed Abaqus in  W***&5@ or Suse Linux 10.0, and used it without any problems...     :-)

Personally, for my kind of work i don't think Multiphysics is a match for Abaqus...   

Is it possible to run abaqus Jobs in interactive environment under Ubuntu 7.10 so as i do in Suse Linux 10.0?
If it is, what should i do to have abaqus CAE running under Ubuntu Gutsy 7.10?

Thanks for your time.

Alex

---

### Post by cherry316316 on 2008-01-20
Hi, it is very much possible to run Abaqus in Ubuntu with out any problem.
for your satisfaction, I have also attached a screen shot of my desktop with Abaqus running on it.

But on the other hand, I am not a very experienced user of Linux,
for some reason, I have everything working just fine on my laptop at present, thanks to all the forums. and I just goto windows only for using skype video , rest I stay all time on ubuntu though.

But, it took me more then 2-3 weeks to make Abaqus running on Ubuntu, as it is not supported on Ubuntu and also , I was 1st trying Abaqus 6.5.

anyway, the last thing i remember is running the documentation 
from the cd directly using -nosystemcheck command
if that doesnt work, i also tried one more thing for installing documention.

I copied the cd on my desktop, then navigate to the documentation installation directory , there u will find a "/media/cdrom0/UNIX/install.bin" which you can run by using the command ```
 chmod a+x install.bin 
 ./install 
```
also , for documentation, you check this website
[http://www.engin.brown.edu:2080/v6.7/](http://www.engin.brown.edu:2080/v6.7/)

well , for installing Abaqus, you have to use 
```
 /cd/setup -nosystemcheck 
```
and for running Abaqus, you can make a link for abaqus in your 
/usr/bin directory using command
```
 ln -s /usr/local/abaqus/command/abaqus  /usr/bin/abaqus

```

but as pointed out above, due to desktop effects, you will get problem when you will run Abaqus . there for you have to use following command
```

XLIB_SKIP_ARGB_VISUALS=1 /abaqus_dir/abaqus cae
[CODE]

or I have made a alias for this command in my bash file
for making alias, in case you don't know, you can check my friends website
[http://debianrules.blogspot.com/2006/02/alias.html](http://debianrules.blogspot.com/2006/02/alias.html)

so i made the alias as 
[CODE] alias abaqus="XLIB_SKIP_ARGB_VISUALS=1 /abaqus_dir/abaqus" 
```
and now for running cae, i use command abaqus -cae and for running job, i use command abaqus -job 

regarding your kernel problem, so I have no idea, make be you can try updating your system and reinstalling Abaqus from scratch.
also, just try to command which is mention above for running gui
XLIB_SKIP_ARGB_VISUALS=1
and see if it works.

good luck and let us know what did you get, i will try to check my system again later in day and see if I can give you some more help.

---

### Post by AlexVader on 2008-01-20
Thanks Cherry316316...

I followed almost the same sequence as you did... I only skipped that flag about disabling desktop effects...

Ok, Uninstalled Abaqus and will start from scatch...  Just tell me, did you upgrade Ubuntu with the MESA, Fortran Compiler, and the rest of the stuff in which the install test fails...?

I didn't do it, and maybe that's the point...   I Installed the documentation, activated the server, installed the licensing application, and Abaqus with the option /media/cdrom0/setup --nosystemcheck without even trying to upgrade... the only upgrade i did before was installing the different shells from Synaptics, nothing "Abaqus related" at least not directly...

Do you think it might be that...? the cause of cae Kernel error stuff... ?

Thanks for your fast answer...  :-)

Alex

---

### Post by cherry316316 on 2008-01-20
well, as I remember , I did install MESA and fortran complier and stuff,
as I was stuck with the installation pretty much like you and I tried all the things possible. But, I am not sure which one helped me in the end.

i also checked this website and contacted the guy, as he is the administrator for his lab
[http://blogs.cae.tntech.edu/mwr/2007/05/03/abaqus-66-on-debian-etch-amd64-port/](http://blogs.cae.tntech.edu/mwr/2007/05/03/abaqus-66-on-debian-etch-amd64-port/)

and , as I check my old emails to various person, i see a comment :
[COLOR="Blue"]I have also installed FORTRAN , g++ , sun-java6 and mesa , but it refuses to verify.[/COLOR]
in the end, it was unable to verify the mesa, but it worked well with it, for verification , it uses some wired stuff which does not fit well on ubuntu , but with nosystemcheck it works fine
But there is mesa and DRI provided in Ubuntu also, 
so you can try following command also
```
 abaqus cae -mesa 
```
but if you want you can installed mesa from this website
[http://www.mesa3d.org/](http://www.mesa3d.org/)
and install DRI [http://www.mesa3d.org/](http://www.mesa3d.org/) for better
performance

then my next comment was
[COLOR="Blue"]when i tried to run abaqus installer according to the command given on your blog
"/media/cdrom0/setup -nosystemchecks -jre /usr/lib/jvm/java-6-sun/jre/  -console"
because when i write  "-jre system" it says VM not found and stuff.

so with the above command, it does runs and install the Abaqus, but when I run Abaqus after installation,
it runs in full transparent mode, which I dont know how to fix. [/COLOR]

the transparency problem was solved by avoiding the Desktop effect

so for a try , u you can use the above commands and see if they help you, try to update your kernel before installation.
well good luck.

---

### Post by AlexVader on 2008-01-21
Hi again....

Well, i will try a new fresh install of Abaqus;
Installed Fortan, G++, Mesa, Sun Java6, all with Synaptic.
One thing still puzzles me: Last time i tried, i opened an rpm for another distro, stripped the libtermcap.so out, placed it in /lib and proceeded, the installer did not complain, so i guess i was on the right track.

This time i want to know if this is the apropriate thing to do, or if i have to tweak some other package to have libtermcap installed...

I have read somewhere that the package libtermcap-compat no longer exists, searched for termcap, and libtermcap in Synaptics... no chance, does libncurses5-dev substitutes libtermcap...? do i have to edit the installer to change all termcap references to ncurses...? I have already installed all ncurses packages...   is this enough...? or should i just do like i did before, and strip libtermcap.so out of the rpm for another distro and place it in /lib ?

Thanks in advance... :-)

---

### Post by cherry316316 on 2008-01-21
i guess , i installed libtermcap from this website, by running the .deb file which i got after using alien [http://rpmfind.net/linux/rpm2html/search.php?query=libtermcap.so.2](http://rpmfind.net/linux/rpm2html/search.php?query=libtermcap.so.2)

no , i didnt convert any references to ncurses.

beside,do u have     XFree86 or Xorg server configured to load the glx module for abaqus viewer can cae ??

and for mesa, even after installing it, when you will run Abaqus -sysinfo , it won't be able to find mesa , but when u will run, it will just work fine, so dont worry

---

### Post by AlexVader on 2008-01-23
Thx Cherry,

That is the same site i downloaded termcap from...  

How do i configured XFree86 or Xorg server  to load the glx module for abaqus viewer cae...? 

Must be pretty simple, but noob as i am...   :-)   I do not see how...

:-)

Thanks

Alex

---

### Post by AlexVader on 2008-01-27
Hi again,

Made some more search in forums, and i guess that the way to load glx modules in X Server is editing the section [modules] in xorg.conf...

Could someone give me a hit on the syntax of that line...?

I mean... i hate to mess around with my xorg.conf...  had a lot of bad experiences before...  I will make a copy like xorg.confOLD, but it would be nice if someone could give me a hint on how to "mess" with [modules] without f***ing  X-Server... :-)

Thanks in advance

Alex

---

### Post by cherry316316 on 2008-01-27
this is what my xorg file says 

Section "Module"
        Load            "glx"
EndSection


beside, i don't remember on top of my head, but I guess installed separately dri.
are u still getting kernel problem ?

---

### Post by AlexVader on 2008-01-27
Didn't try yet...

Will try tomorrow... just wanted to have all variables controlled so as to know exactly what is the sequence to install correctly:

So far i have installed Fortran, G++, MESA, and Sun-Java6.
Will update my xorg.conf, and tomorrow for a fresh new install of Abaqus, with positive results...  I Hope :-D

Just want to get all the steps correctly so that i can clean winShit partition out of my laptop instead of double booting it...

I Have Abaqus installed in Win... but the WinXP sucks...If i could do all my work in Linux...  would be great....

Thanks for your time :-)

Alex

---

### Post by AlexVader on 2008-01-28
Well,  :-(

No luck man, 

Guess i will have to compile the DRI libs from  [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

I am planning to compile the libdrm-2.3.0.tar.gz from [http://dri.freedesktop.org/libdrm/](http://dri.freedesktop.org/libdrm/)

Since i am using Ubuntu 7.10 I guess i do not need to upgrade to Xorg 6.9...

One strange thing:

When i was installing the documentation, it complained about missing libtermcap.so.2... BUT i installed the termcap....deb package that resulted from 
%alien termcap...rpm,   anyway, i uncompressed the rpm package, and cp the libtermcap.so.2 (renamed the lib) to /lib...   Didn't complain anymore, and allowed me to start help server...

Installed the licensing, started the lmgrd service, installed the app, export LM_License_file=/usr/local/flexlm/licences/license.dat, and finally...

/usr/local/abaqus/Command/abaqus cae...

... well, the rest you already know...   :-(   I'm almost giving up any hope here...
...guess i will have to go back to Suse Linux 10, without any wireless...   :-(

Alex

---

### Post by AlexVader on 2008-01-29
No Luck... definitely...

I did

%tar -xzvf /home/alex/desktop/dri/libdrm-2.3.0.tar.gz 
%cd /home/alex/desktop/dri/libdrm
%./configure
%make
%make install
%make clean

and then, for the final test  ...

/usr/local/abaqus/Command/abaqus cae

...error in Abaqus/cae kernel   :(

And what sucks is that it does not tell what is missing...

And i guess it must be something simple and stupid...   :-(

My modules section in Xorg.conf is the same as yours...

I already installed Abaqus 6.7-1 x32 for Linux under Novell Suse 10.0, and OpenSuse 10.1, and SLED 10.0 SP1, it launched without any prob...

The only catch I have w/ Suse Linux 10.0 is that it does not reckon my hardware out of the box, like Ubuntu, nor does it have an update manager like Synaptic...  

The problem w/ SLED 10 SP1, or OpenSuse 10.1 is that it does not allow me to work with Pro/Engineer unlsess i am connected to the web...

I guess there is some kind of bug with PORTMAP service...

So taht really leaves me w/ only two options Ubuntu 7.10, or Suse Linux 10.0... and i definitely prefer Ubuntu...

---

### Post by AlexVader on 2008-01-31
:-) Guess what... 

I solved the problem...

I only neede to use the -mesa flag in the end of the /abaqus cae command...

Now I can use Abaqus in Interactive mode...

:-)

Thanks for yr help.. 

Alex

---

### Post by cherry316316 on 2008-01-31
Congrats, good for you, now welcome to Ubuntu.

:)

if you want, you can make a alias for mesa command in your bashrc file.

Do you have to use that funny command XLIB_SKIP_ARGB_VISUALS=1  to avoid desktop effects ?

Enjoy

---

### Post by AlexVader on 2008-02-01
Hi...

Regrettably I don't... :-( My graphics card is an ATI Mobility Radeon x2300, meaning it does not support graphical 3d acceleration, at least not with the restricted driver of Ubuntu...  don't know yet if it will be different w/ the most recent drivers of ATI, but i suspect not...

I have an Asus F3Jr, and i guess the guys at ASUS are Bill's friends...  :-(

Alex

---

### Post by babuz' on 2008-02-02
The "-mesa" option slows down the Abaqus CAE to an unacceptable level so this is no solution at the end of the day.

Since your video card drivers do not have the full hardware 3D acceleration support you need to disable the 3D acceleration in the xorg.conf. To do so you go to the **Section "Device"** and set the option **DRI** to false:

Option   "DRI" "False"

This option works with the "Intel" video driver. Check your ATI drivers documentation for disabling the 3D acceleration.

In SUSE 10 you can disable 3D acceleration in the video card options through some GUI dialog where you can uncheck 3d acceleration. In Ubuntu Gutsy, however I could not find any dialog for this so I edited the xorg.conf.

This solution does not bring you to the level of rendering speed under Windows but is definitely faster than the "-mesa" option.

---

### Post by AlexVader on 2008-02-02
Hi Babuz',

The relevant section of my xorg.conf is

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

No reference to DRI, whatsoever...

Does the -mesa option slows down the numeric speed performance of Abaqus too ?

I mean, one preprocesses or defines a jof, this is highly interactive, but not as time consuming to the overall FEA analysis process as the solution itself, then comes the postprocessing, i suppose U mean that -mesa slows down the preprocessing and the postprocessing, not the solution itself...

Anyway, my section device has no reference to DRI, what would you advise me to do so as not to degrade Abaqus performance...  ?

Thanks for your time

Alex

---

### Post by babuz' on 2008-02-04
[SIZE="3"]I added the "DRI" option by myself.

If this helps, here is listing of my xorg.conf (for intel video).[/SIZE]

[FONT="Courier New"]Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graph
ics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-TV" "TV"
        **Option          "DRI" "False"**
        Option          "Legacy3D" "False"
        Option          "AccelMethod" "XAA"
EndSection[/FONT]

---

### Post by NeiNastran on 2008-02-11
You guys might want to post on a Linux forum as well. There are a lot of sharp ppl out there that can probably solve your install problem

---

### Post by helmi_um on 2008-03-04
Hi there everyone. I'm using Abaqus 6.7 for my research study. Anyone here knows how to generate the deflection on a loaded beam? FYI my reserach is on scissors lift. Hope for some reply..thanks, cheers..

---

### Post by madhur on 2008-04-03
Hi
I have just started using Abaqus for my research work. I was wondering if any one of you knew how I could edit the input file created by the job manager and then run it. Basically I have to enter the void ration of soil. Abaqus/CAE does not support it, so I have to mention the void ration in the .inp file after creating the input file. After editing this input file, how am I supposed to run this? By submitting the job, it doesn't consider the changes that I make in the input file since it makes a new inp file according to the CAE specifications.

---

### Post by melios on 2008-06-06
Hi all,

I am currently trying to evaluate the Abaqus CAE (student version) as a replacement to the Ansys. I tried to install it after installing the Visual Studio 2005 ( trial) and Intel Fortran 9.1(trial). However, when running the verification of Abaqus the following error occurs:


Requirement:    Microsoft Visual C++ 7.1 or 8.0
Product:        Abaqus make utility with C++
Status:         Fail - Unable to locate and/or determine the version of a
                C++ compiler on this system.  If Visual C++ or Visual Studio
                .NET is installed on this system, please load the
                vcvars32.bat file before running Abaqus.

Requirement:    Intel Fortran Compiler 8.1 or 9.1
Product:        Abaqus make utility with Fortran and Abaqus with user
                subroutines
Status:         Fail - Unable to locate and/or determine the version of a
                Fortran compiler on this system.  If Intel Fortran is
                installed on this machine, please load ifortvars.bat before
                running Abaqus.

This seems to be a usual problem with Abaqus. However, due to limited knowledge neither of the solutions posted on the net solved the problem. Tried to run vcvars32.bat but after doing that neither Abaqus nor Fortran were able to locate Visual Studio. 

Any help would be much appreciated. Bear in mind that my knowledge is limited on the these software.

Thank you in advnace and sorry for any proplems...

---

### Post by poohatek on 2008-06-09
> **madhur said:**
> Hi
I have just started using Abaqus for my research work. I was wondering if any one of you knew how I could edit the input file created by the job manager and then run it. Basically I have to enter the void ration of soil. Abaqus/CAE does not support it, so I have to mention the void ration in the .inp file after creating the input file. After editing this input file, how am I supposed to run this? By submitting the job, it doesn't consider the changes that I make in the input file since it makes a new inp file according to the CAE specifications.

You simply run just the solver by:

prompt$ abaqus job=jobname cpus=howmanycpus interactive

Regards
Kuba

---

### Post by neoflight on 2008-10-09
Hello,

I wrote a howto on installing abaqus 6.8-1 on linux machines which can be found 

Here: [http://www.caejournal.com](http://www.caejournal.com)


Edit: Link fixed. Thanks

---

### Post by neoflight on 2008-10-10
I know that, that method works with fedora, and centOS. Installing Java is critical. I should also point out that a good graphics card is essential to a good CAE performance. 

I some how got away with debian but was slower compared to CentOS.

I just ignored warning about termcap and did not bother

---

### Post by krischeu on 2008-10-21
Hi,
i am using **abaqus 6.8-1** on **ubuntu 8.04 lts 64-Bit**.
I can run jobs with 1 cpu perfectly.
abaqus job=test1 cpu=1
But if i want to start the same job with 2 cpu's
an errormessages comes up.

can anyone give me a hint?

cat test1.log
Abaqus/Explicit checked out 6 tokens.
<118 out of 250 licenses remain available>.
Tue Oct 21 11:53:13 2008
End Abaqus/Explicit Packager
Begin Abaqus/Explicit Analysis
Tue Oct 21 11:53:13 2008
Run mpirun
**Host key verification failed.**
mpirun: Warning one more more remote shell commands exited with non-zero status, which may indicate a remote access problem.
Tue Oct 21 11:53:13 2008

If i do an 
[B]rsh sun6 ls
rsh krischeu@sun6 ls
It works perfectly without a password.[/B]

I killed my auth and known-host file.
Generated a new one --> ssh-keygen
Than i do cat cat id_rsa.pub >> authorized_keys


**cat /etc/ssh/sshd_conf**
{{{# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts no
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

}}}

---

### Post by neoflight on 2008-10-31
> **krischeu said:**
> Hi,
i am using **abaqus 6.8-1** on **ubuntu 8.04 lts 64-Bit**.
I can run jobs with 1 cpu perfectly.
abaqus job=test1 cpu=1
But if i want to start the same job with 2 cpu's
an errormessages comes up.

can anyone give me a hint?

cat test1.log
Abaqus/Explicit checked out 6 tokens.
<118 out of 250 licenses remain available>.
Tue Oct 21 11:53:13 2008
End Abaqus/Explicit Packager
Begin Abaqus/Explicit Analysis
Tue Oct 21 11:53:13 2008
Run mpirun
**Host key verification failed.**
mpirun: Warning one more more remote shell commands exited with non-zero status, which may indicate a remote access problem.
Tue Oct 21 11:53:13 2008

If i do an 
[B]rsh sun6 ls
rsh krischeu@sun6 ls
It works perfectly without a password.[/B]

I killed my auth and known-host file.
Generated a new one --> ssh-keygen
Than i do cat cat id_rsa.pub >> authorized_keys


**cat /etc/ssh/sshd_conf**
{{{# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts no
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

}}}

What is your .env file looks like? did you edit that file by any chance?

---

### Post by krischeu on 2008-10-31
.env File?
I do not changed anything.
I found a workaround which is not recommended from abaqus.

in the abaqus_v6-File there is an entry with mpi.
i changed this to THREADS. After this i am able to start jobs at least with 2 to 8 cpu's.

A warning is coming up but it can be ignored.

If another hints came up, please let me know.

cheers,

Heinz

---

### Post by neoflight on 2008-10-31
> **krischeu said:**
> .env File?
I do not changed anything.
I found a workaround which is not recommended from abaqus.

in the abaqus_v6-File there is an entry with mpi.
i changed this to THREADS. After this i am able to start jobs at least with 2 to 8 cpu's.

A warning is coming up but it can be ignored.

If another hints came up, please let me know.

cheers,

Heinz

Oh :) that is the same abaqus_v6.env file I was talking about. Experienced users encourage us to edit it to add certain attributes  which otherwise would have to be provided every time a job is run.

Memory management, doc paths, # of cores are a few of them.
I could run jobs in 4 cores on my Intel quad 6600. 

I will report if I could find any precise info on this.

Link to our CAE forum is given in my signature. Still working on it :d

---

### Post by 1234mike on 2008-11-20
Hi

i am a new user on abaqus. Does anyone have the command meaning list, coz i have a set of data from my friend and i need to fins out the meaning of them. for example what does (*NODE  NSET=BASE)etc.

thanks

---

### Post by Xnst on 2008-11-26
Hi 1234mike,

what you are looking for is the abaqus keywords manual. It is in the documentation package. 

If you do not have the manuals you could probably find the information you need in the documentation for calculix, [http://www.calculix.de]("http://www.calculix.de") . Calculix is a GPLed FE-software that uses the same syntax in the input-file as abaqus.

---

### Post by lumpwood on 2009-01-11
> **melios said:**
> Hi all,

I am currently trying to evaluate the Abaqus CAE (student version) as a replacement to the Ansys. I tried to install it after installing the Visual Studio 2005 ( trial) and Intel Fortran 9.1(trial). However, when running the verification of Abaqus the following error occurs:


Requirement:    Microsoft Visual C++ 7.1 or 8.0
Product:        Abaqus make utility with C++
Status:         Fail - Unable to locate and/or determine the version of a
                C++ compiler on this system.  If Visual C++ or Visual Studio
                .NET is installed on this system, please load the
                vcvars32.bat file before running Abaqus.

Requirement:    Intel Fortran Compiler 8.1 or 9.1
Product:        Abaqus make utility with Fortran and Abaqus with user
                subroutines
Status:         Fail - Unable to locate and/or determine the version of a
                Fortran compiler on this system.  If Intel Fortran is
                installed on this machine, please load ifortvars.bat before
                running Abaqus.

This seems to be a usual problem with Abaqus. However, due to limited knowledge neither of the solutions posted on the net solved the problem. Tried to run vcvars32.bat but after doing that neither Abaqus nor Fortran were able to locate Visual Studio. 

Any help would be much appreciated. Bear in mind that my knowledge is limited on the these software.

Thank you in advnace and sorry for any proplems...

Abaqus Student Version doesn't support Make or Subroutine features so it doesn't matter that the compilers aren't being found. You'll need a research or commercial version to use these features.

---

### Post by neoflight on 2009-01-20
> **lumpwood said:**
> Abaqus Student Version doesn't support Make or Subroutine features so it doesn't matter that the compilers aren't being found. You'll need a research or commercial version to use these features.

Thank you. I did not know that. we were planning to buy one.

---

### Post by neoflight on 2009-03-28
Our caeforums (includes discussion on abaqus, ansys, etc) are looking for participation. everyone is welcome. check my sig

---

### Post by AlexVader on 2009-03-29
Hi neoflight

This maybe a bit off-way in a thread pertaining to Abaqus (very powerful FEA package BTW... how would you rate Abaqus vs Adina vs Ansys ...? ), but I think if clearly fits CAE/engineering/scientific software, so here it is:

As an adept of Open Source software, I am trying to shift my work ( I am a research  Mechanical engineer ) away from proprietary software to OSS, so if i can do it, I will make my design in BRL CAD instead of Pro Engineer ( BTW, PTC stopped releasing Linux versions...  :-(   ), Calculix/Code Aster instead of Ansys/Abaqus/Adina, Tetgen/Netgen/GMSH/Salome instead of Pointwise/ICEM-CFD/Ensight, OpenFOAM/Code Syrthes/Code Saturne instead of Fluent/Fidap/CD Adapco and GetDP instead of Ansoft HFSS...

All those wonderful pieces of software were generously contributed by the OSS community, and me myself have already contributed some solvers and utilities to the OpenFOAM community, anyway the main problem with these packages is that they can be user-unfriendly, meaning that: the learning curve is rather slow...  ( just try to set up an elastostatic problem to be solved in getDP and you will understand what i mean...  :-)  )

I am trying to build from source ( since I have ubuntu 8.10 AMD64 and want to take full advantage of my CPU and my 16 GB RAM ) applications like Cantera [http://sourceforge.net/projects/cantera#item3rd-2](http://sourceforge.net/projects/cantera#item3rd-2) ( for chemical kinetics deflagration/detonation transitions ), flash [http://flash.uchicago.edu/website/home/](http://flash.uchicago.edu/website/home/) (nuclear fusion burn propagations dense plasma ), GetDP [http://geuz.org/getdp/](http://geuz.org/getdp/) ( Microwave/ electromagnetic scattering/ propagation analysis ) and Salome [http://www.salome-platform.org/home/presentation/overview/](http://www.salome-platform.org/home/presentation/overview/) ( General Finite Elemets pre/post processor for FEA package Code Aster )

so my question is :

Have you (or anyone you know in this forum ) managed to compile these codes from source ?

My problems are : trying to compile Cantera, when i make, after having installe all the dependencies, there is a missed #include, when I add it in a file, that delays the compilation error; #include <cstdlib> and and  #include <cstring> ;

Trying to compile flash ( you do not have the source code.. :-(  ) but the problem is that in the compilation ( make ) It claims that mpif90 is not in the system, but when I type mpif90 in a shell i get 

--------------------------------------------------------------------------
Unfortunately, this installation of Open MPI was not compiled with
Fortran 90 support.  As such, the mpif90 compiler is non-functional.

--------------------------------------------------------------------------


What can i do to enable F90 support....? I only see F77 and F 95 compilers in the repos...


About Salome, the thing is a bit more cranky: The salome-meca package is not a 64 bits app and it randomly reboots by OS...   weird isn't it ?! I wonder if anyone has ever compiled this from scratch to a 64 bit platform, I mean salome ( standalone ) not salome-meca, since I already have Code Aster compiled to 64...

With GetDP, after ./configure when i make i get this :

ranlib ../lib/libArpack.a
make[1]: Leaving directory `/home/alex/Desktop/GetDP/getdp-1.2.1/Arpack'
f77 -o bin/getdp -Llib -lMain -lParser -lPost -lFunction -lIntegration -lGeoData -lDofData -lNumeric -lSparskit -lDataStr -lFMM -lArpack -llapack -lblas -lgsl -lgslcblas -lm
/usr/bin/f77: No input files specified
make: *** [link] Error 255

Do you have any experience compiling those apps...?

Thanks in advance...  :-)

Best regards


Alex

---

### Post by AlexVader on 2009-03-29
Hi Forum...

Make some small progress relating to the Flash Code (nuclear Hydrodynamics) [http://flash.uchicago.edu/website/home/](http://flash.uchicago.edu/website/home/)...   The solution is to change in the Makefile.h the entries for mpif90 for mpif90.openmpi, like this

#----------------------------------------------------------------------------
# Compiler and linker commands
#
#   Use the MPICH wrappers around the compilers -- these will automatically
#   load the proper libraries and include files.  Version of MPICH prior
#   to 1.2.2 (?) do not recognize .F90 as a valid Fortran file extension.
#   You need to edit mpif90 and add .F90 to the test of filename extensions,
#   or upgrade your MPICH.
#----------------------------------------------------------------------------
FCOMP   = mpif90.openmpi
CCOMP   = mpicc.openmpi
CPPCOMP = mpiCC.openmpi
LINK    = mpif90.openmpi


Only now, when I make inside the /objects folder created in the /flash folder, where the executable file pertaining to my problem ( Spherical shock implosion of a fusion plasma )  

I get this... :

root@iskandhar:/usr/local/flash/object# make
mpif90.openmpi -c -fast -r8 -i4   -DN_DIM=2 -DMAXBLOCKS=1000 -DNXB=8 -DNYB=8 -DNZB=1  SelfSimilarMotionFunctions.F90
gfortran: unrecognized option '-r8'
cc1: error: unrecognized command line option "-i4"
cc1: error: unrecognized command line option "-fast"
make: *** [CosmologicalFunctions.o] Error 1
root@iskandhar:/usr/local/flash/object# 

Seems that the compiler flags differ from mpif90 to mpif90.Openmpi....

Can someone give me some hint on the corresponding flags... on *.openmpi to mpif90...?

Thanks in advance

Alex

---

### Post by AlexVader on 2009-03-29
Hi again Forum...  :-)

GetDp can successfully be installed on 8.10AMD64 ( the binary that they release for download is a 32 bit ver )...

When you ./configure and make, an error pops out, because g77, the linker of f77 is no longer present in the repos...

Here is what I did  :

Quote

 [B]Re: Seriously need to get g77 back on Intrepid 8.10
I just added the following lines to the source.list after the lines of universe repositories for intrepid:

Code:

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe 
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe

(Note: hu should be changed to your country code i.e. us, gb, de, etc.)

after that in the terminal:

Code:

sudo aptitude update
sudo aptitude install g77

That worked for me.
Last edited by horvathd; November 18th, 2008 at 07:46 PM.. [/B]

After that, make compiles the app, and make install places it in the default location /usr/bin

... This is getting closer...  :-)

I only need to compile flash executables, cantera-1.7, and salome 4.1.4 to 64 bits...  :-)


Best regards 

Alex

---

### Post by neoflight on 2009-03-30
> **AlexVader said:**
> Hi again Forum...  :-)

GetDp can successfully be installed on 8.10AMD64 ( the binary that they release for download is a 32 bit ver )...

When you ./configure and make, an error pops out, because g77, the linker of f77 is no longer present in the repos...

Here is what I did  :

Quote

 [B]Re: Seriously need to get g77 back on Intrepid 8.10
I just added the following lines to the source.list after the lines of universe repositories for intrepid:

Code:

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe 
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe

(Note: hu should be changed to your country code i.e. us, gb, de, etc.)

after that in the terminal:

Code:

sudo aptitude update
sudo aptitude install g77

That worked for me.
Last edited by horvathd; November 18th, 2008 at 07:46 PM.. [/B]

After that, make compiles the app, and make install places it in the default location /usr/bin

... This is getting closer...  :-)

I only need to compile flash executables, cantera-1.7, and salome 4.1.4 to 64 bits...  :-)


Best regards 

Alex

Hi,

I like abaqus better than ansys. Never used adina. Its just a growing application now i think. I would like to invite you to join our forums in my sig :) Your knowledge, help, input are wanted !. I have browsed through most of the applications you mentioned. but i am not an expert in any of them ( i work with abaqus/ansys for now)

Regarding f90 support: i think g95 provides that support. Never tried to compile with it though. please check that and let us know.

---

### Post by AlexVader on 2009-03-30
Hi Neoflight

Joined the forum... If anybody would like me to share some experience on Adina and OpenFOAM, I'd be willing to share it...  well, not OpenFOAM... CFD is not FEA... I guess there won't be anyone asking about Fluent, CD Adapco of CFX in FEA Analysis, right...?! those three are FVM... a bit different from FEA...  

BTW. did you know that that "growing application" as you called it is the only commercial FEA/CFD package that has built-in FSI (Fluid Structural Interaction ) capabilities with arbitrary rheological models...?...  Even the AllMighty Abaqus must resort to coupling with Fluent via UDFs to tackle this kind of problems...  :-)

Anyway...  I will now try to build Cantera...   I will try to simulate wether a standing detonation in a supersonic reacting flow is sustainable... Cantera can do it if I couple it with a compressible shock wave propagation solver of OpenFOAM... 

Figure this...  if that standing detonation is in a fixed locus, so are the short lived reactive species created in the chemical reaction zone ( assuming that their mean lives and mean free paths are in steady state ) As those species are in a high energetic state, they may constitute a powerful lasing medium, provided their deexcitation energy is high... If that locus is placed in an optical resonating Q-switched chamber ( maybe separating one of the mirrors by a variable opacity saturable medium ) I guess one can build a "device" ( man, i luv the word DEVICE, it is a bit "Manhattan Project" nostalgic huh...?!  :-D   ) that could "shed" some light over the North Korean Taepo Dong ICBMs even before they leave the korean peninsula...   no..!?   Just one of my "funny" ideas...

Anyway...

Feel free to ask me about Adina and OpenFOAM...

Best regards

Alex

---

### Post by rac2407 on 2009-04-04
Hello can anyone tell me how to give time varying forces in abaqus??

---

### Post by lumpwood on 2009-04-05
> **AlexVader said:**
> Hi Neoflight
  

BTW. did you know that that "growing application" as you called it is the only commercial FEA/CFD package that has built-in FSI (Fluid Structural Interaction ) capabilities with arbitrary rheological models...?...  Even the AllMighty Abaqus must resort to coupling with Fluent via UDFs to tackle this kind of problems...  :-)


Alex

I'm kind of biased on this but pretty sure FSI is now tackled in Abaqus through a new built-in Coupled Eularian Lagrangian capability...could be wrong though

---

### Post by susanaQ on 2009-04-15
Hi! I'm using ABAQUS for sound propagation analisys. Can anyone tell me how to apply impedance boundary condition?

---

### Post by AlexVader on 2009-04-20
> **lumpwood said:**
> I'm kind of biased on this but pretty sure FSI is now tackled in Abaqus through a new built-in Coupled Eularian Lagrangian capability...could be wrong though

Hi Lumpwood

Greets, been away for a while...

So.. about Abaqus...  Really..?? meaning that Abaqus does no longer need an External CFD solver to tackle FSI problems...??  AWESOME... is it in version 6.8-1...?

Where can I find more info about this...?

I Just got an education license from a former University Professor, he says wonders about Abaqus... that I should try it...  etc etc...

So... where can i find some more info on Abaqus solving "HARD"  FSI engineering problems, like aeroelastic coupling in eigenvalue analysis of structures in compressible flow ( analysis of turbulence excited ressonance in an aircraft frame, for instance )...?


Best Regards

Alex

---

### Post by neoflight on 2009-04-22
I guess you could couple that. I am not sure if that is already built-in in the general release or a addon.

---

### Post by lumpwood on 2009-04-27
Yes, Abaqus 6.7-EF1 is the first release with this in-built capability. Its part of the newly developing 'multi-physics' side of Abaqus so its still in its infancy. Insofar as capabilities are concerned I would be far from an expert in this field, but their blurb seems to suggest it can handle wave loading to some degree.([http://www.simulia.com/products/extd_multiphysics.html](http://www.simulia.com/products/extd_multiphysics.html))

I'd imagine that it falls down on the whole CFD side, especially with more complex flows, so coupling with Fluent/Star-CD etc. would probably still be a better bet for now. This article gives a decent high-level overview of where CEL fits in the scheme of things...[http://machinedesign.com/article/fe-update-couplings-for-multiphysics-1011](http://machinedesign.com/article/fe-update-couplings-for-multiphysics-1011)

---

### Post by neoflight on 2009-04-27
> **lumpwood said:**
> Yes, Abaqus 6.7-EF1 is the first release with this in-built capability. Its part of the newly developing 'multi-physics' side of Abaqus so its still in its infancy. Insofar as capabilities are concerned I would be far from an expert in this field, but their blurb seems to suggest it can handle wave loading to some degree.([http://www.simulia.com/products/extd_multiphysics.html](http://www.simulia.com/products/extd_multiphysics.html))

I'd imagine that it falls down on the whole CFD side, especially with more complex flows, so coupling with Fluent/Star-CD etc. would probably still be a better bet for now. This article gives a decent high-level overview of where CEL fits in the scheme of things...[http://machinedesign.com/article/fe-update-couplings-for-multiphysics-1011](http://machinedesign.com/article/fe-update-couplings-for-multiphysics-1011)

Thanks for the info Lumpwood. I am not sure how confident abaqus is in this integration. So I would use it with caution.

---

### Post by billkill on 2009-05-16
> **babuz' said:**
> The "-mesa" option slows down the Abaqus CAE to an unacceptable level so this is no solution at the end of the day.

Since your video card drivers do not have the full hardware 3D acceleration support you need to disable the 3D acceleration in the xorg.conf. To do so you go to the **Section "Device"** and set the option **DRI** to false:

Option   "DRI" "False"

This option works with the "Intel" video driver. Check your ATI drivers documentation for disabling the 3D acceleration.

In SUSE 10 you can disable 3D acceleration in the video card options through some GUI dialog where you can uncheck 3d acceleration. In Ubuntu Gutsy, however I could not find any dialog for this so I edited the xorg.conf.

This solution does not bring you to the level of rendering speed under Windows but is definitely faster than the "-mesa" option.

I am trying to run Abaqus 6.8-1 on Suse Linux. The graphics card on my laptop is an intel one 
```

>lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```If i try to run abaqus viewer, it quits with the message
```

Abaqus Error: Abaqus/CAE Kernel exited with an error.
Abaqus Error: Abaqus/Viewer exited with an error
ABQvwrK.exe[14072]: segfault at 7461ac ip b3792e7e sp bfe1bdb0 error 4 in libpython24.so[b36a3000+30e000]

```Enabling or disabling "3d acceleration" doesnt seem to make any difference. Can you please post your xorg.conf since you seem to have the same graphics card as I.

Just to add the direct rendering is on:
```

> glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20080716 x86/MMX/SSE2

```Thanks
Bill

---

### Post by potenza on 2009-05-18
hi everyone.
I was wondering is it possible to make midsurface from imported part? I managed to do it with the part made in abaqus, but it seems impossible with the imported part.

---

### Post by 6dof on 2009-06-05
Abaqus/CAE doesn't have a method for creating mid-planes from solid geometry.  However, you can use the continuum shells in this case.  So you can work directly on your 3D geometry without the need to create a mid-plane.  These elements are reduced to 2D shell theory in the solver and solve efficiently like typical shell elements.  There are some limitations, of course.  For instance the mesh region has to be swept meshable.  Otherwise you can create a solid element mesh, covert it to a mesh part (orphan mesh) then offset a surface mesh to create a mid-plane model.

---

### Post by susanaQ on 2009-07-21
hi everyone.
If I have a cube of acoustic elements is possible to impose a boundary condition with a **linear** acoustic pressure?
thanks

---

### Post by Volume on 2009-07-21
I'm an Engineer, and I use Ubuntu for MATLAB and OCTAVE all the time.

Good stuff, and I like the idea of a "science" community..

Best

---

### Post by James Dee on 2009-11-11
Hello,

I have one question about Documentation Web Server or how can I start web server?

I want to start server with ```
*abaqus_dir*/Documentation/installation_info/v6.8/startServer
```
but error appeared
```
*abaqus_dir*/Documentation/bin/monitor.x: Command not found
```

I installed documentation, as is written in the Abaqus Installation and Licence Guide, with recomanded option that web server should be installed. Also in the Guide is written that server should be started as I try it but nothing. Does anybody have a clue where is a problem?

Thnx
JamesDee

P.S. I found a problem. libtermcap.so is missing.

---

### Post by Claus7 on 2009-11-11
Hello,

> **Volume said:**
> I'm an Engineer, and I use Ubuntu for MATLAB and OCTAVE all the time.

Good stuff, and I like the idea of a "science" community..

Best

+1

Regards!

---

### Post by kingstreet on 2009-12-19
**Dear ABAQUS experts,** 
 
I have modeled and analysed a simply supported RC Slab using ABAQUS cae 6.8-2 with Concrete Damaged Plasticity. I found out that the results of load vs central deflection graph is too stiff at elastic region. This is too far out compared to experimental result I've got. 
 
The type of elements used are:
 
RC Slab -  C3D8R
Steel bars - T3D2 (embedded elements into concrete)
 
Please help me on how to reduce the stiffness of load vs central deflection graph. If anyone interested to view and check my model, I could send the file to you later.
 
Thanks for your cooperation.

---

### Post by looyong on 2010-01-23
hi, maybe you can try one of the followings:

1) change the dilation angle for concrete or other parameters of CDP
2) change the tension stiffening data / softening of your concrete unless you have material tests results that you need to stick closely to.
3) use a finer mesh for your model
4) have you tried to use beam elements, B31, instead of truss elements for your reinforcement. you can embed them also. 

hope this help

---

### Post by looyong on 2010-01-23
hi all,

i am trying to use a connector - join + cardan to join a beam to the middle of a column. a load will be applied to the free edge of the beam to create a moment and rotation at the connector. 

i am using "join" to join the node of the beam and the column. "cardan" is used because i have the moment - rotation data of the connector. combining both of this and applying a tip load, i can check from the output of the connector, rotation, whether this simulation will give me results closed to my data.

however, i am having problems defining the connector. 
1) abaqus standard gives me warning that part of the model is not connected. 
2) rotation output at the connector is zero.
3) upon zooming in on the deflected shape, i found that at the point where the beam and the column is connected, the beam actually floats up the column; it seems that there is no rotation.

i am trying my best to read the documentation by abaqus and follow as closely to the instructions but i could not get it to work. i think the problem might be in the choosing of nodes in Abaqus/CAE or in some interaction process. as for defining the properties of the cardan connection, i have included the elastic and plastic properties which i think might not have contributed to the error that i am having now.

this is part of my master's thesis. i really hope someone can help me. thank you.

---

### Post by mefht on 2010-04-09
Hi
 
I am simulating four point bending using ABAQUS. The beam undergoes fully plasticity. The problem is The FE  results do not match exactly with analytical solutions.
Has any body got any thought on this?

---

### Post by adib88 on 2012-03-19
hi..

i need someone to help me in four point bending using ABAQUS..there is no tutorial on this..please...thank you.. =)

---

### Post by overdrank on 2012-03-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

