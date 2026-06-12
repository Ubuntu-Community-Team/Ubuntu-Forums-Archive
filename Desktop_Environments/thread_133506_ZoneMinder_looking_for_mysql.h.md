---
title: "ZoneMinder looking for mysql.h"
date: 2006-02-20
forum: Desktop Environments
---

### Post by transistor on 2006-02-20
I've run
```
sudo ./configure --with-webdir=/var/www --with-cgidir=/var/www/cgi-bin
```
and get

```
checking for unistd.h... yes
checking how to run the C++ preprocessor... g++ -E
checking mysql/mysql.h usability... no
checking mysql/mysql.h presence... no
checking for mysql/mysql.h... no
configure: error: zm requires mysql/mysql.h
```

I've searched Synaptic for 'mysql' and tried installing some of the more obvious pacages but I'm still stuck at this point.

Any ideas?

I'm compiling a HowTo as I go along. Where's the best place to post it?

---

### Post by piedamaro on 2006-02-20
You need to install mysql headers file, sorry don't know which package provides them but I bet it's mysql*dev* something.
There is an howto section on this forum.

---

### Post by transistor on 2006-02-20
Gracia piedamaro.
I had a good search in Synaptic for 'mysql' and then for 'headers'. I can't see anything like mysql.h or *dev.

---

### Post by total numpty on 2006-03-01
have you worked it out yet transistor? if so, can you advertise where the step by step guide may be as me and a friend have been trying to install zoneminder on ubuntu for a while now but with no luck whatsoever.

thanks in advance :confused:

---

### Post by Ramses de Norre on 2006-03-01
```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure
./configure
apt-get install checkinstall
checkinstall -D make install

```

Found this on the forums and it works great to find needed packages! (run it in the source directory).

---

### Post by BrownieMan on 2006-03-21
[QUOTE=total numpty]have you worked it out yet transistor? if so, can you advertise where the step by step guide may be as me and a friend have been trying to install zoneminder on ubuntu for a while now but with no luck whatsoever.[/QUOTE]

I'm also trying to get it installed. Anyone get it installed yet, I need a howto.

---

### Post by transistor on 2006-03-22
Update:
I couldn't figure it out so I've put the job on hold for a while. I'm still finding my way around with Linux. Ubuntu has made this much easier.

transistor

---

### Post by transistor on 2006-04-30
OK. A new PC with lots of RAM. Clean install of Ubuntu. Trying to follow the Debian install doc and adapt it for Ubuntu. I'm also trying to construct a Howto for everyone else to improve on.

Here's what I've doing.  I've downloaded the Zoneminder Debian package and tried to install it. On every error I add the required package using Synaptic. I'm now stuck at 
```
checking for perl module LWP::UserAgent... no
configure: error: zm requires LWP::UserAgent

```
I can't figure out what this is.

**Synaptic**
Start Synaptic Package Manager (System > Administration > Synaptic Package Manager) and mark the following for installation
	apache2
	build-essential
	libdate-manip-perl
	libdbi-perl
	libdbd-mysql-perl
	libjpeg62-dev
	libmysqlclient14-dev (or latest version)
	libssl-dev
	php5
	php5-mysql
	zm
Click 'Apply' and let them install.

**Test your server**
You should now have your web server running. Test this by adding a phpinfo script to your web server as follows:
```
sudo gedit /var/www/testphp.php
```

Add the following line:
	<?php phpinfo(); ?>

Save and exit.

Test apache and php from the pc by going to the following adress :
	[http://localhost/testphp.php](http://localhost/testphp.php)

Test apache and php with another pc by going to the following adress :
	[http://yourip/testphp.php](http://yourip/testphp.php) where yourip is the ip address of the PC you're setting up.

**Zoneminder**
Download Zoneminder from [www.zoneminder.com](www.zoneminder.com).
Open the archive (.tar.gz) and extract all files to 'tmp'.
Start a terminal window.
```
cd /tmp
ls <enter>
``` and you should see the Zoneminder directory - ZoneMinder-1.22.1 in my case.
```
cd ZoneMinder-1.22.1 <enter>
``` (Type your version number as it appears in the ls directory listing.)

```
sudo ./configure --with-webdir=zoneminder --with-cgidir=cgi-bin
```
This is where the errors mentioned at the top occur.

Can anyone help with this or is my strategy all wrong?

Thanks.

---

### Post by Ramses de Norre on 2006-04-30
Use my earlier post to install and update auto-apt then do ```
sudo auto-apt run ./configure --with-webdir=zoneminder --with-cgidir=cgi-bin
```

---

### Post by transistor on 2006-05-01
Bonjour Ramses, et merci.

**Two problems:**
1. auto-apt is not installed by default. I have installed EasyUbuntu ([http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)) and just asked it to add the extra repositories. Then I used Synaptic to install auto-apt. I think it installed OK.

2. I rerun ```
sudo ./configure --with-webdir=/var/www/zm --with-cgidir=/var/www/cgi-bin
``` but I still get 
```
checking for perl module LWP::UserAgent... no
configure: error: zm requires LWP::UserAgent
``` This is a Perl module, I think.
[B]
Two questions:[/B]
1. Do I really need all these steps.
2. Why does auto-apt not pick up this particular library?
3. If I have to download the module manually where should I install it?

Merci.

---

### Post by transistor on 2006-05-01
OK, I found this. It looks like libwww-perl is what I want.

LWP (for "Library for WWW in Perl", also called libwww-perl) is a set of Perl modules that allow requests to be sent to the World Wide Web.
[http://en.wikipedia.org/wiki/LWP](http://en.wikipedia.org/wiki/LWP)

Thanks to all.

---

### Post by Ramses de Norre on 2006-05-01
You need to run the configure script with auto-apt, follow all the steps from my first post about auto-apt and add the extra options to ./configure on every line contenting it.

---

### Post by transistor on 2006-05-02
Thanks again Ramses. I think I am almost finished. I had a few problems.

1. I got a few errors that auto-apt didn't fix. I had to manually install (from Synaptic) gawk, libavcoded-dev and ffmpeg.

2. Auto-apt automatically gets all the required Perl modules (lots of them) and for each one pops up a list box with an Install / Cancel button at the bottom. Some of the boxes are too big for the screen and there is no way to get to the Install with the mouse. The solution is to hit Shift-Tab twice on each dialog to get the focus on the install button before pressing Enter. Try this on some of the smaller dialogs before you hit the big ones.

3. ZoneMinder requires some parameters for the configure steps. These below seem to work OK.
```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure --with-webdir=/var/www/html --with-cgidir=/var/www/cgi-bin
./configure --with-webdir=/var/www/html --with-cgidir=/var/www/cgi-bin
apt-get install checkinstall
checkinstall -D make install
```

The result is that I have success at all steps except the last. Here's what happens:

```
# checkinstall -D make install

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
Making install in src
make[1]: Entering directory `/home/don/Desktop/ZoneMinder-1.22.1/src'
g++  -g -O2  -L/usr/lib -L/usr/lib/mysql   -o zmc  zmc.o zm.o zm_db.o zm_config.o zm_coord.o zm_box.o zm_poly.o zm_image.o zm_event.o zm_zone.o zm_camera.o zm_local_camera.o zm_remote_camera.o zm_file_camera.o zm_monitor.o zm_user.o zm_mpeg.o zm_jpeg.o zm_regexp.o zm_signal.o zm_buffer.o zm_debug.o  -lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg
/usr/lib/libavformat.a(dc1394.o): In function `dc1394_read_header':
: undefined reference to `dc1394_create_handle'
/usr/lib/libavformat.a(dc1394.o): In function `dc1394_read_header':
: undefined reference to `dc1394_get_camera_nodes'
.
.                [many more undefined references]
.
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_decode_frame':
: undefined reference to `gsm_decode'
collect2: ld returned 1 exit status
make[1]: *** [zmc] Error 1
make[1]: Leaving directory `/home/don/Desktop/ZoneMinder-1.22.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

```

Does anyone know how to fix this?

---

### Post by transistor on 2006-05-02
Phil (Mr. ZoneMinder) suggests ([http://www.zoneminder.com/forums/viewtopic.php?p=19688#19688](http://www.zoneminder.com/forums/viewtopic.php?p=19688#19688))
> This is an ffmpeg problem. As I don't know whether you had to manually run configure or not I can't say whether it is because ffmpeg is missing or maybe just that you have a problem with the version. You will usually need to make sure you have ffmpeg cvs if installing from source or ffmpeg-devel if installing from a package.
I had installed ffmpeg with Synaptic.
Can anyone give me a clue how to fix this? (Phil hasn't used Ubuntu.)

Thanks.

---

### Post by mks113 on 2006-05-03
I'm running into the same annoying issues.  Ubuntu has been very good for me on my desktop, but when I tried to install zoneminder, I found lots of missing dependancies.  I've used apt-get and cpan to get everything, but now I'm getting the same errors as transistor.

ffmpeg is installed, apt-get isn't showing a package for ffmpeg-devel as suggested in the above reply.  

Michael

---

### Post by transistor on 2006-05-04
I've sorted out the original mysql.h query so I've started a new thread for the remaining ffmpeg problem at [http://ubuntuforums.org/showthread.php?p=984327#post984327](http://ubuntuforums.org/showthread.php?p=984327#post984327).

Thanks to all who contributed here.

---

