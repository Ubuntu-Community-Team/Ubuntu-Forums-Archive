---
title: "No sound in ZSNES"
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by grte on 2005-12-14
Okay, so I haven't got any sound in ZSNES.

I've tried killall esd, nothing.  I've run it with sudo, nothing.  I've installed libsdl1.2debian-all, nothing.

I've tried SNES9x, and it hasn't got sound either.  Any ideas?  Sound works with everything else.

Also, I'm using 1.42

---

### Post by 0okami on 2005-12-14
here's what i did to get zsnes  (zsnes 1.40) with sound: 

sudo apt-get install zsnes
(installed zsnes) 

zsnes
(to run the emulator)

pressed "z" to continue. 
(only shows for first time users)

in zsnes, click config and select sound 
Make sure Enable sound is selected. 
Select enable stereo (if your sound card supports it) 

Thats all it took here. Might be different on your end. 

now to figure out why it sounds so... terrible. hmm.


****edit*** 
in the sound config of zsnes,  i set sampling rate to 44100khz and enabled sound buffering. Restarted Zsnes, and now it sounds crystal clear.  :)

---

### Post by grte on 2005-12-14
Both already on, I'm afraid.

---

### Post by grte on 2005-12-14
By the way, here's the output of terminal:

```
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.
Please report crashes to [email]zsnes-devel@lists.sourceforge.net[/email].

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

ZSNES could not find any joysticks.
```

---

### Post by 0okami on 2005-12-14
do all other system sounds work? post us the zsnes configuration file here please. This file can be found in: ~/.zsnes/zsnesl.cfg

To get the info, in a terminal type: gedit ~/.zsnes/zsnesl.cfg
Then just copy and paste it here

(here an example of mine at its current state...) 



```


; ZSNES Configuration file



; Frame Skip = 0 .. 9



FrameSkip = 0



; Auto Frame Skip = 0 or 1 (1 = ON)



AutoFrameSkip = 1



; Player 1/2 Input Device.  Use the GUI to set these values

; NOTE : Using this to select joysticks manually will NOT work!



Player1Device = 1

Player2Device = 0



; Keyboard Scancodes/Joystick Mappings for Keyboard 1 & 2

; In order of Right, Left, Down, Up, Start, Select, B, Y, A, X, L, R

; Use the GUI to set these values



ScanKey1 = 94, 92, 96, 90, 28, 15, 44, 45, 30, 31, 16, 17

ScanKey2 = 209, 211, 207, 199, 26, 27, 38, 37, 25, 24, 23, 36



; Share Player 3 and 4 control inputs with Player 1 and 2 to allow

; 2 devices to be shared on a single player.  This feature automatically

; disables MultiTap (Multiplayer 5) support.  Set this to 1 to enable.



Pl34to12Share = 0



; Percent to Execute [50 .. 150]



Execute = 100



; Video Mode, 0 - 15

;   0 = 256x224 WIN           1 = 256x224 FULL

;   2 = 512x448 WIN           3 = 640x480 FULL

;   4 = 256x224  OGL WIN      5 = 512x448  OGL WIN

;   6 = 640x480  OGL FULL     7 = 640x576  OGL WIN

;   8 = 768x672  OGL WIN      9 = 896x784  OGL WIN

;  10 = 1024x896 OGL WIN     11 = 800x600  OGL FULL

;  12 = 1024x768 OGL FULL    13 = 640x480  OGL WIN

;  14 = 800x600  OGL WIN     15 = 1024x768 OGL WIN

;  16 = VARIABLE OGL WIN



VideoModeLin = 10



; Sound Emulation = 0 or 1 (1 = ON)



Sound = 1



; Sound Sampling Rate

;   0 =  8,000 Hz, 1 = 11,025 Hz, 2 = 22,050 Hz

;   3 = 44,100 Hz, 4 = 16,000 Hz, 5 = 32,000 Hz

;   6 = 48,000 Hz



SoundRate = 3



; Stereo (0 = off, 1 = on)



Stereo = 1



; Stereo Reversed.  Swaps left channel with right. (0 = off, 1 = L <-> R)



ReverseStereo = 0



; GUI Disable (1 = Disable GUI, 0 = Enable GUI)



GUIDisable = 0



; New Graphics Engine (1 = Enable, 0 = Disable)



NewGfx = 1



; Scanlines (0 = Disable, 1 = Full, 2 = 25 3 = 50



Scanlines = 2



; Interpolation (1 = Enable, 0 = Disable)



Interpolation = 0



; Disable Echo  (1 = Yes, 0 = No)



EchoDisable = 0



; Sound Volume Level (0 .. 100)

; Note : Setting this too high can cause sound overflow which degrades quality



Volume = 100



; Set this to 1 if you do not want ZSNES to save the configuration files.



DontSave = 0



; Savefile directory.  Leave it blank if you want the save files to be in the

; same directory as the games.  It should be in a format like : C:\dir\dir



SaveDirectory = 



; Game directory.  This is the directory where the GUI starts at.

; ZSNES automatically writes the current directory here upon exit.



GameDirectory = /home/ookami/Desktop/mario world


```

---

### Post by grte on 2005-12-14
Yes, all other system sounds work.  The only sound issues I'm having at this point are for three programs: ZSNES, SNES9x, and Battle for Wesnoth.

Here's my .cfg file:

```
; ZSNES Configuration file



; Frame Skip: 0 = Auto, 1-10 = Skip 0 .. 9



FrameSkip = 0



; Player 1/2 Input Device.  Use the GUI to set these values

; NOTE : Using this to select joysticks manually will NOT work!



Player1Device = 1

Player2Device = 0



; Keyboard Scancodes/Joystick Mappings for Keyboard 1 & 2

; In order of Right, Left, Down, Up, Start, Select, B, Y, A, X, L, R

; Use the GUI to set these values



ScanKey1 = 94, 92, 96, 90, 28, 54, 44, 30, 45, 31, 32, 46

ScanKey2 = 209, 211, 207, 199, 26, 27, 38, 37, 25, 24, 23, 36



; Share Player 3 and 4 control inputs with Player 1 and 2 to allow

; 2 devices to be shared on a single player.  This feature automatically

; disables MultiTap (Multiplayer 5) support.  Set this to 1 to enable.



Pl34to12Share = 0



; Percent to Execute [50 .. 150]



Execute = 100



; Video Mode, 0 - 15

;   0 = 256x224   R WIN        1 = 256x224  R FULL

;   2 = 512x448   DR WIN       3 = 640x480  DS FULL

;   4 = 256x224   OR  WIN      5 = 512x448  ODR WIN

;   6 = 640x480   ODS FULL     7 = 640x480  ODS WIN

;   8 = 640x576   ODR WIN      9 = 768x672  ODR WIN

;  10 = 800x600   ODS FULL    11 = 800x600  ODS WIN

;  12 = 896x784   ODR WIN     13 = 1024x768 ODS FULL

;  14 = 1024x768  ODS WIN     15 = 1024x896 ODR WIN

;  16 = 1280x1024 ODS FULL    17 = VARIABLE ODR WIN



VideoModeLin = 3



; Sound Emulation = 0 or 1 (1 = ON)



Sound = 1



; Sound Sampling Rate

;   0 =  8,000 Hz, 1 = 11,025 Hz, 2 = 22,050 Hz

;   3 = 44,100 Hz, 4 = 16,000 Hz, 5 = 32,000 Hz

;   6 = 48,000 Hz



SoundRate = 3



; Stereo (0 = off, 1 = on)



Stereo = 1



; Stereo Reversed.  Swaps left channel with right. (0 = off, 1 = L <-> R)



ReverseStereo = 0



; GUI Disable (1 = Disable GUI, 0 = Enable GUI)



GUIDisable = 0



; New Graphics Engine (1 = Enable, 0 = Disable)



NewGfx = 1



; Scanlines (0 = Disable, 1 = Full, 2 = 25%, 3 = 50%)



Scanlines = 0

; Interpolation (1 = Enable, 0 = Disable)



Interpolation = 0



; Disable Echo  (1 = Yes, 0 = No)



EchoDisable = 0



; Sound Volume Level (0 .. 100)

; Note : Setting this too high can cause sound overflow which degrades quality



Volume = 100



; Set this to 1 if you do not want ZSNES to save the configuration files.



DontSave = 0



; Savefile directory.  Leave it blank if you want the save files to be in the

; same directory as the games.  It should be in a format like : C:\dir\dir



SaveDirectory = /home/avatar/.zsnes



; Game directory.  This is the directory where the GUI starts at.

; ZSNES automatically writes the current directory here upon exit.



GameDirectory = /home/avatar/Emulation/SNES


```

---

### Post by 0okami on 2005-12-14
config looks good. 

Ok, what is your default sound  card? 
system->preferences->sound
(In my case, i have my nvidia nforce2 selected.) 

Also, lets go to:
applications->sound&video->Sound control
This will load the mixer. 

Select: 
file->change Device 
(dont change it yet... just tell me what is selected) 
(In my case, i have my nvidia nforce2 selected.)

In that same mixer window, Select
Edit->preferences. 
Put a check mark on just about everything in there.  
click close. 

check for muted devices that should not be muted, and raise their volumen. 

test zsnes.
(i actually recomend letting run ZSNES in the background with a rom loaded while your are poking at the volume controls. just make sure its not too loud to scare you when the sound comes on :)

---

### Post by grte on 2005-12-14
Default soundcard is an Audigy 2 Value

I don't see a sound control, but I assume you mean Volume control.  The device selected is Audigy 2 Value

The only volume control that's muted is the Line-in.  Everything else seems to be maxed out.  Unmuted line in and turned it up, still no sound.

---

### Post by 0okami on 2005-12-14
[QUOTE=grte]Default soundcard is an Audigy 2 Value

I don't see a sound control, but I assume you mean Volume control.  The device selected is Audigy 2 Value

The only volume control that's muted is the Line-in.  Everything else seems to be maxed out.  Unmuted line in and turned it up, still no sound.[/QUOTE]


Ok, at this point im not exactly sure what to do next... 

You could try changing things around in:

System->Preferences->multimedia Systems selector
the tab that says Audio 
Default sink
Output: (i have ALSA selected)
Default source I have OSS.  

Press test on the Alsa option. You should hear a mid-freq beep.  
If not, try setting the output to OSS setting. 

all of those worked for me... unfortunatly, im not quite sure what the problem on your side might be as my skill in linux is not yet advanced.  

if you come across a solution please post it, Id like to know what happend.

---

### Post by fct on 2005-12-14
Try this:

$ sudo lsmod |grep oss

If you don't get any output, you're lacking oss emulation (for apps depending on the previous sound system used in linux). Don't know if that's your problem with zsnes, but you can try to load OSS emulation like this:

$ sudo modprobe snd_pcm_oss snd_mixer oss

Hope it solves your problem.

---

### Post by GeoMX on 2005-12-14
I fixed that one by installing libsdl1.2-esd. Now sound works fine in zsnes.

Best wishes,
José Jorge (GeoMX).

---

### Post by grte on 2005-12-14
Okay, I've got another problem before I can try getting ZSNES to work.  After playing with the volume controls, I now have no sound at all.  Is there any way to restore volume levels to defaults?

---

### Post by grte on 2005-12-14
Okay, well I haven't figured out how to get sound back with my normal sound card, but I've got it running through the onboard sound card, so I could try fixing this again.

So I tried sudo lsmod |grep oss and got the following output:

```
snd_seq_oss            29440  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    48644  21 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
```

Used the second command you advised, still no sound...

I've also tried installing libsdl1.2-esd, but still didn't work.

---

### Post by grte on 2005-12-14
Okay, update, I've gotten sound working in ZSNES.  I'm not exactly certain how, but I ran the automatix script, and all of a sudden it works.  Could it have been Timidity midi support that I was missing?  As an added bonus, sound is working for Wesnoth, too.

On a related note, though, my Audigy 2 is still foobar'd...If anyone knows how to restore default volumes, I'd be eternally grateful.

---

### Post by pizzach on 2006-03-23
This looks like an old thread, but I'm going to add my notes for anyone who may happen by it.

I didn't have sound until I turned the volume up (under Config>Sound).  At 10% it was unhearable.

The statement about about sdl made me realize there is an sdl driver for Alsa too. libsdl1.2debian-alsa to be exact.  If you don't use esd like me, this you need this driver.  I accidently used OSS first, but with OSS I can only get one application to have sound at a time.  

To make the sound not pop and stuff you need to go to Config>Sound in the menues and change the check from Gaussian to Cubic Spline or 8-point.  Enabling high quality on the low pass doesn't hurt either.

---

### Post by btnheazy03 on 2006-04-20
I got mine to work! either .. .

sudo apt-get install libsdl1.2-esd

or

sudo apt-get install libsdl1.2debian-alsa

, depending on what sound system you're using

---

### Post by onlainari on 2008-05-13
Ok solved the problem below by running zsnes with "-ad sdl" option suggested at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470410#20](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470410#20)


- I have volume bar at 100%, I have enabled sound and stereo sound. I have tried to enable surround sound too.

- I have libsdl1.2debian-alsa installed

- I installed the timidity package ( i guess that installed some midi support)

- I have tried to enable all those weird alsamixer bars

when i run zsnes from console (super user or user) i get this about sound:

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

when i open a rom, one of the text on bottom left says interleaved: no ...
i wonder what that means(?)

and lsmod |grep oss gives aboout the same output(or so it looks at quick glance) as grte

I think i have tried all the hints given in this thread so far but it didnt help :/  ..well i didnt and dont want to install automatix, but i tried the timidity thing which didnt help:/

im running xubuntu 8.04

---

### Post by ge0ffrey on 2008-06-14
zsnes -ad sdl
solved it for me too

---

### Post by Korsaire71100 on 2008-07-16
resolve for me too

thanks guys
and viva GNU/Linux !!!!!!!!

---

### Post by interim descriptor on 2008-08-03
Edit: Nevermind

---

### Post by lambdacore on 2008-08-12
Hey guys, just to let you know.
I had no sound either and I tried everything in this thread.
The only thing that worked for me is doing the zsnes -ad sdl.

So go ahead, it solved it for me. Just do : 

zsnes -ad sdl

in the console.

---

### Post by tuxxy on 2008-08-12
snes9express in the repos works great.

---

### Post by grossaffe on 2008-08-13
> **tuxxy said:**
> snes9express in the repos works great.

i prefer the GTK port of SNES9x, but whatever floats your boat.

---

### Post by skip mcshwang on 2008-08-13
ZSNES works for me when I run it from the terminal or turn off system sounds. I think the sound that gnome makes when launching a program from the menus stops the sound initialising in ZSNES.

---

### Post by Hawk__0 on 2008-08-17
Solved for me too with -ad sdl!! Thanks!
I just edited my menu shortcut to have those options on.  Works great :D

---

### Post by euchrid33 on 2008-10-06
I had a pretty similar problem to the ones people have mentioned here.  I got the sound going by starting znes as superuser.  I don't know if there's a better solution, a more permanent fix, but I just open the terminal and use sudo zsnes and I'm away.  I do have to do this every time I want to run it, which is a pain, but at least it works.

---

### Post by victorbrca on 2008-10-17
I already had libsdl1.2debian-alsa installed. Tried "zsnes -ad sdl" and it worked.


Vic.

---

### Post by soelk on 2008-10-18
Confirmed. Works for me too on Hardy 32-bit.

For us mortal gui people: 
System->Preferences->Main Menu->Games
Right click ZSNES Emulator and chose properties
Under "command" put. "zsnes -ad sdl" (without the quotes).

---

### Post by dfreer on 2008-10-18
> **soelk said:**
> Confirmed. Works for me too on Hardy 32-bit.

For us mortal gui people: 
System->Preferences->Main Menu->Games
Right click ZSNES Emulator and chose properties
Under "command" put. "zsnes -ad sdl" (without the quotes).

You do know, that once you run zsnes with the -ad sdl option, it's saves the preference? No need to modify the launch options, just run in terminal once.

---

### Post by soelk on 2008-10-19
> **dfreer said:**
> You do know, that once you run zsnes with the -ad sdl option, it's saves the preference? No need to modify the launch options, just run in terminal once.

Ah, you're right. It is a clever app in that way. It's been a while since the days when I reluctantly ran ZSNES from the command line (in 19XX using version 0.4XX). :)

---

### Post by rick08 on 2008-10-20
I had the same problem, but i fixed it searching through the forums.  I had to go into the zsnes configuration and change the audio type.  I will search the forums for that link and post it later.

---

### Post by themrrobert on 2009-01-10
:popcorn:
:KS

Ok here is what you need to do. 

Assuming the SDL libraries are installed (Including SDL_Sound/Audio) you need to modify the config file as follows:

~/.zyns/zsnesl.cfg

Find the lines like this:
```

;  ----
; -- Sound --
;  ----

; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"


```

Change the line:  libAoDriver="auto" to:
```

libAoDriver="sdl"

```

---

### Post by gabo.cr on 2009-02-01
Hey lambdacore !
Typing this in terminal:

zsnes -ad sdl

Works like a charm, Thanks !!

:)

---

### Post by denseralvo on 2009-03-07
solved the problem

go to your zsnes icon the right click select properties then select launcher then add to your zsnes -ad sdl then close.

I have now sound in my znes. thank guys

---

### Post by wpwend42 on 2009-03-14
I just wanted to jump in and say this solved my problem with ZSNES also.  Now I think I just need to tweak the graphics, seems to be running a little fast.

---

### Post by gigo6000 on 2009-04-04
Thanks guys,   zsnes -ad sdl worked for me!

---

### Post by WorldWithoutMS on 2009-05-25
> **denseralvo said:**
> solved the problem

go to your zsnes icon the right click select properties then select launcher then add to your zsnes -ad sdl then close.

I have now sound in my znes. thank guys

Hi there guys. deselravo? wrote the above quote. Thats call and I totally agree with him, but some users of ubuntu prefer to have their desktops with no icon shortcuts like me. So here is how I did it.

To get zsnes emulator to open correctly with sound, you must first set up the command line to open the application in a terminal rather than through the GNOME menu system. I am not sure, but I think GNOME menu system runs applications with some other pre sound driver other than the one intended (in this case, the "-ad sdl").

But, to preserve the empty clean feel of the desktop, one (like myself) still desperately wants to access and execute his applications from the GNOME menu. So here is how I did it. Note: this is for the 8.04 LTS release of Ubuntu. It might work on other versions and might not, you will just have to try it. Also, from what I have read, from previous messages, is that the -ad sdl will work with most sound cards. Anyway this is what I did.

1: Open up terminal window and type "sudo apt-get install libsdl1.2debian-alsa".

2: Once installed, close the terminal window. Navigate GNOME menu, ie. System > Prefferences > Main Menu.

3: Under the list of menus on the left, click "Games".

4: On the right side of the window under "Items", locate "ZSNES Emulator" and ensure it is ticked. Right click it and select "properties".

5: In the "Launch Properties" window, select under the "Type:" dropdown menu > Application in Terminal.

6: Within the same window inside the "Command" box, add "-ad sdl" to the line, so that it now reads "zsnes -ad sdl".

If you follow those six points, you should now be able to open ZSNES within the GNOME menu and not have to use a desktop shortcut. Now ZSNES appears like any other menu item within the GNOME. :P

There is only one downside to the method I use. If you want to run ZSNES, it must either be the first application you run once your computer is started up, or if it is not the first app., then you will need to restart your computer to make it work. Once the GNOME sound file (or whatever it is) starts up under any app., the slave file (?) "-ad sdl" file just will not open.

This downside does bother me though, all the same. Has anyone got any idea how to solve this part.

---

### Post by dfreer on 2009-05-26
> **WorldWithoutMS said:**
> To get zsnes emulator to open correctly with sound, you must first set up the command line to open the application in a terminal rather than through the GNOME menu system. I am not sure, but I think GNOME menu system runs applications with some other pre sound driver other than the one intended (in this case, the "-ad sdl").

The GNOME menu system simply launches the program, same as if you launched it from a terminal, only it doesn't show the terminal output. It does not change how ZSNES works at all, unless something else has been changed (user permissions, launch options, different path/binaries).

> **WorldWithoutMS said:**
> But, to preserve the empty clean feel of the desktop, one (like myself) still desperately wants to access and execute his applications from the GNOME menu. So here is how I did it. Note: this is for the 8.04 LTS release of Ubuntu. It might work on other versions and might not, you will just have to try it.

Not really important: The GNOME menu launcher for ZSNES is just a text file called /usr/share/applications/zsnes.desktop, which is the same type of file that is created on the Desktop, just perhaps with different launch options. This should work with any GNOME system IIRC.

> **WorldWithoutMS said:**
> 
1: Open up terminal window and type "sudo apt-get install libsdl1.2debian-alsa".


Just to let users know, this installs an ALSA-only enabled build of SDL. There is also libsdl1.2debian-oss, libsdl1.2debian-esd, and a libsdl1.2debian-all package (which contains all of the above, change your environment variable SDL_AUDIODRIVER to set the sound system you wish to use). Personnally I find OSS works best for me, but YMMV.

> **WorldWithoutMS said:**
> 6: Within the same window inside the "Command" box, add "-ad sdl" to the line, so that it now reads "zsnes -ad sdl".

There is only one downside to the method I use. If you want to run ZSNES, it must either be the first application you run once your computer is started up, or if it is not the first app., then you will need to restart your computer to make it work. Once the GNOME sound file (or whatever it is) starts up under any app., the slave file (?) "-ad sdl" file just will not open.


"-ad sdl" is not a file, it's a [commandline argument]("http://en.wikipedia.org/wiki/Command_line_argument") It is telling ZSNES which audio driver it should attempt to use. Here's a list (not sure if it is up-to-date):
```
-ad <>		Audio Driver (note you may not have all of these):
	auto	Select a driver automatically - uses SDL without libao
	null	No sound, only available with libao
	oss	Open Sound System, only available with libao on UNIX systems with OSS
	alsa	Advanced Linux Sound Architecture, only available with libao on Linux systems with ALSA
	alsa09	Advanced Linux Sound Architecture, only available with libao on Linux systems with ALSA
	polyp	polypaudio (next generation GNOME sound server), only available with libao and new versions of GNOME
	esd	ESounD or Enlightened Sound Daemon, only available with libao and ESD installed
	sun	Sun Microsystem's audio system, only available with libao and Solaris or certain BSD systems
	irix	IRIX audio system, only available with libao and IRIX systems
	nas	Network Audio System, only available with libao and NAS installed
	arts	Analog RealTime Synthesizer sound, only available with libao on systems with aRts (KDE)
	sdl	Simple DirectMedia Layer sound
```

When you launch ZSNES for the first time, it will create a file in the current user's home directory ~/.zsnes/zsnesl.cfg. If you launch it with the "-ad sdl" option, it will set the default to be SDL **IN** the config file. Henceforth, *everytime* you run ZSNES, it should use the SDL option until you change it. There should really be no need to set this as a permanent launch option to begin with.

As for why ZSNES will only work for you when you run it the first time, I'm not entirely sure. My guess would be a conflict with another sound-outputting application, I know with pSX, killing pulseaudio generally solves the conflict. 

I'd recommend trying OSS along with libao myself, as I've never had the problem you are experiencing using it, but you would need a build of ZSNES with libao enabled.

---

### Post by many_boomers on 2009-06-06
> **dfreer said:**
> You do know, that once you run zsnes with the -ad sdl option, it's saves the preference? No need to modify the launch options, just run in terminal once.

Not for me it doesn't. I have to enter it every time.

It does work with -ad sdl, but even when I edit the properties of applications>games>zsnes I still have to go command line commando. 

Ubuntu studio 8.10 P4 3.2G/2Gram Intel ICH5 (EWWWW!) sound.

---

### Post by shirato on 2009-08-08
I have looked through the thread and tried doing what was suggested, but I still don't have sound. I am using a soundblaster live 24-bit card and it works fine for everything I tied so far except zsnes.

---

### Post by bigdee973 on 2009-10-10
(error)

---

### Post by jonasg on 2010-06-13
I don't know why but zsnes -ad oss works for me.

---

