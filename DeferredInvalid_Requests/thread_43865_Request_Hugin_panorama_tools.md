---
title: "Request: Hugin panorama tools"
date: 2005-06-23
forum: Deferred/Invalid Requests
---

### Post by ericsp on 2005-06-23
see the topic. Installing from debian repositories does not work for simple people like me. Get the error with libpano12 and when I try to install it, another problem.

Eric

---

### Post by kblood on 2005-08-10
Another vote here. This would be great!

---

### Post by zovirl on 2005-08-16
yes, I would love having hugin available.  Looks like we might not have long to wait:
[http://lists.debian.org/debian-wnpp/2005/08/msg00272.html](http://lists.debian.org/debian-wnpp/2005/08/msg00272.html)

---

### Post by avilella on 2005-08-29
Another vote: hugin seems to be a great tool!

---

### Post by sargo on 2005-09-03
Another vote more...  Since Ubuntu has good graphical tools Hugin would be a great addition...

---

### Post by cotcot on 2005-09-14
I join the club. Hugin is nowadays a must. I had it running on SuSE 9.2 a year ago and have it running on MS XP because the install in Hoary failed. I have seen that libpano12 and emblend are in Breezy, so the way cannot be so long. It can run in Sarge also.

---

### Post by Xanf on 2005-10-11
And one vote more!
I also miss a stitiching tool in Breezy!

---

### Post by tikal26 on 2005-10-19
another vote. we really need hugins in breezy

---

### Post by kiddo on 2005-10-22
panoramaaaaaaa I have tons to stitch, waiting for a way to get hugin without spending a month trying to get its dependencies solved! *votes*

---

### Post by ProNoblem on 2005-10-27
Unfortunatly I'm also bound to windows for my stitching.., so another vote for Hugin is here..

---

### Post by ericsp on 2005-10-30
I mailed the guy who posted this message [http://lists.debian.org/debian-wnpp/2005/08/msg00272.html](http://lists.debian.org/debian-wnpp/2005/08/msg00272.html)

Here is his answer:
> 
> still pending, I think they won't be before Dapper Drake, but maybe with
> the backports....
>
> Hub

so we need to be patient.

Eric

---

### Post by Books on 2005-12-01
Any news on Hugin?

I really need this one. And Hugin is one of the few tools keeping me on Windows, so count another vote here. Thanks!

Books

---

### Post by kblood on 2005-12-01
Apparently, you can get it from this unofficial repository:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

I haven't tried, because I followed a guide to compile it all and be happy with it :)

Good luck.

---

### Post by jdong on 2005-12-01
Not in Dapper, not in Sid... Try contacting MOTU.

---

### Post by surfer63 on 2005-12-28
Hi all,

I recently switched from Slackware to Kubuntu 5.10 (Breezy Badger) and as an enthousiastic user of Hugin, I wanted that also on my Kubuntu. No working package to be found however. As I'm used to compile/build packages myself I looked for instructions (as I'm new to debian-like linuxes. 
I found the instructions on [http://planet.ubuntu-fr.org/index.php/?q=hugin](http://planet.ubuntu-fr.org/index.php/?q=hugin)

After having built hugin and tools I decided to create an automatic script for myself and other (K)Ubuntu users (after having read several forums with requests).

The script atached downloads, builds and installs autopano-sift, panotools, enblend and hugin 0.5  and does it all automatically. When done (and that takes some time off course) you can start hugin.
It does not add menu items for hugin and the tools.

I attached the script to this post. I works for me and one of my friends (also on Kubuntu 5.10)

Instructions for use:
- Save the script to your home directory as hugin-0.5 (for example. It is attached as hugin-0.5.txt as I could not attach it otherwise)
- open a terminal/console
- sudo sh hugin-0.5 (or what you called the script)
- Sit back, answer some occasional questions whether to download libraries and so on
- Cross your fingers and hope it will work for you too
- When finished you can start hugin (hopefully)

Please note: I will answer questions and respond to bugs about my script, but as already mentioned: I have some years of linux (Slackware) experience, but uptil now only two weeks of Kubuntu experience. Don't expect me to deal with all kind of difficult (K)Ubuntu (debian) like questions.

Good luck,
Harry

---

### Post by ERam123 on 2005-12-29
Have you been able to get autopanog.exe to run properly?  It loads ok but it throws a lot of errors my way when I try to actually compute some control points.

---

### Post by surfer63 on 2005-12-30
Yes, that can be. 

What I forgot to mention is that I also downloaded mono directly from the mono site as the Breezy mono packages are not that good.

- Download the mono installer from [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads)
(It runs on every linux distribution)
- do from a terminal window and in the directory where you downloaded mono:
     sudo chmod a+x mono-1.1.12.1_0-installer.bin  (to make it executable)
     sudo mono-1.1.12.1_0-installer.bin   (to install mono)
When mono has installed
- modify your /etc/ld.so.conf (if it doesn't exist, create it)
- add the following two lines
/opt/mono-1.1.12.1/lib
/usr/local/lib
(The second is just to be sure)
- do a sudo ldconfig

- logout (end session) and login again (this to effectuate the changes to ~/.profile and ~/.bashrc)

good luck

---

### Post by ericsp on 2006-01-16
[QUOTE=surfer63]Hi all,

...

I attached the script to this post. I works for me and one of my friends (also on Kubuntu 5.10)

....
Good luck,
Harry[/QUOTE]


Hey Harry,

GREAT script. Worked perfectly for me. Enblend is crasshing sometimes if I make huge panorama's, but in general everything is OK! Thanks a lot for sharing!

Eric

---

### Post by cotcot on 2006-02-07
I used the script above. The installation is fine but the working not. Autopanog loads with this error in a window titled "wxExecute error" : 

commando:autopanog.exe --output autopano_result_tempfile.pto --imagelist /tmp/ap_imgnamesDS5MO3
failed with error code: 1   

Making manual control points and using PTStitcher gives an error code : PTStitcher stopped with non-zero (or non null) error code.

Making manual control points and using nona works fine.

Are there any new ideas for autopanog and PTStitcher ?

---

### Post by anders on 2006-02-16
I also used the script and it seems to work fine. Thanks surfer63 for making it available!

---

### Post by pimlottc on 2006-03-23
The hugin snapshot binary debs worked for me.  They're linked from the [download page]("http://hugin.sourceforge.net/download/").  Here's what I did:

1. Install libwxgtk2.5.3

Hugin snapshots are compiled against this older version of libwxgtk.  You can use the version from hoary, which you can download from [http://packages.ubuntu.com/hoary/libs/libwxgtk2.5.3]("http://packages.ubuntu.com/hoary/libs/libwxgtk2.5.3").
Save it somewhere and then manual install it:

```
sudo dpkg -i libwxgtk2.5.3_2.5.3.2ubuntu4_i386.deb
```

If it complains about dependancies, the easiest thing to do is just install breezy's version of libwxgtk first, which will draw in the dependancies automatically.

```
sudo apt-get install libwxgtk2.6.0
```

2. Add hugin snapshot repository to APT sources

Add the following lines to the end of /etc/apt/sources.list:

```
# hugin snapshots
deb http://3demi.net/debian debs/
```

3. Update packages and install hugin (& enblend)

```
sudo apt-get update
sudo apt-get install hugin enblend
```

You can also use Synaptic for this step if you're more comfortable with it.

I did this under breezy, probably will work under dapper as well.

---

### Post by cotcot on 2006-04-10
I have hugin working under dapper the same way the previous poster did. 
The autopano.exe does not work (it is claiming for mono corlib version 46 but detected version 47 ; it suggest to download a newer :confused: version from the mono site). PTStitcher does not work either. However PTStitcher is working better than nona (as i can see with hugin running on XP and under Gentoo)

---

### Post by randomas on 2006-08-31
I would like to add another vote for the request of this tool set.

---

### Post by surfer63 on 2006-08-31
Hi all,

The poster pimlottc, as well as the hugin website itself, pointed us to [http://3demi.net/debian/debs/](http://3demi.net/debian/debs/). I used that one too. However, the packages no longer seem to be maintained as they are stil at 0.53 and hugin has now reached (stable version) 0.61 so I refurbished my "old" script (see 28th Dec post).
Again, it works for me. I hope it works for you too. The script is attached to this post.

-autopano-sift is now part of the Universe repositories and does not longer need to be built.
-panotools (libpano) 2.7 is also part of the Universe repositories but too low in build for hugin 0.6x. hugin needs 2.8.x. We still need to compile & build that one.
- Enblend version 2.5 is used.
- Hugin 0.61 is used.
- No autopano.exe is built as I think that autopano-sift works better (and is nice to use).


Prerequisites:
- A working internet connection (You never guessed that).
- You need to have Universe enabled in your repositories (I assume you know how to do that, otherwise check the (K)Ubuntu user manuals).
(- and possibly: uninstall hugin 0.53 from [http://3demi.net/debian/debs/](http://3demi.net/debian/debs/) before running the script and remove/disable this repository).

Instructions for use of this script:
- Save the script to your home directory as hugin-061 (for example. It is attached as hugin-061.txt as I could not attach it otherwise)
- open a terminal/console
- do a chmod a+rx hugin-0.61 (or whatever you called the script).
- sudo ./hugin-061 (or whatever you called the script). The sudo command runs the script with root authorizations/rights to be able to install the software. The sudo command will ask for a password. This is your OWN password, NOT the root password (in case you didn't know).
- Sit back, answer some occasional questions whether to download libraries and so on
- After every phase of dowloading, building, compiling and installing the script will pause and question you to abort or continue. This also gives you the possibility to check on errors (don't mind the warnings). Increase the height of your terminal (temporarily) to see more information in one glance.
- Cross your fingers and hope it will work for you too.
- A subdirectory panorama will be created where all work takes place. Aftwerwards this directory wil be removed again.
- When finished you can start hugin from a terminal window (hopefully). No icon in the menu will be created. You can use autopani-sift and enblend directy from inside hugin.


Success,
Harry

---

### Post by randomas on 2006-09-01
The deb repositories worked for me,although autopano.exe doesn't work ptsticher does and gives good results.
I'm trying the compile script, but I'm running into problems:

libboost-thread-dev and wxwidgets dependencies need to be added to the script. 

At the moment it fails to compile due to errors in imagegrapgh.h and PTOptimise.h 

I'll try and see what can be done (like trying another version) ;)

---

### Post by randomas on 2006-09-01
Ok got it to compile ... On my pc another of the "apt" lines of script needed repeating :
```
 apt-get install libwxgtk2.6-dev gettext wx-common libboost-thread-dev libboost-thread1.33.1 libboost-graph-dev libgtk2.0-dev
```
Also if you've been playing with XGL you've also probably aded some repositories and need to downgrade certain libraries to install libgtk2.0-dev.

Now that it's working a few things have changed even though basic functionality is the same. Trying to use autopano or autopano-sift from within hugin still doesn't work (I use autopanog to generate a .pto and then load it in hugin) also ptsticher is not working. 

Thanks to everyone for the work involved hope this helps anyone else getting stuck.

---

### Post by surfer63 on 2006-09-04
Hi Randomas,
 
You mention: 
> **randomas said:**
> Trying to use autopano or autopano-sift from within
hugin still doesn't work
I did mention that I didn't include autopano as I prefer autopano-sift.
 
Can you explain what isn't working with autopano-sift. Can't you start it
from Hugin, Doesn't it send back to hugin the points it calculates, Does it
give error messages ?

I attached  an updated script. I added the line you mentioned also twice. I don't know whether this is an apt-get bug. I will check other forums about it.

bye,
Harry

---

### Post by S.nazari on 2006-09-09
I have used the script and everything is installed but now everytime I try to select Ptsticher as the stiching engine everything crashes with this message in the terminal. 
(hugin:17587): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

is there a script to remove all this and would it be possible to create .deb using this script. ? 

Thanks
Sorush

---

### Post by surfer63 on 2006-09-11
> **S.nazari said:**
> I have used the script and everything is installed but now everytime I try to select Ptsticher as the stiching engine everything crashes with this message in the terminal. 
(hugin:17587): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
It has something to do with gtk+, glib or something else from gnome. You do not mention (nor does you profile tell it) whether you use Ubuntu (with Gnome) or Kubuntu (on KDE). If you use Kubuntu try installing the package gnome-core. This will add all necessary "basic setup" Gnome libraries and so on. (You can always remove it again.)

> **S.nazari said:**
> 
is there a script to remove all this and would it be possible to create .deb using this script. ? 
I suppose it is possible, but I don't know how to do that.

---

### Post by surfer63 on 2006-09-11
> **S.nazari said:**
> I have used the script and everything is installed but now everytime I try to select Ptsticher as the stiching engine everything crashes with this message in the terminal.

Another thing: Does it work if you use nona instead of ptsticher ?

---

### Post by S.nazari on 2006-09-11
Well I have just install gnome-core and nothing really happens.. 
I get the same silent crash. I don't really know how to trace it back. 
nano yes it does work but very badly since no feathering happens.

---

### Post by surfer63 on 2006-09-11
Sorry,

I don't know how to help you further. I'm not a programmer.

---

### Post by S.nazari on 2006-09-17
how would I remove the programs that I installed using your script?

---

### Post by surfer63 on 2006-09-18
You can remove the "standard binaries" by issueing the following command (from a terminal window):
sudo apt-get remove autopano-sift mono mono-mcs libglade-cil libwxgtk2.6-dev  libboost-thread-dev libboost-thread1.33.1 libboost-graph-dev libgtk2.0-dev libboost-dev libtiff4-dev libjpeg62-dev
(above all on one line)

This leaves some standard (graphic) libraries on your system, but you need them anyway when using other (graphic) programs and were most probably already on your system.

The other compiled, built and installed binaries and libraries can be removed by using the follwing rm commands (from a terminal window):
sudo rm /usr/local/bin/PT*
sudo rm /usr/local/bin/auto*
sudo rm /usr/local/bin/enblend
sudo rm /usr/local/bin/hugin
sudo rm /usr/local/lib/autopano*

All other (temporary and intermediate) files were already removed in the build script.

Success.

---

### Post by tom_ on 2006-09-24
surfer63 .....
thank you for your efforts on this as the hugin suite is def something i used to use with affection and would love to see it in ubuntu again soon.

i have been messing around with your script a good bit of the afternoon but still have the following problems ...

========================

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
E: Broken packages

=======================

.... and naturally am not making in progress in the face of this.

Do you have any recommendations as to how i can get out of the grip of this dependancy "trap" ???

:-({|=

---

### Post by surfer63 on 2006-09-26
Hi Tom,

I changed the script a little. One of the lines says: 
apt-get install libwxgtk2.6-dev .......... libgtk2.0-dev


I changed that to:
apt-get -y --force-yes install libwxgtk2.6-dev ....libgtk2.0-dev

This forces the installation of (among others) libgtk2.0-dev and its dependencies (At least that should happen).

###
##Please try the attached (complete) script.
###
**Update 28 Sept: I removed the attached script hugin-061a.txt as it is no longer necessary, based upon Tom_'s latest mail of 28 Sept. Please use the script attached to one of my previous posts.**

---

### Post by tom_ on 2006-09-27
UH OH .....

Surfer63 ....

I have uncovered the reason i was unsuccessful running your script here and it was all my fault .... please reinstate, or delete, the changed script just in case.

My problem was, and i don't quite understand how it came about, is that i did not have the updates repository in my sources.list and the two items i had not received were both involved in the problems i was experiencing with dependancies.

Sorry for putting you to the trouble you went to and please once again accept my appreciation of what you have done here as I now have a functioning hugin/enblend/autosift suite.

Tom_

---

### Post by surfer63 on 2006-09-28
Tom_,

Thanks for the feedback: no bad feelings whatsoever. 
I removed the modified hugin-061a script.

---

### Post by tom_ on 2006-10-08
Surer63,

You have really done very well with that .... its all running very very well here now and i amdelighted.

I have been fiddling with some hugin stuff in Edgy Eft as well but its only a partial answer there as neither autopano-sift nor enblend are included.

Looks like your script will be handy there too in a month or so.

Best regards and deepest appreciation for a highly valuable and superior panorama stitcher.

---

### Post by kukir on 2006-10-09
Surfer63,
nice script. Everything looked fine while it was running but when I tried to run hugin I got the following:

hugin: error while loading shared libraries: libpano12.so.0: cannot open shared object file: No such file or directory

Unfortunately I was not able to figure out what went wrong.
Anybody?

---

### Post by surfer63 on 2006-10-10
Kukir,

I attached the panotools part of the script to this post. It will download, build and install the panotools only (and will off course not touch the rest). It waits after every relevant step so you can check what's going wrong.

 Instructions for use of this script:
 - Save the script to your home directory as panotools (for example. It is attached as panotools-check.txt as I can't attach shell scripts directly for security sake)
 - open a terminal/console
 - do a chmod a+rx panotools (or whatever you called the script).
 - sudo ./panotools (or whatever you called the script). The sudo command runs the script with root authorizations/rights to be able to install the software. The sudo command will ask for a password. This is your OWN password, NOT the root password (in case you didn't know).
 - Check what's going on. In case of errors: let me know. If no errors show up, it should work.
The following files should be installed (including path):
/usr/local/lib/libpano12.so.0.0.0
/usr/local/lib/libpano12.so.0
/usr/local/lib/libpano12.so
/usr/local/lib/libpano12.la

Succes

---

### Post by kukir on 2006-10-12
Thanks for the help. 
Unfortunately the script does not give away any clues. No error messages, nothing special as far as I can tell. The files are there but hugin does not find them. Is there a chance to find out where exactly hugin is searching?

---

### Post by surfer63 on 2006-10-13
Hi Kukir,

Please do from a terminal window:
> 
mkdir ~/panorama
cd ~/panorama
wget "http://surfnet.dl.sourceforge.net/sourceforge/hugin/hugin-0.6.1.tar.bz2"
tar xvfj hugin-0.6.1.tar.bz2
cd hugin-0.6.1
./configure --with-unicode=yes | tee configure.log


The last line "copies" all output to configure.log.
So please check the configure.log. It should contain the following lines:
checking for PanoTools support ...
configure: pano home set to /usr/local
checking pano12/panorama.h usability... yes
checking pano12/panorama.h presence... yes
checking for pano12/panorama.h... yes
checking pano12/queryfeature.h usability... yes
checking pano12/queryfeature.h presence... yes
checking for pano12/queryfeature.h... yes
panotools query functions enabled
checking for fcnPano in -lpano12... yes
checking for execute_stack_new in -lpano12... yes
checking if Panotools package is complete... yes

*- And -*

Shared libraries --enable-shared=no
Static libraries --enable-static=yes
JPEG             --with-jpeg=           have_jpeg  = yes
PNG              --with-png=            have_png   = yes
TIFF             --with-tiff=           have_tiff  = yes
ZLIB             --with-zlib=           have_zlib  = yes
**PANO             --with-pano=           have_pano  = yes**
BOOST            --with-boost=          have_boost = yes
Unicode          --with-unicode=yes

*- And -*
  PANO_FLAGS       = -I/usr/local/include -DHasPANO
  LIB_PANO         = -L/usr/local/lib -lpano12


If "something" is not correct, let me know or attach/copy in the configure.log. 
However, if everything is correct I really have to think deep (meaning: I don't know right now).

---

### Post by kukir on 2006-10-17
Hi surfer,
I did what you proposed and got exactly the same lines as the ones you posted. Did you try your script on Dapper Drake too? I'm running the amd64 version, might this be the problem?
Anyway, thanks for the help. I'll leave it for now and give it another try in Edgy Eft in a few days.
Best regards

---

