---
title: "Skype problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by nbx909 on 2005-10-14
Using the newest deb from skype.com
> 
michael@mikeubuntu:~/Desktop$ sudo dpkg -i skype_1.2.0.17-1_i386.deb
Selecting previously deselected package skype.
(Reading database ... 68859 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.17-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
michael@mikeubuntu:~/Desktop$

so i try
> michael@mikeubuntu:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
michael@mikeubuntu:~$

I installed libqt-mt but skype isn't takeing it since it wants  libqt3c102-mt. 
Any suggestions on how to get skype to work?

---

### Post by manicka on 2005-10-14
[http://www.ubuntuforums.org/showthread.php?t=75107&highlight=skype+breezy](http://www.ubuntuforums.org/showthread.php?t=75107&highlight=skype+breezy)

---

### Post by nbx909 on 2005-10-15
okay i did that and skype worked thanks, but then i installed the fglx drivers using this faq [http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+radeon+9600](http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+radeon+9600) today and it uninstalled skype and libqt3c102-mt  because fglrx-control depends on libqt3-mt. any suggestions?

---

### Post by NoXiS on 2005-10-15
Hi

Check out this page for a solution to your problem. The exact same thing was driving me nuts!

[http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/)

There is a slight error in the 'depends' line on the page though, it should read:

Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)


And note that the instrctions on that page also do not use the double-hyphen for extended parameters for dpkg, so they should read something like:

dpkg-deb --extract skype_1.2.0.17-1_i386.deb.orig skype.tmp

Here is my complete DEBIAN/control file.


Package: skype
Version: 1.2.0.17-1
Section: non-free/net
Priority: extra
Architecture: i386
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.4.1-3), libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0)
Installed-Size: 8945
Maintainer: Skype Technologies <info@skype.net>
Description: Free Internet Telephony - The whole world can talk for free
 Skype is free Internet telephony that just works.
 Skype offers free superior sound quality Internet telephony. In addition, it
 includes:
 .
  * Conference calling - enables simultaneous and seamless voice communication
    between groups of up to five friends, family or colleagues.
 .
  * Global Directory - the user-built global Skype contacts directory with
    numerous search options and an easy add-a-contact tool
 .
  * Customization - My Picture image display
 .
  * Mobility - login into Skype account on more than one PC anywhere
    in the world.
 .
  * Multiple Skype accounts on one PC

---

### Post by iNerdSure on 2005-10-15
Encountered this error:

:~/skype-deb$ sudo dpkg -i skype_1.2.0.17-1_i386.deb
Password:
Selecting previously deselected package skype.
(Reading database ... 67839 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.17-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

Where have I gone wrong? Any advise or suggestions? Thanks.

---

### Post by nbx909 on 2005-10-15
Noxis that is not helpful because we can not use libqt3c102-mt because we need the newer verson for the ati drivers.

---

### Post by nbx909 on 2005-10-15
download the Dynamic binary tar.bz2 verson from [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/) and untar it. Then copy the folder to /usr/share/skype and /usr/local/share/skype click on the file named skype and it should launch in a few seconds.

---

### Post by NoXiS on 2005-10-15
@nbx909

I don't think I misunderstood your problem. That fix removes skype's dependancy on libqt3c102-mt and allows it to use the installed libqt3-mt instead, which is what your ATI drivers use.

Hope that makes it clearer. What the fix is essentially doing is altering the file contained inside the deb package that contains a list of the dependancies and saying 'use libqt3c102-mt OR libqt3-mt', the relevant change in the 'depends' line is:  libqt3c102-mt (>= 3:3.3.3.2) | libqt3-mt ( | is the symbol for OR).

I had never taken a deb file apart and rebuilt one either, but the process, and following the instructions on that page, is pretty straightforward.


@iNerdSure

Fire up Synaptic or(use apt-get) and install the 'libstdc++5' package. I presume you had already fixed the Skype package as mentioned in my previous post?

---

### Post by iNerdSure on 2005-10-16
@NoXis

Many thanks. I managed to get Skype working eventually, including configuring the appeance with KControl. Skype comes default for KDE, hence installed on Ubuntu, the default windows and fonts are very large. 

Many thanks to everyone who posted their solutions for me to install by trial and error. 

In the end, I got Skype on my laptop : )   At least I can msg callers that my laptop is ok, except that there is no SOUND ..

Now, the next challenge .. to get the sound and video working : (

---

### Post by movil on 2005-10-26
Did someone got the audio in Skype to work ?
I'm really interested on getting it working.

On another topic:
Is possible to use  Google talk audio calls somehow ?


I like very much Ubuntu :)

Update: Now it works with alsa right ? So finally I got it working!

---

### Post by Jingo on 2005-10-26
I installed Skype in 3 different ways, because it is using 40% cpu.

Using the static qt package uses about 10-20% cpu, but I think it is still not good enough... anyone having the same problem?

/Jingo

---

### Post by Doc.Caliban on 2005-10-29
[QUOTE=movil]Did someone got the audio in Skype to work ?[/QUOTE]

I installed Ubuntu to see if I could go without Windows.  In XP I use Skype every day for phone calls, both outgoing and incoming. 

I've been having trouble getting Skype to start at all, but before I bother troubleshooting that, I need to know if it's going to be a waste of time... does the sound work or not?  If not, that's going to be a deal breaker and I'll go back to XP straight away.

-Doc

---

### Post by Typhoon on 2005-10-29
I have just set up skype on my Ubuntu breezy and installed it (using a remote desktop) for a friend who lives 10,000 miles away :-)

Get the .deb package from

[http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html](http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html)

Install it with 

sudo dpkg -i skype_1.2.0.18-1_i386.deb.html

Try to run it. Look and see if there are error messages. If so, you may have to install several more packages from Synaptic. I don't remember exactly what they are, but one of them is libqt3-mt

This version takes a long time to load (about 30 seconds). This is a bug, and there are discussions somewhere about how to fix it, but I haven't bothered.

HTH,
Typhoon

---

