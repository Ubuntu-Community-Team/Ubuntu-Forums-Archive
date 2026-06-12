---
title: "Urban Terror"
date: 2007-12-28
forum: Game Specific Discussions
---

### Post by compiledkernel on 2007-12-28
Discuss here.

---

### Post by Rhubarb on 2007-12-28
Urban Terror website: [http://www.urbanterror.net/](http://www.urbanterror.net/)

I used to play UrT quite a lot when I used windows (back in the old days).  Now I haven't really bothered with UrT because:
[LIST]
[*]Quake3 based games are terrible to play if you lag by >100ms
[*]Battleye created huge problems for me in 64bit and 32bit ubuntu (thankfully they've ripped out battleye now).
[*]Even running UrT in wine created some minor problems for me (any button I pressed during the game causes the game to think I pressed that button twice).
[*]I've found that Assault Cube fits my needs perfectly [http://assault.cubers.net/](http://assault.cubers.net/)
[/LIST]

Edit:  I'll try out the new version of UrT now =D

---

### Post by Wumpus55 on 2007-12-30
I just tried to load UrT 4.1 but my graphics are all screwed up.  I think it is my ATI driver.  Unfortunately, it is a laptop and I can't get an NVIDIA card for it.   

Have you seen any configuration stuff for 4.1 on ubuntu?

---

### Post by Rhubarb on 2008-01-12
Ok, UrT 4.1 is just brilliant!
No more crashing, no more battleye, it works perfectly in 64 and 32bit ubuntu here.
The only thing I hold against UrT (which is really to do with ioquake3) is that it doesn't play well if you have >100ms lag.  I'm used to assault cube + sauerbraten internet play (it works fine with >300ms lag).

I'll be playing UrT much more often now, online and hopefully at LAN games.

---

### Post by userid on 2008-01-12
Excellent CS-type shooter, I've run both client and server on ubuntu 7.04 and 7.10 without any problems (ATI 9700, nvidia geforce 8400gs).

There's a very good install script elsewhere on this forum, although 4.10 just wants to be unzipped and run

---

### Post by Istonian on 2008-02-07
I downloaded it, but how do I get it to run. I even made it executable, but it won't start.

---

### Post by littletinman on 2008-02-16
I donwloaded it to and i unziped the folder in my home folder. Then what? is this suposed to run with quake 3?

---

### Post by oldjimsteele on 2008-03-13
[deleted]
Got it working, never mind.

---

### Post by MattThLinuxNewb on 2008-06-15
Hi,
I downloaded the urban terror zip (UrbanTerror_41_FULL.zip) for linux/mac, extracted it to my /usr/local/games directory and made ioUrbanTerror.i386 executable, but when I try to run it nothing happens. Here's the console output:

```

matt@matt-desktop:/usr/local/games/UrbanTerror$ ./ioUrbanTerror.i386 
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
99 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8600 GT/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
^3WARNING: no shader files found
Received signal 11, exiting...
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
matt@matt-desktop:/usr/local/games/UrbanTerror$

```

Couldn't find info on any forums about this. Any help would be great, thanks.

---

### Post by MattThLinuxNewb on 2008-06-15
Fixed: my download was corrupted... fixed it by "verifying local data" in my bittorrent client.

---

### Post by hongleong on 2008-06-22
Am using Hardy 8.04. Downloaded UrT 4.1.

The graphics is ok but there is no sound. The UrT log says:

> ------ Initializing Sound ------
Initializing SDL audio driver...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
--------------------------------

Amarok and VLC are all churning out sound alright.

Any idea what could be the cause? Thanks...

=============================
Post updated 20080623 12.18am
=============================

I found a workaround solution from twright in another thread [http://ubuntuforums.org/showthread.php?t=815414&highlight=urban+terror]("http://ubuntuforums.org/showthread.php?t=815414&highlight=urban+terror")

From the menu, goto System > Preferences > Sound. For 'Sound Events::Sound playback', change it from 'Autodetect' to 'ALSA - Advanced Linux Sound Architecture'. Restart the computer.

This works for me. :)

---

### Post by SammyBoy247 on 2008-06-27
Just thought I'd say I've been playing for about 3 months now on a x64 Hardy Ubuntu and it worked straight out of the box and I JUST CAN'T STOP PLAYING (and I really should be doing much more important things)

Shoot you later.

---

### Post by von Stalhein on 2008-07-11
Downloaded it and installed.
It worked fine for about 2 mins (I checked I could start it) so I then tried to tweak the graphics etc.

Anyway, I lost mouse and general functionality.

I've deleted the original install. There have been several reboots of the machine since then (dual boot and about a week of normal use). 

After reinstalling, I've made the ioUrbanTerror.i386 file executable.

The game starts, but I can't change any of the setup options, and I still have no mouse. 

It feels like there's some residual setup stuff buggering the install - is there some sort of purge to make sure??

Any help appreciated, I'd really like to get this up & going.:(

---

### Post by spencerhc on 2008-07-11
There should be no problem, all you have to do is unzip it

I have been playing this for about 3 months and its one of the most addicting games ever. 

I also have a clan that I founded:

[http://www.xterminatorclan.co.nr]("http://www.xterminatorclan.co.nr")

---

### Post by crhylove on 2008-08-03
I'm having the EXACT same problem.  The game opens, sound, gfx are all alright (though somewhere in between fullscreen and windowed), and there is no mouse.  Any thoughts are appreciated.  x64 Hardy.

---

### Post by Paulo Wageck on 2008-11-30
I have played UT for a few days now.

Last weekend I played with my cousing on a server from my home. 

We have managed to play on same teams from my local network/isp on a nearby server on the internet. It was really fun.

Now I am at his house with our computers, but it seens that we can't do this at his house. We can play in DIFFERENT servers simultaneously but not on the SAME one like we did from my house...

I think it's a router/modem/isp glitch... 

I have placed one computer on the DMZ and the other on port forwarding... disabled automatic port forwarding on the adsl modem and the router.... but everytime we trie to connect on the same server one gets disconected....  any clues??? I have tried everything I know... and I am starting to think its a problem with the modem/router..... 

I have a DSL-500B modem (D-Link) and a Linksys wrt54g router... 

Any idea/help is apreciated.

Thanks!

---

### Post by Paulo Wageck on 2008-11-30
its simple   on one of the PC  you need to change your   net_port too 2961

so while the game is launch drop down the console by press the  ~  key that is below ESC and type this.


Code:

 
   
   /seta net_port "2961" 



The reason this occor is that you both use the same medium to connect to the internet so both your machines are giving the same External IP address so the server cannot differ the 2 connection and it drops one.   setting one to use a different ports allows the server to recognise two different connections being made

---

### Post by dynamethod on 2008-12-08
oh man this game OWNS!!!, dl the other night, works really really well on my 8.10 machine =), totally addictive

my in game name is SPOON_DOGS_FTW <- add me if you want

---

### Post by michaelzap on 2008-12-08
To those of you who lose your mouse after launching UT: Make sure that you turn off Compiz before running it. I use Alt+F2 to run [COLOR="Red"]metacity --replace[/COLOR] before launching UT and [COLOR="Red"]compiz --replace[/COLOR] after I'm done. Works like a charm.

---

### Post by Bramkaandorp on 2009-02-01
Just a little bump.

I currently have Ultimate Edition 2.0 Gamers installed, which has Urban terror pre-installed.

But is Urban Terror In the ubuntu repositories, or is that exclusively the case in Ultimate Edition?

Cheers,

Bram

---

### Post by typek_pb on 2009-02-08
hi guys, 

I'm using UT4.1 from getdeb repository on Intrepid.
It crashes too frequently during gameplay.

I tried it under Gnome (official one packages) with esuond used instead of pulseaudio, and desktop effects off. Tried also KDE (4.2 from kubuntu-experimental repo) desktop effects off. Didn't help at all.

Interesting is that there are less freezes under KDE where I need to do reset (Ctrl+Alt+Backspace usually helps), mostly just app crashes are there.

Example crash case:
```

ioQ3 1.35urt linux-i386 Aug 10 2008
----- FS_Startup -----             
Going through search path...       

----------------------
8313 files in pk3 files
execing default.cfg    
execing q3config.cfg   
execing autoexec.cfg   
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.         
----- Initializing Renderer ---- 
-------------------------------  
QKEY found.                      
----- Client Initialization Complete -----
----- R_Init -----                        
...loading libGL.so.1:                    
Calling SDL_Init(SDL_INIT_VIDEO)...       
SDL_Init(SDL_INIT_VIDEO) passed.          
Initializing OpenGL display               
...setting mode 4: 800 600                
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!         
Initializing OpenGL extensions                      
...ignoring GL_S3_s3tc                              
...ignoring GL_EXT_texture_env_add                  
...using GL_ARB_multitexture                        
...using GL_EXT_compiled_vertex_array               
...ignoring GL_EXT_texture_filter_anisotropic       

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                                                                                                                                                                                                                    
GL_MAX_ACTIVE_TEXTURES_ARB: 2                                                                                                                                                                                                                
                                                                                                                                                                                                                                             
PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)                                                                                                                                                                                        
MODE: 4, 800 x 600 fullscreen hz:N/A                                                                                                                                                                                                         
GAMMA: hardware w/ 0 overbright bits                                                                                                                                                                                                         
CPU:                                                                                                                                                                                                                                         
rendering primitives: single glDrawElements                                                                                                                                                                                                  
texturemode: GL_LINEAR_MIPMAP_NEAREST                                                                                                                                                                                                        
picmip: 1                                                                                                                                                                                                                                    
texture bits: 32                                                                                                                                                                                                                             
multitexture: enabled                                                                                                                                                                                                                        
compiled vertex arrays: enabled                                                                                                                                                                                                              
texenv add: disabled                                                                                                                                                                                                                         
compressed textures: disabled                                                                                                                                                                                                                
Initializing Shaders                                                                                                                                                                                                                         
----- finished R_Init -----                                                                                                                                                                                                                  
------ Initializing Sound ------                                                                                                                                                                                                             
Initializing SDL audio driver...                                                                                                                                                                                                             
SDL audio driver is "alsa".                                                                                                                                                                                                                  
SDL_AudioSpec:                                                                                                                                                                                                                               
  Format:   AUDIO_S16LSB                                                                                                                                                                                                                     
  Freq:     22050                                                                                                                                                                                                                            
  Samples:  470                                                                                                                                                                                                                              
  Channels: 2                                                                                                                                                                                                                                
Starting SDL audio callback...                                                                                                                                                                                                               
SDL audio initialized.                                                                                                                                                                                                                       
----- Sound Info -----                                                                                                                                                                                                                       
    1 stereo                                                                                                                                                                                                                                 
16384 samples                                                                                                                                                                                                                                
   16 samplebits                                                                                                                                                                                                                             
    1 submission_chunk                                                                                                                                                                                                                       
22050 speed                                                                                                                                                                                                                                  
0xa382060 dma buffer                                                                                                                                                                                                                         
No background file.                                                                                                                                                                                                                          
----------------------                                                                                                                                                                                                                       
Sound initialization successful.                                                                                                                                                                                                             
--------------------------------                                                                                                                                                                                                             
Sound memory manager started                                                                                                                                                                                                                 
Loading vm file vm/ui.qvm...                                                                                                                                                                                                                 
VM file ui compiled to 737597 bytes of code                                                                                                                                                                                                  
ui loaded in 33931488 bytes on the hunk                                                                                                                                                                                                      
UI menu load time = 563 milli seconds                                                                                                                                                                                                        
UI menu load time = 392 milli seconds                                                                                                                                                                                                        
16 bots parsed                                                                                                                                                                                                                               
13 crosshairs parsed                                                                                                                                                                                                                         
--- Common Initialization Complete ---                                                                                                                                                                                                       
Opening IP socket: localhost:27960                                                                                                                                                                                                           
Hostname: pb-desktop                                                                                                                                                                                                                         
IP: 127.0.1.1                                                                                                                                                                                                                                
Started tty console (use +set ttycon 0 to disable)                                                                                                                                                                                           
72.26.193.226:27960 resolved to 72.26.193.226:27960                                                                                                                                                                                          
----- FS_Startup -----                                                                                                                                                                                                                       
Going through search path...                                                                                                                                                                                                                 

handle 1: music/mainmenu.wav
----------------------      
16626 files in pk3 files    
RE_Shutdown( 0 )            
Hunk_Clear: reset the hunk ok
----- R_Init -----           

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_NEAREST                
picmip: 1                                            
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: disabled                                 
compressed textures: disabled                        
Initializing Shaders                                 
----- finished R_Init -----                          
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 494 milli seconds                
UI menu load time = 373 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
Loading vm file vm/cgame.qvm...                      
VM file cgame compiled to 1617707 bytes of code      
cgame loaded in 34383680 bytes on the hunk           
stitched 0 LoD cracks                                
...loaded 7436 faces, 159 meshes, 222 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image                                      
UI menu load time = 27 milli seconds                                                
13 crosshairs parsed                                                                
CL_InitCGame: 20.78 seconds                                                         
1820 msec to draw all images                                                        
Com_TouchMemory: 0 msec                                                             
^2urt.voxel.net ^3 Stats Tracking! ^7| Play nice!                                   
pb-ubuntu joined the blue team.                                                     
pb-ubuntu entered the game                                                          
^2urt.voxel.net ^3 Stats Tracking! ^7| Play nice!                                   
RE_Shutdown( 0 )                                                                    
Hunk_Clear: reset the hunk ok                                                       
----- R_Init -----                                                                  

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_NEAREST                
picmip: 1                                            
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: disabled                                 
compressed textures: disabled                        
Initializing Shaders                                 
----- finished R_Init -----                          
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 533 milli seconds                
UI menu load time = 372 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
----- FS_Startup -----                               
Going through search path...                         

----------------------
24939 files in pk3 files
Added favorite server 85.214.105.188:27960
2 servers listed in browser with 13 players.
85.214.105.188:27960 resolved to 85.214.105.188:27960
Server is full.                                      
Server is full.                                      
RE_Shutdown( 0 )                                     
Hunk_Clear: reset the hunk ok                        
----- R_Init -----                                   

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_NEAREST                
picmip: 1                                            
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: disabled                                 
compressed textures: disabled                        
Initializing Shaders                                 
----- finished R_Init -----                          
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 513 milli seconds                
UI menu load time = 369 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
----- FS_Startup -----                               
Going through search path...                         

----------------------
33252 files in pk3 files
2 servers listed in browser with 78 players.
Scanning for servers on the local network...
151 servers listed in browser with 303 players.
725 servers not listed due to filters, packet loss or pings higher than 800
82.103.128.193:27960 resolved to 82.103.128.193:27960                      
----- FS_Startup -----                                                     
Going through search path...                                               

handle 1: music/mainmenu.wav
----------------------      
41565 files in pk3 files    
RE_Shutdown( 0 )            
Hunk_Clear: reset the hunk ok
----- R_Init -----           

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_NEAREST                
picmip: 1                                            
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: disabled                                 
compressed textures: disabled                        
Initializing Shaders                                 
----- finished R_Init -----                          
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 484 milli seconds                
UI menu load time = 360 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
Loading vm file vm/cgame.qvm...                      
VM file cgame compiled to 1617707 bytes of code      
cgame loaded in 34383680 bytes on the hunk           
stitched 0 LoD cracks                                
...loaded 4502 faces, 95 meshes, 100 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image                                      
UI menu load time = 25 milli seconds                                                
13 crosshairs parsed                                                                
CL_InitCGame: 12.13 seconds                                                         
3004 msec to draw all images                                                        
Com_TouchMemory: 0 msec                                                             
Ndolemon joined the red team.                                                       
Ndolemon entered the game                                                           
Lap_boy say: Play fair or be BANNED ... !                                           
$trik.............er managed to slow down Comanche's SR-8 round just a little.      
pb-ubuntu joined the blue team.                                                     
pb-ubuntu entered the game                                                          
Lap_boy say: Play fair or be BANNED ... !                                           
Kakashi got a lead enema from }o$x{iceblaze's retro M4.                             
^4.:|Ao7|:.Green2^7 (BLUE Watch Tower Area): ^3Thanks                               
}o$x{iceblaze managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.    
Fonkster managed to slow down Pisol's SR-8 round just a little.  NEEP NEEP!         
Comanche managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.         
Ripper was on the wrong end of Michal-(Svk).'s G36.                                 
SeBiDi timed out                                                                    
}o$x{iceblaze managed to slow down Pisol's SR-8 round just a little.  NEEP NEEP!    
Pisol got a lead enema from menime[]SPAIN[]'s retro M4.                             
Kakashi was on the wrong end of Michal-(Svk).'s G36.                                
Michal-(Svk). managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.    
.:|Ao7|:.Green2 got a lead enema from menime[]SPAIN[]'s retro M4.                   
$trik.............er managed to slow down Comanche's SR-8 round just a little.      
You were hit in the Legs by }o$x{iceblaze for 17% damage.                           
You hit }o$x{iceblaze in the Torso for 44% damage.                                  
You were hit in the Kevlar by }o$x{iceblaze for 29% damage.                         
You were hit in the Legs by }o$x{iceblaze for 17% damage.                           
menime[]SPAIN[] was MP5K spammed without mercy by Ripper.                           
^4Kakashi^7 (BLUE Base Area): ^3Thanks                                              
^4Ripper^7 (BLUE Base Area): ^3Requesting medic. Status: near death                 
You were hit in the Kevlar by Comanche for 100% damage.                             
pb-ubuntu managed to slow down Comanche's SR-8 round just a little.                 
Comanche had 100% Health.                                                           
Ripper bled to death from menime[]SPAIN[]'s attacks.                                
^1menime[]SPAIN[]^3: ^3argg xD                                                      
*ARMAGEDON* connected                                                               
^4Kakashi^7 (BLUE Base Area): ^3Negative                                            
.:|Ao7|:.Green2 was torn asunder by Fonkster's crass AK103.                         
[OS]bobgael connected                                                               
^4Kakashi^7 (BLUE Base Area): ^3Requesting medic. Status: near death                
^4Kakashi^7 (BLUE Base Area): ^3Requesting medic. Status: near death                
Fonkster was MP5K spammed without mercy by Pisol.                                   
}o$x{iceblaze managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.  NEEP NEEP!
*ARMAGEDON* joined the red team.                                                            
*ARMAGEDON* entered the game                                                                
^4Kakashi^7 (BLUE Base Area): ^3Requesting medic. Status: near death                        
Kakashi was taken out by Ripper's PSG1. Plink!                                              
Michal-(Svk). was MP5K spammed without mercy by $trik.............er.                       
$trik.............er got a lead enema from menime[]SPAIN[]'s retro M4.                      
^4Ripper^3: ^3negative                                                                      
[OS]bobgael joined the blue team.                                                           
[OS]bobgael entered the game                                                                
You hit menime[]SPAIN[] in the Arms for 17% damage.                                         
You hit menime[]SPAIN[] in the Kevlar for 29% damage.                                       
menime[]SPAIN[] was pistol whipped by $trik.............er.                                 
}o$x{iceblaze was taken out by Ripper's PSG1. Plink!                                        
Michal-(Svk). was pistol whipped by $trik.............er.                                   
Comanche was MP5K spammed without mercy by Oo-NastyCommie-Oo.                               
Michal-(Svk). disconnected                                                                  
Fonkster was MP5K spammed without mercy by Pisol.                                           
Ndolemon managed to slow down $trik.............er's SR-8 round just a little.              
}o$x{iceblaze managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.  NEEP NEEP!
Oo-NastyCommie-Oo was MP5K spammed without mercy by *ARMAGEDON*.                            
You hit menime[]SPAIN[] in the Head for 100% damage.                                        
menime[]SPAIN[] was on the wrong end of pb-ubuntu's G36.                                    
Comanche managed to slow down [OS]bobgael's SR-8 round just a little.                       
Ndolemon bled to death from Ripper's attacks.                                               
^1menime[]SPAIN[]^3: ^31 min plz                                                            
VASSIRI connected                                                                           
menime[]SPAIN[] joined the spectators.                                                      
^4Oo-NastyCommie-Oo^3: ^3lol no !                                                           
*ARMAGEDON* was taken out by Ripper's PSG1. Plink!                                          
.:|Ao7|:.Green2 was MP5K spammed without mercy by }o$x{iceblaze.                            
}o$x{iceblaze managed to slow down $trik.............er's SR-8 round just a little.         
VASSIRI joined the red team.                                                                
VASSIRI entered the game
Ndolemon was taken out by Ripper's PSG1. Plink!
$trik.............er managed to slow down *ARMAGEDON*'s SR-8 round just a little.
Ripper was torn asunder by Fonkster's crass AK103.
*ARMAGEDON* managed to slow down [OS]bobgael's SR-8 round just a little.
VASSIRI was MP5K spammed without mercy by Oo-NastyCommie-Oo.
Oo-NastyCommie-Oo was torn asunder by Fonkster's crass AK103.
Pisol managed to slow down }o$x{iceblaze's SR-8 round just a little.
Ndolemon played 'catch the shiny bullet' with .:|Ao7|:.Green2's LR-300 rounds.
[OS]bobgael managed to slow down *ARMAGEDON*'s SR-8 round just a little.
Pisol disconnected
*ARMAGEDON* managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
}o$x{iceblaze got a whole lot of hole from Ripper's DE round.
.:|Ao7|:.Green2 managed to slow down VASSIRI's SR-8 round just a little.
pb-ubuntu joined the spectators.
Lap_boy say: Play fair or be BANNED ... !
}o$x{iceblaze managed to slow down $trik.............er's SR-8 round just a little.
Fonkster managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
Ripper managed to slow down *ARMAGEDON*'s SR-8 round just a little.
VASSIRI managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
Comanche managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
*ARMAGEDON* managed to slow down [OS]bobgael's SR-8 round just a little.
^7(SPEC) menime[]SPAIN[]^3: ^3ok
^7(SPEC) menime[]SPAIN[]^3: ^3im here
menime[]SPAIN[] joined the red team.
menime[]SPAIN[] entered the game
}o$x{iceblaze played 'catch the shiny bullet' with .:|Ao7|:.Green2's LR-300 rounds.
*ARMAGEDON* managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
Ndolemon managed to slow down [OS]bobgael's SR-8 round just a little.
Kakashi was torn asunder by Fonkster's crass AK103.
Fonkster managed to slow down $trik.............er's SR-8 round just a little.
Comanche played 'catch the shiny bullet' with .:|Ao7|:.Green2's LR-300 rounds.
Ripper got a lead enema from menime[]SPAIN[]'s retro M4.
menime[]SPAIN[] was MP5K spammed without mercy by $trik.............er.
^4Oo-NastyCommie-Oo^3: ^3shame
Oo-NastyCommie-Oo got a lead enema from menime[]SPAIN[]'s retro M4.
Ripper managed to slow down VASSIRI's SR-8 round just a little.
$trik.............er managed to slow down *ARMAGEDON*'s SR-8 round just a little.
}o$x{iceblaze managed to slow down [OS]bobgael's SR-8 round just a little.
*ARMAGEDON* played 'catch the shiny bullet' with .:|Ao7|:.Green2's LR-300 rounds.
[OS]bobgael managed to slow down Ndolemon's SR-8 round just a little.
Kakashi got a lead enema from menime[]SPAIN[]'s retro M4.
Ndolemon managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
^1menime[]SPAIN[]^3: ^3jaja
Ripper managed to slow down VASSIRI's SR-8 round just a little.
Oo-NastyCommie-Oo managed to slow down *ARMAGEDON*'s SR-8 round just a little.
[OS]bobgael managed to slow down *ARMAGEDON*'s SR-8 round just a little.
*ARMAGEDON* managed to slow down $trik.............er's SR-8 round just a little.
$trik.............er got a lead enema from menime[]SPAIN[]'s retro M4.
menime[]SPAIN[] managed to slow down Oo-NastyCommie-Oo's SR-8 round just a little.
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Shutdown tty console

```

my glxinfo output follows:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440/AGP/SSE/3DNOW!
OpenGL version string: 1.5.8 NVIDIA 96.43.09
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence, 
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod, 
    GL_SUN_slice_accum

48 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x42 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x45 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x46 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x47 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x48 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x49 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x4e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

55 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x51  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x52  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x53  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x55  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5a  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5d  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x62  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x65  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x67  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x69  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6a  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6b  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6f  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x71  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81  0 sg  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x82  0 sg  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x83  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x84  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x85  0 sg  0  0  0 r  .  .  0  0  0  0  4 16  0 16 16 16 16  0 0 None
0x86  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0x87  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None

```
Can anyone help? Thanks.

---

### Post by eenofonn on 2009-02-11
Urban Terror is Awesome!!! I have even decided to run my own server "Southeast AK UrbanTerror" so that I can get a better experience (less lag)  Anyone who wants to play on it is welcome to (tho it's not up all the time).  I have it running on 8.10 server and I love it.... 


The other cool thing about UrT is that it's cross platform so I can play on my Kubuntu box / my hackintosh / and Vista Machine :(

check out my site [http://geekontherock.com/blog/](http://geekontherock.com/blog/) if you are interested in playing on my server I am looking for input 

-eenofonn

---

### Post by eenofonn on 2009-02-12
> **michaelzap said:**
> To those of you who lose your mouse after launching UT: Make sure that you turn off Compiz before running it. I use Alt+F2 to run [COLOR="Red"]metacity --replace[/COLOR] before launching UT and [COLOR="Red"]compiz --replace[/COLOR] after I'm done. Works like a charm.

you might want to look into compiz switch... does the job pretty well and has a cool icon ;)

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by eenofonn on 2009-02-12
> **Bramkaandorp said:**
> Just a little bump.

I currently have Ultimate Edition 2.0 Gamers installed, which has Urban terror pre-installed.

But is Urban Terror In the ubuntu repositories, or is that exclusively the case in Ultimate Edition?

Cheers,

Bram

As far as I know it's not in the repos... but you can get it from Getdeb 

[http://www.getdeb.net/app/Urban+Terror](http://www.getdeb.net/app/Urban+Terror)

I think it might be in the playdeb repos

---

### Post by eenofonn on 2009-02-12
> **Wumpus55 said:**
> I just tried to load UrT 4.1 but my graphics are all screwed up.  I think it is my ATI driver.  Unfortunately, it is a laptop and I can't get an NVIDIA card for it.   

Have you seen any configuration stuff for 4.1 on ubuntu?

are you still having problems with this or do you know about envy?

---

### Post by Bramkaandorp on 2009-02-22
Apparently getdeb works again.

I am in seventh heaven.

Cheers,

Bram

---

### Post by glennmm on 2009-05-11
Hey All,
I played, UT 4.1 with my friend, (UT 4.1 is just superb :) ) but when i tried to installed it, I also faced some graphcs problem..

---

### Post by jakejw93 on 2010-06-14
[http://www.youtube.com/watch?v=NvwEMpdEkBQ](http://www.youtube.com/watch?v=NvwEMpdEkBQ)

Gameplay video of urban terror in Linux,

The game reminds me of counter strike and is much fun to play!

---

### Post by maniat1k on 2012-02-15
I am tryng to get some bots in a localhost server, just for me so I follow this steps:

[http://namchangkorpa.wordpress.com/2010/03/18/adding-bots-in-urban-terror/](http://namchangkorpa.wordpress.com/2010/03/18/adding-bots-in-urban-terror/)

The game runs and my bots are there but when I'm intereact with them the game crashes:
```
------ Game Initialization -------
gamename: q3ut4
gamedate: Dec 21 2007
2 teams with 31 entities
-----------------------------------
16 UT bots parsed
53 arenas parsed
UI menu load time = 577 milli seconds
UI menu load time = 378 milli seconds
16 bots parsed
13 crosshairs parsed
UI menu load time = 37 milli seconds
13 crosshairs parsed
Bienvenidos!
Cheteka joined the blue team.
Cheteka entered the game
Bienvenidos!
]/exec bot_3.cfg
Com_sprintf: overflow of 2 in 2
loaded skill 1 from bots/default_c.c
loaded skill 1 from bots/ut_puma_c.c
loaded puma from bots/ut_puma_t.c
Com_sprintf: overflow of 2 in 2
loaded cached skill 1.000000 from bots/default_c.c
loaded skill 1 from bots/ut_penguin_c.c
loaded skill 4 from bots/default_c.c
loaded skill 4 from bots/ut_penguin_c.c
loaded penguin from bots/ut_penguin_t.c
Com_sprintf: overflow of 2 in 2
loaded cached skill 1.000000 from bots/default_c.c
loaded skill 1 from bots/ut_cobra_c.c
loaded cobra from bots/ut_cobra_t.c
Spawning bot
Spawning bot
Spawning bot
=lvl1=Puma connected
=lvl2=Penguin connected
=lvl1=Cobra connected
^3Warning: no alt routes without Neutral Flag
=lvl1=Cobra joined the blue team.
=lvl1=Cobra entered the game
=lvl1=Puma joined the red team.
=lvl1=Puma entered the game
=lvl2=Penguin joined the blue team.
=lvl2=Penguin entered the game
2 teams with 31 entities
Cheteka joined the red team.
Cheteka entered the game
Bienvenidos!
^1Cheteka^7 has taken the ^4Blue^7 flag!
You hit =lvl1=Cobra in the Kevlar for 29% damage.
You hit =lvl1=Cobra in the Kevlar for 29% damage.
DOUBLE SIGNAL FAULT: Received signal 11, exiting...
----- Client Shutdown (Received signal 11) -----
Closing SDL audio device...
*** glibc detected *** /usr/lib/games/urbanterror: double free or corruption (!prev): 0x0c6a2150 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ebc2)[0x17ebc2]
/lib/i386-linux-gnu/libc.so.6(+0x6f862)[0x17f862]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0x18294d]
/usr/lib/libSDL-1.2.so.0(SDL_WaitThread+0x46)[0x5c3136]
/usr/lib/libSDL-1.2.so.0(SDL_AudioQuit+0x3e)[0x5bab1e]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x6d)[0x5b9edd]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1b)[0x5b9f7b]
/usr/lib/games/urbanterror[0x819af88]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d31)[0xbecd31]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0x1e20ce]
======= Memory map: ========
00110000-00286000 r-xp 00000000 08:02 3312       /lib/i386-linux-gnu/libc-2.13.so
00286000-00288000 r--p 00176000 08:02 3312       /lib/i386-linux-gnu/libc-2.13.so
00288000-00289000 rw-p 00178000 08:02 3312       /lib/i386-linux-gnu/libc-2.13.so
00289000-0028c000 rw-p 00000000 00:00 0 
0028c000-0029d000 r-xp 00000000 08:02 11903      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0029d000-0029e000 r--p 00010000 08:02 11903      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0029e000-0029f000 rw-p 00011000 08:02 11903      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
0029f000-002bc000 r-xp 00000000 08:02 12136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
002bc000-002bd000 r--p 0001c000 08:02 12136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
002bd000-002be000 rw-p 0001d000 08:02 12136      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
002be000-002c8000 r-xp 00000000 08:02 3357       /lib/i386-linux-gnu/libnss_nis-2.13.so
002c8000-002c9000 r--p 00009000 08:02 3357       /lib/i386-linux-gnu/libnss_nis-2.13.so
002c9000-002ca000 rw-p 0000a000 08:02 3357       /lib/i386-linux-gnu/libnss_nis-2.13.so
002cd000-002f5000 r-xp 00000000 08:02 3342       /lib/i386-linux-gnu/libm-2.13.so
002f5000-002f6000 r--p 00028000 08:02 3342       /lib/i386-linux-gnu/libm-2.13.so
002f6000-002f7000 rw-p 00029000 08:02 3342       /lib/i386-linux-gnu/libm-2.13.so
002f7000-00300000 r-xp 00000000 08:02 11897      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00300000-00301000 r--p 00008000 08:02 11897      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00301000-00302000 rw-p 00009000 08:02 11897      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00302000-0030b000 r-xp 00000000 08:02 11915      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
0030b000-0030c000 r--p 00008000 08:02 11915      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
0030c000-0030d000 rw-p 00009000 08:02 11915      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
0030f000-00311000 r-xp 00000000 08:02 11893      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00311000-00312000 r--p 00001000 08:02 11893      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00312000-00313000 rw-p 00002000 08:02 11893      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00313000-0031a000 r-xp 00000000 08:02 243144     /usr/lib/fglrx/libatiuki.so.1.0
0031a000-0031b000 rw-p 00006000 08:02 243144     /usr/lib/fglrx/libatiuki.so.1.0
0031b000-00321000 r-xp 00000000 08:02 12031      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
00321000-00322000 r--p 00005000 08:02 12031      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
00322000-00323000 rw-p 00006000 08:02 12031      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
00323000-0032b000 r-xp 00000000 08:02 3393       /lib/i386-linux-gnu/libwrap.so.0.7.6
0032b000-0032c000 r--p 00007000 08:02 3393       /lib/i386-linux-gnu/libwrap.so.0.7.6
0032c000-0032d000 rw-p 00008000 08:02 3393       /lib/i386-linux-gnu/libwrap.so.0.7.6
0032d000-00332000 r-xp 00000000 08:02 11927      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
00332000-00333000 r--p 00004000 08:02 11927      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
00333000-00334000 rw-p 00005000 08:02 11927      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
00334000-0033a000 r-xp 00000000 08:02 12057      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
0033a000-0033b000 r--p 00005000 08:02 12057      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
0033b000-0033c000 rw-p 00006000 08:02 12057      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
0033c000-00341000 r-xp 00000000 08:02 29298      /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
00341000-00342000 r--p 00004000 08:02 29298      /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
00342000-00343000 rw-p 00005000 08:02 29298      /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
00343000-0035f000 r-xp 00000000 08:02 3333       /lib/i386-linux-gnu/libgcc_s.so.1
0035f000-00360000 r--p 0001b000 08:02 3333       /lib/i386-linux-gnu/libgcc_s.so.1
00360000-00361000 rw-p 0001c000 08:02 3333       /lib/i386-linux-gnu/libgcc_s.so.1
0036b000-00372000 r-xp 00000000 08:02 3376       /lib/i386-linux-gnu/librt-2.13.so
00372000-00373000 r--p 00006000 08:02 3376       /lib/i386-linux-gnu/librt-2.13.so
00373000-00374000 rw-p 00007000 08:02 3376       /lib/i386-linux-gnu/librt-2.13.so
00374000-00460000 r-xp 00000000 08:02 11925      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
00460000-00464000 r--p 000eb000 08:02 11925      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
00464000-00465000 rw-p 000ef000 08:02 11925      /usr/lib/i386-linux-gnu/libasound.so.2.0.0
00465000-00596000 r-xp 00000000 08:02 11891      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00596000-00597000 ---p 00131000 08:02 11891      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00597000-00598000 r--p 00131000 08:02 11891      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00598000-0059a000 rw-p 00132000 08:02 11891      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
0059a000-0059b000 rw-p 00000000 00:00 0 
0059b000-005ae000 r-xp 00000000 08:02 3374       /lib/i386-linux-gnu/libresolv-2.13.so
005ae000-005af000 r--p 00012000 08:02 3374       /lib/i386-linux-gnu/libresolv-2.13.so
005af000-005b0000 rw-p 00013000 08:02 3374       /lib/i386-linux-gnu/libresolv-2.13.so
005b0000-005b2000 rw-p 00000000 00:00 0 
005b5000-00623000 r-xp 00000000 08:02 9742       /usr/lib/libSDL-1.2.so.0.11.3
00623000-00624000 r--p 0006e000 08:02 9742       /usr/lib/libSDL-1.2.so.0.11.3
00624000-00625000 rw-p 0006f000 08:02 9742       /usr/lib/libSDL-1.2.so.0.11.3
00625000-0064d000 rw-p 00000000 00:00 0 
0064d000-00687000 r-xp 00000000 08:02 143417     /usr/lib/fglrx/libatiadlxx.so
00687000-00689000 rw-p 0003a000 08:02 143417     /usr/lib/fglrx/libatiadlxx.so
00689000-00699000 rw-p 00000000 00:00 0 
00699000-006e5000 r-xp 00000000 08:02 68524      /usr/lib/i386-linux-gnu/libpulse.so.0.13.4DOUBLE SIGNAL FAULT: Received signal 6, exiting...
Terminado (killed)

```

how can I solve this?

---

