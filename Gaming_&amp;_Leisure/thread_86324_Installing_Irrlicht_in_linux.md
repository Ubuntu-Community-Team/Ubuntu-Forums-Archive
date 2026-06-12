---
title: "Installing Irrlicht in linux"
date: 2005-11-04
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2005-11-04
Talk about "not enough info":

> HOW TO COMPILE THE ENGINE WITH LINUX



If you wish to compile the engine in linux yourself, unzip the source source.zip

file in the \source directory. Run a 'make' in the now existing new subfolder 'Irrlicht'.

After this, you should be able to make all example applications in \examples.

Then just start an X Server and run them, from the directory where they are.



If you get a compiling/linking problem like 



 undefined reference to `glXGetProcAddress'

 

Then there are several solutions: 

A) This disables the use of OpenGL extensions:

  Open the file IrrCompileConfig.h, comment out _IRR_LINUX_OPENGL_USE_EXTENSIONS_,

  and recompile Irrlicht using 

  make clean

  make

B) Replace all opccurrences of 'glXGetProcAddress' with 'glXGetProcAddressARB' and run a

   make

   This will solve the issue but keep the OpenGL extension enabled.


Yay!!! Now somebody want to tell me what that means? How does one "make"?

(for those of you who are not tollerant of newbs coming in with insane questions like this, and are of the opinion that we ought to do more than ask questions, remember that if developers were more thorough, and would put exact instructions with their software, we'd all get along better, and more people would be using Linux. This is the number one problem with Linux as I see it. Programmers and developers write stuff like they are talking to each other, then chastise anyone who asks to be taught. Please, if you are one of these people, take time to reflect on your position, then come help us migrate away from the dark side...)

(think about what if programmers did as sloppy a job writing code as they do writing instructions...)


By the way, what I'm looking for is an editor with which I can create models for UT.

---

### Post by Harleen on 2005-11-05
[QUOTE=BLTicklemonster]Yay!!! Now somebody want to tell me what that means? How does one "make"?[/QUOTE]

By tying "make" on the command prompt. Quite easy, isnt it?;)

---

### Post by BLTicklemonster on 2005-11-05
Had it worked like that, I'd not have asked :)

---

### Post by Harleen on 2005-11-05
Without a more precise description, what has failed, you probably won't get more help than that. ;-)

Just out of curiosity: Wherefore do you want to compile Irrlicht? It's just a 3d-engine and no complete application, as far as I know.

---

### Post by BLTicklemonster on 2005-11-05
Okay, I've got a folder full of stuff that won't do anything when I double click on them. 

How much more precise I can get than that, I don't know.

from the terminal, do I go cd /home/bill/irrlicht* 

and then ... or what?

---

### Post by Harleen on 2005-11-05
[QUOTE=BLTicklemonster]
from the terminal, do I go cd /home/bill/irrlicht* 

and then ... or what?[/QUOTE]

Just a blind guess from the compilation tips you posted above:

```

cd source
make

```

or something like that...
There has to be one folder, that contains a file named "Makefile". Running "make" in that folder should do the trick.

---

### Post by madjo on 2005-11-05
Those instructions are for developers, because Irrlicht isn't a complete application (as has been mentioned here already), so it might be my guess that they know how to compile things...

and yeah, that is done from the command line... it is quite hard to do 'make' from within a GUI.

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=madjo]Those instructions are for developers, because Irrlicht isn't a complete application (as has been mentioned here already), so it might be my guess that they know how to compile things...

and yeah, that is done from the command line... it is quite hard to do 'make' from within a GUI.[/QUOTE]

lol ya think?

I'll give it a shot later. Right now I'm hung up trying to do vmware. Thanks.

---

### Post by mbaszczewski on 2006-09-09
```
make
g++ -Wno-reorder -I../../include -Izlib -Ijpeglib -Ilibpng -DIRRLICHT_EXPORTS=1  -c -o CIrrDeviceLinux.o CIrrDeviceLinux.cpp
In file included from CIrrDeviceLinux.cpp:5:
CIrrDeviceLinux.h:25:38: error: X11/extensions/xf86vmode.h: No such file or directory
CIrrDeviceLinux.h:223: error: &#8216;XF86VidModeModeInfo&#8217; does not name a type
CIrrDeviceLinux.cpp: In destructor &#8216;virtual irr::CIrrDeviceLinux::~CIrrDeviceLinux()&#8217;:
CIrrDeviceLinux.cpp:120: error: &#8216;oldVideoMode&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:120: error: &#8216;XF86VidModeSwitchToMode&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:121: error: &#8216;XF86VidModeSetViewPort&#8217; was not declared in this scope
CIrrDeviceLinux.cpp: In member function &#8216;bool irr::CIrrDeviceLinux::createWindow(const irr::core::dimension2d<int>&, irr::u32)&#8217;:
CIrrDeviceLinux.cpp:170: error: &#8216;XF86VidModeQueryExtension&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:180: error: &#8216;XF86VidModeModeInfo&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:180: error: &#8216;modes&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:187: error: &#8216;XF86VidModeGetAllModeLines&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:191: error: &#8216;oldVideoMode&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:336: error: &#8216;XF86VidModeSwitchToMode&#8217; was not declared in this scope
CIrrDeviceLinux.cpp:337: error: &#8216;XF86VidModeSetViewPort&#8217; was not declared in this scope
make: *** [CIrrDeviceLinux.o] Error 1
```

What's wrong?
I probably haven't file: X11/extensions/xf86vmode.h but how i can setup this? ](*,) 
I need some package?
Thank's for help :-k

PS
I use Code::Blocks

---

### Post by namor on 2006-11-12
I had the same problem, but solved it.
Simply install the libxxf86vm-dev package and logically it's dependencies. :)

---

### Post by idlewire on 2008-01-12
[http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux]("http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux")

The irrlicht wiki has been ridiculously helpful to me.  It can help you set up code::blocks if you want to use it.

---

### Post by ebharv on 2008-03-22
> **idlewire said:**
> [http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux]("http://www.irrlicht3d.org/wiki/index.php?n=Main.CompilingOnLinux")

The irrlicht wiki has been ridiculously helpful to me.  It can help you set up code::blocks if you want to use it.

Ok what version of Code::Blocks do you have and how did you install it. I've used it in windows, great ide, but the only version I've found for linux is wwaayy older than the windows version.


Should've done this edit earlier, code::blocks installs from the default repositories now. Not the newest version but it's fairly recent.

---

