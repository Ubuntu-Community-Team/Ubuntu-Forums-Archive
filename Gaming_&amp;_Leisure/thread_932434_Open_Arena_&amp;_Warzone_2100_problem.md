---
title: "Open Arena &amp; Warzone 2100 problem"
date: 2008-09-28
forum: Gaming &amp; Leisure
---

### Post by DeathCrypt on 2008-09-28
Hi i've just started using Ubuntu again as I now have a decent computer. I asked my friends if they knew any good games for it and they said Open Arena and Warzone 2100 so I downloaded them from the add/remove thing on the applications bar and whenever I go on them my monitor says that it's out of range. I only have a monitor thats 1024 x 768 so is there a way to make it run at that?

---

### Post by greenkernel on 2008-10-10
The following error message pops up in my terminal emulator when I'm trying to compile (actually, I'm just trying to configure) the source file of warzone2100-2.1_beta5.

> configure: error: Package requirements (openal >= 0.0.8) were not met:

Package @requirements@ was not found in the pkg-config search path.
Perhaps you should add the directory containing `@requirements@.pc'
to the PKG_CONFIG_PATH environment variable
Package '@requirements@', required by 'OpenAL', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENAL_CFLAGS
and OPENAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I've already installed openal-0.0.8. But, it's still not okay. Please advise me what to do. Thanks.

Regards,
[COLOR="DarkGreen"]
greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-10
also its -dev package (needed for compiling).

---

### Post by greenkernel on 2008-10-10
> **Artificial Intelligence said:**
> also its -dev package (needed for compiling).
Thanks for your suggestion. I've downloaded [COLOR="DarkRed"]libopenal1_1.3.253-4ubuntu1_i386.deb[/COLOR] and [COLOR="DarkRed"]libopenal-dev_1.3.253-4ubuntu1_i386.deb[/COLOR] and already installed them. But, it's not okay yet. The error message is same as the previous one. As follows:-
> configure: error: Package requirements (openal >= 0.0.8) were not met:

Package @requirements@ was not found in the pkg-config search path.
Perhaps you should add the directory containing `@requirements@.pc'
to the PKG_CONFIG_PATH environment variable
Package '@requirements@', required by 'OpenAL', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENAL_CFLAGS
and OPENAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Please, somebody help me ...
Thanks in advance.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
hmm...strange, but you actully do not need to compile Warzone2100

You can get a .deb here; [http://www.playdeb.net/available_games.html](http://www.playdeb.net/available_games.html)

Or else try this compiling guide; [http://gaming.gwos.org/doku.php/guides:64bit:warzone_2100](http://gaming.gwos.org/doku.php/guides:64bit:warzone_2100)

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> hmm...strange, but you actully do not need to compile Warzone2100

You can get a .deb here; [http://www.playdeb.net/available_games.html](http://www.playdeb.net/available_games.html)

Or else try this compiling guide; [http://gaming.gwos.org/doku.php/guides:64bit:warzone_2100](http://gaming.gwos.org/doku.php/guides:64bit:warzone_2100)
Thanks you very much for your help, AI. I'm just a newbie for Linux in fact. Why I'm trying to compile it by myself is I just want to learn compiling so that I can deal with the worst scenarios (if a program is not available in pre-compiled package). Now, I'm facing another problem: SDL (Simple DirectMedia Layer). When I'm trying to play Battle for Wesnoth or Balazar there is an error message as follows:
> Battle for Wesnoth v1.4
Started on Sat Oct 11 08:18:32 2008

20081011 08:18:32 error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.
I probably did uninstall some important SDL libraries during my previous configuration. But, I don't know what exactly it is and I've no idea how to install SDL again. I can play Battle for Wesnoth two days ago. But, I can't play it now. Please help me. Thanks.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
Try search in synaptic package manager for libsdl

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> Try search in synaptic package manager for libsdl
When I run [COLOR="DarkRed"]*apt-cache search libsdl*[/COLOR] in my terminal emulator, I've the following result.
> [COLOR="DarkGreen"]libsdl-image1.2 - image loading library for Simple DirectMedia Layer 1.2[/COLOR]
[COLOR="DarkGreen"]libsdl-image1.2-dev - development files for SDL 1.2 image loading libray[/COLOR]
libsdl-pango-dev - text rendering with Pango in SDL applications (development)
libsdl-pango1 - text rendering with Pango in SDL applications (shared library)
[COLOR="DarkGreen"]libsdl-ttf2.0-0 - ttf library for Simple DirectMedia Layer with FreeType 2 support[/COLOR]
libsdl-ttf2.0-dev - development files for SDL ttf library (version 2.0)
[COLOR="DarkGreen"]libsdl1.2-dev - Simple DirectMedia Layer development files[/COLOR]
[COLOR="DarkGreen"]libsdl1.2debian - Simple DirectMedia Layer[/COLOR]
[COLOR="DarkGreen"]libsdl1.2debian-all - Simple DirectMedia Layer (with all available options)[/COLOR]
libsdl1.2debian-alsa - Simple DirectMedia Layer (with X11 and ALSA options)
libsdl1.2debian-esd - Simple DirectMedia Layer (with X11 and esound options)
libsdl1.2debian-oss - Simple DirectMedia Layer (with X11 and OSS options)
fische - Stand-alone sound visualisation for Linux
[COLOR="DarkGreen"]libsdl-console - console that can be added to any SDL application[/COLOR]
[COLOR="DarkGreen"]libsdl-console-dev - development files for libsdl-console[/COLOR]
libsdl-erlang - Erlang bindings to the Simple Direct Media Library
[COLOR="DarkGreen"]libsdl-gfx1.2-4 - drawing and graphical effects extension for SDL[/COLOR]
libsdl-gfx1.2-dev - development files for SDL_gfx
[COLOR="DarkGreen"]libsdl-net1.2 - network library for Simple DirectMedia Layer[/COLOR]
libsdl-net1.2-dev - Development files for SDL network library
libsdl-ocaml - OCaml bindings for SDL - runtime files
libsdl-ocaml-dev - OCaml bindings for SDL - development files
libsdl-perl - SDL bindings for the Perl language
libsdl-ruby1.8 - Ruby/SDL interface for Ruby
libsdl-sge - extension of graphic functions for the SDL multimedia library
libsdl-sge-dev - development files for libsdl-sge
libsdl-sound1.2 - Decoder of several sound file formats for SDL
libsdl-sound1.2-dev - Development files for SDL_sound
libsdl-stretch-0-2 - stretch functions for Simple DirectMedia Layer
libsdl-stretch-dev - development files for SDL_stretch library
libsdl1.2debian-arts - Simple DirectMedia Layer (with X11 and aRts options)
libsdl1.2debian-nas - Simple DirectMedia Layer (with X11 and NAS options)
libsdl1.2debian-pulseaudio - Simple DirectMedia Layer (with X11 and PulseAudio options)
lgeneral - A "Panzer General" - like game
[COLOR="DarkGreen"]libsdl-mixer1.2 - mixer library for Simple DirectMedia Layer 1.2[/COLOR]
libsdl-mixer1.2-dev - development files for SDL1.2 mixer library

The libraries in green colour are already installed. What should I do next? Should I install all of them? I can't play untill now. Thanks.

Regards,
[COLOR="DarkGreen"]
greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
Did you compile wesnoth as well?

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> Did you compile wesnoth as well?
No, I just installed Wesnoth from Add/Remove Applications which can be found in Applications menu on the upper panel.

---

### Post by Perfect Storm on 2008-10-11
Found the error at SDL homepage;

> SDL doesn't use the X11 video driver if it can't open the X display, and if no other drivers are available, it will report this error.
To fix this, set your display environment variable appropriately:
sh: DISPLAY=:0 ; export DISPLAY
csh: setenv DISPLAY :0
If you still have problems, try running xhost + localhost
Finally, if all those didn't work, and you built SDL from source, make sure that you have the X11 development libraries installed, otherwise you'll get a version of SDL that doesn't include X11 display support. After you install the X development libraries, you need to "make clean" and then rerun the configure and build process.

[http://www.libsdl.org/faq.php?action=listentries&category=3#25](http://www.libsdl.org/faq.php?action=listentries&category=3#25)

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> Found the error at SDL homepage;
> SDL doesn't use the X11 video driver if it can't open the X display, and if no other drivers are available, it will report this error.
To fix this, set your display environment variable appropriately:
sh: DISPLAY=:0 ; export DISPLAY
csh: setenv DISPLAY :0
If you still have problems, try running xhost + localhost
Finally, if all those didn't work, and you built SDL from source, make sure that you have the X11 development libraries installed, otherwise you'll get a version of SDL that doesn't include X11 display support. After you install the X development libraries, you need to "make clean" and then rerun the configure and build process.
[http://www.libsdl.org/faq.php?action=listentries&category=3#25](http://www.libsdl.org/faq.php?action=listentries&category=3#25)
Thanks, AI. But, I'm perhaps too stupid to solve my problem.
I'm using BASH, so I try to type [COLOR="DarkRed"]DISPLAY=:0 ; export DISPLAY[/COLOR] in my terminal emulator. But, nothing happened. I've no idea about "[COLOR="DarkRed"]try running xhost + localhost[/COLOR]", so I ignored it. Finally I'm quite confused about SDL and X11. As I mentioned above, I've already installed [COLOR="DarkRed"]libsdl1.2deban-all[/COLOR] library in my system. The description of that library is "This version of SDL is [COLOR="DarkRed"]compiled with X11[/COLOR], aalib, and ggi graphics
drivers and oss, esound, alsa, arts, nas and pulseaudio sound drivers". So, I assumed that X11 is already there. How do you think? I'm quite wired about SDL ..... By the way, I really appreciate your helpful posts.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
SDL is the Open Source answer to DirectX (simplified explaination), X is which controls DE/WM interface and hardware (simplified explaination).


How about your other games that uses SDL do they run? Also which video card do you have?

I havn't such error before (or heard) so I'm a bit lost in the matter.

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> SDL is the Open Source answer to DirectX (simplified explaination), X is which controls DE/WM interface and hardware (simplified explaination).


How about your other games that uses SDL do they run? Also which video card do you have?

I havn't such error before (or heard) so I'm a bit lost in the matter.
I've installed the following games that probably use SDL ('cause I'm not sure those programs are using SDL or not).

[COLOR="DarkRed"]Adonthell - Waste's Edge[/COLOR]
I installed it yesterday but, could not play due to SDL error. compiled myself.

[COLOR="DarkRed"]Balazar[/COLOR]
I installed it yesterday but, could not play due to SDL error. Installed by Synaptic Package Manager.

[COLOR="DarkRed"]Battle for Wesnoth[/COLOR]
I installed it a few months ago. I can play it until before yesterday. Installed by Synaptic Package Manager.

[COLOR="DarkRed"]Lincity NG[/COLOR]
I installed it yesterday but, could not play due to SDL error. Installed by Synaptic Package Manager.

[COLOR="DarkRed"]Metal Blob Solid[/COLOR]
I installed it a few days ago. I can play it until before yesterday. Installed by Synaptic Package Manager.

As you can see, none of the above programs can play now. Some programs (eg. Wesnoth and Metal Blob Solid) stopped working since yesterday due to SDL error.

I'm currently using NVIDIA GeForce 6200 TurboCache (PCI-E) graphics card. I've already installed restricted modules for that graphics card too.
My Linux kernel is 2.6.24-19-generic. GNOME version is 2.22.3.
Thanks.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
What changes did you made since the the error happened? Installed/removed anything? Didyou update/upgrade something?

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> What changes did you made since the the error happened? Installed/removed anything? Didyou update/upgrade something?
I did install and uninstall some games and libraries yesterday. The problem is I don't remember how many games and libraries I installed/uninstalled and what exactly they are. In addition, some libraries requested to uninstall other libraries during installation (for example, if I want to install [COLOR="DarkRed"]libsdl1.2debian-alsa[/COLOR], the package manager asked me to uninstall [COLOR="DarkRed"]libsdl1.2debian-all[/COLOR] first). So, I probably uninstalled some important libraries which are needed for SDL to function properly.

But, what I don't understand is the Wesnoth case: I can't play now even though I've already installed all of the dependencies for it. When I checked in Synaptic Package Manager, the dependencies for Wesnoth are as follows:
> libbost-iostreams1.34.1
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
zlib1g
wesnoth-all
wesnoth-data
I've already checked whether all of the above are already installed or not. All of them are already installed!! But, still can't play it. I don't know how to handle it. Not only Wesnoth, but also other games that use SDL. I can't play them now. I'm really wired ... (I still can play some games such as FreeCiv and Robots though).

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
Check synaptics history and install the removed libs.

---

### Post by greenkernel on 2008-10-11
> **Artificial Intelligence said:**
> Check synaptics history and install the removed libs.
I'm really sorry for giving you such trouble.

I've already installed back the libraries (totally 23 libs). But, it doesn't work still.

Thanks for your patient and help.

Regards,
[COLOR="DarkGreen"]
greenkernel[/COLOR]

---

### Post by Perfect Storm on 2008-10-11
Perhaps you should make a seperate thread in the general discussion forum about the issue regarding your SDL problem. I can't regrettably help you further as it's nothing I've experienced or heard of :-/

---

