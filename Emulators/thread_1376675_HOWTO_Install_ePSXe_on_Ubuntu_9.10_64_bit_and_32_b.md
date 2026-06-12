---
title: "HOWTO: Install ePSXe on Ubuntu 9.10 64 bit and 32 bit."
date: 2010-01-09
forum: Emulators
---

### Post by Exadrid on 2010-01-09
Some credit goes to **Franky06** and **Gimox** from this thread <[http://ubuntuforums.org/showthread.php?t=550304](http://ubuntuforums.org/showthread.php?t=550304)> for starting  the script and giving the idea.

These scripts will work on Ubuntu 9.10 x86_64 & i386, any other are to be tested and confirmed.

Thanks to **Zenazic** for testing the 32bit.

The installers will install and fix all know problems for ePSXe 1.6 for Linux.

**HOW TO**

To use download the script needed and run it. Dont forget to set the ownership.

**                                                                                          OR**

Run

64bit

> 
Download and locate file in terminal
sudo chmod 777 ./installepsxe-64bit.sh
./installepsxe-64bit.sh
> 
Download and locate file in terminal
sudo chmod 777 ./installepsxe-32bit.sh
./installepsxe-32bit.sh
[B]What it installs

[/B]1) epsxe 1.6 for linux
2) unzip if you dont have it
3) pete's plugins, P.E.Op.S. plugins, JoyPad plugins...
4) 2 mem card
5) an alias in .bashrc for epsxe
6) libgtk1.2, libgtk1.2-common, libglib1.2 for 32bit (even in 64bit)
7) change permition on the file /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules to null (0000) (this can be revered just look in the script itself)

**What you have left to do**

Restart computer to get the libcanberra error to go away.
Download bios, called SCPH1001.BIN
Configure it in the GUI
[B]
Fixes
[/B] 
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

**Errors**

**kukuku** has pointed out that maybe, if you are Europe or somewhere els you will need to change the mirror in the script. Change it from "mirrors.kernel.org" to "mirrors.eu.kernel.org" or the place where you come from. Thanks.

If any problems shows in terminal or if you want me to add something just post here or email me at **[EMAIL="exadrid@gmail.com"]exadrid@gmail.com[/EMAIL]** and i will try to solve the problem.


**[COLOR=Red]UPDATE[/COLOR]**

I can no longer fix this script or make it better because i have switched my Distro to Arch Linux (great people should try it out). I will still try to troubleshoot for people in this thread but can no longer try it out myself.

If anyone what to take over and fix it for future Ubuntu updates go for it. If no one takes over and it does not work on Lucid I can definitly help anyone who wants to try (even w/o much knolege). This was my first script and i think i did not bad at it (>200 downloads and not much problems YAY) and I would not mind helping out someone who is just starting off.

If someone does make a updated one, can you please e-mail me or post in this thread (i get emails every new posts). I would just like to see whats been added to it (by pure curiosity).

Have fun, hope it works for (at least) Lucid.

---

### Post by mister_playboy on 2010-01-10
Thanks, I'll give it a try.

---

### Post by Saiko Berry on 2010-01-10
Does this work with normal games from the Disc Drive?

---

### Post by riminicat on 2010-01-10
Hey thanks for the work you put into this, I appreciate it!  I can now run my games without running scripts to run pSX! Now I'll try to do this on an old mac so my brother can play games!

---

### Post by Exadrid on 2010-01-10
> **Saiko Berry said:**
> Does this work with normal games from the Disc Drive?

Yes it does, i was not able to mount it normally in the computer but i just inserted it and took the option run from CDROM in ePSXe.

_**Also if anyone used the 32bit script and it worked can you please confirm it.**_

---

### Post by zenazic on 2010-01-11
yay, first post, lol.
yes the 32-bit script does work, I'm playing Oddworld Abe's Oddysee on ePSXe now. :D
thanks for doing such an awesome script since PCSX is quite... um, unsightly. ;)

---

### Post by Exadrid on 2010-01-11
Welcome to the forum Zenazic!

I want to thank you for testing my 32 bit.

---

### Post by beckettwarren on 2010-01-12
Hello,
Thanks for the script, running it on Kubuntu Karmic 64.

Was able to load the bios, but when I try opening an ISO I get:
```
* Loading ISO Format [BIN/IMG2352] (+subchannel) ok
 * NTSC cdrom detected.
plugins/libgpu.so: cannot open shared object file: No such file or directory
```

or ```
* Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeopsMesaGL.so.1.0.78]
NVIDIA Corporation
GeForce 9600 GT/PCI/SSE2
 * Open gpu[0]
plugins/libspu.so: cannot open shared object file: No such file or directory
```

Not sure what is missing, the plugins are working when I go to config. Any suggestions?

---

### Post by Exadrid on 2010-01-12
Did you run the script in superuser. (as in sudo ./installepsxe-64bit.sh) if you did, delete the directory with the lines below and restart not sudoing (it will ask half way in if it needs to). The reason i think is that the directory is in the wrong permition.

> cd ~
sudo rm -r epsxe

Hope this helps, if it does or does not, can you let me know so i can add it to the first post.

---

### Post by kukuku on 2010-01-20
I tried the 32-bit version, which worked after I replaced the "mirrors.kernel.org" address in the script with "mirrors.eu.kernel.org". After setting the arrow keys to numpad keys, everything in the program itself seems to work perfectly.

---

### Post by Exadrid on 2010-01-20
Great, il add that in the first post. Thanks for pointing it out.

---

### Post by Kcj1993 on 2010-01-20
I still get this:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

:(

---

### Post by Exadrid on 2010-01-20
OK 2 things

First: 32 bit or 64 bit

Second: can you copy/past the whole terminal from the moment you start the script to the end. Can you post it here, or if you don't want to Send it to my email @ [EMAIL="exadrid@gmail.com"]exadrid@gmail.com[/EMAIL].

the way to do this in in terminal find the file and go ./installepsxe-32bit.sh (or 64bit.sh)

Thanks i hope i can fix this.

Exadrid

---

### Post by Rave Gloves on 2010-01-21
Can i install this on ubuntu 9.04?

---

### Post by alexandrius on 2010-01-22
Guys download the pSX for Windows and run it with wine works brilliant and no need to any libraries listed upper!

---

### Post by Exadrid on 2010-01-22
> **Rave Gloves said:**
> Can i install this on ubuntu 9.04?

Hypothetically it would work, cause i barely changed anything for the 32bit, just fixed a couple.

But the 64-bit, i don't know, it cant hurt to try it.

> Guys download the pSX for Windows and run it with wine works brilliant and no need to any libraries listed upper!

Yes but the site for pSX has been down for quite a while now and it is not the easiest thing to find online. Not to mention its not much harder to run this script.

---

### Post by Mornedhel on 2010-01-24
I've tried the 64bit script on Karmic. Everything proceeds smoothly until the mv from epsxe/tmp/usr/bin to /usr/bin fails (/home/username/epsxe/tmp/usr/bin: no such file or directory). The script ends with Installation complete, but obviously I can't run an executable that does not exist.

Did you perchance forget to include the actual executable ?

---

### Post by Exadrid on 2010-01-24
Sorry, its just a line i forgot to take out, if you run epsxe by typing 

> epsxe

in terminal it should work. I will update updated my script and took that part off and fixed another little error.

If it does not work try rerunning the script.

---

### Post by Mornedhel on 2010-01-24
Sorry, I forgot to mention that nothing happens when I run epsxe. The executable returns immediately without any output.

Because of the failed mv, I thought that maybe epsxe was a wrapper to the real executable and that was why nothing happened.

---

### Post by Exadrid on 2010-01-24
So, nothing at all happens you run it? Thats just weird.

---

### Post by sau_sage114 on 2010-01-24
has anyone gotten FFVII working with this? im running Ubuntu 9.10 32-bit and I can get cloud off the train but when the blue guys show up it just freezes

---

### Post by Exadrid on 2010-01-25
Try using different visual plugins. Or make sure you got everything set the right way.

---

### Post by Shpongle on 2010-01-30
> **kukuku said:**
> I tried the 32-bit version, which worked after I replaced the "mirrors.kernel.org" address in the script with "mirrors.eu.kernel.org". After setting the arrow keys to numpad keys, everything in the program itself seems to work perfectly.

im on a laptop is there any way to make it use the default arrow keys, they just dont seem to work

---

### Post by jellyxbean on 2010-02-01
I would just like to say Thank you to the people who made this. I must have tried PCSX PCSX DF PSX and all kinds of others and couldn't get a single one to work till this.
So thank you very much for making this so easy on us. I just had to say this. Because it made my weekend

---

### Post by LANmine on 2010-02-03
woot, first post! :D

It seem's I'm getting a libgtk error whenever I try to run "epsxe" in the terminal.  Here's the output if it helps: 

```
nick@nick-ubuntu:~$ epsxe
/home/nick/epsxe/epsxe: error while loading shared libraries: 
libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```Also, the first time I got this i decided to try and apt-get it myself, which gave me this:

```
sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate

```Any thoughts?

**EDIT:** Ok, it seems I've downloaded/run the script in the *original* tutorial that you linked, not the 64-bit attachment at the end of the first post.  My mistake! 8-[  Although running "epsxe" in terminal still gives me the same libgtk error... I'm stumped o_O

---

### Post by Matthew Sforcina on 2010-02-03
> **beckettwarren said:**
> Hello,
Thanks for the script, running it on Kubuntu Karmic 64.

Was able to load the bios, but when I try opening an ISO I get:
```
* Loading ISO Format [BIN/IMG2352] (+subchannel) ok
 * NTSC cdrom detected.
plugins/libgpu.so: cannot open shared object file: No such file or directory
```or ```
* Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeopsMesaGL.so.1.0.78]
NVIDIA Corporation
GeForce 9600 GT/PCI/SSE2
 * Open gpu[0]
plugins/libspu.so: cannot open shared object file: No such file or directory
```Not sure what is missing, the plugins are working when I go to config. Any suggestions?

I found a solution to this one.

I did 

[I]locate libspu

/home/morgan/epsxe/plugins/libspuPeopsOSS.so.1.0.9
/usr/local/games/epsxe/plugins/libspuPeopsALSA.so.1.0.9
/usr/local/games/epsxe/plugins/libspuPeopsOSS.so.1.0.9
/usr/local/games/epsxe/plugins/libspuPeteNull.so.1.0.1

[/I]I used the second line, the ALSA, because that is the driver I am using...
I simply copied and renamed the file the name of the missing file

[I]sudo cp /usr/local/games/epsxe/plugins/libspuPeopsALSA.so.1.0.9 /usr/local/games/epsxe/plugins/libspu.so

[/I]You will have to change the file path to wherever your plugin is installed.
It now works.

> nick@nick-ubuntu:~$ epsxe
/home/nick/epsxe/epsxe: error while loading shared libraries: 
libgtk-1.2.so.0: cannot open shared object file: No such file or directory

For this one, I am running Ubuntu Karmic 9.1 64bit and I have the wrong libs in my usr/lib32 directory. And when I tried to install the libs from a package, it told me 'wrong architecture', I have only been using Linux a week now, so I have been doing lots of searching around and sometimes good concrete advice is hard to find on the various specific troublespots.

The libs required to get rid of this error with this architecture I found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 

Scroll down to "search contents of packages" 

Type in the file libgtk-1.2.so.0
Select Jaunty Distribution
Search
Download the libgtk-1.2-dbg
Go to download directory in shell

Then type the following commands:

[I]dpkg --extract libgtk1.2-dbg_1.2.10-18.1build2_i386.deb libgtk-1.2
cd libgtk-1.2[/I]
sudo cp -r /home/morgan/Downloads/libgtk-1.2/usr/lib/* /usr/lib32/

That should do it

Any other libs that you are missing use...

*getlibs -l* [libnamegoeshere]
For every error that comes up with a missing library use the above command with the filename specified in the [librarynamegoeshere]

and if you don't have getlibs

*sudo apt-get install getlibs*

...

It took me two days to figure this out, with no experience in Linux. 

I'm learning quickly! :KS

---

### Post by Loronal on 2010-02-04
:p:popcorn::popcorn::KS Nice I think Ill use that if i have any problems

---

### Post by Loronal on 2010-02-04
Terminal just kills it when i try to run epsxe doesnt say anything else just killed this is what it looks like
/home/MyUser/epsxe/epsxe
killed

Im running kubuntu 9.10 with 32-bit

---

### Post by Exadrid on 2010-02-06
Ok, i do not know if it works on kubuntu. Are you trying /home/MyUser/epsxe/epsxe to start it?

If so just try epsxe in terminal.

---

### Post by RevKeltina on 2010-02-13
I'm trying to figure out how this thing works, but not having much luck getting the config correct.  I'm working on a Compaq V6000, 32-bit, Ubuntu 9.10.  The install goes all right until I get through the config and attempt to run the ISO.  Then I get a black screen and this message in terminal:

> Gdk-ERROR **: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.I ran the lspci command to obtain my specific graphics chipset for you, in case you need any info from there:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Device 30bb
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30bb
:I have no idea what all that means!  Anyway, perhaps I am using the wrong plugin for my chipset and don't know it.  I have tried loading with the other plugins in the config menu, but none of them seem to work any better.

Maybe someone knows how to work around this or where I can obtain the correct plugin for my chips?

---

### Post by Exadrid on 2010-02-16
According to other forums, it would be the graphic plugin you are using, since (from what i can tell) its not a high end card you will need to use some other plugin. Hypothetically there should be a working one already installed (unless i took it out (stupid me if i did)). 

I can no longer confirm this since I no longer have Ubuntu on my system (YAY Arch). I will, sometime soon, install VB on Arch but i can no longer test the 64bit since my card does not have work w/ virtualisation in 64bit. (More on updated first post).

---

### Post by Sparckus on 2010-02-17
> **Loronal said:**
> Terminal just kills it when i try to run epsxe doesnt say anything else just killed this is what it looks like
/home/MyUser/epsxe/epsxe
killed

Im running kubuntu 9.10 with 32-bit

I got the same error, found this in this [thread]("http://forums.ngemu.com/generic-epsxe-queries/128407-ubuntu-9-10-epsxe.html") on ngemu.


Open terminal and cd to your epsxe directory then:

```
sudo apt-get install upx-ucl
upx -d epsxe
```

Edit:

Oh aye forgot to say thanks to the OP, much appreciated. :popcorn:

---

### Post by RevKeltina on 2010-02-26
All right!  Now that little snippet of code worked out.  I now get the intro screen I'm supposed to see.  Now, if I can just get this cheap controller I own to stop hanging things up, I should be all set.  I'll let you know if I can't figure that one out.  (Serves me rigth for buying a $0.99 one on ebay!)

Here's the meat and potatoes of the issue, if you are interested.....

> * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/upton/epsxe/bios//Scph1001.bin].
 * Init ISO code ... ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17]
 * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
 * Open spu[0]
padJoy: cannot open cfg/padJoy.cfg * Init pad[0][libpadJoy-0.8.so]
padJoy: trying to start a thread; if it hangs, you must disable multithreading
                                                                               * Open pad[0]
Gdk-ERROR **: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


---

### Post by RevKeltina on 2010-02-26
Can someone offer some clarification, please....

Being rather new to programming and the inner workings of systems, I have not yet encountered the term multithreading.  Doing some reading up on what it is, it seems to me that it is just two different operations running at the same time.  But, I thought that all systems ran numerous programs at the same time...your op system is always running, along with your web browser, mail, or whatever else you might be working on.  

Could someone maybe explain that I am missing here?  If I were to attempt to disable the multithreading as requested in my log, would I just be able to run one program at once?

---

### Post by RevKeltina on 2010-02-26
Ok, cheap game pad is functioning.....had to dl ammoQ's padjoy Joy Device Driver to get it going all right.......

on to the next issue.......black screen instead of game when loading .iso from hard drive

This is fun! lol

---

### Post by RevKeltina on 2010-02-26
Pass around the cigars, I have accomplished my first truly challenging task in Ubuntu!!!  For all those other poor souls like I am, searching for the correct instructions, here is what I did to cure the black screen....

I used the Software Center to get a program call GMount....then, I created a folder in my home directory to mount the iso image to and ran GMount to do that.  Opened epsxe while the iso was mounted and ran it out of the new folder I had made.

I hope that make sense to you....took me forever to figure it out!  I'm glad I did because now I have the awesome sense of accomplishment, and I don't have to climb into the back of the attic to get my packed up ps1 and games out!

---

### Post by DoktorSeven on 2010-02-26
> **RevKeltina said:**
> Can someone offer some clarification, please....

Being rather new to programming and the inner workings of systems, I have not yet encountered the term multithreading.  Doing some reading up on what it is, it seems to me that it is just two different operations running at the same time.  But, I thought that all systems ran numerous programs at the same time...your op system is always running, along with your web browser, mail, or whatever else you might be working on.  

Could someone maybe explain that I am missing here?  If I were to attempt to disable the multithreading as requested in my log, would I just be able to run one program at once?

I know you've fixed the issue by disabling padJoy (probably an issue with how padJoy interacts with your system; it notes something about Gdk which is a part of the GTK window rendering API, meaning it couldn't draw something right), but it likely had nothing to do with multithreading.  The message meant disabling multithreading in that plugin only (i.e. make the plugin do only one thing at a time rather than using threads which might have caused problems on a minority of test systems, which is why they printed that warning message out -- it shows up on everyone's output so it's generally best ignored).

In other words, padJoy was having other issues; that message just shows up regardless, just so you know.

---

### Post by athelas on 2010-02-27
Hello.

First of all: Greeat work! Thanks!

I am using Kubuntu 9.10 64bit. Everything worked fine and I can start epsxe. But unfortunately I don't have sound and I can't use my Joypad.
Has anyone an idea?

---

### Post by Exadrid on 2010-02-28
The joypad has to have the drives installed on your computer first. Hope this helps.

---

### Post by Upstartof77 on 2010-02-28
Just wanted to thanks Exadrid for making this. Saved me the hour long headache of trying to do it all manually. Thanks a lot!

---

### Post by Exadrid on 2010-02-28
Your welcome! I did it exacly for that reason because i was just pissed at figuring out how to install this.

Now that just creepy fast!!!! MWAHAHAHAHAHAH (gets email notification)

---

### Post by RevKeltina on 2010-03-01
Thank you, Doktor for explaining that.....and here my kids thought I was too old to learn something new!  I am actually learning a lot reading all these posts on here!  I guess you really can teach an old dog new tricks! :-)

---

### Post by athelas on 2010-03-03
Hey,
Sorry, had a few problems with my Laptop and switched now to Ubuntu 9.10 64bit again.
Can you tell me how I can install drivers manually?

---

### Post by NiGhtMarEs0nWax on 2010-03-04
can you play ePSXe without a controller? ie using the keyboard?

---

### Post by Exadrid on 2010-03-04
@[athelas]("http://ubuntuforums.org/member.php?u=1025076") I can probably if you tell me what kind it is (the number would be great)

@[NiGhtMarEs0nWax]("http://ubuntuforums.org/member.php?u=726941") yes, it works great w/o it but you cant use the joystick.

---

### Post by evo9 on 2010-03-05
Original problem solved!

New problems abound :(

I'm trying to figure out how to get my controller to work in epsxe but with no luck. Right now it will only let me config keyboard buttons.

Any help would be appreciated.

---

### Post by letodude on 2010-03-05
First post, hi!   > **DillByrne said:**
> im on a laptop is there any way to make it use the default arrow keys, they just dont seem to work

 I have the same problem, or more accurately actually only a couple of keys are working, no matter how i configure the pad keys in the options..   Did anyone find a decent solution to this?

---

### Post by letodude on 2010-03-09
up?

---

### Post by fictivetoast on 2010-03-14
> **athelas said:**
> ...unfortunately I don't have sound

+1.  Successfully installed on 10.04 Lucid, but as others have mentioned, no sound and can't use the arrow keys on my laptop.  Arrow keys aren't too big a deal, but not having sound irks me - tempted to just take the speed hit and run through wine instead.  Anyone have luck with sound natively?

---

### Post by keldecow on 2010-03-18
It's a pain that I had to register just to get these scripts. So I uploaded them to a file host (ubuntu.pastebay.com).

32-bit epsxe for Ubuntu 9.10 - [http://ubuntu.pastebay.com/90087](http://ubuntu.pastebay.com/90087)
64-bit epsxe for Ubuntu 9.10 - [http://ubuntu.pastebay.com/90086](http://ubuntu.pastebay.com/90086)

:)

---

### Post by darkpuma on 2010-03-20
Thanks for this tutorial.
It works perfectly on my Ubuntu (32bit). :cool:

---

### Post by arnab_das on 2010-03-21
i am facing a weird issue. using 9.10 64 bit. i did exactly as u have directed here.

but finally, after restarting my PC when i start the emulator i get a weird look of the program:
[IMG]http://img682.imageshack.us/img682/4066/23025079.png[/IMG]

---

### Post by lucasgz on 2010-03-27
awesome thanks a lot :D

---

### Post by fakhri on 2010-04-01
I prefer using the latest windows version (1.7.0) with wine. It has better sound and graphic output. Use the OpenGL/OpenGL2 gpu plugin. If the game didn't show correctly in fullscreen mode, you probably have to turn composite off.
Here is a pic:

---

### Post by trent_2v on 2010-04-03
Hello.. I am new with ubuntu and i have ubuntu 9.10 so i dont very familiar with steps that i had to execute in the terminal.. please someone could tell me in especific and detail words what a had to do to install the emulator.. im already unzip the tar and execute the file that was inside of that but then a dont know what to do.. i apologise for my ignorance.. but please.. I need help.. Thank you..

---

### Post by skaparate on 2010-04-13
Hello, I'm new in the forum, so I want to thank you for the script. Now, unfortunately I have a problem when trying to configure the epsxe plugins (video or sound). When i execute epsxe (terminal), it shows the game interface, but when i click on config -> video or config -> sound it closes and shows the following error:

Error Message
> 
nico@nico-desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
plugins/libgpuPeopsMesaGL.so.1.0.78: undefined symbol: glColorTableEXTnico@nico-desktop:~$I have been unable to figure out how to solve; I have been looking for some answers in google, but foung nothing.

The script worked fine, actually epsxe it's installed. I have the BIOS and it seems that everything is in order.

Here is my pc specs (if it helps):

O.S: Ubuntu 9.10 x64
Processor: Phenom II x4 965 (3.4 Ghz)
RAM: 4 GB 1333mhz.
Video card: Radeon HD 4670 512 MB.

I hope someone has any clue. I will keep looking in google, so if I find something, will post it.

[QUOTE=trent_2v]
Hello.. I am new with ubuntu and i have ubuntu 9.10 so i dont very familiar with steps that i had to execute in the terminal.. please someone could tell me in especific and detail words what a had to do to install the emulator.. im already unzip the tar and execute the file that was inside of that but then a dont know what to do.. i apologise for my ignorance.. but please.. I need help.. Thank you..[/QUOTE]

After installing the file you must execute the emultator from a terminal, simply write **epsxe** then press enter. That should execute it, so you can configure the bios, plugins (video, sound, gamepad, etc.), then you can play.

Greetings to everyone.

---

### Post by ottothecow on 2010-04-23
for anyone unable to get sound in 9.10 or newer...try

padsp ./epsxe

and set it up yo use OSS...this puts a pulseaudio wrapper around the program that intercepts the OSS calls and gives you sound

---

### Post by myromance123 on 2010-05-06
I just wanted to report that the script for 32-bit works on Lucid (Ubuntu 10.04).

 I can run the game from images I made.
I seriously want to thank you Exadrid, it was painless :)

PS: Only issue is that there is no sound. Also, randomly my  gamepad is detected and not detected.
Also, after updating Lucid I get this from trying to open up  config->sound or config->video,
```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or direct
```

---

### Post by ifraser on 2010-05-06
A much simpler solution for 64-bit users:  PCSX Reloaded.  Google it and enjoy.  Works immediately.

---

### Post by TempleNav on 2010-06-09
HEY! I keep getting this error whenever I try to configure the video or sond plugins...  
* Running ePSXe emulator version 1.5.2.
plugins/libgpuPeopsMesaGL.so.1.0.78: undefined symbol: glColorTableEXTusername@username-desktop:~$ 

what is going on?

---

### Post by emoguitarist06 on 2010-07-15
First off great script! Everything installed perfectly and no errors or anything! Ubuntu 9.10 32 Bit

However I downloaded Alundra from some torrent and I convered the IMG file to ISO using ccd2iso in the terminal but whenver I start the game all that shows a black screen. I've tried all 3 graphics plugins with no results. I tweaked the graphics a little (not really knowing what I'm doing) and still no help.

I'm hoping that maybe the file I have is just bad?

I was hoping if anyone was interested in downloading this ISO from my dropbox and determine if it is that ISO or if it is my ePSXe
PM or email Phillip.Griego@gmail for my Dropbox

Please help!

(p.s. if I was to buy a ps1 game and place it in my cd player would it run?)

---

### Post by Exadrid on 2010-07-15
Your file could just be bad, and did you remember to get the Bios for the playstation online somewhere (cant tell you).

I will not download your file because i have horrible Internet and i cant download quickly (not to mention I would, if i was you, take that off this website because you could get banned for giving illegal stuff away). 

Third, it should work using a normal PS1 game in the cd drive, it words for me quite well. (it does not alway mount the same way a normal cd would, just try run from cd in epsxe). 

Also, wow long time that i did not post in this forum... I have stopped using Ubuntu and moved to ARCH linux, something everyone should do. MUCH BETTER.

---

### Post by emoguitarist06 on 2010-07-15
Yeah you're probably right.
But of course I downloaded the bios you recommended :)

Arch Linux?
Can you list the benefits as opposed to Ubuntu?

---

### Post by emoguitarist06 on 2010-07-17
PSX CD WORK PERFECT!! Thanks again for this awesome script!

Still no luck on getting any game that I find at random torrent sites to work though :(

If anyone knows of a good place to get psx roms/isos please PM or email me at [email]phillip.griego@gmail.com[/email]

appreciate the help!

---

### Post by fakhri on 2010-07-29
hey thanks for the great script. It worked out for me. Honestly I prefer using the windows version with WINE. But, since I can't run the bios through it, I need the Linux version.

Good job, pal!!!

---

### Post by DookiePants on 2010-08-05
I installed 1.6 for Linux 64bit (Ubuntu 9.10) using the script. I'm able to launch EPSXE, but when I go to file-> Load ISO, EPSXE crashes and this shows up in the syslog:

Aug 5 17:33:13 library kernel: [15862.102822] ioctl32(4:2018): Unknown cmd fd(12) cmd(00005314){t:'S';sz:0} arg(ffb075b0) on /home/xbmc/epsxe/bios/scph1001.bin

---

### Post by Cetega on 2010-08-12
Just wanted to say thanks for making these scripts, they've been a huge help! I've just recently started playing with Linux Mint 9 KDE on a couple of systems (64bit desktop and 32bit laptop), and I was having some trouble figuring out how to get ePSXe up and running. These scripts works nearly flawlessly on both systems. All I had to do after was rename libspuPeopsOSS.so.1.0.9 to libspu.so, and ePSXe fired right up.

Thanks again!

---

### Post by ayumu on 2010-08-24
I used 64bits script in 10.04. This ran fine. Thanks!

---

### Post by texaswriter on 2010-08-25
```
 texaswriter@texaswriter-laptop:~/Downloads$ sh installepsxe-64bit.sh 
--2010-08-25 00:53:55--  http://www.epsxe.com/files/epsxe160lin.zip
Resolving www.epsxe.com... 74.52.136.42
Connecting to www.epsxe.com|74.52.136.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 180407 (176K) [application/zip]
Saving to: `epsxe160lin.zip'

100%[==============================================================================================================================>] 180,407      292K/s   in 0.6s    

2010-08-25 00:53:55 (292 KB/s) - `epsxe160lin.zip' saved [180407/180407]

[sudo] password for texaswriter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unzip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Archive:  epsxe160lin.zip
   creating: bios/
 extracting: bios/erase.me           
   creating: cfg/
 extracting: cfg/erase.me            
   creating: cheats/
 extracting: cheats/chrono_cross_ntsc.cht  
 extracting: cheats/tarzan_pal.cht   
 extracting: cheats/breath_of_fire_4_usa.cht  
   creating: docs/
  inflating: docs/epsxe_en.txt       
  inflating: docs/epsxe_linux_en.txt  
  inflating: docs/epsxe_linux_sp.txt  
  inflating: docs/epsxe_sp.txt       
  inflating: epsxe                   
  inflating: keycodes.lst            
   creating: memcards/
 extracting: memcards/delete.me      
   creating: patches/
   creating: plugins/
 extracting: plugins/remove.me       
   creating: snap/
 extracting: snap/kill.me            
   creating: sstates/
 extracting: sstates/punch.me        
 extracting: sstates/kill.me         
--2010-08-25 00:54:02--  http://www.pbernert.com/gpupetexgl209.tar.gz
Resolving www.pbernert.com... 85.13.129.40
Connecting to www.pbernert.com|85.13.129.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173744 (170K) [application/x-gzip]
Saving to: `gpupetexgl209.tar.gz'

100%[==============================================================================================================================>] 173,744     93.1K/s   in 1.8s    

2010-08-25 00:54:04 (93.1 KB/s) - `gpupetexgl209.tar.gz' saved [173744/173744]

mv: cannot stat `/home/texaswriter/epsxe/plugins/cfg*': No such file or directory
--2010-08-25 00:54:04--  http://www.pbernert.com/gpupeopsmesagl178.tar.gz
Resolving www.pbernert.com... 85.13.129.40
Connecting to www.pbernert.com|85.13.129.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198157 (194K) [application/x-gzip]
Saving to: `gpupeopsmesagl178.tar.gz'

100%[==============================================================================================================================>] 198,157      105K/s   in 1.8s    

2010-08-25 00:54:07 (105 KB/s) - `gpupeopsmesagl178.tar.gz' saved [198157/198157]

--2010-08-25 00:54:07--  http://www.pbernert.com/gpupeopssoftx118.tar.gz
Resolving www.pbernert.com... 85.13.129.40
Connecting to www.pbernert.com|85.13.129.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 179407 (175K) [application/x-gzip]
Saving to: `gpupeopssoftx118.tar.gz'

100%[==============================================================================================================================>] 179,407      174K/s   in 1.0s    

2010-08-25 00:54:09 (174 KB/s) - `gpupeopssoftx118.tar.gz' saved [179407/179407]

--2010-08-25 00:54:09--  http://www.pbernert.com/spupeopsoss109.tar.gz
Resolving www.pbernert.com... 85.13.129.40
Connecting to www.pbernert.com|85.13.129.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40695 (40K) [application/x-gzip]
Saving to: `spupeopsoss109.tar.gz'

100%[==============================================================================================================================>] 40,695      63.2K/s   in 0.6s    

2010-08-25 00:54:10 (63.2 KB/s) - `spupeopsoss109.tar.gz' saved [40695/40695]

--2010-08-25 00:54:10--  http://members.chello.at/erich.kitzmueller/ammoq/down/padJoy082.tgz
Resolving members.chello.at... 80.109.240.79
Connecting to members.chello.at|80.109.240.79|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48399 (47K) [application/x-gzip]
Saving to: `padJoy082.tgz'

100%[==============================================================================================================================>] 48,399      67.8K/s   in 0.7s    

2010-08-25 00:54:12 (67.8 KB/s) - `padJoy082.tgz' saved [48399/48399]

--2010-08-25 00:54:12--  http://mirrors.kernel.org/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2-common_1.2.10-18.1build2_all.deb
Resolving mirrors.kernel.org... 149.20.20.135, 204.152.191.39
Connecting to mirrors.kernel.org|149.20.20.135|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 208606 (204K) [text/plain]
Saving to: `libgtk1.2-common_1.2.10-18.1build2_all.deb'

100%[==============================================================================================================================>] 208,606      230K/s   in 0.9s    

2010-08-25 00:54:13 (230 KB/s) - `libgtk1.2-common_1.2.10-18.1build2_all.deb' saved [208606/208606]

Selecting previously deselected package libgtk1.2-common.
(Reading database ... 223655 files and directories currently installed.)
Unpacking libgtk1.2-common (from libgtk1.2-common_1.2.10-18.1build2_all.deb) ...
Setting up libgtk1.2-common (1.2.10-18.1build2) ...

--2010-08-25 00:54:17--  http://mirrors.kernel.org/ubuntu/pool/universe/g/glib1.2/libglib1.2ldbl_1.2.10-19build1_i386.deb
Resolving mirrors.kernel.org... 149.20.20.135, 204.152.191.39
Connecting to mirrors.kernel.org|149.20.20.135|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 122724 (120K) [text/plain]
Saving to: `libglib1.2ldbl_1.2.10-19build1_i386.deb'

100%[==============================================================================================================================>] 122,724      197K/s   in 0.6s    

2010-08-25 00:54:19 (197 KB/s) - `libglib1.2ldbl_1.2.10-19build1_i386.deb' saved [122724/122724]

--2010-08-25 00:54:19--  http://mirrors.kernel.org/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18.1build2_i386.deb
Resolving mirrors.kernel.org... 204.152.191.39, 149.20.20.135
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 877192 (857K) [text/plain]
Saving to: `libgtk1.2_1.2.10-18.1build2_i386.deb'

100%[==============================================================================================================================>] 877,192      223K/s   in 3.8s    

2010-08-25 00:54:24 (223 KB/s) - `libgtk1.2_1.2.10-18.1build2_i386.deb' saved [877192/877192]

Installation complete. When wanting to run epsxe, just type epsxe or /home/texaswriter/epsxe/epsxe
Now you will need to get bios on the internet, cant tell you here unfortunatly. Its called SCPH1001.BIN.

```

Installed on 64-bit Ubuntu Lucid 10.04. Posting here for posterity. Will update this post or make a subsequent post with more information

---

### Post by papershoes on 2010-09-07
Ubuntu 10.04 64bit

I'm getting this error after using the epsxe command.
**error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory**


"locate libncurses.so.5" results...

/lib/libncurses.so.5
/lib/libncurses.so.5.7
/usr/lib/libncurses.so.5 (symlink point to libtermcap.so in same directory, is this normal?)

---

### Post by texaswriter on 2010-09-07
Hope this doesn't hijack the "thread", but I have since decided to use a program called PCSXR, in fact google pcsxr codeplex and it will take you to the appropriate site. Works great for linux, but there are Linux, Windows, and Mac OSX versions. This project is currently being maintained.

---

### Post by emoguitarist06 on 2010-09-12
ePSXe has worked great on my Karmic 32bit machine but suddently stopped working. I think they only thing that has changed is that I updated my karmic rhythmbox to lucid's rhythmbox (i have no clue if this affects anything) but here's the error message I get.

```
phillip@EeePC-1201N:~$ cd .epsxe/
phillip@EeePC-1201N:~/.epsxe$ ls
bios             epsxe.png                                   patches
cfg              epsxe.svg                                   plugins
cheats           installepsxe-32bit.download                 psx.svg
dfinput.cfg      keycodes.lst                                snap
docs             libglib1.2ldbl_1.2.10-19build1_i386.deb     sstates
epsxe            libgtk1.2_1.2.10-18.1build2_i386.deb        tmp
epsxe160lin.zip  libgtk1.2-common_1.2.10-18.1build2_all.deb
epsxe.pic        memcards
phillip@EeePC-1201N:~/.epsxe$ ./epsxe 
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/phillip/.epsxe/bios//SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] (+subchannel) ok
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsMesaGL.so.1.0.78] 
NVIDIA Corporation
ION/PCI/SSE2
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
Sound device not available!
 * Open spu[0] 
plugins/libDFInput.so: cannot open shared object file: No such file or directoryphillip@EeePC-1201N:~/.epsxe$ ^C
phillip@EeePC-1201N:~/.epsxe$ ls
bios             epsxe.png                                   patches
cfg              epsxe.svg                                   plugins
cheats           installepsxe-32bit.download                 psx.svg
dfinput.cfg      keycodes.lst                                snap
docs             libglib1.2ldbl_1.2.10-19build1_i386.deb     sstates
epsxe            libgtk1.2_1.2.10-18.1build2_i386.deb        tmp
epsxe160lin.zip  libgtk1.2-common_1.2.10-18.1build2_all.deb
epsxe.pic        memcards
phillip@EeePC-1201N:~/.epsxe$ cd plugins/
phillip@EeePC-1201N:~/.epsxe/plugins$ ls
cfgDFCdrom     libDFInput.so                libspuPeopsOSS.so.1.0.9
cfgDFInput     libDFSound.so                peops_soft_readme_1_18.txt
cfgDFSound     libDFXVideo.so               peops_soft_version_1_18.txt
cfgDFXVideo    libgpuPeopsMesaGL.so.1.0.78  readme_1_9.txt
cfgpeopsxgl    libgpuPeopsSoftX.so.1.0.18   readme.txt
dfinput.cfg    libgpuPeteXGL2.so.2.0.9      version_1_9.txt
dfiso.cfg      libpadJoy-0.8.so             version.txt
libDFCdrom.so  libpeopsxgl.so
phillip@EeePC-1201N:~/.epsxe/plugins$ 

```

I don't get it because I do have libDFInput.so but I don't understand the shared object part
please help!
[B][COLOR="Red"]
EDIT: No longer need the help as I'm now running PCSX-Reloaded on Lucid 64 bit[/COLOR][/B]

---

### Post by otakun on 2010-10-31
> **texaswriter said:**
> Hope this doesn't hijack the "thread", but I have since decided to use a program called PCSXR, in fact google pcsxr codeplex and it will take you to the appropriate site. Works great for linux, but there are Linux, Windows, and Mac OSX versions. This project is currently being maintained.

Wow thanks alot that work great:P:P, i almost tear my head bald trying to play psx in ubuntu 10.04. And PCSXR just work great out of the box d(O_O)b two thumbs up for you sir!!

---

### Post by mishaokami on 2010-11-06
you can try piping oss to pulseaudio by typing the following:

padsp epsxe

it worked for me.

---

### Post by Mazukambax on 2010-12-05
Works like a charm, thank you very much. :)

---

### Post by mikmalot on 2010-12-06
nvm, I'll go through the thread

---

### Post by Je Et on 2011-05-23
> **Saiko Berry said:**
> Does this work with normal games from the Disc Drive?

You could just make an ISO of the game.

---

### Post by madjr on 2011-05-23
> **texaswriter said:**
> Hope this doesn't hijack the "thread", but I have since decided to use a program called PCSXR, in fact google pcsxr codeplex and it will take you to the appropriate site. Works great for linux, but there are Linux, Windows, and Mac OSX versions. This project is currently being maintained.

deb installers available here:

[http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

and in playdeb repos (remember to add the repos)

[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by Zarkks on 2011-06-02
How, thanks dude !! :D

---

### Post by balisto on 2011-09-25
Thanks a lot

---

### Post by G_R_O_N_D on 2011-09-30
I suspect that I'll have problems down the road getting ePSXe to work*, but my current issue is totally confounding:

I downloaded ePSXe v1.7 and unarchived it. I got the plugins and BIOS and whatnot.
The problem is, the executable file does absolutely nothing.
I've double-clicked the icon in the file manager, I've attempted to launch it via terminal with the "exec" command, and I've created a script to launch it; nothing returns anything.
I've used the "sudo upx -d epsxe" command, and that didn't change anything.

I'm at a loss, as there's nothing to work with. There's no obvious issues or error messages, just a clean nothing regardless of what I do.

I'm running Ubuntu 11.04 (GNOME, not Unity) on a Dell Inspiron 1545 laptop.


*I know that ePSXe will require GTK1.2, and I don't have this and am having trouble finding it for my Natty...

---

### Post by thatguruguy on 2011-09-30
Seriously. Use pcsx-r.

---

