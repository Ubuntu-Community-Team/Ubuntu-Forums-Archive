---
title: "Easycam 2 download and install problems"
date: 2009-04-25
forum: General Help
---

### Post by falcon7876 on 2009-04-25
I just upgraded to Ubuntu 9.04 and I was trying to install the easycam program for my logitech quickcam. Needless to say it failed and the output that it gave me was:

root@sean-laptop:/home/sean# apt-get install easycam2-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
E: Broken packages

Any help? or if you know how to install a driver for:

Bus 001 Device 002: ID 046d:09a4 Logitech, Inc.

that would be awesome

Thank you

---

### Post by executorvs on 2009-04-26
I also had issues with this, I suspect it may have to do with a python error which is affecting a few other packages.
I posted the same issue here: [http://ubuntuforums.org/showthread.php?t=1104804](http://ubuntuforums.org/showthread.php?t=1104804)
and here: [http://ubuntuforums.org/showthread.php?t=100384](http://ubuntuforums.org/showthread.php?t=100384)

one of the packages which is having issues with python bindings in jaunty is the Alarm-Clock package. also I've had issues getting packages which have python 2.5 or 2.4 to build on any of my jaunty systems.

again, I don't know that it's the same issue but older versions of python are used by all the programs I've had issue with recently.

---

### Post by misaelrod on 2009-04-29
I'm having the same issue with easycam. Thanks in advance to anyone that posts a solution.

---

### Post by zbyram on 2009-05-06
I'm having the exact same problem.

---

### Post by krivosh on 2009-05-10
easy&clean solution:
-install easycam-qt package instead ;-) (tried, works for my xubuntu Jaunty..should on gnome too)

console&dirty solution: (also tried, but this is not recommended)
-force package manager to forget the missing dependencies.
The thing is, that you in fact most probably HAVE the missing package installed, just the newer version(python2.5-) which easycam doesn't recognize. So:
-install the easycam-core package as usual
-make sure that you have the dependencies for easycam-gtk package OK (python2.5-glade2, python2.5-gtk2, gksu, cheese) - if not, install them as usual
-download the package to your disk, e.g. to home folder, from [http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb](http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb)
-from console, go to the directory with package and install it by 
  sudo dpkg --force-depends -i easycam2-gtk.deb
-this will make the package manager to turn the dependency errors to warning. 
-be prepared that synaptic, aptitude etc. will complain about broken package easycam-gtk and will want to uninstall it. You can mark this package to be ignored - but in fact you can uninstall easycam as soon as the driver is installed, don't you :P

---

### Post by executorvs on 2009-05-10
could you possibly walk us through the "dirty solution"?? I would like to be familiar with the alternate route.

---

### Post by mouchkine on 2009-05-12
> **executorvs said:**
> could you possibly walk us through the "dirty solution"?? I would like to be familiar with the alternate route.

Hi everyone! I'm just another NOOB (newbie, 4th day on Ubuntu) around... but proud to say that thanks to KRIVOSH (many thanks!) links... I was able to understand more of Linux and Ubuntu command line!

But... my ACER ORBICAM (Logitech integrated in Aspire 5570) is working... ID 046d:09b0 ... still not sure if it's due to VL4 drivers or/and EasyCam2... but surely coming from the same guys at [http://blognux.free.fr/]("http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb").

I'll show you my steps, so maybe it can be useful to you... from the Terminal.

First, we need to download easycam2-core.deb and easycam2-gtk.deb from the site.
Choose to save the files (the installer will accept [COLOR=Red]core[/COLOR] but not [COLOR=Red]gtk[/COLOR] module).
You could also download and install the [COLOR=Red]easygspca[/COLOR] module (my webcam was giving some signs with this module (maybe it will do the job for you)).

[COLOR=Red]Easycam2-core module:[/COLOR] [http://blognux.free.fr/ubuntu/dists/...sycam2-core.deb]("http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb")
[COLOR=Red]Easycam2-gtk module:[/COLOR][ ]("http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb")[http://blognux.free.fr/ubuntu/dists/...sycam2-gtk.deb]("http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easycam2-gtk.deb")
[COLOR=Red]Easygspca: [/COLOR][http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easygspca.deb](http://blognux.free.fr/ubuntu/dists/hardy/main/binary-i386/easygspca.deb)

Open the Terminal (Applications -> Accessories -> Terminal)

cd /home/*username*/*Documents*  (replace username by yours) -> [COLOR=Red]cd[/COLOR] directs terminal to the specific place

sudo dpkg --force-depends -i easycam2-core.deb
sudo dpkg --force-depends -i easycam2-gtk.deb

And if you decided to download the easygspca module:

sudo dpkg --force-depends -i easygspca.deb

Quit the Terminal. Go to Applications->Accessories, there you should see Easycam2. Open it.
You'll be able to install the drivers and if you want to check if it working, after intallation is completed... click in the menu EXECUTE... it will open [COLOR=Red]Cheese[/COLOR].

You don't have [COLOR=Red]Cheese[/COLOR], you can get it from [COLOR=Red]Synaptic Package Manager[/COLOR] (System->Admin..) Or you can check your webcam status in [COLOR=Red]Ekiga[/COLOR]. (Applications->Internet).

Don't forget to uninstall Easycam modules in Package Manager...

**[COLOR=DarkOrange]~~ Well... that didn't work for me... even if my Orbicam reacted for 1st time since Ubuntu Jaunty installation...[/COLOR]** :confused::(

The trick for me was from there... [http://linuxtv.org/repo/](http://linuxtv.org/repo/)

From what I understood, same guys behind easycam... 

You need to go to the Terminal... first install [COLOR=Red]Mercurial [/COLOR](Ubuntu supposed to have it, but still asking me to install it... whatever!)

sudo apt-get install mercurial

and then... follow the instruction from [SIZE=2][COLOR=Red] [/COLOR][/SIZE][SIZE=2][COLOR=Red]*Checkout V4L-DVB or dvb-apps and *[/COLOR][/SIZE][COLOR=Red]*[SIZE=2]How to build the v4l-dvb kernel modules[/SIZE]*[/COLOR][SIZE=2][COLOR=Red][I].

Don't panic... the process is kind of long, charging the drivers... [SIZE=1][COLOR=Black]

**(I'm a noob so I know I probably didn't have to do all this... but my webcam is working... so that's the point no?)**[/COLOR][/SIZE][/I][/COLOR][/SIZE]

**Enjoy.... and thanks again Krivosh for the lead... My Acer 5570 is now 100% functional...**

---

### Post by BornOle on 2009-06-19
> **krivosh said:**
> easy&clean solution:
-install easycam-qt package instead ;-) (tried, works for my xubuntu Jaunty..should on gnome too)

Thanks to krivosh for this solution, I'm running Xubuntu too and it works as a charm!

---

### Post by merlin666 on 2009-08-16
Thanks for the instructions. I managed to get easycam installed, but it finds the WRONG webcam. It identifies an IC200C whereas I have a Micro Innovations IC100C that has the same USB ID but a different chip. According to 

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations)

it requires patching of the gspca source code, but this may not be possible anymore with jaunty. Any suggestions would be welcome.

---

