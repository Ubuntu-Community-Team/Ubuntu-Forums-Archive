---
title: "FlightGear 2, .DEB ???"
date: 2010-03-01
forum: Gaming &amp; Leisure
---

### Post by juancarlospaco on 2010-03-01
**I want a .DEB of [FlightGear 2]("http://www.flightgear.org/Gallery-v2.0/"), TYA**

:)

---

### Post by juancarlospaco on 2010-03-02
*Bump dump*

---

### Post by davec64 on 2010-03-02
>     *   Download  pre-built Slackware packages courtesy of Jon Stockill. (v2.0.0)
    * **Ubuntu: On Ubuntu, FlightGear can now be installed using the "synaptic" tool.**
    * Download pre-built Debian packages courtesy of Ove Kaaven. (v1.0.0)
    * Download pre-built Fedora Core [2,3,4] packages courtesy of Steve Hosgood. (v0.9.10) [Mirror 1] [Mirror 2] [Mirror 3]
    * Download pre-built Pardus binary packages. (v0.9.10) 1. Program executable. 2. Program data. 

Looks like you can do it through Synaptic!!  :)

---

### Post by juancarlospaco on 2010-03-02
> **davec64 said:**
> looks like you can do it through synaptic!!  :)

**v 1.9.1**

---

### Post by davec64 on 2010-03-02
Ahh, didn't spot that! :)

---

### Post by davec64 on 2010-03-02
I couldn't fin a deb package but I found this compilation script on the Flightgear forum here:[http://www.flightgear.org/forums/viewtopic.php?f=2&p=67504]("http://www.flightgear.org/forums/viewtopic.php?f=2&p=67504")

> I have created a modified version of the download_and_compile.shscript to build using simgear/osg/flightgear specified for the 2.0.0 version (And data too of course).
[http://brisa.homelinux.net/fgfs/download_and_compile-2.0.0.sh]("http://brisa.homelinux.net/fgfs/download_and_compile-2.0.0.sh")
Anybody wants to test it ?
I tested it on a 9.10, and it worked for me.
next step is my deb packages.....

He doesn't appear to have got around to producing the deb yet.

I've not tried it, but it may be of use to you.

Best of luck!

---

### Post by juancarlospaco on 2010-03-02
Ty :)

---

### Post by tegwilym on 2010-03-28
I just discovered the new version is out.  Looks nice, but not sure where to get it from.  The main web page for the sim has "bandwidth exceeded".

Still no new repository for Ubuntu or another location to get a .deb from?  Anyone have some luck with this yet?

Tom

---

### Post by tegwilym on 2010-03-28
Oh, duh....just saw Davec's reply above I'll try his file. 

T.


> **tegwilym said:**
> I just discovered the new version is out.  Looks nice, but not sure where to get it from.  The main web page for the sim has "bandwidth exceeded".

Still no new repository for Ubuntu or another location to get a .deb from?  Anyone have some luck with this yet?

Tom

---

### Post by tegwilym on 2010-03-28
Grrr.....I guess I'll have to find another source, that script goes to the flightgear.org site which is gone right now. 



> **tegwilym said:**
> Oh, duh....just saw Davec's reply above I'll try his file. 

T.

---

### Post by ubudog on 2010-03-30
It is back up now.

---

### Post by tegwilym on 2010-03-30
Yep.  I saw it was up and I downloaded it using the script that the guy on this thread provided.  Everything installed, but just a little confused about how to run the program with the different planes. I start the file that lets you pick the plane and airport, but then nothing happens.  Another file with start he 172 Simulator but I guess I need to read the manual now.  Heh!

Tom

---

### Post by brunesto on 2010-04-07
> **juancarlospaco said:**
> **I want a .DEB of [FlightGear 2]("http://www.flightgear.org/Gallery-v2.0/"), TYA**

:)

Hi, another way to get flightgear 2 is to repackage the slackware txz packages into deb . It works on my pc with ubuntu 9.10 ...

1) install alien and xz for dealing with packages
```
 sudo apt-get install alien xz
```2) download all the fg packages from
[http://packages.flightgear.org.uk/slackware-13.0/](http://packages.flightgear.org.uk/slackware-13.0/)


3) convert them
copy them into a single directory e.g. f2
```

cd f2
xz -d *.txz # decompress all the packages
gzip *.tar # recompress them for alien
sudo alien *.gz # repackage into .deb

```4) install the deb
Before installing the deb packages, uninstal the previous flightgear if you have it installed.

```

sudo gdebi flightgear_2.0.0-2_all.deb 
sudo gdebi flightgear-data_2.0.0-2_all.deb  
sudo  gdebi freealut_1.1.0-2_all.deb  
sudo  gdebi openal-soft_1.11.753-2_all.deb  
sudo  gdebi openscenegraph_2.9.6-2_all.deb

```if some of the  .deb fail to install, check in the output which is the conflicting file, uninstall the corresponding package with synaptic and repeat the installation of the .deb

 One last step:
```

sudo apt-get install libpng3 libglut3

```At this point fgfs2 should be properly installed :)
Enjoy!

---

### Post by Hoshimaru on 2010-04-13
Too bad it doesn't work with Ubuntu 10.04 ^^"
Segfault. Haven't looked more into it atm... Back to windows & FS 2004 :3

---

### Post by Sealbhach on 2010-04-13
I used the Download and Compile script on Ubuntu 10.04, worked like a charm. Very easy to do:

[http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu](http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu)

Just download the download_and_compile.sh script, stick it in your /home folder, make it executable and run it. I usually just double-click the script in Nautilus and select "Run in Terminal".

That's all you need to do, the script does the rest, like fetching dependecies and all that. Give it an hour or maybe two, to get all it's stuff done.

The great advantage with this is you get the very latest version.

When it's complete, you will find a run_fgrun.sh file in your home folder. That will start up the Flightgear Wizard for you.

.

---

### Post by ubudog on 2010-04-14
Thanks.

---

### Post by Tsu jan on 2010-06-22
In Debian Squeeze, I made deb packages from the slackware ones as brunesto suggested and just installed openscenegraph, flightgear-data and flightgear. FlightGear worked fine after I installed the transitional package libpng3. So, most probably, this will work in Ubuntu 10.4 too.

---

### Post by tegwilym on 2010-06-22
Cool!  I'll try that.  I never got it working right, or at least wasn't able to figure out how to get it running.  I kept ending up with some 172 mode or something.  

I did just get some new Seattle Scenery for FSX, but prefer other sims.  :)

Tom

---

### Post by Tsu jan on 2010-06-22
However, it seems that there's some (minor?) problem: I have a dual core CPU and when I run FlightGear 2, only one of the cores is highly used. With the previous version, both cores were used sequentially, which is the correct behavior. I don't know if this is some bug in the Slackware packages or in FlightGear 2 itself, or it's only due to the conversion of txz to deb with alien (which is more probable).

Previously, I'd tried to compile from the source and succeeded in compiling openscenegraph and simgear, but flightgear had given me error messages.

For now, I downgrade to v1.9.1 until the proper Debian or Ubuntu packages are ready.

---

