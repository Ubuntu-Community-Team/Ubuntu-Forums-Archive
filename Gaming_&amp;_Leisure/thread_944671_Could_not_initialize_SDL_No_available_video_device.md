---
title: "Could not initialize SDL: No available video device"
date: 2008-10-11
forum: Gaming &amp; Leisure
---

### Post by greenkernel on 2008-10-11
When I am trying to play Battle for Wesnoth, the following error comes up:
> Battle for Wesnoth v1.4
Started on Sat Oct 11 08:18:32 2008

20081011 08:18:32 error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.
I have already installed the following dependencies for Wesnoth too.
> libbo0st-iostreams1.34.1
libc6
libfreetype6
libfribidi0
libgcc1
libsdl-image1.2
libsdl-mixer1.2
libsdl-net1.2
libsdl1.2debian
libstdc++6
libx11-6
python2.5
wesnoth-data
zlib1gI'm using NVIDIA GeForce 6200 TurboCache (PCI-E), the restricted driver for NVIDIA is already installed too, Linux kernel 2.6.24-19-generic and GNOME 2.22.3.

When I check with the SDL's FAQ page ([http://www.libsdl.org/faq.php?action=listentries&category=3#25](http://www.libsdl.org/faq.php?action=listentries&category=3#25)), I see the following solution.
> SDL doesn't use the X11 video driver if it can't open the X display, and if no other drivers are available, it will report this error.
To fix this, set your display environment variable appropriately:
sh: DISPLAY=:0 ; export DISPLAY
csh: setenv DISPLAY :0
If you still have problems, try running xhost + localhost
Finally, if all those didn't work, and you built SDL from source, make sure that you have the X11 development libraries installed, otherwise you'll get a version of SDL that doesn't include X11 display support. After you install the X development libraries, you need to "make clean" and then rerun the configure and build process. I'm using BASH, so I try to type [COLOR="DarkRed"]DISPLAY=:0 ; export DISPLAY[/COLOR] in my terminal emulator. But, nothing happened. I've no idea about "[COLOR="DarkRed"]try running xhost + localhost[/COLOR]", so I ignored it. Finally I'm quite confused about SDL and X11. I've already installed [COLOR="DarkRed"]libsdl1.2deban-all[/COLOR] library in my system too. The description of that library is "This version of SDL is [COLOR="DarkRed"]compiled with X11[/COLOR], aalib, and ggi graphics drivers and oss, esound, alsa, arts, nas and pulseaudio sound drivers". So, I assumed that X11 is already there. But, the problem still exists.

Could anyone help me solve the problem, please? Thanks.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by molgren on 2008-10-29
I had the same problem when installing other packages, namely RUDL, SDL_mixer, and log4r. I reinstalled the latest SDL packages and the problem was fixed. Visit the following link, download the tarball sourcecode,  ./configure   then   make    then      sudo make install

Hopefully you will be all set after that. Let me know how it turns out!

---

### Post by imblack on 2009-08-31
My friend the easiest solution is to do following:

sudo apt-get remove libsdl1.2debain-all
sudo apt-ge install libsdl1.2debain-dev

Then go to SDL's official site, download the latest libsdl-dev tar and configure and compile and install.

Thats it :)

---

### Post by Akuma_s on 2009-11-21
> **molgren said:**
> I had the same problem when installing other packages, namely RUDL, SDL_mixer, and log4r. I reinstalled the latest SDL packages and the problem was fixed. Visit the following link, download the tarball sourcecode, ./configure then make then sudo make install

Hopefully you will be all set after that. Let me know how it turns out!

> **imblack said:**
> My friend the easiest solution is to do following:

sudo apt-get remove libsdl1.2debain-all
sudo apt-ge install libsdl1.2debain-dev

Then go to SDL's official site, download the latest libsdl-dev tar and configure and compile and install.

Thats it :)

It worked like a charm!!
All the 3D games now work soo smooth:D
Thanks all... :p

---

### Post by rajke88 on 2012-07-28
> My friend the easiest solution is to do following:

sudo apt-get remove libsdl1.2debain-all
sudo apt-ge install libsdl1.2debain-dev

Then go to SDL's official site, download the latest libsdl-dev tar and configure and compile and install.

Thats it 

I just want to confirm that this method works on Ubuntu 12.04 LTS X64! you saved me a system reinstall trouble. Just library names have changed on Ubuntu 12.04 LTS, people should just pay attention now on library names that are not the same.. On Ubuntu 12.04 they should use this commands

```
sudo apt-get remove libsdl1.2debian
```
```
sudo apt-get install libsdl1.2-dev
```
and then to download latest sdl from here [http://www.libsdl.org/](http://www.libsdl.org/), at this point of time it is sdl 1.2 so download it from here [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php). Extract it to Desktop using archeve manager.

CD to that folder from terminal. To do that open terminal. and type:
```
cd  /home/yourusername/Desktop/SDL-1.2.15
```
and then compile it 
```
./configure
```
wait it to finish configuring type following code hit enter
```
make
```
wait it finish compiling, type following code and hit enter
```
make install
```

Thats it your games will work :D this is tut for total nooobs i had spare time so i wanted to help others too. Hope it was helpful. Thanks imblack for posting his solution it was very helpful.

---

### Post by Perfect Storm on 2012-07-28
Old thread.


Closed.

---

