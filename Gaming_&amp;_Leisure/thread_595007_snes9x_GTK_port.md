---
title: "snes9x GTK port"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by Juan_VCS on 2007-10-28
[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874&sid=f379151c5033320bcabc9bd1c85a7d1c](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874&sid=f379151c5033320bcabc9bd1c85a7d1c)

Just tried it and it seems to work great! (with opengl support and all)

Don't be fooled by the prefs screen the second time you run it, the options are actually saved. *Edit: deleted the xml config file and now they seem to work properly.*

---

### Post by cookies on 2007-10-28
Cool! 

I thought Snes9x died, but this is awesome! Much better than gsnes9x.

---

### Post by nerdy_girlscout on 2008-02-05
From what I've tried, this port is just about perfect! I even removed ZSNES now since this is so good. I would kindly like to request this to be added to the ubuntu repos as fast as possible :D

---

### Post by mister_k81 on 2008-02-06
OK, so I just tried it out, and I have to say that it's a huge improvement over the Snes9x emulator that is already in the repositories. Everything seems to work flawlessly for me so far, I might even replace zsnes with this one.

---

### Post by &#12465;&#12452;&#12488; on 2008-02-19
Oh man, this improved snes9x a lot. ZSNES still is better, but this GUI is great; at least now there's a good alternative on the 64-bit platform! Hopefully this'll make the repositories.

---

### Post by grossaffe on 2008-02-19
> **&#12465 said:**
> Oh man, this improved snes9x a lot. ZSNES still is better, but this GUI is great; at least now there's a good alternative on the 64-bit platform! Hopefully this'll make the repositories.

can someone help me figure out how to get this to work in Gutsy Gibbon?  I'm still pretty new to linux.  i downloaded the pre-compiled binary with GTK and openGL support, but the program never even appears to attempt to run when i try to open a rom through it.

---

### Post by mister_k81 on 2008-02-19
> **grossaffe said:**
> can someone help me figure out how to get this to work in Gutsy Gibbon?  I'm still pretty new to linux.  i downloaded the pre-compiled binary with GTK and openGL support, but the program never even appears to attempt to run when i try to open a rom through it.

You might need to install the portaudio dependency. You can find  it by opening up the Synaptic Package Manager and  doing a search for libportaudio.

---

### Post by grossaffe on 2008-02-20
> **mister_k81 said:**
> You might need to install the portaudio dependency. You can find  it by opening up the Synaptic Package Manager and  doing a search for libportaudio.

I think its already installed (in the Synaptic Package Manager, its has "18.1-6" under the "Installed Version" tab)

---

### Post by &#12465;&#12452;&#12488; on 2008-02-20
If you run the application via a terminal, perhaps you'll see what's causing the crash by the output.

---

### Post by grossaffe on 2008-02-20
> **&#12465 said:**
> If you run the application via a terminal, perhaps you'll see what's causing the crash by the output.


how is the terminal command structured for it?

---

### Post by mister_k81 on 2008-02-20
> **grossaffe said:**
> I think its already installed (in the Synaptic Package Manager, its has "18.1-6" under the "Installed Version" tab)

Ah... you need to look for the version marked 19+ I think? It should be called libportaudio2 in the repositories.

> **grossaffe said:**
> how is the terminal command structured for it?

you can start it in the terminal by typing: 

/home/your-user-name/snes9x-directory(or wherever it is located)/snes9x-gtk

---

### Post by grossaffe on 2008-02-20
> **mister_k81 said:**
> Ah... you need to look for the version marked 19+ I think? It should be called libportaudio2 in the repositories.



you can start it in the terminal by typing: 

/home/your-user-name/snes9x-directory(or wherever it is located)/snes9x-gtk

where does the ROM fit into it?  or does this version actually have a gui interface that can locate them after running?

edit: ok, i ran it in terminal, apparently i'm missing libgtksomething:
```
error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by DoktorSeven on 2008-02-20
> **grossaffe said:**
> where does the ROM fit into it?  or does this version actually have a gui interface that can locate them after running?

edit: ok, i ran it in terminal, apparently i'm missing libgtksomething:
```
error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

```

**sudo apt-get install libgtkglext1**

---

### Post by grossaffe on 2008-02-20
that one did the trick, thank you.

---

### Post by GSZX1337 on 2008-02-20
I keep getting an error when I compile this.

```

gszx1337@G-Man:~/Desktop/snes9x-1.51-src$ make install
Installing to NONE

```

I didn't get any errors during make.

---

### Post by RemmyLee on 2008-02-20
There is no install target in the make script. Just move the file wherever you want it.

---

### Post by grossaffe on 2008-02-21
well now that i've got it working, i can honestly say that i think this is the best SNES emulator working in linux.  I was upset at first because it was running at half speed, but then i discovered that i just didn't have openGL enabled.  once i turned that on, it ran perfectly smooth.  ZSNES, on the other hand, usually starts to give me audio problems.

---

### Post by GSZX1337 on 2008-02-21
I don't have any audio in SNES9x GTK. I installed the latest libportaudio in the Synaptic Package Manager, but I still don't have any audio.

---

### Post by zerhacke on 2008-02-21
Was ist dis?  I thought snes9x died long ago... this is a pleasurable surprise.

I don't think I'm going to remove zsnes yet, but depending on how it works with my admittedly crappy shared memory architecture video adapter I just may.

---

### Post by grossaffe on 2008-02-21
> **GSZX1337 said:**
> I don't have any audio in SNES9x GTK. I installed the latest libportaudio in the Synaptic Package Manager, but I still don't have any audio.

try libportaudio2

---

### Post by GSZX1337 on 2008-02-21
> **grossaffe said:**
> try libportaudio2

I tried that, but I got a message saying "A later version is already installed."

EDIT: Turned out a restart fixed it. :P Thanks anyway.

---

### Post by GSZX1337 on 2008-02-28
I cannot seem to enable OpenGL. I have compiled it according to the creator's directions.

```
snes9x-1.51-src$ ./configure --with-gtk --with-opengl
```

I'm pretty sure that I have all the dependencies. I'll check as soon as I get back to my Ubuntu 'puter.

---

### Post by grossaffe on 2008-02-29
> **GSZX1337 said:**
> I cannot seem to enable OpenGL. I have compiled it according to the creator's directions.

```
snes9x-1.51-src$ ./configure --with-gtk --with-opengl
```

I'm pretty sure that I have all the dependencies. I'll check as soon as I get back to my Ubuntu 'puter.

did you go into the options and enable OpenGL from there?  i downloaded the pre-compiled version with openGL support but it was off by default.

---

### Post by GSZX1337 on 2008-02-29
> **grossaffe said:**
> did you go into the options and enable OpenGL from there?  i downloaded the pre-compiled version with openGL support but it was off by default.

The OpenGL option is greyed out. I can't click on it.

---

### Post by GSZX1337 on 2008-02-29
Bump.

---

### Post by mister_k81 on 2008-02-29
Do you have libgtkglex1-dev installed? Other then that I dunno what the problem could be. :???:

---

### Post by grossaffe on 2008-02-29
> **GSZX1337 said:**
> The OpenGL option is greyed out. I can't click on it.

in that case, why don't you try just downloading the pre-compiled version with openGL support?  how much of advantage could it be to compile it yourself?

---

### Post by GSZX1337 on 2008-02-29
> **mister_k81 said:**
> Do you have libgtkglex1-dev installed? Other then that I dunno what the problem could be. :???:
I have it installed, but I'm not able to use OpenGL.

> **grossaffe said:**
> in that case, why don't you try just downloading the pre-compiled version with openGL support?  how much of advantage could it be to compile it yourself? It says it's i386, I'm running the 64-bit version of Ubuntu Gutsy Gibbon.

---

### Post by grossaffe on 2008-03-01
> **GSZX1337 said:**
> I have it installed, but I'm not able to use OpenGL.

 It says it's i386, I'm running the 64-bit version of Ubuntu Gutsy Gibbon.

ah, i see.  alrighty then, proceed.

---

### Post by GSZX1337 on 2008-03-01
I figured out how to compile ZSNES for my version [here]("http://ubuntuforums.org/showthread.php?t=588744"). I will be sure to email or PM the creator of the port my problem so that he may fix it in case others are having it. Thank you all for helping me, though.

---

### Post by XSP on 2008-03-01
I was having a similar problem when I first attempted to compile it. For some reason, a configuration option seemed to have been cached when I first configured it without OpenGL support.

I had to redownload the source and ./configure --with-gtk --with-opengl --with-joystick && make

After that it was working great.

---

### Post by vvlist on 2008-03-02
Does anyone know if there is a precompiled deb for gutsy for this?

---

### Post by grossaffe on 2008-03-02
> **vvlist said:**
> Does anyone know if there is a precompiled deb for gutsy for this?

check the link, there's a precompiled version there to download.

---

### Post by vvlist on 2008-03-03
> **grossaffe said:**
> check the link, there's a precompiled version there to download.

How dumb of me. I missed that link for some reason. Thanks!

---

### Post by grossaffe on 2008-03-07
> **GSZX1337 said:**
> I cannot seem to enable OpenGL. I have compiled it according to the creator's directions.

```
snes9x-1.51-src$ ./configure --with-gtk --with-opengl
```

I'm pretty sure that I have all the dependencies. I'll check as soon as I get back to my Ubuntu 'puter.

bump, now that i have 64-bit ubuntu on my laptop, i'm interested in seeing this.

---

### Post by grossaffe on 2008-03-14
i've been trying to compile it myself now on my 64-bit system, but i'm having a problem with the ./configure command, its telling me:
```
christian@christian-laptop:~/Desktop/snes9x-1.51-src$ ./configure --prefix=/usr --with-gtk --with-opengl
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by Omnios on 2008-03-14
this sounds interesting but how do you get your roms to the computer?

---

### Post by GSZX1337 on 2008-03-14
> **Omnios said:**
> this sounds interesting but how do you get your roms to the computer?

Can't ask that here.

---

### Post by Omnios on 2008-03-14
> **GSZX1337 said:**
> Can't ask that here.
 
K never mind.

---

### Post by DoktorSeven on 2008-03-14
Using this on Hardy has revealed one minor problem on my system, but I'm not sure if it's related to the program itself or the unstable nature of prerelease Hardy; just putting this out in case someone else runs into it or the issue continues.

On first run (from either compiled or binary form) going to the Preferences window seems to attempt to open the preferences, then that window disappears, leaving the main window open yet frozen.  Apparently the preferences window is still around, but just hidden.  

Pressing Escape will "close" this hidden window, unfreezing the main window.  All future attempts to open the preferences window succeeds, until you close and rerun the app where it happens again.

Just putting that out there for anyone that might have the problem.

---

### Post by grossaffe on 2008-03-18
i think i'm having some dependency issues trying to compile it.  first issues was SDL, but i got that cleared up, now its Xv libs or something like that.

---

### Post by mrThefter on 2008-04-29
For those whom it may concern...
Hardy uses pulseaudio now; snes9x uses OSS and that needs to be routed through pulse. "padsp snes9x-gtk" to get sound.

---

### Post by grossaffe on 2008-04-29
> **mrThefter said:**
> For those whom it may concern...
Hardy uses pulseaudio now; snes9x uses OSS and that needs to be routed through pulse. "padsp snes9x-gtk" to get sound.

so does that mean it needs to be recompiled?

---

### Post by mrThefter on 2008-04-29
No. Just run it with padsp prepended.
$ padsp snes9x-gtk
That should make it work just fine.

---

### Post by grossaffe on 2008-04-29
is padsp another program i'll need?  and i guess i'll need to write a script if i want an executable, won't i?

---

### Post by mrThefter on 2008-05-01
No. padsp comes installed with pulseaudio. As for executable, launchers and menu items can just be edited.
padsp applies for all oss-based sound software.

---

### Post by Juan_VCS on 2008-06-07
[Netplay support added](http://www.snes9x.com/phpbb2/viewtopic.php?p=24203#24203)
I really hope this makes its way into the official repos for 8.10.

---

### Post by mister_k81 on 2008-06-07
I'm not sure whats going on, but I'm having problems with the latest version. I'm getting low FPS and high CPU usage when running it in OpenGL mode. I thought I fixed the problem by un-checking the "use pixel-buffer objects" box under the OpenGL options, but it seemed to have returned when I closed the emulator and opened it back up again... :( 

Running it in Xvideo mode seems to work fine though, even though it filters everything and I can't seem to turn that feature off.  I also did try netplay though, by connecting it to a Windows Vista laptop. It seemed to work pretty well. 

But, I guess I'll just stick to the older version that I was using (which was marked version 27), since OpenGL works fine there, and I probably wouldn't use netplay much anyway.

---

### Post by frenchn00b on 2008-06-07
> **Juan_VCS said:**
> [http://www.snes9x.com/phpbb2/viewtopic.php?p=22874&sid=f379151c5033320bcabc9bd1c85a7d1c](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874&sid=f379151c5033320bcabc9bd1c85a7d1c)

Just tried it and it seems to work great! (with opengl support and all)

Don't be fooled by the prefs screen the second time you run it, the options are actually saved. *Edit: deleted the xml config file and now they seem to work properly.*

btw, does netplay, really works ??

---

### Post by doorknob60 on 2008-06-07
I love Zsnes due to it's GUI, but it has sound issues, so this might be my answer! The binary segfaulted for me so I'll go compile it later. EDIT: This is a keeper :) Thanks for showing me this

---

### Post by BearOso on 2008-06-11
> **mister_k81 said:**
> I'm not sure whats going on, but I'm having problems with the latest version. I'm getting low FPS and high CPU usage when running it in OpenGL mode. I thought I fixed the problem by un-checking the "use pixel-buffer objects" box under the OpenGL options, but it seemed to have returned when I closed the emulator and opened it back up again... :( 
Please try revision 32, and turn off (or leave off) the Allow non-power-of-two textures box in the OpenGL preferences. I received a similar bug report where NPOT textures were the slowdown problem, and this was the only big thing changed in OpenGL from 28+, so this will hopefully fix things for you.

As far as PBO performance drops are concerned, I've only ever seen Pixel-buffer objects improve the texture upload speed and reduce CPU usage in the machines I have available. Like NPOT, though, this may vary among OpenGL implementations, so you'll just have to experiment with it and its two formats.

---

### Post by mister_k81 on 2008-06-11
Thanks for the update BearOso, I really appreciate what you're doing with this port. :)

The problem seems to be fixed now. I did try running it with NPOT turned off and on to see if there were any noticeable differences,  the slowdown problem seems to be fixed in both cases... Hmmmm... I also tried wit Pixel-buffer objects enabled and disabled too, and there was no problem with that either, this time. 

I ran version 31 again right after that, to see it wasn't a Ubuntu/ latest kernel update that might have fixed this problem, and no, it still suffers from high CPU usage and slow frame rates.  So whatever the problem was, it's gone now.

---

### Post by braveerudite on 2008-06-12
woot this is great snes9x-, gtk - 1.51.33-1 was just release an hour ago.

go here: [https://launchpad.net/~bearoso/+archive](https://launchpad.net/~bearoso/+archive)

---

### Post by mister_k81 on 2008-06-19
> **Juan_VCS said:**
> [Netplay support added](http://www.snes9x.com/phpbb2/viewtopic.php?p=24203#24203)
I really hope this makes its way into the official repos for 8.10.

I just made a suggestion here to add it to the repos: 

[http://brainstorm.ubuntu.com/idea/10022/](http://brainstorm.ubuntu.com/idea/10022/)

I'm not sure if it will be much help... but vote anyway. :popcorn:

---

### Post by braveerudite on 2008-06-23
> **mister_k81 said:**
> I just made a suggestion here to add it to the repos: 

[http://brainstorm.ubuntu.com/idea/10022/](http://brainstorm.ubuntu.com/idea/10022/)

I'm not sure if it will be much help... but vote anyway. :popcorn:

Good job man.  I open an account just to be able to vote.

---

### Post by GSZX1337 on 2008-07-23
I cannot get audio working in SNES9X. I've tried setting it to use SDL, ASLA, and OSS.

Here's the terminal output:
```
gszx1337@G-Man:~$ snes9x-gtk %F
Reading config file /etc/snes9x/snes9x.conf
Starting sound
    --> (OSS)...No device info available.
    --> (ALSA : NVidia CK804: NVidia CK804 - IEC958 (hw:0,2))...Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1291
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->playback, outParams, self->primeBuffers, hwParamsPlayback, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1865
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1986
Failed (Invalid sample rate)
Couldn't initialize sound
Error opening: %F

```

---

### Post by BearOso on 2008-07-23
> **GSZX1337 said:**
> I cannot get audio working in SNES9X. I've tried setting it to use SDL, ASLA, and OSS.

Here's the terminal output:
```
gszx1337@G-Man:~$ snes9x-gtk %F
Reading config file /etc/snes9x/snes9x.conf
Starting sound
    --> (OSS)...No device info available.
    --> (ALSA : NVidia CK804: NVidia CK804 - IEC958 (hw:0,2))...Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1291
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->playback, outParams, self->primeBuffers, hwParamsPlayback, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1865
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1986
Failed (Invalid sample rate)
Couldn't initialize sound
Error opening: %F

```
Try turning up the playback rate in the sound preferences. Snes9x uses 32000hz as the default because that is what the SNES uses, but some sound cards and sound servers don't like it. Try the 44100hz or 48000hz settings.

---

### Post by Agentflit on 2008-07-26
I can't get the binary to run, I figure it's because I need libgtkglext1, but when I type "sudo apt-get install libgtkglext1" I get "E: Couldn't find package libgtkglext1" .... any ideas?

---

### Post by GSZX1337 on 2008-07-27
> **BearOso said:**
> Try turning up the playback rate in the sound preferences. Snes9x uses 32000hz as the default because that is what the SNES uses, but some sound cards and sound servers don't like it. Try the 44100hz or 48000hz settings.

The sound problem was a Linux problem, not an SNES9x problem. Thanks anyway though. ;)

> **Agentflit said:**
> I can't get the binary to run, I figure it's because I need libgtkglext1, but when I type "sudo apt-get install libgtkglext1" I get "E: Couldn't find package libgtkglext1" .... any ideas?

Try [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"), It'll find the appropriate libraries for you.

---

### Post by BigSilly on 2008-07-27
Excellent this. One of the best on Linux I say. It MUST go in the repos!

---

### Post by Agentflit on 2008-07-27
getlibs gave me this error:

"Package libgtkglext1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtkglext1 has no installation candidate"

:confused:

I'm running on a LiveCD by the way, would that make any difference?

---

### Post by GSZX1337 on 2008-07-27
> **Agentflit said:**
> getlibs gave me this error:

"Package libgtkglext1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtkglext1 has no installation candidate"

:confused:

I'm running on a LiveCD by the way, would that make any difference?

I'm not sure why you're getting this error, but I found libgtkglext1[here]("http://packages.ubuntu.com/feisty/libs/libgtkglext1") in the Ubuntu Package Search.

> **BigSilly said:**
> Excellent this. One of the best on Linux I say. It MUST go in the repos!

I second that, especially since new comers will want to stay with Add/Remove, and there isn't an SNES emulator for 64-bit currently.

---

### Post by Agentflit on 2008-07-30
I got it working by the way. Runs fantastic, just needed a couple libs. Thanks!

---

### Post by dadslayer on 2008-11-22
Hi guys,

Hope you can help me out with this. I've just installed this awesome port and gotta say that it works almost perfectly... almost, because it can't detect my gamepad's direction controls (nor its joystick controls), so I can't move (rest of buttons are working perfectly, though).

Any clues?

P.S.: sorry for bumping such an old thread.

---

### Post by grossaffe on 2008-11-22
so does that mean that you went in to the options where the control pad configuration was and tried to set the controls but it didn't work?

---

### Post by dadslayer on 2008-11-22
> **grossaffe said:**
> so does that mean that you went in to the options where the control pad configuration was and tried to set the controls but it didn't work?
Exactly. I only could set up control pad's buttons (A, B, X, Y, etc.). However, when I try to set up control pad's arrow keys (or its joystick) it won't detect them... :confused:

---

### Post by grossaffe on 2008-11-22
> **dadslayer said:**
> Exactly. I only could set up control pad's buttons (A, B, X, Y, etc.). However, when I try to set up control pad's arrow keys (or its joystick) it won't detect them... :confused:
Its probably a problem with your joystick driver thing.  I don't remember what you want to use, though.  maybe jstest?

---

### Post by dfreer on 2008-11-23
> **dadslayer said:**
> 
Hope you can help me out with this. I've just installed this awesome port and gotta say that it works almost perfectly... almost, because it can't detect my gamepad's direction controls (nor its joystick controls), so I can't move (rest of buttons are working perfectly, though).

Let me guess, you used jscalibrator/jscal/whatever?

[http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185](http://snes9x.com/phpBB2/viewtopic.php?p=25185#25185)
[http://ubuntuforums.org/showthread.php?t=729049](http://ubuntuforums.org/showthread.php?t=729049)
[http://board.zsnes.com/phpBB2/viewtopic.php?t=12253](http://board.zsnes.com/phpBB2/viewtopic.php?t=12253)

---

### Post by badfish69 on 2009-02-27
I am running the latest version on Intrepid. I have no sound. In console i get ```
Initializing sound...
    --> (OSS : /dev/dsp1, latency 32ms)...OK

```

---

### Post by mocha on 2009-03-02
> **badfish69 said:**
> I am running the latest version on Intrepid. I have no sound. In console i get ```
Initializing sound...
    --> (OSS : /dev/dsp1, latency 32ms)...OK

```

Try running it like this "pasuspender snes9x-gtk"

"pasuspender" causes pulseaudio to suspend temporarily while you're running it.  There is another pulseaudio utility called "padsp" which tries to wrap OSS apps in pulse, you can try that as well.  "aoss" is yet another wrapper that wraps OSS apps in Alsa.

---

### Post by cggaret on 2009-03-02
I had the same problem and fixed it by uninstalling jscalibrator, deleting the .joystick file in my home directory, and rebooting.  Hope this helps.

---

### Post by amano on 2009-03-29
Under Jaunty Jackalope (beta) I cannot get Snes9x-GTK only to run using the command [COLOR="Red"]padsp snes9x-gtk[/COLOR] and setting the snes9x sound driver to OSS.

---

### Post by mocha on 2009-03-29
> **amano said:**
> Under Jaunty Jackalope (beta) I cannot get Snes9x-GTK only to run using the command [COLOR="Red"]padsp snes9x-gtk[/COLOR] and setting the snes9x sound driver to OSS.

What about using pasuspender?  When I use pasuspender under Intrepid, snes goes to 100% CPU.  padsp was the only solution for me.  Hopefully we find a fix for this, as many of us will be upgrading soon.

---

### Post by barnacleboy on 2009-11-07
I've been using snes9x-gtk as my SNES emulator and it's fantastic, hopefully this bump will get more people using it. However I'm now having a problem with it.

On Karmic when I open snes9x-gtk the menu bar is missing. Apparently pressing escape toggles hiding/showing the menubar, I've tried this and it isn't appearing. I've re-installed but the problem persists. I've changed the default settings in the .xml file but that didn't work.

Ideas anyone? Please?

Edit: After re-installing building from source and re-starting in failsafe Gnome it's working again! Now for a little Final Fantasy 3 on a Sunday afternoon...

---

### Post by Vexmaster on 2010-01-19
OMG!! This works perfectly! No I can get rid of those other crappy SNES emulators.

TY! TY! TY!\\:D/\\:D/\\:D/\\:D/

---

### Post by dfreer on 2010-01-19
BTW, Snes9x just had a new release... comes with GTK+ support built in I believe:
[http://snes9x.com/phpBB2/viewtopic.php?t=4542](http://snes9x.com/phpBB2/viewtopic.php?t=4542)

---

### Post by BigSilly on 2010-01-21
> **dfreer said:**
> BTW, Snes9x just had a new release... comes with GTK+ support built in I believe:
[http://snes9x.com/phpBB2/viewtopic.php?t=4542](http://snes9x.com/phpBB2/viewtopic.php?t=4542)

Thanks very much for the heads up on this. Definitely one of my favourite emulators.

I've found Bearoso's PPA on LaunchPad. Would you consider this safe to add to Ubuntu? Thanks. :)

---

