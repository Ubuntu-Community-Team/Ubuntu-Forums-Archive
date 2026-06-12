---
title: "Alien Arena"
date: 2007-10-15
forum: Game Specific Discussions
---

### Post by Perfect Storm on 2007-10-15
**UGA's News Discussion of Alien Arena.**

Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by compiledkernel on 2007-10-15
I happen to love this game in all its quake 2 goodness.

---

### Post by Raj_Dharwad on 2007-10-18
Dear Fellow Gamers & Ubuntu Makers,

I just downloaded Alien Arena 2007 from there official website, i then unzipped it to my "/home/lingaraj/Desktop/Documents/alienarena2007", to begin with i am technical support expert & eat, live & breath computers & windows for a living, but Ubuntu is my first venture, i just love it, i dont have any knowledge abt programming although i can easily follow instructions type them in the terminal, the read me file says 
------xxxxx-----
(Linux)


Simply unzip the archive in your /usr/local/games folder or wherever you wish to place the game.



Type ./crx to run the game, or ./crded to start a dedicated server or use the shortcuts installed in the menu.



Source files are included, so you may compile the binaries yourself if necessary.  Please visit the forum if you have any questions regarding this.
"
-----xxxxx-------
 my question is where do i type ./crx to run the game, or ./crded & what do i type before or after that in the terminal if i am supposed to type it in terminal, The only other icons i have are .png & .ico files which are of no use. I am also trying to search at there forums until then... any help wud be much appreciated...

with regards,

Raj Dharwad
(First timer at Ubuntu)

---

### Post by Perfect Storm on 2007-10-18
There's a guide here: [http://gaming.gwos.org/doku.php/guides:alienarena](http://gaming.gwos.org/doku.php/guides:alienarena)

---

### Post by Raj_Dharwad on 2007-10-18
Hello A.I,

thanks for that link, but the instructions are not quite understandable nor can i follow them properly as they dont provide instructions step by step, for example:- 
----XXXX---
cd ~/Desktop
mkdir ~/.Games
unzip alienarena2007-20071011-linux.zip -d ~/.Games
----XXXX----

am i supposed to type this in one straight line or these are 3 separate commands? i know i sound stupid but when i type cd ~/Desktop i get mssg :- bash: cd: /home/lingaraj/desktop: No such file or directory. 

could u possibly help me a little bit more, or can download this from synaptics package manager? will it automatically install it for it if i download it from there?

regards,

Raj

---

### Post by Perfect Storm on 2007-10-18
I don't think AA is in the synaptic, well not the latest and great anyway.

They are seprated

cd ~/Desktop [enter]
mkdir ~/.Games [enter]
etc.

---

### Post by Raj_Dharwad on 2007-10-18
Hi A.I,

actually AA is available in synaptic but as u mentioned old version is available, i also was trying to install the latest Nvidia drivers for my Geforce FX 5200 128MB card, but when i run it terminal it asks me to run as root, how to run it as a root, this sounds similar to run as administrator in windows... i just dont know the rite command for this.. root login... I also started downloading the game thru synaptics since i have a slow connection i will have to wait for abt 6hrs :( for it to complete,  The only mssg i get is bash: cd: /home/lingaraj/desktop: No such file or directory, after the first step, Alienarena2007-20071011-linux.zip is just sitting there, is der a linux installer just like windows installer?

regards,

Raj

---

### Post by Shay Stephens on 2007-10-21
I have a question about making a launcher.  I have AlienArena in my home folder, but when I try to create a launcher and use the command:
/home/me/alienarena2007/AlienArena

but that never works.  I have to navigate to the folder and launch the program directly or by cd'ing into the folder in the terminal and running ./AlienArena,  What am I missing?

---

### Post by Perfect Storm on 2007-10-21
Raj_Dharwad:
Try **cd Desktop** and see if it works.
If it doesn't start a new thread in UGA forum.

Shay Stephens:
Please check our [http://gaming.gwos.org/doku.php/guides:alienarena](http://gaming.gwos.org/doku.php/guides:alienarena) -> guide to se how it's done (under launcher). You need to make a script.

---

### Post by Raj_Dharwad on 2007-10-25
Hi A. I,

Actually i installed it thru SPM and everything went fine, i am able to play the game fine. Until i learn more abt programming & linux commands, i am very much interested in learning programing & want to become a good programmer & contribute to linux world. I have started to learn python, i know it is the wrong place to ask this question, but you can send me an email rather than replying to this post. How did u start your programming lessons?

Regards,

Raj

---

### Post by rykel on 2008-01-12
Hi all,

I have problems running Alien Arena 6.10 on Ubuntu Gutsy... the sound is choppy. *Anyone help?*

btw, to run the game, simply unzip the file somewhere, and double-click on **crx** and it should run. If not, check if crx is executable.

---

### Post by asmugone on 2008-02-07
I installed through synaptec and everything went fine. Running a amd 2 gigahrtz proccessor with ubuntu gutsy gibbon and a ati raddeon 9500. 
Im currently running the newest restricted drivers.

When I try to run it on console I get this.
smug@drunkenmonkey:~$ alien-arena
using /home/smug/.alien-arena/data1/ for writing
using /home/smug/.alien-arena/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  33
  Current serial number in output stream:  39


Contents of my xorg, *people almost always want this*

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

any help would be much appreciated!!!

---

### Post by Perfect Storm on 2008-02-07
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"

That most be the smallest screen 1x1 :guitar:
"832x624"???


Have you tried the other ATI driver?

---

### Post by p_breakfast on 2008-07-13
I installed alien arena 2007 using synaptic and everything is working perfectly except for the fact that my hosted games can't be reached online.

Even as a dedicated server games don't appear online.
I already redirected ports 27900 to 27950 on my modem but still no result.

Are there other things that I can try?

---

### Post by spectrum on 2009-02-22
I got a similar problem that asmugone, the game starts and shows me the menu, but whe clicking single player and "Start Game", it crashes:

Console message:

ldig@argentina:~$ alien-arena 
using /home/ldig/.alien-arena/data1/ for writing
using /home/ldig/.alien-arena/arena/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: VIA Technology
GL_RENDERER: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
GL_VERSION: 1.2 Mesa 7.0.3-rc2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
...GL_ARB_fragment_program not found
------------------------------------
======== CRX Initialized ========

------- Loading game.so -------
LoadLibrary (./arena/game.so)
==== InitGame ====
Master server at 69.143.100.63:27900
Sending a ping.
------- Server Initialization -------
0 entities inhibited
0 teams with 0 entities
-------------------------------------
Player connected
Sending heartbeat to 69.143.100.63:27900
0.0.0.0:0: client_connect
game will be changed for next game.




Atlantis
Ping acknowledge from 69.143.100.63:27900
Received signal 11, exiting...
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3600002
  Serial number of failed request:  511
  Current serial number in output stream:  513

In my case, just plain intel X3100 graphics

---

### Post by paul kinell on 2009-12-21
This worked for me, save it to your /home/user/.scripts directory and setup a launcher to call it. There should be a aa.png icon to decorate the menu entry in /home/user/.alienarena, that's assuming you've installed aa to that directory.

#!/bin/bash
# Start Alien Arena
cd ~/.alienarena export DISPLAY=:0 && ./crx

---

### Post by jakejw93 on 2010-06-14
[http://www.youtube.com/watch?v=8m8kwzUpX3A](http://www.youtube.com/watch?v=8m8kwzUpX3A)

Gameplay video of this amazing FPS in Linux!

Fantastic game overall and is recommended to anyone who enjoys first person shooters!

---

### Post by Annigma on 2010-08-19
This is a fun game. No deep thought required, but obvious skill involved if you actually want to do well.
I tried it the other night for the first time. Surprisingly, I did rather well at first, but I must've got cocky or something since I did rather badly in the last couple of games I played.. :lolflag:

I just went to start it up in Ubuntu (having got it from Software Centre last night), and it does nothing, so I'm off to win7 to die. I'll try and get it working 'here' when I'm more sober :D

---

