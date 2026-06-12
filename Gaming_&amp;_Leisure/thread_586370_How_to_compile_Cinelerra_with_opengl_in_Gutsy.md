---
title: "How to compile Cinelerra with opengl in Gutsy?"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by fizgig on 2007-10-22
I swear I've installed every package that had the words **opengl** and **dev** in it yet ./configure still tell me that the opengl 2 libraries are missing.

Anyone know the package I need to install to get opengl support in cinelerra?

---

### Post by fizgig on 2007-10-22
Well, I looked at the configure script and saw that the test for opengl was to look for a file called libGL.so in /usr/X11R6/lib or something.

I saw that it wasn't there.  In synaptic I saw that the installed files for nvidia-glx-new-dev included /usr/lib/libGL.so

So, I took a look in the dir myself and saw a broken link for libGL.so but a valid link for libGL.so.1 in the /usr/lib dir.

I modified the check in the configure script by making the libs line:

[B]LIBS="/usr/lib/libGL.so.1"

[/B]opengl is now enabled when I configure.

I'm compiling now.  If it fails, I'll see if I can fix it and report back what I had to do.

---

### Post by sullenx on 2007-10-23
I tried what you did, and it's not working..It still says "missing". I have every single package needed.  I'm compiling in 86_64.  Anyone help?

---

### Post by fizgig on 2007-10-23
Can't help too much with just that description.  Mind giving me the last few lines of the configure output?

---

### Post by sullenx on 2007-10-23
I think your problem was a matter of getting libraries.  Editing the config file is usually not a good thing to do.  Try this: 

sudo apt-get install libgl1-mesa-swx11-dev

---

### Post by fizgig on 2007-10-25
Thanks for the tip.  I'm not in gutsy right now but I think when I selected to install that package in synaptic, it wanted to uninstall a ton of other packages which seemed like a red flag.

p.s.  The compile went fine but it is a bit unstable when I use the program.  I'll be able to get 2 minutes of use out of it and then the program gets unresponsive.  I can drag the windows around but I can't push any buttons in the program.

---

### Post by cotcot on 2007-10-29
I compiled cinelerra with OpenGL in Gutsy successfully.

This is how I did it (it contains fragments of other threads and tutorials) :

> Before you start with the tutorial, you need to install all the packages that are needed (you need to have the extra repositories enabled for this, check out the Ubuntu wiki if you want to know how to do this, or check this thread: [http://www.ubuntuforums.org/showthread.php?t=188264):](http://www.ubuntuforums.org/showthread.php?t=188264):)

Code:
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libiec1394-dev libtiff4-dev subversion checkinstall yasm

I learned most of this from this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)
Thanks to Iprofil for learning me the (Cinelerra) compiling basics 
Cinelerra community version homepage: [http://cvs.cinelerra.org](http://cvs.cinelerra.org)
Offical Cinelerra homepage with explanation of what Cinelerra is: [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

1. Compiling and installing x264

First we need to compile x264, because the x264 packages in the Ubuntu repositories are not compiled correctly to be used for compiling Cinelerra (in 32-bit Ubuntu they are compiled correctly but in 64-bit Ubuntu they are not). The first thing we need to do is get the latest x264 revision:

Code:
svn co svn://svn.videolan.org/x264/trunk x264

Then cd into the folder (cd x264) and execute the configure file. However, you need to add the flag --enable-pic, this way x264 will compile in the right way so you can use it with the compilation of Cinelerra.

Code:
./configure --enable-pic

When this is ready, we will compile x264, just type 'make' when you are inside the x264 folder:

Code:
make

After this, install it with 'make install':

Code:
make install

Now you are done with installing x264, let's move on to the important part: compiling and installing Cinelerra!

2. Compiling and installing Cinelerra

Get the latest revision of Cinelerra:

Code:
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual

cd into the hvirtual folder that was created when downloading to latest revision and edit the autogen.sh file with gedit:

Code:
gedit autogen.sh


Find this:

# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7

and remove the hashes (#) in front of both lines, and save the file.
Now we are going to compile Cinelerra. cd to the hvirtual directory and execute the following commands:

Code:
./autogen.sh
./configure
make
sudo make install

During make I had to install "nasm" to overcome this error :
Quote:
.libs/fdct_mmx.o: No such file or directory
> make[2]: *** [libmpeg2enc.la] Error 1 
I followed this way of solving to overcome the error in make in the quote :
Quote:
For some reason there was a problem just on the AMD64 system. It is
> probably just a temporary problem with the state of cinelerra-cvs or with
> the way my system was configured. I got the following error:
> make[4]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> : --update de.po cinelerra.pot
> rm -f de.gmo && : -c --statistics -o de.gmo de.po
> mv: cannot stat `t-de.gmo': No such file or directory
> make[3]: *** [de.gmo] Error 1
> make[3]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> make[2]: *** [stamp-po] Error 2
> make[2]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> make[1]: *** [all-recursive] Error 1
> make[1]: Leaving directory `/home/dfort/test/cinelerra/hvirtual'
> make: *** [all] Error 2
> 
> It isn't good to go on after a make error like this. What I did may have
> been a bad thing, but since I'm only going to use English it probably
> didn't do any harm:
> $touch po/de.gmo
> $touch po/es.gmo
> $touch po/sl.gmo
> $touch po/fr.gmo 

code
touch po/de.gmo
touch po/es.gmo
touch po/sl.gmo
touch po/fr.gmo
touch po/it.gmo
touch po/pt_BR.gmo
touch po/eu.gmo

I have now cinelerra compiled on an AMD64 with OpenGL enabled.


The following errors occurred when starting cinelerra :

void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7ffffff">/proc/sys/kernel/shmmax

This is what the cinelerra manual tells and was enough to solve the error message  :

For a permanent change, add to the `/etc/sysctl.conf' file the following line: 
kernel/shmmax=0x7fffffff
or if you prefer: 
kernel.shmmax = 2147483647
For the first time, to avoid restarting your computer, use the following command as root: 

code :
sysctl -p

---

### Post by sullenx on 2007-10-30
I will try it out..i was getting stuck in the -fPic part, where i would pass that flag and it wouldn't take it.

---

### Post by jan_everts on 2007-11-19
Thanks for the howto.

I had one last error remaining when starting cinelerra :( :
*cinelerra: error while loading shared libraries: libquicktimehv-1.6.0.so.1: cannot open shared object file: No such file or directory.*

Installing:
libarts1-mpeglib (4:3.5.8-0ubuntu1)
libmpeg-dev (1.3.1-8)
libmpeg1 (1.3.1-8)
libmpeg2-4-dev (0.4.1-1)
libmpeg3-1 (1.5.4-5)
libmpeg3-dev (1.5.4-5)
 did the trick :).

Cinelerra now works with Opengl and it is so much faster.
:guitar:

---

### Post by crossan007 on 2007-11-23
i did it really easily.. 
[http://cvs.cinelerra.org/](http://cvs.cinelerra.org/)   just followed the directions there and made a copy of libGL.s0.1 to libGL.so.1.2


it might crash because its an older version of the libraries, but it required nothing more than synaptic and a simply file copy.    any comments on this please let me know, it appears to be working for me.   no re-compiling

---

### Post by DishBreak on 2007-12-01
> **sullenx said:**
> I think your problem was a matter of getting libraries.  Editing the config file is usually not a good thing to do.  Try this: 

sudo apt-get install libgl1-mesa-swx11-dev

I've put that in synaptic, and it tells me i will need to remove my nvidia glx drivers and my ubuntu-desktop package. doesn't sound like a good thing to me. :-k

---

### Post by Jehu on 2007-12-02
Try this:
sudo ln -s /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2

---

### Post by DishBreak on 2007-12-02
Okay, so i created a link to the missing file. but now:
Result:

```
vishal@dishbreak-ix:~$ sudo ln -s /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
[sudo] password for vishal:
vishal@dishbreak-ix:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on dv nov 23 13:59:58 CET 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)
vishal@dishbreak-ix:~$ 

```

Things are even more informative now. =_= Might my nvidia's restricted driver be causing a problem?

---

### Post by swmiller6 on 2007-12-02
[http://lab.dyne.org/cinelerra/Gutsy](http://lab.dyne.org/cinelerra/Gutsy)

Followed that guide and everything worked great....

swmiller6

---

### Post by Gluggie on 2007-12-04
> **DishBreak said:**
> Okay, so i created a link to the missing file. but now:
Result:

```
vishal@dishbreak-ix:~$ sudo ln -s /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
[sudo] password for vishal:
vishal@dishbreak-ix:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on dv nov 23 13:59:58 CET 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)
vishal@dishbreak-ix:~$ 

```

Things are even more informative now. =_= Might my nvidia's restricted driver be causing a problem?

I have the same problem, also using nvidia. :(

---

### Post by nemo.r on 2007-12-08
I was trying to get cinelerra to work, so I typed 

```
sudo apt-get install libgl1-mesa-swx11-dev 
```

into the terminal, it said it wanted to remove 

```
libgl1-mesa-dri libgl-mesa-glx nvidia-glx-new
```

And I said yes, which I realise now was a really stupid thing to do but anyway... 

Then I restarted my computer and it came up with a warning saying the computer is using low resolution do I want to continue, I said yes, and it comes to a low-res version of my login page.

I typed in my username and password and it gives me an error message saying my login and password are incorrect. (I've repeated this many times, I'm typing it right I'm certain).

Then I click restart and the terminal appears, I can login fine in the terminal.

I tried reinstalling my old libgl stuff, but it first says they are not 'confirmed' or words to that effect, do I want to continue anyway? I click yes, then it says unable to connect to the site, so they are not downloaded.


I removed the libgl1-mesa-swx11-dev without any trouble, 


Now when I start up I go straight to the low res login page, and I can't seem to get back to the terminal. (Which is why I can't remember the exact messages it gave me)

Is there a way to force start the terminal?
I was wondering if I couldn't connect because I am using wireless, so I can connect via ethernet, but there doesn't seem much point if there's no terminal.

Is there a way to get around the login page?


Most importantly how do i get my old libgl stuff back?

Any help would be massively appreciated, I don't much care if cinelerra never works, I just want to get back into my computer!!

Thanks in advance.

---

### Post by DishBreak on 2008-01-06
hey, not sure if you're still having problems. I gave up working on Cinelerra because i was afraid of running into a problem like yours. 
wireless shouldn't make a difference, but ethernet isn't a bad idea to try.

a couple of things you can try:
1) go to a recovery mode. if your machine only has linux on it, press esc when it says "Loading GRUB menu" or something to that effect on boot. from the menu select a recovery mode. 
Try installing the packages again using apt-get. 

2) manually download the packages. 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
find the packages you need here and try manually installing them on your computer. use the command
```
 sudo dpkg -i <package.deb>
```

3) use envy to reinstall drivers. this might actually be your best bet. 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It will reinstall the driver and take care of any issues you might have with dependencies.

I know this might be too little, too late...but i thought i'd try to help out.

live and learn =)
DishBreak

---

