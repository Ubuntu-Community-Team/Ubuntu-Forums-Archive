---
title: "Cant find opengl when runing configure"
date: 2005-10-05
forum: Gaming &amp; Leisure
---

### Post by drgreborn on 2005-10-05
Trying to install the game SCOURGE. When I try to run ./configure it gives me this errors
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking whether make sets ${MAKE}... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for working const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for strdup... yes
checking for finite... yes
checking for isnan... yes
checking for _finite... no
checking for _isnan... no
checking for ieeefp.h... no
checking for /proc/self/maps... yes
checking whether everything is installed to the same prefix... yes
checking whether binary relocation support should be enabled... yes
checking for pthread_getspecific in -lpthread... yes
checking whether binary relocation should use threads... yes
checking for Win32 platform... no
checking for Mac OSX platform... no
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -ldl... yes
checking for main in -lm... yes
checking for deflate in -lz... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.0.1... yes
checking for SDL_JoystickOpen... no
*** This version of SDL doesn't have joystick support.
*** Configuring without joystick support.
checking for Mix_OpenAudio in -lSDL_mixer... no
*** SDL_mixer not found.  Configuring without audio support.
checking for SDLNet_Init in -lSDL_net... no
*** SDL_net not found.  Configuring without network support.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
*** Hmm, you don't seem to have OpenGL libraries installed in the standard
*** location (/usr/lib).  I'll check in /usr/X11R6/lib, since
*** many distributions (incorrectly) put OpenGL libs there.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library
Anyone has any ideas why this is happening? And how to fix this? Thank you.

---

### Post by Perfect Storm on 2005-10-05
sudo apt-get install libgl1-mesa-dev
sudo apt-get install libopenal-dev
sudo apt-get install libsdl-mixer1.2-dev
sudo apt-get install libsdl-net1.2-dev


That's what I can see you're missing

---

### Post by drgreborn on 2005-10-05
ok thanks mate I'll try that. Just wondering is this got anything to do with me using a NVIDIA driver? Since it creates another set of opengl libs?
No dice mate. My repositories don't seem to have them. Are they in a specific repository source?

---

### Post by Perfect Storm on 2005-10-05
Not at all. Nvidia Driver and OpenAL is completly diffrent. The nvidia driver is to your hardware and the openal is to get your nvidia or Ati or whatever to run Software...umm well it's a bit difficult for me to explain since english is not my native language, but I think the explaination will cover it :)

---

### Post by drgreborn on 2005-10-05
sudo apt-get install libgl1-mesa-dev  <-- I cant seem to install this. I have sudo apt-get install libglu1-mesa-dev though.

---

### Post by drgreborn on 2005-10-05
[QUOTE=Artificial Intelligence]Not at all. Nvidia Driver and OpenAL is completly diffrent. The nvidia driver is to your hardware and the openal is to get your nvidia or Ati or whatever to run Software...umm well it's a bit difficult for me to explain since english is not my native language, but I think the explaination will cover it :)[/QUOTE]
Ah ok I get it. Thanks alot mate you've be a super help.

---

### Post by Perfect Storm on 2005-10-05
Did you enable the stuff in the rept.? [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
cut out the:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

They don't exist anymore.

---

### Post by drgreborn on 2005-10-05
Yup I unhashed the other repositories. But still cant seem to find the libgl1

---

### Post by Perfect Storm on 2005-10-05
I'm on breezy therefore it perhaps got another name. Try open synaptic package manager and make a search libgl

---

### Post by Perfect Storm on 2005-10-05
umm...perhaps better to search for **mesa** instead

---

### Post by drgreborn on 2005-10-05
I was able to insatll all teh other except the first one. Hmmm this is weird.

---

### Post by drgreborn on 2005-10-05
When I try to just do a apt-get install libgl1 I get teh following
Package libgl1 is a virtual package provided by:
  xlibmesa-gl 6.8.2-10.1
  mesag3-glide2 5.0.0-5.1
  mesag3+ggi 5.0.0-5.1
  mesag3 5.0.0-5.1
You should explicitly select one to install.

---

### Post by Perfect Storm on 2005-10-05
but you should install **sudo apt-get install libgl1-mesa-dev** not libgl1 alone or am misunderstanding something?

---

### Post by drgreborn on 2005-10-05
The problem I am facing is that when I do " apt-get install libgl1-mesa-dev", it returns me an error stating that it could not be found.
If it is not to much to ask from you, could you tell me which repositories do you have listed in your source.list? So sorry bout this.

---

### Post by Perfect Storm on 2005-10-05
It's no problem at all, don't worry :)

I love to give my repo. but if you are on hoary my breezy repo won't help you.

Lets start with the beginning again :)
System ---> Adminstration ---> Synaptic package manager
then press the search button and write mesa
scroll down to you find something that looks similiar to **libgl1-mesa-dev** Perhaps it's without the 1 in it or something :) 
Right click it and mark it install then press the apply button.

---

### Post by drgreborn on 2005-10-05
yup its libglu1-mesa-dev and it is installed. So i'm rather perplexed as to why I can't build the file. ^^;

---

### Post by Perfect Storm on 2005-10-05
Try to ./configure it again and see what it says....

I've to go now, but I'll be back about 5 hours

---

### Post by drgreborn on 2005-10-06
Checking where the libglu1-mesa-dev is located returned this
/usr/lib
/usr/lib/libGLU.a
/usr/include
/usr/include/GL
/usr/include/GL/glu.h
/usr/share
/usr/share/doc
/usr/share/doc/libglu1-mesa-dev
/usr/share/doc/libglu1-mesa-dev/copyright
/usr/share/doc/libglu1-mesa-dev/README.Debian
/usr/share/doc/libglu1-mesa-dev/changelog.gz
/usr/share/doc/libglu1-mesa-dev/changelog.Debian.gz
/usr/lib/libGLU.so

Is this correct? Am I supposed to add something into bash.bashrc or something or into the ldconfig or something? Thanks

---

### Post by Perfect Storm on 2005-10-06
That seems right enough.
But did you tried to compile the game now?
What's the output of the terminal now?

---

### Post by drgreborn on 2005-10-06
Same thing. mate. maybe I've forgotten something. Gonna check to see that I have everything needed.

---

### Post by drgreborn on 2005-10-06
Ok could install it using the .package version of installer. Now th eproblem is that it is ultra lag ad I cant see my mouse pointer. ^^; Lol one problem after another. The game by the way is S.C.O.U.R.G.E the rouge clone.

---

### Post by Perfect Storm on 2005-10-07
Could be a S.C.O.U.R.G.E problem . I don't have that game so I can't help you there :/

---

