---
title: "Doom 3"
date: 2005-07-20
forum: Gaming &amp; Leisure
---

### Post by immoral giant on 2005-07-20
I installed Doom 3 and copied over the pk4 files.

It seems to load up fine but then comes up with this error:

```

glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
Regenerated world, staticAllocCount = 0.
idRenderSystem::Shutdown()
Sys_Error: couldn't find game dynamic library

``` 

How do i fix this??

---

### Post by immoral giant on 2005-07-20
I just re ran the run file and it seems to have fixed that problem, but I have no sound.

I get sound in all other games and in the desktop

---

### Post by artinla on 2005-07-20
Are you running onboard sound?

I have had much better success with a SBLive or Audigy.

NVidia sound is a PITA.

Try killall ESD and then run the game.

---

### Post by immoral giant on 2005-07-20
No im running on a 5.1 SB.  I had tried killing ESD which fixes the problems with Enemy Territory, but not with Doom 3.

Also after i kill ESD, then reload it, my music doesnt play through Music Player.

---

### Post by artinla on 2005-07-20
Well, that is basically the exact same configuration that I am running.  I do not have to kill ESD and Doom3 runs perfectly.  

You should be able to run the game error free without any significant tweaking.  Are you running Doom3 in wine/cedega or using the native installer?

BTW, if the music that you are having trouble with is MP3, I installed mpg321 and things worked much better. FWIW.

Good luck

Art

---

### Post by immoral giant on 2005-07-21
I installed mpg321 but i see no difference on my system at all.  Is it a seperate player?

Doom 3 runs ok, it's a bit laggy compared to windows and it doesnt seem to write to the config file or put the serial on to the xpkey file.  So i have to manually type it in everytime, and still no sound with ESD or without ESD.

I tried through the shortcut and through the terminal.  ET only works through the terminal once ESD is stopped.

---

### Post by endy on 2005-07-21
Have you tried setting alsa up for doom 3 as mentioned in the faq?

[http://zerowing.idsoftware.com/linux/doom/#head-8a3e830015ce79941f7f69f6d5323d0e52ab126f](http://zerowing.idsoftware.com/linux/doom/#head-8a3e830015ce79941f7f69f6d5323d0e52ab126f)

I used the following if it's of any use:

```
// sound
seta s_alsa_pcm "surround51"
seta s_numberOfSpeakers "6"
``` 

If this doesn't work, paste the output from the console so we can see the exact error :)

---

### Post by synap on 2005-08-05
doom3 +set s_alsa_pcm surround51 got sound working for me.
havent tested 
doom3 +set s_alsa_pcm surround51 +set s_numberOfSpeakers 6
yet.

The game is crazy dark, Im assuming it was designed that way.

---

### Post by drizek on 2005-08-05
ya, its meant to be dark

---

### Post by immoral giant on 2005-08-05
when i try to get libesd-alsa0.  I get this:

```
root@ubuntu:/home/james # sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate
```

---

### Post by immoral giant on 2005-08-05
Don't worry, i tried +set s_driver oss instead.

Now i have sound...but a low framerate.

Is that due to the engine on linux or the ati drivers?

I got 37.7 fps in the timedemo on 800x600 at low settings, no shadows.
On XP i get 50 fps in the timedemo on 1024x768 at high settings, no shadows.

EDIT:  I decided to play anyway through the game and was surprised to see, i was getting 60fps (maybe well over due to the cap) in normal gameplay.  So i put the settings to 1024x768 on medium settings, then just before i ran the timedemo i saw in the console that it was autodetecting my vram as 96mb, although i have clearly told it to see 128 in the config file, now im getting 40fps on the timedemo.

---

### Post by drizek on 2005-08-05
[QUOTE=immoral giant]Don't worry, i tried +set s_driver oss instead.

Now i have sound...but a low framerate.

Is that due to the engine on linux or the ati drivers?

I got 37.7 fps in the timedemo on 800x600 at low settings, no shadows.
On XP i get 50 fps in the timedemo on 1024x768 at high settings, no shadows.

EDIT:  I decided to play anyway through the game and was surprised to see, i was getting 60fps (maybe well over due to the cap) in normal gameplay.  So i put the settings to 1024x768 on medium settings, then just before i ran the timedemo i saw in the console that it was autodetecting my vram as 96mb, although i have clearly told it to see 128 in the config file, now im getting 40fps on the timedemo.[/QUOTE]
 no, ati just sucks ;)

youre lucky it even works at all on an ati card.

---

### Post by immoral giant on 2005-08-05
My card does not suck.  runs fine on windows, must be either drivers in linux (which ive heard ati lack in that department) or the doom 3 engine on linux.

---

### Post by drizek on 2005-08-05
[QUOTE=immoral giant]My card does not suck.  runs fine on windows, must be either drivers in linux (which ive heard ati lack in that department) or the doom 3 engine on linux.[/QUOTE]

I never said ATI cards suck. They are actually pretty good. But ATI the company sucks cause their linux support is crap.

---

### Post by kemosabe79 on 2005-10-05
Ive tried everything here (and everywhere else on the net) and I still get no sound from Doom3. I get this message everytime:

----------- OSS Sound Initialization -----------
opened sound device '/dev/dsp'
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
WARNING: mmap 32768 bytes on device /dev/dsp failed: Input/output error

close sound device
WARNING: sound subsystem disabled

-------------------------------------------------------

Im using N-force2 onboard sound. Should I update my Nvidia chipset drivers and try again?

edit: Oops I forgot to mention I have sound in everything else.

---

### Post by seethru on 2005-10-05
[QUOTE=kemosabe79]Ive tried everything here (and everywhere else on the net) and I still get no sound from Doom3. I get this message everytime:

----------- OSS Sound Initialization -----------
opened sound device '/dev/dsp'
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
WARNING: mmap 32768 bytes on device /dev/dsp failed: Input/output error

close sound device
WARNING: sound subsystem disabled

-------------------------------------------------------

Im using N-force2 onboard sound. Should I update my Nvidia chipset drivers and try again?

edit: Oops I forgot to mention I have sound in everything else.[/QUOTE]
try running doom3 through aoss

```
aoss doom3
```

---

### Post by kemosabe79 on 2005-10-05
[QUOTE=seethru]try running doom3 through aoss
```
aoss doom3
```[/QUOTE]
Command not found. Any other suggestions? 

I also forgot to mention in my other post that I'm using the Linux client.

---

### Post by seethru on 2005-10-05
[QUOTE=kemosabe79]Command not found. Any other suggestions? 
I also forgot to mention in my other post that I'm using the Linux client.[/QUOTE]
sudo apt-get install alsa-oss then try aoss doom3

---

### Post by kemosabe79 on 2005-10-06
Ok, Im running it through aoss. Now I have sound, but its just crackling really bad.

---

