---
title: "Where did QGIS go?"
date: 2008-04-25
forum: Education &amp; Science
---

### Post by jmarius on 2008-04-25
Does anyone know why QGIS is no longer available in Hardy? A google search brings a link that claims package is not available in the distro: [http://packages.ubuntu.com/hardy/science/qgis](http://packages.ubuntu.com/hardy/science/qgis). The cached page shows QGIS v0.8.1 in the universe repo.

---

### Post by machoo02 on 2008-04-26
Not sure why it's no longer in the repos, but there are a couple of PPA's that have the latest and greatest QGIS (although they were compiled for Gutsy).

---

### Post by Eric Pihopa on 2008-04-26
The gutsy version launchpad has dependency issues in when used in Hardy:
[http://ppa.launchpad.net/qgis/ubuntu/dists/gutsy](http://ppa.launchpad.net/qgis/ubuntu/dists/gutsy)

There is no workaround yet.

---

### Post by gonvelho on 2008-04-26
This is really very bad:mad:. I use mainly Ubuntu with QGIS. Is there any preview for a Hardy release?

---

### Post by jdb on 2008-04-26
I've had to go back to Gutsy because of this.
I sure hope they get it resolved soon.

jdb

---

### Post by Eric Pihopa on 2008-04-27
Now have a workaround for Hardy.

Once the Hardy in stall is complete, find a gutsy cd and use synaptic to "Add CD ROM" or enable the Gutsy repositories.
Install the "libgsl0" from gutsy. This does not appear to conflict with Hardy.

Disable the gutsy repositories, then enable:
deb [http://ppa.launchpad.net/timlinux/ubuntu](http://ppa.launchpad.net/timlinux/ubuntu) gutsy main

Install Qgis in the normal way. 

Cheers
Eric

---

### Post by shmendrik on 2008-04-28
After the upgrade to hardy I installed the .deb file from

[https://launchpad.net/ubuntu/hardy/i386/libgsl0/1.9-3](https://launchpad.net/ubuntu/hardy/i386/libgsl0/1.9-3)

and then 

sudo apt-get install qgis 

works fine, and qgis runs fine.

edit: I am using the gutsy repository for qgis.
deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) gutsy main
from
[http://download.qgis.org/downloads.rhtml](http://download.qgis.org/downloads.rhtml)

---

### Post by jmarius on 2008-04-30
Good news everyone. There is a hardy repo now:
deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

---

### Post by earlycj5 on 2008-05-01
> **jmarius said:**
> Good news everyone. There is a hardy repo now:
deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

Good news indeed!  Thank you.

---

### Post by domzo on 2008-05-06
Many thanks for this.

I have added the following line to the end of my /etc/apt/sources.list:

deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

However, when I fetch updates with adept_manager (kde) or apt-get I get an error when trying to read the repository:

Failed to fetch [http://ppa.launchpad.net/qgis/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/qgis/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

Not sure whether this is a problem with my Hardy install or with the repository... any ideas?

---

### Post by domzo on 2008-05-06
To clarify, if I do a wget on the Packages.gz archive then that works however it does not unzip correctly on my machine. So perhaps it is a problem with that file?

(or it could still be a problem with my machine.. I'm still investigating)

---

### Post by jdb on 2008-05-06
It worked fine for me, I'm running 32 bit hardy so I don't know about 64 bit.
The file I got was qgis_0.10.0-6~hardy_i386.deb and the checksum on it is:

sum qgis_0.10.0-6~hardy_i386.deb 
63149  8316

jdb

---

### Post by domzo on 2008-05-06
Thanks for the info. I still haven't got it to work here - very odd..

---

### Post by rogerdean on 2008-06-25
I've downloaded QGIS from 

deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

and all the dependencies that this pulled in from Ubuntu repos. However when I try to launch (from terminal - there's no icon set up) I get a Python error -

"Couldn't load SIP module
Python support will be disabled"

Then QGIS loads, although I've not tested functionality yet. Is this a problem? What could I do to make QGIS happy? And will we get a complete and trouble-free version?

Allbest
Roger

---

### Post by jdb on 2008-06-25
> **rogerdean said:**
> I've downloaded QGIS from 

deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main

and all the dependencies that this pulled in from Ubuntu repos. However when I try to launch (from terminal - there's no icon set up) I get a Python error -

"Couldn't load SIP module
Python support will be disabled"

Then QGIS loads, although I've not tested functionality yet. Is this a problem? What could I do to make QGIS happy? And will we get a complete and trouble-free version?

Allbest
Roger

Install these & you should be OK.

python-sip4
- Python/C++ bindings generator runtime library
- qgis needs this to start without errors
python-qt4
- Python bindings for Qt4
- qgis needs this to start without errors

jdb

---

### Post by sawjew on 2008-07-09
I have installed Qgis from the ppa but the grass plugin doesn't work.  Grass works on its own but when I start qgis from the terminal I get "ERROR 1: libgrass_I.so: cannot open shared object file: No such file or directory" and the Grass plugin doesn't appear in Qgis.

Does anyone have any ideas?

---

### Post by roderikk on 2008-10-21
Notwithstanding all the troubles you have to install it above, but why was QGIS removed?

And has anybody installed it on Intrepid?

---

### Post by sawjew on 2008-10-22
I have tried to install it on Intrepid using this PPA repository,

```
deb http://ppa.launchpad.net/mixo-mixo/ubuntu intrepid main
```

but I get a segmentation fault when I try to use it.

---

### Post by maphew on 2008-10-27
> **sawjew said:**
> I have installed Qgis from the ppa but the grass plugin doesn't work.  Grass works on its own but when I start qgis from the terminal I get "ERROR 1: libgrass_I.so: cannot open shared object file: No such file or directory" and the Grass plugin doesn't appear in Qgis.

Does anyone have any ideas?

The following made that particular error go away for me: create a text file called libgrass.conf in /etc/ld.so.conf.d, containing:
```

#Make libgrass_I.so visible to ld.so
/usr/lib/grass/lib

```
Then issue the following command:
```

sudo ldconfig

```
-- Copied from [http://help.nceas.ucsb.edu/GRASS_6_on_Ubuntu](http://help.nceas.ucsb.edu/GRASS_6_on_Ubuntu)

I can't issue some grass commands like r.in.gdal for some as yet unknown reason -- "warning: cannot read module  description(r.in.gdal)" -- though r.out.gdal.tiff works fine.

---

### Post by tfogwill on 2008-10-31
@sawjew: 
glad to see you're using our PPA and trying out our packages - we're working hard to get qgis working in intrepid.  Please keep testing the packages at:
  [https://launchpad.net/~scubuntu-dev/+archive](https://launchpad.net/~scubuntu-dev/+archive)
and
  [https://launchpad.net/~mixo-mixo/+archive](https://launchpad.net/~mixo-mixo/+archive)

See more about what we're trying to do at 
[http://scubuntu.meraka.org.za/wiki/](http://scubuntu.meraka.org.za/wiki/)

Regards
Thomas

---

### Post by shahriv on 2008-11-01
Hi,

I also tried to install qgis on a fresh intrepid, but I get a segmentation fault.

```
gdb qgis
```

shows:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb49576d0 (LWP 11226)]
0xb6b20d4b in sincos () from /usr/lib/libgdal1.5.0.so.1
```

What can I do?

---

### Post by Lars&#1758; on 2008-11-04
i am also getting a segmentation error when running qgis in ubuntu 8.10 intrepid ibex.

i could not find the config files mentioned in this related post either [http://forum.qgis.org/viewtopic.php?f=2&t=4248&p=6519&hilit=segmentation#p6519](http://forum.qgis.org/viewtopic.php?f=2&t=4248&p=6519&hilit=segmentation#p6519)

:?

---

### Post by HydrologyGuy on 2008-11-04
I have the same issues.  I also have a clean install of Ubuntu 8.10.

I deleted the configuration files (and their directories) and I still get the same error:

```

Warning: No valid projection. Unable to set map units.
Segmentation fault
```

:confused:

I hope we get this working soon - it's too good a program to miss.

Thanks.

---

### Post by radiognome on 2008-11-07
I get the same Warning and segmentation-errror (but the error is in Dutch).

Qgis for me is an indespensible program for my desktop, so since a week I have to take my private Mac to the office and back home daily to watch the results of my doings to the postgis server.

Hope someone finds a sollution soon....

Martin

---

### Post by HydroModeler on 2008-11-08
I am also having this problem on 8.10.

---

### Post by HydroModeler on 2008-11-08
I ran the gdb qgis command and got the following:

[Thread 0xb43beb90 (LWP 9894) exited]
[Thread 0xb3bbdb90 (LWP 9895) exited]
Warning: No valid projection. Unable to set map units.
Warning: No valid projection. Unable to set map units.
Warning: No valid projection. Unable to set map units.

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb47e16d0 (LWP 9887)]
0xb69aad4b in sincos () from /usr/lib/libgdal1.5.0.so.1

---

### Post by radiognome on 2008-11-10
I did have an update on qgis this morning (Ibex-AMD-64), but still

Debug: 
**********************************
Debug: QgsApplication state:
Debug: Prefix       :/usr
Debug: Plugin Path  :/usr/lib/qgis
Debug: PkgData Path :/usr/share/qgis
Debug: Theme Path   :/usr/share/qgis/themes/default/
Debug: User DB Path :/usr/share/qgis/resources/qgis.db
Debug: **********************************

Warning: No valid projection. Unable to set map units.
Warning: No valid projection. Unable to set map units.
Warning: No valid projection. Unable to set map units.
Segmentatiefout

---

### Post by HydroModeler on 2008-11-12
Update: I reinstalled QGIS from the launchpad ppa (because I reinstalled my OS) and it worked, but had some error messages regarding python.  Then I found this post:

[http://lists.qgis.org/pipermail/qgis-trac/2007-October/003159.html](http://lists.qgis.org/pipermail/qgis-trac/2007-October/003159.html)

I installed python-sip4 and python-qt4 per the link and everything seems to be fine now.

Hope that helps someone.

---

### Post by HydrologyGuy on 2008-11-15
I got an updated version. I still get the error messages, but at least it doesn't crash.

---

### Post by mariashaun on 2008-11-19
I’m a big fan of qGIS, my favorite GIS desktop client. I recently upgraded to Ubuntu Linux 8.04 LTS, a.k.a Hardy Heron, and was amazed to find that qGIS was no longer part of the standard Ubuntu repositories, which is absolutely dissapointing - anyways, here is a workaround to getting qGIS installed on Ubuntu. Of course, compiling from source is always an option, but I’m going with the ‘Ubuntu way’ here.
The latest version of QGIS for Ubuntu is available at [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/). Add this entry:
deb [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/) hardy main
to your Sources list, usually available at
/etc/apt/sources.list
And Update your Ubuntu sources:
sudo apt-get update
Now install qgis:
sudo apt-get install qgis

However, when I tried starting qGIS from the command line, I got the following 2 errors/warnings:

    Couldn’t load SIP module. Python support will be disabled

And

    Couldn’t load PyQt bindings. Python support will be disabled.

The above 2 can be corrected by installing the following packages in Ubuntu:
sudo apt-get install python-sip4
sudo apt-get install python-qt4
And with the above steps completed, I now can run QGIS again. Viva GIS :)

---

### Post by skatetokil on 2008-12-19
Ok, so it seems like the problem is solved for 8.04, what about Intrepid?

8.1 fix anyone? I'm dying here.

---

### Post by LaserJock on 2008-12-20
For those of you wondering what happened to qgis in Ubuntu, I can hopefully shed some light. Essentially, Ubuntu removed it because Debian removed it. Now, that begs the question, why did Debian remove it? The answer is, according to Debian [bug #474604]("http://bugs.debian.org/474604"), that it was just too buggy for them to keep. This isn't purely that qgis is too buggy, but that the packages were of unsuitable quality overall for Debian to keep. Hopefully in the future somebody will pick it up and get it back into Debian/Ubuntu.

-LaserJock

---

### Post by sawjew on 2008-12-20
I have Qgis working fine in Intrepid AMD64 using the repository and fixes given by mariashaun in post #30.

---

### Post by skywatcher on 2008-12-25
I followed the advice given by mariashaun, but I receive the following when trying to install QGIS on Intrepid:

```
The following packages have unmet dependencies:
  qgis: Depends: libgdal1-1.4.0 but it is not installable
        Depends: libqgis-core1 but it is not going to be installed
        Depends: libqgis-gui1 but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
        Recommends: qgis-plugin-grass but it is not going to be installed
E: Broken packages

```

Is there a way to resolve this?

---

### Post by jdb on 2008-12-25
> **skywatcher said:**
> I followed the advice given by mariashaun, but I receive the following when trying to install QGIS on Intrepid:

...

Is there a way to resolve this?

I went to this link:

[http://download.qgis.org/downloads.rhtml](http://download.qgis.org/downloads.rhtml)

and followed the instructions for Intrepid.

It worked great on a clean install of 16 bit Intrepid.

Just make sure you answer yes when it asks if you want to install without verification

BTW, click on the visitor link at the bottom of the qgis download page, it displays a map of the world that shows all the recent downloads of qgis.
Pretty cool!!

jdb

---

### Post by skywatcher on 2008-12-26
Hi jdb

Thanks for the advice, which turned out to be a most welcome Christmas gift!  I now have QGIS working on Intrepid, just in time for a last-minute look at some maps before I embark on a trip along the South African West Coast tomorrow.

Chris

---

### Post by diog3n3s on 2009-02-02
I was having this same problem (segmentation fault) for qgis 1 on Intepid, it was fixed by upgrading gdal related packages.  Apparently the original qgis install installed older gdal libs, a second look found they needed an upgrade.

---

### Post by Tomas_IV on 2009-02-07
Hi all,
reading this thread, the dependenncy, segfault, and python problems some of you have remind me mine problems when I was switching repositories to get Qgis and Grass from. I found that when I had any problems like that it usually helped:
[LIST=1]
[*]set all the repositories I want to use on (i.e. Qgis ppa and all Ubuntu repositories - I always have on everything including multiverse, not sure if needed in this case)
[*]Uninstall everything related to QGIS and GRASS.
```
sudo apt-get remove qgis grass qgis-grass-plugin python-qgis python-sip python-qt
```
[*]install everything again: 
```
sudo apt-get install qgis grass qgis-grass-plugin python-qgis python-sip python-qt
```
[/LIST]
Not sure if I managed to mention all the packages needed to reinstall, but hope so.

---

### Post by carpex on 2009-03-26
I still get the seg fault when trying to run QGIS 1.0 in Intrepid on my 64 bit install. I installed from the PPA repos. The program won't load at all. I tried uninstalling and reinstalling everything, to no avail. :(

If somebody finds another solution, please let me know!

CP

---

### Post by YLP on 2009-03-27
I've got the same problem : when launching qgis (from ppa repository) in Xubuntu the starting window opens, then nothing... Same with Grass GIS, it seems to start but then somehow crashes down. Anybody got an idea ? Could it be that it's too heavy for my computer ? (pentium III)
Thanks
Yann

---

### Post by exhuma.twn on 2009-08-28
Same here. The last message visible in the splash screen is:

```
Starting Python
```

gdb trace:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb48089e0 (LWP 6910)]
0xb67df5eb in strlen () from /lib/tls/i686/cmov/libc.so.6
```

I do some python development on this machine. Could that be related?

---

