---
title: "Setting up Skype in Breezy Badger (easy way)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by zingibong on 2005-10-13
1. Download Skype .deb file from Skype.com
NOW BEFORE INSTALLING SKYPE
2. Open Synaptic and install **gcc-3.3-base** and then **libstdc++5**
3. Go to [this Debian page]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fq%2Fqt-x11-free%2Flibqt3c102-mt_3.3.4-3_i386.deb&md5sum=ef0153655738cd107b81fafa5724897e&arch=i386&type=main") and download **libgt3c102-mt** from the location nearest to you.
4. Go to the folder where you saved Skype file and write the command:
sudo dpkg -i skype_1.2.0.17-1_i386

That's it. :)

---

### Post by bengtfalke on 2005-10-13
Thanks for this, I was just goint to write a thread about it.....:) 

However a bit of information is missing for me. The installation complains about the libgt3c102-mt not being installed. I just downloaded it.... how do I install it?

regards/falke

---

### Post by cbudden on 2005-10-13
type sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb to install libqt3c102-mt_3.3.4-3.

---

### Post by bengtfalke on 2005-10-13
Sorry but this doesnt work. It complains about dependencies with amaroK.... This process resulted in broken packeges that I had to search for and remove..... Have you checked this installation on 5.10?

---

### Post by Jad on 2005-10-13
I had same problem, and this solve it
[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)

---

### Post by zingibong on 2005-10-13
I dont use Kubuntu, so I really dont know how to fix it on it. :???: 
On Ubuntu it works good, though. :)

---

### Post by bengtfalke on 2005-10-13
I use Ubuntu as well, so that is not the problem for me....
regards/falke

---

### Post by johannes on 2005-10-13
Works really nice! Thanks.

---

### Post by Jad on 2005-10-13
Please report which one worked with you so others can try it first.

---

### Post by Beaky on 2005-10-13
I had a conflict between skype and k3b.  This was solved by downloading skype from [seveas.ubuntulinux.nl]("seveas.ubuntulinux.nl").  Unfortunately, I forgot to make a copy before installing the release of Breezy and the page is blank when I now try to access it.  Does anyone have a copy or alternative location which I could download, please?
The page now states that it is "broken" but does not say if or when it will be re-instated.
[COLOR="Red"]
This has now been fixed.[/COLOR]

---

### Post by Jeltje on 2005-10-14
Unfortunately, this method does not work for me. 
When I do "sudo dpkg -i libqt3c102-mt_3.3.4-3_i386.deb", I get error messages that another libqt is essential for the fglrx package and therefore the package cannot be installed.
However, using the statically linked skype package does work. It takes some time to load but it works. 
The only additional thing I had to do, was enabeling my microphone.
Skype did not work very well for me under Hoary.

---

### Post by mal on 2005-10-15
I also managed to get skype working with the statically linked package.  However, I have to change to the skype directory to run it or the ring sounds don't work (I found this out from another thread).  (ie cd /opt/skype-1.2.0.17/ ; ./skype)

There is probably an easy way to do this from a panel launcher??

Note that I have been trying to get skype to send its ring tones to a second sound device, so that the headphones can be left plugged in, but it does not seem to handle this very well.  I wish there was a suitable GPL application to use instead of skype!

Mal

---

### Post by zerooo on 2005-10-17
Works for me well. (ver. skype_1.2.0.17-1_i386)

---

### Post by alof8k on 2005-10-17
Is skype broken in breezy badger? I'm not using breezy at the moment so I can't check, but wouldn't the instructions over at ubuntu guide work easier? 

[http://www.ubuntuguide.org/#skype]("http://www.ubuntuguide.org/#skype")

---

### Post by cbudden on 2005-10-17
Yes it is.  It wants a library which has a different name in Ubuntu than it wants, so will not install.  I sucessfully used an older version aswell.  Also it doesn't close out the sound device properly (1.2.0.17).  

Anyone know how to get dual sounds working with skype?  I have tried running aoss skype but i cannot call or take calls with this.

---

### Post by Sprinker on 2005-10-18
This link works....it installs first pop....no questions asked!!
[Click Here]("http://www.mneylon.com/blog/go.php?http://www.mneylon.com/skype_1.2.0.11_i386.deb"):razz:

---

### Post by KramTW on 2005-10-19
There is a version of Skype (version 1.2.0.17) with this problem fixed, you can install it by:

-As root, edit your sources.list file to include the following 2 lines.
[INDENT][/INDENT]deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
[INDENT][/INDENT]deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
[COLOR="RoyalBlue"]sudo gedit /etc/apt/sources.list[/COLOR]
-Install Skype using Synaptec Package Manager or [COLOR="RoyalBlue"]sudo apt-get install skype[/COLOR]

And you should have Skype working.

If you want to authenticate the packages in this repository you can find the instructions here: [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

Good luck

---

### Post by Inside on 2005-11-02
try doig what is on the 1st post but while installing the package instead of:

dpkg --install  libqt3c102-mt_3.3.4-3_i386.deb

try

dpkg --install --auto-deconfigure libqt3c102-mt_3.3.4-3_i386.deb

ad then install skype package :-)

---

### Post by mips on 2005-11-03
Just use "Automatix' to install Skype...

Skype v1.2.0.11 and later all have a bug that wont let you make more than one skypeout call. you will have to close & restart skype to make another call.

---

### Post by JediPottsy on 2005-11-03
how can i change the look of skype? its all black, aswell as other KDE apps. I dont have kde installed nemore, tho i did use a black theme,,,which sucked

---

### Post by mips on 2005-11-07
This should thread should solve your problem,   [http://ubuntuforums.org/showthread.php?t=76633](http://ubuntuforums.org/showthread.php?t=76633)

---

### Post by skyboy on 2005-11-08
from : [http://forum.skype.com/viewtopic.php?p=169829&highlight=#169829](http://forum.skype.com/viewtopic.php?p=169829&highlight=#169829)

resolve dependencie yourself :
In order to have it install cleanly on Ubuntu Breezy, you have to change the DEBIAN/control file to check for the libqt3-mt library: 
 Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0) 


mv skype_1.2.0.18-1_i386.deb skype_1.2.0.18-1_i386.deb.orig 
 mkdir skype.tmp 
 dpkg-deb --extract skype_1.2.0.18-1_i386.deb.orig skype.tmp 
 dpkg-deb --control skype_1.2.0.18-1_i386.deb.orig skype.tmp/DEBIAN 
 # Now use your favorite editor to edit the Depends line as above: 
 vi skype.tmp/DEBIAN/control 
 dpkg --build skype.tmp 
 mv skype.tmp.deb skype_1.2.0.18-1_i386.deb 

sudo dpkg -i skype_1.2.0.18-1_i386.deb

---

### Post by Copter on 2005-11-08
hi!

i found somewhere, some time ago this method and it works just ok (without full duplex (cant listen to b-m-p at the same time) but i think its my onboard intel card issue problem or something)```

sudo nano /etc/atp/sources.list
	deb http://www.paul.sladen.org/debian all skype
sudo apt-get update
sudo apt-get install skype
```i use Kubuntu Breezy.

copter :]

---

### Post by grugnog on 2005-11-10
[QUOTE=mips]Just use "Automatix' to install Skype...

Skype v1.2.0.11 and later all have a bug that wont let you make more than one skypeout call. you will have to close & restart skype to make another call.[/QUOTE]

I second this - "Automatix" is the easiest way to install Skype :)
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) for download

To fix the bug read: [http://ubuntuforums.org/showthread.php?p=480578#post480578](http://ubuntuforums.org/showthread.php?p=480578#post480578)

[QUOTE=grugnog]:
Skype for linux has a couple of bugs:
* Using OSS directly which stops any other program using the soundcard whilst Skype is running and
* (in versions 1.2.0.11, 1.2.0.17 & 1.2.0.18 at least) not closing the sound device after a call - so even Skype cannot use it.

Someone has made a fix for these at:
[http://juljas.net/linux/skype/](http://juljas.net/linux/skype/) and
[http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

The only problem with these is that it is just a tarball and needs make, gcc and some libraries installed to build it. However I did find a .deb at:
[http://debian.fam.cx/index.php?plugi...refer=uploader](http://debian.fam.cx/index.php?plugi...refer=uploader)
This works great. The only hiccup is that it installs the libskype_dsp_hijacker.so in /usr/lib and then looks for it in /usr/local/lib - just move the file there and it works. It should be easy to tweak the .deb to fix this however.

Then just run skype_dsp_hijacker instead of skype and the problems are fixed (just change the gnome Skype menu item).

Hopefully Skype will be fixed sometime - but this at least makes it usable!
[/QUOTE]

---

### Post by cvmostert on 2005-12-11
[QUOTE=Inside]try doig what is on the 1st post but while installing the package instead of:

dpkg --install  libqt3c102-mt_3.3.4-3_i386.deb

try

dpkg --install --auto-deconfigure libqt3c102-mt_3.3.4-3_i386.deb

ad then install skype package :-)[/QUOTE]

this worked for me after doing a

dpkg -i libqt3c102-mt_3.3.4-3_i386.deb

after the auto deconfigure step... and then install skype... seemd to work.. 

ciao

---

