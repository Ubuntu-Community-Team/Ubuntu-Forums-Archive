---
title: "warsow and loki install problems?"
date: 2005-11-22
forum: Gaming &amp; Leisure
---

### Post by ren wins on 2005-11-22
i've never tried to install a game onto linux (at least, one that wasnt available through yast or synaptic)
so i dont really know what's going on here

what i do know
is that i downloaded the warsow tar.gz and unpacked it
and when that did nothing, i downloaded the loki installer.run and ran it

now i have a shortcut to warsow in my applications menu, but when i try to run it, the screen goes black for a second, then returns back to the desktop with my mouse pointer locked in the upper right hand corner.

amd XP 2200+
512mb ram
nvidia fx 5700+

i'm pretty new at this, so if you need any more info, you might have to tell me where to find it :\

thanks

edit: i have a shortcut to warsow in my applications menu (applications > other > warsow)

---

### Post by Perfect Storm on 2005-11-22
tar.gz contains is properly something you need to compile or have dynamic or static structure to play. Need more input to solve that...


Please run Warsow in the terminal and post the output.

---

### Post by ren wins on 2005-11-22
i tried running warsow in the terminal

but it froze my mouse again, so i cant copy/paste it anywhere

hmm, actually... 
i'm on a different computer b/c of wireless problems (i've got a thread in desktop support)
so i could try to copy it manually


edit: is there a command to slow down the flood of text that pops up so i can read it?

---

### Post by ren wins on 2005-11-22
as a side note, according to gkrellm, i'm only using 4-6% of my CPU

are there any commands to list processes?

edit:
killall warsow returns >  warsow: no process killed 

i assume that means that warsow isnt running somewhere, and my mouse is misbehaving for other reasons (it's a wireless microsoft mouse, but it's got fresh batteries, and it's right next to it's reciever)

---

### Post by Perfect Storm on 2005-11-22
If you have a non-wireless mouse in the house, try it.

---

### Post by ren wins on 2005-11-22
oh, here's something interesting
at the very end of all that warsow loading buissiness

it says >  =======warsow initialized ======= 
unknown command "d1"
Recieved signal 11, exiting... 

(sorry i'm kinda flooding my own thread)

---

### Post by ren wins on 2005-11-22
double post

---

### Post by ren wins on 2005-11-22
i figured out i could scroll in terminal w/o a mouse
at the very begining of stuff, right after i typed warsow, the terminal said it >  added pk3 file ./basewsw/blablabla for 9 pk3 files (seems normal)

then it said >  using /home/laserwolf/.warsow/basewsw for writing
unknown command "snd_restart"
Unknown command "in_restart"
execing default.cfg
couldn't exec config.cfg
coundn't exec autoexec.cft
fs_usehomedir is write protected.
server running at 20 pps
consol initialized


----sound initialization -----
bla bla bla 
bla

starting SDL audio callback...
SDL audio initialized.
LoadLIbrary (libvorbisfile.so):(libvorbisfile.so: cannot open shared object file
: No such file or directory)
sound samping rate: 22050
-------------------

---- R_Init -----
a bunch of stuff about resolution my graphics card

GL_RENDERER: GeFroce FX 5700 Ultra/AGP/SSE/3DNOW!
GL_VERSION: 2.0.0 NVIDIA 76.67
GL_EXTENTIONS bla bla

mode:3, fullscreen
CDS: enabled
picmip: 0
texturemode: GL_LINEAR_MIPMAP_NEAREST
swap interval: disabled
compiled vertex array: enabled
multitexture: enabled
texture cube map: enabled
texture3D: enabled
texenv add: enabled
texenv combine: enabled
texenv dot3: enabled
NVtexenv combine4: enabled
texture edge clamp: enabled
anisotripic filtering: disabled
compressed textures: disabled
draw range elements: enabled
BGRA byte order: enabled
----finished R_Init------

initializing shaders
bla bla ther's  20 of 'em

-----------------
LoadLibrary (.basewse/ui_i386.so):((null))
===== warswo initialized ======
inknown command "d1"
recieved signal 11, exiting...



i'll go see if i can chase down a wired mouse... but i dont think that's the problem.... (i'm no profesional, i suppose)

edit: disabled smilies

---

### Post by ren wins on 2005-11-23
did i scare everyone off of my problem?
i'd copy/paste stuff but the internet on my machine is bust
and i cant seem to get much help with it in the desktop support forum

---

### Post by Perfect Storm on 2005-11-27
> LoadLIbrary (libvorbisfile.so):(libvorbisfile.so: cannot open shared object file
: No such file or directory)

see if this will work:

```

sudo apt-get install libvorbis0a libvorbisenc2 libvorbisfile3 

```

---

### Post by ShapeShifta on 2006-01-01
I have this problem as well....

I loaded it up and goes black for like 3 seconds then my mouse pointer gets stuck on the top left corner of the screen.

---

### Post by RobOrr on 2008-05-31
I have this problem as well. Will post terminal output shortly (if it's still not working), once update to warsow .42 is done.

I am using a microsoft wired optical mouse, so it's not likely to be the mouse itself getting confused.

---

### Post by DemoneyesKyo on 2010-01-19
I've had Loki installed for awhile now and it played fine, but after awhile in bugs in the game got annoying, clicking on summons would make you run at them, summons blocking you in with enemies, ect. So i got the newst patch, 1.8.3 i believe, and when i go to load and play the game again, it gives me a "Missing PROTECT.DLL" error. i know downloading random .dll's is not a good idea at all, so could anyone help me out? im on Windows 7, thanks in advance.

---

### Post by Perfect Storm on 2010-01-19
> **DemoneyesKyo said:**
> I've had Loki installed for awhile now and it played fine, but after awhile in bugs in the game got annoying, clicking on summons would make you run at them, summons blocking you in with enemies, ect. So i got the newst patch, 1.8.3 i believe, and when i go to load and play the game again, it gives me a "Missing PROTECT.DLL" error. i know downloading random .dll's is not a good idea at all, so could anyone help me out? im on Windows 7, thanks in advance.

This is an Ubuntu Linux OS forum.

[http://www.ubuntu.com/](http://www.ubuntu.com/)

You should try a Windows forum for your problem.
Thread closed.

---

