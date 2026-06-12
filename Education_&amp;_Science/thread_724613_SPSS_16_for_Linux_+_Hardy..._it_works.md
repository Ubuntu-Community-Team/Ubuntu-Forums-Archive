---
title: "SPSS 16 for Linux + Hardy... it works"
date: 2008-03-14
forum: Education &amp; Science
---

### Post by tekDragon on 2008-03-14
I just wanted to let anyone interested know that SPSS 16 for linux does work. At first impression everything works fine though the processing of analyses seems somewhat slower than on windows (same machine).

There were a few quirks I had to deal with to get it all going.

The installer is Java based and there currently is a bug that appears to cause a lot of Java based stuff to fail on Hardy. To be able to run the Java based installer run the following command:

```
export LIBXCB_ALLOW_SLOPPY_LOCK=true
```

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this...  you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

```
export AWT_TOOLKIT="MToolkit"
```

Don't ask me what that does I didn't come up with it myself.

You can then create a launcher that will launch SPSS by using the command to  \SPSS16\bin\spss rather than "SPSS" (in caps which is the regular launcher).

There you have it. I didnt come up with any of this myself but I pieced it together from random searches. (i.e. this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272"))

To: Mods...  is this the right forum section for this?

Hope this helps a few of you.

As far as I know there are no Java based problems in 7.10.

---

### Post by gunksta on 2008-03-17
Now that is really interesting. Thanks for posting this.

---

### Post by tekDragon on 2008-03-17
Thanks,

Using it right now actually. SPSS was my last hold out to making the switch to linux complete and at this moment I'm in a position to give it a serious attempt for the first time.

---

### Post by tekDragon on 2008-03-18
OK...  over the past few days I've noticed odd behaviour someone might have insight in. It seems that in the output viewer whenever SPSS renders tables it peaks CPU usage. Makes it a bit harder to use when lots of scrolling is required. I don't have the know how to tell if this is due to Hardy strangeness, oddness in some libraries/dependencies, or if it's just buggy because this is the initial SPSS on linux release with a GUI...

I'm fairly certain it's the latter but if it's one of the former it would be great to be able to fix it.

---

### Post by Brian96 on 2008-03-24
My department has volume licenses for SPSS for Windows. Does anybody know if I could get SPSS for Linux under the same license, or would the department have needed to purchase the Linux version?

---

### Post by tekDragon on 2008-03-24
I dont know... that's stuff I never have to deal with. Usually though the companies sell licenses separately for a reason so I doubt you;d have much luck. If you have access to the actual license numbers you could try and snag one of the copies of SPSS for linux floating around online... It's possible they'll be valid and your use of the software would at least be semi-legit. Either way you can install it without a license to run a 14 day trial, that'd be good to see if/how well you can run it...  better off anyway before getting your dept. to possibly invest in a new license.

Also, I've noticed that the issues I've been having re: CPU loads with tables are definitely worse when I have more and bigger tables, but that also seems to be the case when I've got lots of tables in OO Writer. I have no idea if the problems are even remotely related. Perhaps both programs are calling on a common library to render tables that could use some optimization...  any thoughts?

---

### Post by dilney on 2008-03-27
@tekDragon: thanks a lot!

Works great!

I am using hardy and compiz and now I have SPSS working :-))

---

### Post by mtelespalla on 2008-03-30
Hello everybody,

I'm a "beginner" user of ubuntu 7.10 (Gusty) but I've already realize that I feel better without Microsoft. In the past days I've tried to move all of my work activities to the new system but I'm still having problem with SPSS.
I've SPSS 16.0 version for Linux but I cannot install it 'cos the installation procedure blocks. 
After the " Launching InstallShield Wizard" message in the terminal the new installer window is completely blank.
Any idea why? Java packages missing? :confused:
Thanks a lot for your help

Marco

---

### Post by yousillygoose on 2008-04-02
I have this same problem also running Gutsy.  Any thoughts anyone

---

### Post by tekDragon on 2008-04-02
Well I remember it took a while after launching installation before anything happened for me. Honestly consider waiting 3-5 mins before giving up on it. Beyond that I'm just a user so I'm really no help.

---

### Post by mtelespalla on 2008-04-03
Thanks for your suggestion.... but....
I waited half an hour but nothing happen..... :( :( :( 
I've notice that if I click near the right-low corner of the blank window the application asks me if I want to exit.... it seems to me that all the buttons and boxes are in the windows but I can't visualize them properly..... :confused:

Marco

---

### Post by susssus on 2008-04-05
I'm currently running on Gutsy and cannot recommend using SPSS 16 for large data tables (>500 entries on +2mhz cpu and 2 gigs of RAM). 

The GUI gets sluggish with them, scrolling becomes impossible to the point where SPSS processes hog all memory and CPU runs close to 100%. I'd guess this problem is definitely on SPSS side, not a Hardy-related thing.

So unless the situation improves dramatically (SPSS has released some fixes) ATM at least I'm stuck with Windows for any SPSS activities, sorry to say :-(

---

### Post by tekDragon on 2008-04-05
Yes that's roughly the same issue I described.

But as I said I notice that when I have large/many tables in an OO document I get similar slowdowns (though not as extreme, presumably because the tables are not as large) so I'm wondering if there's a larger issue at work here.

---

### Post by susssus on 2008-04-05
tekDragon, I did some browsing and found [http://qa.openoffice.org/issues/show_bug.cgi?id=78780](http://qa.openoffice.org/issues/show_bug.cgi?id=78780) for the OO behaviour. Agree with you, seems pretty similar as the SPSS problem.

---

### Post by tekDragon on 2008-04-05
Nice find.

Yes it seems similar..  that's why I was wondering if there's a problem with some library that's called on to draw tables or something. Unfortunately my knowledge of the workings of Linux/Ubuntu pretty much end there. When I have a little time to kill later I'll see if I can find out if there are similar issues with SPSS Linux on Redhat which I believe is the main "supported" build.

---

### Post by tekDragon on 2008-04-05
Actually...  digging has resulted in some interesting finds.

This thread
[http://groups.google.com/group/comp.soft-sys.stat.spss/browse_thread/thread/647118758f84e1be/3cb6e8510544b081](http://groups.google.com/group/comp.soft-sys.stat.spss/browse_thread/thread/647118758f84e1be/3cb6e8510544b081)

Seems to indicate that SPSS 16 altogether (windows/mac/linux) has issues.

And there are hotfixes already, one of them meant to address the performance with tables issues.

[http://support.spss.com/ProductsExt/SPSS/Patches/SPSSforLinux/index.html](http://support.spss.com/ProductsExt/SPSS/Patches/SPSSforLinux/index.html)

I'll see if I can get those on and how it goes.

---

### Post by tekDragon on 2008-04-05
> **mtelespalla said:**
> Hello everybody,

I'm a "beginner" user of ubuntu 7.10 (Gusty) but I've already realize that I feel better without Microsoft. In the past days I've tried to move all of my work activities to the new system but I'm still having problem with SPSS.
I've SPSS 16.0 version for Linux but I cannot install it 'cos the installation procedure blocks. 
After the " Launching InstallShield Wizard" message in the terminal the new installer window is completely blank.
Any idea why? Java packages missing? :confused:
Thanks a lot for your help

Marco

I've been installing the hotfixes and I noticed the same thing. You probably need to disable compiz for the install with

metacity --replace

---

### Post by mtelespalla on 2008-04-05
> **tekDragon said:**
> I've been installing the hotfixes and I noticed the same thing. You probably need to disable compiz for the install with

metacity --replace

damn.... you are right... it was enough to disable the desktop effect and now it's fine.... thanks for your advice.....

Marco

---

### Post by ian_33 on 2008-04-05
I use Stata and this is also available for linux:

[http://www.stata.com/support/faqs/unix/](http://www.stata.com/support/faqs/unix/)

---

### Post by tekDragon on 2008-04-06
OK I've managed to install the hotfixes. I had to reinstall to get everything working.

The only way I could make things work was to install SPSS as root in the default /opt/SPSSInc/SPSS16 folder. When the progam was installed in /home/SPSS16 I had issues. So far I've noticed that rendeing tables is still slow. I have yet to try it for an extended period of time and see if it slows to the point of being unusable.

I've been seeing people with Macs and Windows PCs also posting complaints about SPSS being slow. Looks like those complaints might be related to the new output files (.spv) which replace the old  format (.spo).

---

### Post by flsantos on 2008-04-23
I just downloaded the demo version of spss for linux, how do I install it on hardy?
Sorry for my lousy english.

---

### Post by Funnylittlething on 2008-05-01
Hiya, I am having a problem with spss:
I managed to install it on Ubuntu 7.10, but it wont even install on 8.04.
I get this message: 

Couldn't display "/media/SPSS160ELin/setup.bin".

There is no application installed for this file type

would anybody know what to do?
Cheers

---

### Post by flsantos on 2008-05-01
How did you install it on gutsy?
Do you have it on disk or on a removable device?
I used the sh comand to open a bin file and it installed right on hardy.
Open a terminal on the folder of the bin file and then just sudo sh setup.bin

---

### Post by jengske_BE on 2008-05-15
Hi all,

i just installed spss 16 on ubuntu hardy, lol now comes the question how in the hell do ya run it /opt/spss/bin/ ?

i work at the VUB brussels and i'm testing if spss runs on linux based pc's.
so that the students learn to use linux instead of the new (stuppid vista version)

my job is only installing desktops and servers so i do not now how the software works.

thx for reply
jengske

---

### Post by flsantos on 2008-05-15
Just create a link like this: "/opt/SPSSInc/SPSS16/bin/SPSS" on the comand line and it will start.
The only problem is that SPSS for linux is incomplete, the non-parametric tests only work in windows.

---

### Post by jengske_BE on 2008-05-15
Information on the license:

i have a classroom licence for windows, thy tell ya to buy a linux licence but i insert the windows code and by wonder it accpted it so if ya got a windows auth. code it wil work on the linux version also.

grtz

---

### Post by flsantos on 2008-05-15
The non-parametric tests also?

---

### Post by jengske_BE on 2008-05-16
The non-parametric tests also?

i really do not now, I'm just testing the installation, and at the moment its installed but it want start up.

think it got something to do with security settings under ubuntu.

but today i only work till 12u. so it will be for next week.

i did the link to the SPSS but no response. thats wy i think its the chmod settings.

but thats for next week, nice weekend all.

grtz

---

### Post by friedolin on 2008-05-19
@tekDragon: Thanks a lot for your installation hints - now the installation on my new hardy system works well, but only until the window where you can make the cross to register spss.com. 
After I have kicked "ok" the system monitor in the panel showed me that the "average system load" went up to 7,8 and the system hang up.
I tried to set higher nice values to some process so that the system stay controllable, but it doesnt work. 
Equal how often I tried it, I could do the installation up to this point and then I have to reboot.

Has someone a idea or better a solution? :(

---

### Post by friedolin on 2008-05-19
In the past I have already installed spss for linux unter gusty and it worked well. 
Now I try to install and my system hang up, althrough the installation AND registration from the spss viewer works well! How could it be? 
The installation and registration process looks quiet similar. :?:

---

### Post by jeroenisblij on 2008-05-30
> **mtelespalla said:**
> damn.... you are right... it was enough to disable the desktop effect and now it's fine.... thanks for your advice.....
Marco
tnx, was looking for this for a while, never would have thought of disabling fancy desktop appearance :)

---

### Post by Bambam2912 on 2008-06-14
If I want to start SPSS with "/opt/SPSSInc/SPSS16/bin/SPSS" it displays:
/opt/SPSSInc/SPSS16/bin/SPSS: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
what could it be? What can I do to get ist work?
I'm relative new to ubuntu, and don't need Windows anymore, would be great if SPSS would work on Hardy

---

### Post by HandeH on 2008-06-18
After upgrading from 7.10 to 8.04 the SPSS 16 did not function anymore. After launching the SPSS, I got the following error message to SPSS Output-window: 

> > >Error # 2072
> >There was an unanticipated problem with the license for this product.
> >This command not executed.
> >Specific symptom number: 4

End of job:  0 command lines  1 errors  0 warnings  6 CPU seconds

The solution was to
```
cd /opt/SPSSInc/SPSS16/bin/

sudo ./SPSSACTIVATOR [authorization code]
```

Authorization code is given without the brackets.

---

### Post by iomp on 2008-06-24
> **Bambam2912 said:**
> If I want to start SPSS with "/opt/SPSSInc/SPSS16/bin/SPSS" it displays:
/opt/SPSSInc/SPSS16/bin/SPSS: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
what could it be? What can I do to get ist work?
I'm relative new to ubuntu, and don't need Windows anymore, would be great if SPSS would work on Hardy

hello!

i've had the same problem.
i've installed the libstdc++5 package and everything works fine (except for some java exceptions that i get..)

cheers!

---

### Post by browncow1 on 2008-09-22
I run the installation for SPSS 16.0 Linux in Ubuntu 8.04. I followed the instructions for turning off compiz.  The installation and registration went fine.  

When I changed the code as suggested in the spss file inside the bin folder.  I still cannot get spss to open up.  Can anyone offer some insight on fixing this problem.  I would greatly appreciate any help.  

Justin

---

### Post by -::Bas::- on 2008-10-03
And got it working under Intrepid: but I assume it works under Hardy just as well:

You want to install an old library, and since it is supposed not to cause any conflicts with the new library, since [the're seperated libraries]("http://gcc.gnu.org/onlinedocs/libstdc++/api.html").
I've tried it and it's running perfectly fine. > sudo apt-get install libstdc++5

Now it will run SPSS when going into /opt/SPSSInc/SPSS16/bin/
and run it like ./SPSS

---

### Post by LexLuthor08 on 2008-10-18
does anyone of you know how to install new modules in spss linux?

I can't find the "licence authorization wizard" which in windows is in the start menu.

---

### Post by pierre.fr34 on 2009-01-14
Hello,

I just installed SPSS 16 on Ubuntu. Great.

The only problem is printing. I can have a look to the print preview and I can select my printer, but when I hit 'OK', nothing happens: no printer activity, no error, just nothing.

Anyone with the same problem ? Any solution ?

NB: SPPS installed in a folder somewhere in the home directory, as suggested somewhere.

Thanks for your help,

Pierre

---

### Post by anotherweinert on 2009-02-03
Just to let Folks know, that the windows version of SPSS 16 installed and working great with the latest edition of Wine. 

I had to configure Compiz, to keep it from blinking….but now it is very solid. I have been using if for about 3 weeks and it has not crashed.   Now I have to get it to work on the Mac.

I am using Intrepid on a dell 1501, and whatever version of Wine that is currently in the repository.  
I am free of Microsoft. 
Thanks for all the help over the months.

---

### Post by meklen on 2009-02-04
Of course, you could always have installed the latest version of PSPP and be free of proprietary software altogether!

apt-get install pspp

---

### Post by shateredsoul on 2009-02-13
Hi, I just noticed this post. I would appreciate it if someone could simplify this for me.  I literally just got ubuntu yesterday... so can someone simplify it for me?

Do I just enter the code into the terminal?   In the directions it also says "you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:"  Does that mean I have to go into the spss folder and edit a file there? what is there? What is the name of that file? 

> **tekDragon said:**
> I just wanted to let anyone interested know that SPSS 16 for linux does work. At first impression everything works fine though the processing of analyses seems somewhat slower than on windows (same machine).

There were a few quirks I had to deal with to get it all going.

The installer is Java based and there currently is a bug that appears to cause a lot of Java based stuff to fail on Hardy. To be able to run the Java based installer run the following command:

```
export LIBXCB_ALLOW_SLOPPY_LOCK=true
```

As far as I can see this only needs to be done once before running the installer and not thereafter to run the program.

Apparently SPSS also doesn't like compiz. It will run fine if you turn off compiz but with compiz on it doesn't display properly. There is a workaround for this...  you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:

```
export AWT_TOOLKIT="MToolkit"
```

Don't ask me what that does I didn't come up with it myself.

You can then create a launcher that will launch SPSS by using the command to  \SPSS16\bin\spss rather than "SPSS" (in caps which is the regular launcher).

There you have it. I didnt come up with any of this myself but I pieced it together from random searches. (i.e. this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1534272"))

To: Mods...  is this the right forum section for this?

Hope this helps a few of you.

As far as I know there are no Java based problems in 7.10.

---

### Post by rkataishi on 2009-03-06
> **shateredsoul said:**
> Hi, I just noticed this post. I would appreciate it if someone could simplify this for me.  I literally just got ubuntu yesterday... so can someone simplify it for me?

Do I just enter the code into the terminal?   In the directions it also says "you need to edit \SPSS16\bin\spss and enter the following code after the "#!/bin/sh" line:"  Does that mean I have to go into the spss folder and edit a file there? what is there? What is the name of that file?


Hello, if you have ubuntu, then you should do this:
(assuming that you already have installed spss 16)

1) Open a terminal (menu:applications, accesories, terminal)
2) type:
sudo nano /opt/SPSSInc/SPSS16/bin/spss

(this command will edit the file "spss" in the "/opt/SPSSInc/SPSS16/bin/" subdirectory)
in the console you should see something like this:
--------------------------------------------------
  GNU nano 2.0.7              File: spss                                     

#!/bin/sh
export AWT_TOOLKIT="MToolkit"
cd "/home/rho/Programas Instalados/SPSSInc/SPSS16"
#"/home/rho/Programas Instalados/SPSSInc/SPSS16/bin/spss"
exec "/home/rho/Programas Instalados/SPSSInc/SPSS16/bin/SPSS" $@
----------------------------------------------------------
In this example i have already pasted the fixing line to the code. Yours have to look like this one.
To quit from nano (console based text editor), press ctrl+x, then "y", then enter.

Ok, you are done.

Now launch spss by doing:
a) in the console:
-cd /opt/SPSSInc/SPSS16/bin/
-sh ./spss

or

b) in the desktop:
right click, create a launcher.
in name: SPSS
In command: /opt/SPSSInc/SPSS16/bin/spss
(you can search the icon in /opt/SPSSInc/SPSS16/bin/ or also in the internet) 

Notes: the file that you should edit does not have extension, so, dont be afraid, nano will recognize that this is a file and not a subdirectory. 

Regards from Argentina

Rodrigo Kataishi

---

### Post by rkataishi on 2009-08-14
> **HandeH said:**
> After upgrading from 7.10 to 8.04 the SPSS 16 did not function anymore. After launching the SPSS, I got the following error message to SPSS Output-window: 



The solution was to
```
cd /opt/SPSSInc/SPSS16/bin/

sudo ./SPSSACTIVATOR [authorization code]
```

Authorization code is given without the brackets.


This does not worked for me.

If you get the 2072 error with specific symptom number 4, you should start the spss licence process all over again.

Follow this steps:

cd /opt/SPSSInc/SPSS16/bin/
sudo ./spsslicence

The last command will start the Licencing WIZARD all over again, erasing previous (old or failing) data, and allowing you to enter your registration code and SPSS code again.

This error might be happening because i upgraded to (first 01, then 02 and afetr that) 16.02.1.

By running SPSSACTIVATOR I achieved no results, my spss keeped unregistered. By running spsslicence I solved it. 

cheers,

R

---

### Post by szymooon on 2009-11-06
spss worked for me under jaunty but after upgrading to 9.10 it has stopped. now it's posting the massage about the lack of libstdc++.so.5
downloaded it, installed it - no effect
than i removed it and followed these instructions [http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html) (because I have 64bit architecture). still the same.
Any ideas? i'd be grateful

---

### Post by marek-b on 2009-11-24
> **szymooon said:**
> spss worked for me under jaunty but after upgrading to 9.10 it has stopped. now it's posting the massage about the lack of libstdc++.so.5
downloaded it, installed it - no effect
than i removed it and followed these instructions [http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html](http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html) (because I have 64bit architecture). still the same.
Any ideas? i'd be grateful

I had the same problem (SPSS 17, ubuntu 9.10 amd64) and luckily found a solution that works! :p

The problem is that SPSS needs libstdc++.so.5 version for i386 architecture. In order to install that version of libstdc in a 64bit environment do the following steps:
1. download and install 'getlibs' script - use Google to find it and learn how to install it
2. get i386 version of libstdc++.so.6: 'http://packages.debian.org/lenny/i386/libstdc++5/download' and download it for example to '/home/me/myfolder/'
3. open terminal
4. type: 'getlibs -i /home/me/myfolder/libstdc++5_3.3.6-18_i386.deb'
5. run SPSS from terminal or launcher

Hope it helps,
Marek

---

### Post by stc77 on 2009-12-04
Yes, this works for me too. Thanks a lot. 
Hardy 9.10, 64-bit, SPSS17.

---

### Post by csa on 2010-01-19
Can anyone please, post a license code for the SPSS 16 linux if you have it? I've been able to install it on Hardy, and it all works fine, except for... I don't have the license code... :(

---

### Post by woodeast on 2010-01-20
I'm staying up late and pulling my hair out over this issue. Please help!

I have successfully installed and activated SPSS 16.0 on my computer, running Ubuntu Karmic Koala 64-Bit. By doing so, I have disabled compiz visual effects, installed libstdc++5_3.3.6-18_i386.deb, and upgraded Java to the latest version ( JRE x64 1.6.0 u18), in the process.

However, when I attempt to run SPSS:

```
./SPSS
```

I am greeted with the following error message:

```

eastwood@woodeast:~/Desktop/SPSSInc/SPSS16/bin$ ./SPSS#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=4766, tid=3312905072
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode)
# Problematic frame:
# C  0x00000000
#
# An error report file with more information is saved as hs_err_pid4766.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted


```

This is the case regardless whether I use 32-bit or 64-bit Java. I feel very, very frustrated.

Please help out if you have any ideas on getting SPSS 16.0 to work on my system. I'd really appreciate it!

(Does SPSS 17/18 support 64-Bit systems? Please PM me if a torrent is available...)

---

### Post by Benic on 2010-01-29
Does anyone have a solution for the very high CPU usage? It takes minutes to do some operations instead of seconds with the Windows version and scrolling is painfully slow!

I tried the Linux version of Stata and it doesn't eat the CPU like the SPSS version. It seems to be a purely SPSS issue.

---

### Post by abhitux on 2010-03-20
I am still wondering...where to download SPSS 17 for Ubuntu. Any download links please? I have SPSS version 16 but then why go through all the hassle of having this installed in the first place? 
Any help would be more than welcome. Thanks in advance.

---

### Post by Benic on 2010-03-21
> **abhitux said:**
> I am still wondering...where to download SPSS 17 for Ubuntu. Any download links please? I have SPSS version 16 but then why go through all the hassle of having this installed in the first place? 
Any help would be more than welcome. Thanks in advance.

It seems that SPSS 17 isn't available for Linux, but I'm not sure about that. Now SPSS is a part of IBM and they released SPSS 18 that works with Windows, Mac and Linux. 

By the way, is it just me or it looks like the new SPSS-IBM is moving closer to business and is slowly quitting academia?

---

### Post by petterwr on 2010-05-06
Just tried to install spss 16 on my 64bit dualcore and did:
export LIBXCB_ALLOW_SLOPPY_LOCK=true

It still hangs on the install shield wizard though, the window comes up but remains grey and nothing more happens.

Any tips?

And yes, I also got the feeling that IBM is changing focus towards the business end. 

Hopefully PSPP will pick up speed. 
I sorely need correlation functions like pearsons rho and spearmans correlation coefficient. There doesnt seem to be an option to contribute money to the project, (at least not on  [http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)) which I would be more than happy to do if it would help speed things up a bit.

---

### Post by kluggot on 2011-05-03
I have managed to install SPSS 16 for Linux on Ubuntu 10.04.

Before install:
Turn off Compiz

Installation
I used the "silent install options" for installation due to the troubles I encountered with the Auth. Wizard and my aim is to shortly recapitulate what I did.

1. Put in your CD or mount your iso-image.

2. Read the "SilentInstallOptions"-file in the root of the disk IOT understand the upcoming steps.

3. Create a file with your favorite editor and add the following information:

```

-V AUTHCODE="[your authentication code]"
-V ISX_SERIALNUM="[your serial number]"

```Save the file and remember the path and filename.

4. Open up terminal and type:
```

export LIBXCB_ALLOW_SLOPPY_LOCK=true

```(not sure if this is  necessary but the computer stalled during installation when I skipped  this step)

5. In terminal, navigate to root of SPSS-disk and execute the install using the following command:
```

sudo./setup.bin -silent -options "/PATHTOFILE/FILENAME"

```This will execute the single user install in silent mode and it will install SPSS to the /opt-directory.

6. When the install is finished (the terminal-prompt has returned) we have to authenticate our install through SPSS-website or their local office. In order to do this we need to give them our lock-code for this specific install on this specific computer.
The lock-code can be retrieved by navigating to the directory in which SPSS was installed (look in /opt/), enter the ./bin-directory, and execute the file "echoid".
```

/opt/SPSSInc/SPSS16/bin$ sudo ./echoid

```The output is your lock-code.

7. Contact your local SPSS-representative and give them your lock-code, you will the retrive an activation-code for your install.

8. Navigate to your SPSS/bin-directory and execute the file "spssactivator" followed by the activation code.
```

/opt/SPSSInc/SPSS16/bin$ sudo ./spssactivator ACTIVATIONCODEWITHALOTOFNUMBERSANDLETTERS#

```9. Launch your activated version of SPSS 16 for LINUX by executing the "spss"-file in your SPSS/bin-directory.
```

/opt/SPSSInc/SPSS16/bin$ sudo ./spss

```


I need to keep Compiz turned off when using SPSS, otherwise it stalls the computer.

---

