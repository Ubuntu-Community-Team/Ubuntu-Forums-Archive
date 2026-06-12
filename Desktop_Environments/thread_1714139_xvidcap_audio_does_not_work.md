---
title: "xvidcap audio does not work"
date: 2011-03-25
forum: Desktop Environments
---

### Post by drdigital on 2011-03-25
Hello every one,
after very very long time searching for good screen recorder I found xvidcap and I tried it. It works fine except it does not record sound.

i issued the command xvidcap --audio yes , I get this message

Error accessing sound input from /dev/dsp
Sound disabled!

any ideas ??

---

### Post by drdigital on 2011-03-26
First time for me to wait all this time. 

has any one have a solution ???

---

### Post by vezolmi on 2011-03-26
I have the same problem. I've tried xvidcap from months ago in different distros, with different options, ... always withous success with the sound.

The last unsuccessful ones I've tried:

[LIST]
[*]Open it from terminal with this command: xvidcap --audio_in /dev/audio (read in [http://writkas.wordpress.com/2010/11/03/problema-sonido-xvidcap/](http://writkas.wordpress.com/2010/11/03/problema-sonido-xvidcap/))
[*]Enter this command from terminal before xvidcap: sudo modprobe snd-pcm-oss (read in [http://www.rationalplanet.com/2009/12/xvidcap-in-fedora-11-error-accessing-sound-input-from-devdsp/](http://www.rationalplanet.com/2009/12/xvidcap-in-fedora-11-error-accessing-sound-input-from-devdsp/))
[/LIST]

---

### Post by vezolmi on 2011-03-27
I've got the solution!!!!: [http://ubuntu-cosillas.blogspot.com/2010/11/xvidcap-grabaciones-de-escritorio-una.html](http://ubuntu-cosillas.blogspot.com/2010/11/xvidcap-grabaciones-de-escritorio-una.html) :

1. Uninstall xvidcap in Synaptic
2. Install xvidcap from [http://sourceforge.net/projects/xvidcap/files/xvidcap/1.1.7/xvidcap_1.1.7jaunty_i386.deb/download](http://sourceforge.net/projects/xvidcap/files/xvidcap/1.1.7/xvidcap_1.1.7jaunty_i386.deb/download)
3. Lock the installed version in Synaptic
4. Install pavucontrol in Synaptic (Needed in Ubuntu 10.04 but not in Linux Mint 10: already present)
5. Open the program with padsp xvidcap
6. Click on the recording button (red circle)
7. Run pavucontrol, go to the Recording tab and there choose Monitor of Analog Stereo Internal Audio

Done!!

To record with sound, the program has always to be run with padsp xvidcap (for example from ALT+F2). To run it always like that from the menu: run alacarte, go to Sound and video, then to XVidCap Screen Capture, Properties and where it says Command put padsp xvidcap.

[ I would add this: ]

The stated is to record the system sound, that is, the one coming out of the speakers, that can be of a song or movie of our hard drive or pendrive played by Totem, of a Flash music video of a website played by Firefox, ...

Nevertheless, sometimes it can be necessary to record the microphone sound, for example if we want to make a videotutorial to explain how a program works. In this case we put xvidcap in recording state, run pavucontrol and in the Recording tab we put Analog Stereo Internal Audio (without  "Monitor of" ahead).

If we only want to record sound (without video) we can run from ALT+F2 gnome-sound-recorder. The first time probably it will be configured to record from the microphone. To record the system sound we run with ALT+F2 gnome-volume-control, go to the Hardware tab and in Profile we put Analog Stereo Output (it's also possible to do this running pavucontrol and using the Configuration tab).

But when we finish we have to put again Analog Stereo Duplex in the Profile of Hardware of gnome-volume-control (or of Configuration of pavucontrol), so we can still choose the origin of the sound when recording with xvidcap.

NB: sometimes, to change from Analog Stereo Duplex to Analog Stereo Output it may be necessary to change first to Off, close, open again and then change finally to Analog Stereo Output. The same for the opposite change. If not, the computer may "not notice" that we have applied the change.

---

### Post by vezolmi on 2011-03-27
drdigital: if the solution of my last post works for you (I hope), it would be good that you marked the thread with [SOLVED], to help more people finding the solution. I think you can do it from "Thread Tools" (up-right).

---

### Post by vezolmi on 2011-03-28
I've found a solution for 64 bits. As my Ubuntu is of 32 bits I haven't tested it, but it looks good: [http://angel-de-vicente.blogspot.com/2011/03/screencasts-with-xvidcap-in-ubuntu-1004.html](http://angel-de-vicente.blogspot.com/2011/03/screencasts-with-xvidcap-in-ubuntu-1004.html) :

In order to install it in my x86_64 system I just have to use the --force-architecture option to the dpkg -i command.

user@host:~/Desktop$ sudo dpkg --force-architecture -i xvidcap_1.1.7jaunty_i386.deb 

But when trying to run it I see that there are some i386 libraries missing. In order to easily install them I use the getlibs script.

user@host:~/Desktop$ padsp xvidcap
xvidcap: error while loading shared libraries: libtheora.so.0: cannot open shared object file: No such file or directory

user@host:~/Desktop$ getlibs /usr/bin/xvidcap

--------------------------------------------

About getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by vezolmi on 2011-03-28
Another option, not to have to change once and again between Analog Stereo Duplex and Analog Stereo Output neither limit the sound source for xvidcap, is to leave Analog Stereo Duplex and use also pavucontrol when we want to change the source of the sound for gnome-sound-recorder. Like the stated for padsp xvidcap, to change where we want to record the sound from, we put gnome-sound-recorder recording, open pavucontrol and in the Recording tab we put the desired option. In this case there is no need to use padsp (xvidcap needs it because it was designed for OSS. What padsp does is to connect OSS with PulseAudio, as shown in [http://linux.die.net/man/1/padsp](http://linux.die.net/man/1/padsp)).

---

### Post by vezolmi on 2011-04-15
baumtopf has found a problem in [http://ubuntuforums.org/showthread.php?t=1714402](http://ubuntuforums.org/showthread.php?t=1714402) :
After a video is recorded xvidcap offers to play it immediately. But if you click on the "Play" button the video is not reproduced.

This problem happens at least in Ubuntu 10.04 because by default it doesn't have installed mplayer, the program that xvidcap uses to play the videos when pressing on the stated button.

There are 2 solutions:

a) Install mplayer from Synaptic.
or
b) Go to preferences (right clicking on the name of the file, for  example test-0000.mpeg, and then cliking on Preferences), then to the  Commands tab, and then in the "Multi-Frame Capture Commands"' "Playback  Command" replace mplayer with totem and click on OK. Then right click  again on the name of the file and click on "Save preferences".

---

### Post by burkestar on 2011-04-18
Here's simple fix that worked for me.  

In XVidCap edit preferences (by right clicking on test-0000.mpeg button), and under "Multi-Frame" tab change the Audio Settings input device from "/dev/dsp" to "/dev/snd".  After clicking OK make sure to save preferences (by right clicking on test-0000.mpeg button again).  Restart xvidcap and it should work!

Cheers!

---

### Post by vezolmi on 2011-04-20
Thanks, burkestar.

Your proposal doesn't work for me.

The solution that works for me is explained above, in my second post in this thread.

Regards

---

### Post by valezero on 2011-07-20
Hello Vezolmi and all with no audio
Here is a video I followed that**[COLOR=black] fixed the problem of[/COLOR][COLOR=black] Xv[/COLOR]idCap (desktop recorder) not having audio**.
 
[COLOR=Blue][http://www.youtube.com/watch?v=kqKZ8wyP9ow](http://www.youtube.com/watch?v=kqKZ8wyP9ow)[/COLOR] 

 It's the only one that worked for me. I don't know why it isn't easier to find.
I'm running Ubuntu 10.10 maverick meerkat on a Sony Vaio VGN-NS190J with dual boot (Windows on the other side which will soon be deleted!!!) :P

---

