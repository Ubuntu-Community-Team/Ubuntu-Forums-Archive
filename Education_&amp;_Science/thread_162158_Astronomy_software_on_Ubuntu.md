---
title: "Astronomy software on Ubuntu?"
date: 2006-04-18
forum: Education &amp; Science
---

### Post by tegwilym on 2006-04-18
Ok, I'm familiar with Stellarium, Kstars and some of the other free Linux astronomy software.  What I'm wondering, is there any "hard-core" software that can be used for imaging/stacking/processing/autoguiding...etc?
I've been using Maxim DL, DSLRFocus, Guidedog, Cartes Du Ciel, Registax, Starry Night Pro, and K3CCDTools just as an example.  These are all Windows applications obviously.  Has anyone used Wine to get these running on Linux?  I have a computer in my backyard observatory that has about 7 devices connected to it through the parallel, serial and a bunch of USB ports to control the telescope, autoguider, cameras, and iTunes for music. ;) 

I'm trying to slowly make the change from M$ to something better - like Ubuntu!  But just like playing games and astronomy, those two things are holding me up from switching completely.  Any ideas on this?

Take a peek at my observatory web site here: [http://www.eastsideastro.org/observatory/](http://www.eastsideastro.org/observatory/)

Tom
-newbie linux user

---

### Post by PriceChild on 2006-04-18
Try this link to search for programs usable in wine:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Searching synaptic has given me "stars"

> star map program that draws the night sky
Stars is an astronomy program that lets you view the sky from
your computer.

Except for generating a small rotation matrix and some parameters,
all math is integer based, allowing very fast display. At 16 bytes
of memory per object, many objects can be loaded at once. Most
graphics are antialiased.

There's also libraries availiable for FITS... supposedly "a data format most used in
astronomy"

---

### Post by ubuntukid on 2006-04-18
If you have automatix then you can install a program called Celestia. I think that's how it's written. It was the test winner in the LXF77 astronomy roundup.

---

### Post by tegwilym on 2006-04-18
[QUOTE=ubuntukid]If you have automatix then you can install a program called Celestia. I think that's how it's written. It was the test winner in the LXF77 astronomy roundup.[/QUOTE]

[QUOTE=Klaidas]Gotta try it out! ;)[/QUOTE]

Kind of what I'm looking for but not quite.  Maxim DL is a high-end application for controlling a CCD camera as well as a telescope mount.  For example, I'm using a 12 inch Meade LX200 Telescope and controlling it remotely with a computer.  I know that Kstars does have an interface in it, but I haven't tried it yet.   My backyard observatory is completely controlled with Windows XP Pro.  I can operate everything remotely using VNC Viewer - for those cold nights when I want to take images, but keep warm indoors with a kitty in my lap.  :) 
I guess I might just have to try running Wine and see if I can get my Windows stuff running in Linux.  Its challenging enough getting all the equipment and remote controls working in Windows alone.  

Tom

---

### Post by Robocoastie on 2006-04-18
I haven't seen a program that can do that as well as the windows products you mentioned which is surprising considering Unix & Science usually fit like two peas in a pod. One program I've used for general use is Xplns [http://www.astroarts.com/products/xplns/index.html](http://www.astroarts.com/products/xplns/index.html) but I don't think it does telescope control. I've never gotten it to work in Ubuntu either because it can't find the fonts but I've never had a problem running it in Xandros.

I've tried to use Starry Night Backyard in xover wine before which does install well but because it uses Quicktime to display nothing ever appears in the screen. Truely odd because you can install Quicktime 6 in xover but it has no ability to tie it to anything other than Mozilla plugins or standalone.

---

### Post by tegwilym on 2006-04-18
[QUOTE=Robocoastie]I haven't seen a program that can do that as well as the windows products you mentioned which is surprising considering Unix & Science usually fit like two peas in a pod. 
.[/QUOTE]
I've read somewhere that Linux still doesn't support web cams very well yet.  I do a lot of planetary/lunar photography with a Vesta Pro webcam.  I guess I'll just have to leave that one set up on Windows and start dual booting the other ones for games and other things.

---

### Post by Robocoastie on 2006-04-21
I knew there was one I used to know of that could control scopes. - Xephem:
[http://www.clearskyinstitute.com/xephem/](http://www.clearskyinstitute.com/xephem/)

---

### Post by zojas on 2006-06-10
the beta version of cartes du ciel 3 is available for linux.

I'm trying to decide how hard it is to get it installed.

[http://www.ap-i.net/skychart/index.php]("http://www.ap-i.net/skychart/index.php")

---

### Post by zojas on 2006-06-10
not too hard. downloaded the binary package (skychart_v3_beta010_linux386.tar.gz) from [http://sourceforge.net/project/showfiles.php?group_id=64092]("http://sourceforge.net/project/showfiles.php?group_id=64092")

then I made a directory called skychart in my home directory. extracted the tarball in there (be careful, it doesn't have a top-level directory, it will make a mess unless you put it in a subdirectory)

it had a binary called 'skychart'. there were also 2 shared libraries in the directory. the runtime linker didn't see the shared libraries at first, so the binary wouldn't run. that was easy to fix though:

```
export LD_LIBRARY_PATH=.
./skychart&
```

works.

---

### Post by ubuntu27 on 2006-06-10
HERE is the list of software for Scientist and educators:

[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by tegwilym on 2006-06-12
[QUOTE=zojas]the beta version of cartes du ciel 3 is available for linux.

I'm trying to decide how hard it is to get it installed.

[http://www.ap-i.net/skychart/index.php]("http://www.ap-i.net/skychart/index.php")[/QUOTE]

Cool! I didn't know there was a Linux verson of that.  I use that all the time on Windows to control my telescope.  That's one of the best astronomy programs around.  I'll give that a try and see if I can get that thing installed on my Ubuntu machine.  Sometimes that can be frustrating since I'm still a Linux noob.  :)

Tom
[www.eastsideastro.org/observatory](www.eastsideastro.org/observatory)

---

### Post by zojas on 2006-06-12
in my next post, I described how to get it running.

---

### Post by tegwilym on 2006-06-12
I guess it isn't happy with the 64 bit Ubuntu.  I had to do a "force" install on it, but when I try to run it the hourglass spins for a while then vanishes.  I'll give it a try on my old 32 bit machine and see what happens. 
I wish there was a single download that has all the packages build into one file like the windows version has. 
...or is there something like this already that I just missed somehow?

Tom

---

### Post by zojas on 2006-06-12
binary package, all in 1. probably will need 32 bit though (I didn't try it on 64bit)

[QUOTE=zojas]not too hard. downloaded the binary package (skychart_v3_beta010_linux386.tar.gz) from [http://sourceforge.net/project/showfiles.php?group_id=64092]("http://sourceforge.net/project/showfiles.php?group_id=64092")

then I made a directory called skychart in my home directory. extracted the tarball in there (be careful, it doesn't have a top-level directory, it will make a mess unless you put it in a subdirectory)

it had a binary called 'skychart'. there were also 2 shared libraries in the directory. the runtime linker didn't see the shared libraries at first, so the binary wouldn't run. that was easy to fix though:

```
export LD_LIBRARY_PATH=.
./skychart&
```

works.[/QUOTE]

---

### Post by keithpeter on 2007-01-06
> **zojas said:**
> the beta version of cartes du ciel 3 is available for linux.

I'm trying to decide how hard it is to get it installed.

[http://www.ap-i.net/skychart/index.php]("http://www.ap-i.net/skychart/index.php")

I'm bumping this one: there is now (Jan 2007) a .deb package available. It needs a library called libgdk-pixbuf2. I installed SkyChart (Cartes Du Ciel) on a xubuntu + OpenOffice2 and Inkscape as follows...

```
sudo aptitude install libgdk-pixbuf2
sudo dpkg -i skychart_3.0.1.2-1_i386.deb.deb

```

having previously downloaded skychart_3.0.1.2-1_i386.deb from the source forge page for the project at [http://sourceforge.net/project/showfiles.php?group_id=64092#files](http://sourceforge.net/project/showfiles.php?group_id=64092#files)

The basic program comes with the Yale Bright Star catalogue. You can add star catalogs by downloading them as .zip files from the sourceforge site above. Unpack the zip file and you will find a folder with the star position data and a text file.  Move the folder and text file to //usr/share/apps/skychart/cat using (for instance, for the Sky 2000 star catalogue down to mag 9)

```
sudo mv sky2000 /usr/share/apps/skychart/cat
```

Now, how do I convince people that this superb app deserves to be in the repositories?

---

### Post by slaanco on 2007-01-09
there is also a linux alternative to IDL, called GDL..

---

### Post by navneeth on 2007-01-09
> **zojas said:**
> the beta version of cartes du ciel 3 is available for linux.

I'm trying to decide how hard it is to get it installed.

[http://www.ap-i.net/skychart/index.php]("http://www.ap-i.net/skychart/index.php")

Here's the installation instructions for Debian. It's as simple as adding a repo to your sources.list. :)
[http://www.ap-i.net/skychart/en/documentation/install_on_linux_debian](http://www.ap-i.net/skychart/en/documentation/install_on_linux_debian)

---

### Post by hansg on 2007-11-27
i have used Cartes du Ciel astro software for years in windows, its also a linux ver.
This  free software is much better then commercial like TheSky, SkyMap, Guide etc.

But how install it in Ubuntu??

Its needed a package like K-star for Cartes du Ciel:lolflag:

regards
h-g

---

### Post by tegwilym on 2007-11-27
Yep.  I'm familiar with Cartes du Ciel.  That is really some of the best astro software that I know of!  I use it all the time in my observatory to control my telescope and aim at the objects I want to image.  I do have Starry Night Pro 5.x, but good as it is, Cartes is just so much easier to use (and requires less hardware).

See my setup here - [http://www.eastsideastro.org/observatory](http://www.eastsideastro.org/observatory)

Sadly, I'm running my observatory on Windows XP since all the software that I used out there is Windows based as well has the hardware (the USB-serial cables).  If I find a somewhat easy way to set this thing up purely on Linux, I'd dump XP totally.  
I will say that I DO control the observatory remotely from my Ubuntu machine in the house remotely with VNC though.  :)

Tom

---

### Post by hansg on 2007-11-27
Real nice observatory Tom, well its not going so well for me and ubuntu, failed to install CdC and XEphem.

Quess i have to install my old RedHat ver 5.2 where i run XEphem in the 90:this:(:(

h-g
[http://tech.groups.yahoo.com/group/vstarint/](http://tech.groups.yahoo.com/group/vstarint/)

---

### Post by tegwilym on 2007-11-27
> **hansg said:**
> Real nice observatory Tom, well its not going so well for me and ubuntu, failed to install CdC and XEphem.

Quess i have to install my old RedHat ver 5.2 where i run XEphem in the 90:this:(:(

h-g
[http://tech.groups.yahoo.com/group/vstarint/](http://tech.groups.yahoo.com/group/vstarint/)

I wish I could use the observatory some more, but we are getting into the ugly time of year here in Seattle.  When it's clear, the moon is full!  

Anyway, did you try the .deb version of Cartes?

[http://sourceforge.net/project/showfiles.php?group_id=64092](http://sourceforge.net/project/showfiles.php?group_id=64092)

Install it like this from the command line (or even just double click on it and the Ubuntu .deb installer should come up)

[COLOR="Black"]** sudo dpkg -i skychart_3.0.1.2-1_i386.deb**[/COLOR]

That *should* do it.

Hmmm...first time I've given some Linux advice.  I'm progressing nicely from my former Windows infection!  :)

Tom


That hould

---

### Post by tegwilym on 2007-11-27
Oh, I've never seen XEphem, I'll try that now and see what that looks like .

Tom

---

### Post by Greg Mueller on 2008-01-15
Hi
New to the Ubuntu forum and Linux
I've just loaded 7.10 and have gotten The Sky 6 and Maxim DL/CCD 4.11 to run. I've been trying CCDsoft 5, but no luck yet.
I'm running them under Wine.
When I say "run" I mean they start up. The Sky seems to do most of it's things correctly, but I haven't had a camera connected to Maxim to see if that works right.

---

### Post by tegwilym on 2008-01-15
> **Greg Mueller said:**
> Hi
New to the Ubuntu forum and Linux
I've just loaded 7.10 and have gotten The Sky 6 and Maxim DL/CCD 4.11 to run. I've been trying CCDsoft 5, but no luck yet.
I'm running them under Wine.
When I say "run" I mean they start up. The Sky seems to do most of it's things correctly, but I haven't had a camera connected to Maxim to see if that works right.

I haven't tried much of my astro software yet.  I wonder how well it will configure with serial, paralell and USB ports?  I have my observatory controlled by windows, but if there was another way.....

---

### Post by Greg Mueller on 2008-01-16
It was my original intention to have 3 small old computers running XP in the observatory to run the mount (ME) and dome, the camera (FLI) and guider. They would all be connected to the warm room to the main computer with PCAnywhere. The problem was that every time I messed with a computer, Windoz would think I was trying to steal it and would make me re-register it. That makes me real mad as I like to mess with my computers and other hardware. I took one of my old computers and wiped off windoz and am using it for a test bed. I was hoping to 100% success running under wine but that's not the case. I hope it's me that's doing something wrong and not Wine

---

### Post by tegwilym on 2008-01-16
> **Greg Mueller said:**
> It was my original intention to have 3 small old computers running XP in the observatory to run the mount (ME) and dome, the camera (FLI) and guider. They would all be connected to the warm room to the main computer with PCAnywhere. The problem was that every time I messed with a computer, Windoz would think I was trying to steal it and would make me re-register it. That makes me real mad as I like to mess with my computers and other hardware. I took one of my old computers and wiped off windoz and am using it for a test bed. I was hoping to 100% success running under wine but that's not the case. I hope it's me that's doing something wrong and not Wine

I have XP in my observatory with VNC running on it.  I can get it all up and imaging, then run into the warm house and control it from there - on my Ubuntu machine with Vncviewer.  Heh!
Have you tried running VNC with it?  I've had excellent luck with that, and best of all it's free.
I know how you feel about messing with computers.  I do that all the time, and it does make me irate that Microsoft won't trust loyal customers with their software.  I DID pay full price, so let me use the damn thing!  Argggh!
I just built a MythTV box last week.  Took a while to get it all running, but I love it.  :)

Finally had a clear night last night and was able to use the observatory for the first time in many months.  A few quick shots of M42, Rosette with the H-alpha, a search for Comet Holmes...then the clouds returned.  *sigh*

Tom

---

### Post by Greg Mueller on 2008-01-16
I just spent the day trying to get Maxim to recognize the FLI camera. When I go into the camera setup page I can set the FLI as the camera but the pull down that is supposed to have "USB" in it has nothing. It's probably because I have not been able to install the FLI software with Wine. 
So close and yet so far.

---

### Post by Greg Mueller on 2008-01-17
I need to try to find help on this.
The way it's supposed to work is when you plug in your ccd camera the program recognizes it and gives you options for connecting to it. Since this camera is USB, Maxim should "sense" that. But it doesn't seem to know when I plug in the camera. In XP it makes a kadunk noise and the option appears in the "Connect To" box. 

I can see the camera in the Device Manager under
82371AB/EB/MB PIIX4 USB

---

### Post by JSuresh on 2008-08-25
I just found this site: [http://www.physics.drexel.edu/~parejkoj/observatory/analysis.shtml](http://www.physics.drexel.edu/~parejkoj/observatory/analysis.shtml)

seems to have a lot of very good photometry software

---

### Post by tegwilym on 2008-08-27
> **JSuresh said:**
> I just found this site: [http://www.physics.drexel.edu/~parejkoj/observatory/analysis.shtml](http://www.physics.drexel.edu/~parejkoj/observatory/analysis.shtml)

seems to have a lot of very good photometry software

Cool.  Another small step closer.  Now if I just had DSI autoguiding, DLSR imaging, RAW conversion, stacking, Dark/flat processing.....etc.  I'd be a happy guy!
I'll have to try playing with the latest version of Wine again and see if anything else runs yet. 

We'll get there slowly.

---

### Post by hubie on 2008-08-27
As part of my job I work a lot with camera images.  I have found [ImageJ]("http://rsbweb.nih.gov/ij/") to be a great program for importing images, importing as stacks, processing as a stack, exporting into a variety of formats, etc.  It is an amazing image processing program to begin with, and it supports macro writing and plug-in development so there is a ton of stuff you can add on.  There is even a set of [astronomy plugins]("http://www.uni-sw.gwdg.de/~hessman/ImageJ/Astronomy/"), though I can't say I have ever tried them (they look quite powerful).  There is also a [nice paper]("http://arxiv.org/ftp/astro-ph/papers/0611/0611686.pdf") on how to use it for astronomy.

ImageJ is written in Java, so it will run on all of your computers.

I've heard that [Registax]("http://www.astronomie.be/registax/") is a popular program for people.  It is a free Windows program, but [here]("http://www.astronomie.be/registax/html/registax_under_linux.html") is how to run it under Wine.

---

### Post by Astrodan on 2008-12-08
> **Greg Mueller said:**
> Hi
New to the Ubuntu forum and Linux
I've just loaded 7.10 and have gotten The Sky 6 and Maxim DL/CCD 4.11 to run. I've been trying CCDsoft 5, but no luck yet.
I'm running them under Wine.
When I say "run" I mean they start up. The Sky seems to do most of it's things correctly, but I haven't had a camera connected to Maxim to see if that works right.
Have you found the solution to your Linux camera problem?

---

### Post by skywatcher on 2009-01-19
I tried to install Skychart on Intrepid using the instructions at this link:

[http://www.ap-i.net/skychart/en/documentation/installation_on_linux_debian]("http://www.ap-i.net/skychart/en/documentation/installation_on_linux_debian")

However, it doesn't work.  Here is the message I get:

```
chris@ubuntu:~$ sudo apt-get install skychart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skychart is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skychart has no installation candidate

```

By the way, I did add the following to /etc/apt/sources.list:

```
deb http://kent.dl.sourceforge.net/sourceforge/ skychart/
```

Can someone point me in the right direction?

---

### Post by kleeman on 2009-01-19
Did you also do

sudo apt-get update

as well. I followed the instructions on intrepid and it worked for me.

---

### Post by skywatcher on 2009-01-20
Yes, I did run sudo apt-get update.

I tried it again after reading kleeman's reply, and saw this message in the output:

Ign [http://kent.dl.sourceforge.net](http://kent.dl.sourceforge.net) skychart/ Packages

Does "Ign" mean ignore?  If so, why?

---

### Post by kleeman on 2009-01-22
It means either the repository doesn't exist or that the data has already been downloaded.

If you use synaptic and search for skychart is it there?
You aren't using a 64bit version of Ubuntu are you?
The reason I ask is that it looks like only i386 debs are available.

---

### Post by skywatcher on 2009-01-22
A search on synaptic shows skychart-pictures only; no skychart.

Oops! Dumb question -- how do I know whether I have a 64-bit version?  The system monitor doesn't show that information. I installed Ubuntu 8.10 from Vista with Wubi on a HP Compaq 6720s laptop, of which the Ubuntu system monitor says:

Processor 0: Intel Core 2 Duo CPU T5470 @1.6 GHz
Processor 1: Intel Core 2 Duo CPU T5470 @1.6 GHz

Unfortunately, that's all I can tell you.

---

### Post by kleeman on 2009-01-23
Open a terminal and type 
uname -a

If it says x86_64 somewhere in the line then you have the 64bit OS installed.

If so you could try downloading the deb manually:
wget [http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/s/sk/skychart/skychart_3.0.1.4-1_i386.deb](http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/s/sk/skychart/skychart_3.0.1.4-1_i386.deb)

Install this deb from the terminal using

sudo dpkg -i --force-architecture skychart_3.0.1.4-1_i386.deb

---

### Post by skywatcher on 2009-01-23
Hi kleeman

Many thanks for the advice.  One's never to old to learn -- I do indeed have the 64-bit version installed.  Does Wubi do that automatically?

Anyway, the installation according to your advice went smoothly, but when I try to run Skychart, I get an error message:

Could not load library libplan404.so

I searched for this file and found it in my home directory in a hidden folder at .local/share/Trash/files/skychart/

I notice that there is another library called libgetdss.so. Should I move these files somewhere else?

Sorry to be a nuisance!

---

### Post by kleeman on 2009-01-23
Sounds messy. Classic problem for a 64bit OS. You could try linux32 which is in the util-linux package. Type
which linux32

If you get something back then type
linux32 skychart

If not install it with
sudo apt-get install util-linux

and try 

linux32 skychart

again.

---

### Post by skywatcher on 2009-01-24
Messy, indeed!

The program starts when I try linux32 skychart, but this message pops up:

SQL database not available
SQL database software is probably not installed!

This message also pops up when, for example, I disable the labels of deepsky objects, and click on "Apply".  Then, when I click on "OK", it pops up again. But the action is nevertheless executed.

The program has the basic (default?) database, because all the constellations, bright stars, planets etc. are there. But it doesn't have the observatory data base, which is not really a problem in my case.

I also discovered that the program starts when I run the skychart executable in the folder that I mentioned in my previous post:

.local/share/Trash/files/skychart/

Do you have any ideas about the SQL database problem?

Thanks a lot for your help -- it is really appreciated!

---

### Post by skywatcher on 2009-01-24
How do I delete this message? Problem with network connection resulted in previous post being placed twice.

---

### Post by kleeman on 2009-01-24
I found a 64 bit package you might want to try.
First uninstall the 32 bit package
sudo dpkg -r skychart

Next get the package

wget [http://www.math.nyu.edu/faculty/kleeman/amd6/skychart_3.0.1.5-4.20081026_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd6/skychart_3.0.1.5-4.20081026_amd64.deb)

then install it with

sudo dpkg -i skychart_3.0.1.5-4.20081026_amd64.deb

Might work better...

---

### Post by skywatcher on 2009-01-24
A slight problem ...

```
wget http://www.math.nyu.edu/faculty/kleeman/amd6/skychart_3.0.1.5-4.20081026_amd64.deb
--2009-01-24 19:13:31--  http://www.math.nyu.edu/faculty/kleeman/amd6/skychart_3.0.1.5-4.20081026_amd64.deb
Resolving www.math.nyu.edu... 128.122.80.243
Connecting to www.math.nyu.edu|128.122.80.243|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-01-24 19:13:35 ERROR 404: Not Found.
```

---

### Post by kleeman on 2009-01-24
Sorry got the address wrong. Try this

wget [http://www.math.nyu.edu/faculty/kleeman/amd64/skychart_3.0.1.5-4.20081026_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/skychart_3.0.1.5-4.20081026_amd64.deb)

---

### Post by skywatcher on 2009-01-24
It finally works!

There are a few other issues now, such as the ugly font on the interface, but that is another matter.

Again, thanks for your help.

---

### Post by sierra_bravo on 2009-08-26
Hi
I had posted the following comment on UbuntuForums (unfortunately, that thread is now read-only, which is why I am posting here).

I would like to report success in installing and running Xplns (one of the finest astronomy software that I've used) on Jaunty. I downloaded the rpms from [http://www.astroarts.com/products/xplns/download.html](http://www.astroarts.com/products/xplns/download.html) (pls note that Xplns is free for use, but not Open Source), converted them to .deb using alien, and installed them.

Upon running, Xplns refuses to start, citing missing character sets. This is easily fixed as follows:


```
$ xplns --locale=us
```

Works without any problems...good to get an old friend back!

sierra bravo


-------------
December 5th, 2007 

Subject: Unable to install xplns on Gutsy


Hi
I was trying to install my old favorite astronomy program, xplns (which is only available in binary format). I am getting the following dependencies. Is there any way that I can fix these dependencies from within Gutsy?

TIA

s.b.

-----------------
$ sudo rpm -ivh xplns-3.3.1-1glibc21.i386.rpm
error: Failed dependencies:
/bin/sh is needed by xplns-3.3.1-1glibc21.i386
ld-linux.so.2 is needed by xplns-3.3.1-1glibc21.i386
libICE.so.6 is needed by xplns-3.3.1-1glibc21.i386
libSM.so.6 is needed by xplns-3.3.1-1glibc21.i386
libX11.so.6 is needed by xplns-3.3.1-1glibc21.i386
libXext.so.6 is needed by xplns-3.3.1-1glibc21.i386
libXp.so.6 is needed by xplns-3.3.1-1glibc21.i386
libXt.so.6 is needed by xplns-3.3.1-1glibc21.i386
libc.so.6 is needed by xplns-3.3.1-1glibc21.i386
libm.so.6 is needed by xplns-3.3.1-1glibc21.i386
libc.so.6(GLIBC_2.0) is needed by xplns-3.3.1-1glibc21.i386
libc.so.6(GLIBC_2.1) is needed by xplns-3.3.1-1glibc21.i386

---

### Post by sroland81 on 2010-01-04
Skycharts do not work in karmic amd64 either 32 bit version using "linux32 skychart" or 64 bit version from the .deb file referenced in this thread. I think that skychart is one of the only sky planetarium software and it must be included in ubuntu software center... does anybody made it run in karmic 64 bit? thanks...

---

