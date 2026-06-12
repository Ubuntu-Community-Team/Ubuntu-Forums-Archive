---
title: "Doom 3 Sound Quality Issue on Breezy"
date: 2005-11-02
forum: Gaming &amp; Leisure
---

### Post by Gaming_Junkie on 2005-11-02
Sound in Doom 3 was running perfectly fine until a few days ago.  I started it up, and the sound's about a half second behind the picture and is making the video quality suffer also.  It also sounds choppy.  I ran the game in a terminal.  This is what it said:

------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.9
opened Alsa PCM device default for playback
device buffer size: 30105 frames ( 361260 bytes )
allocated a mix buffer of 49152 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 8.000000
...using GL_1.4_texture_lod_bias
...using GL_EXT_shared_texture_palette
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/ben/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: May 10 2005
Initializing event system
...472 event definitions
Initializing class hierarchy
...142 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2079.47 MHz
Compiled 'removeInitialSplineAngles': 2000.1 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67866, 1357320 bytes
   Functions: 2108, 250452 bytes
   Variables: 147244 bytes
    Mem used: 2478772 bytes
 Static data: 2277552 bytes
   Allocated: 3284208 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 16700
512 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.6
256 MB Video Memory
Async thread started
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei failed: Broken pipe
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Broken pipe
preparing audio device for output
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 3762 out of 4096
snd_pcm_writei short write: 1881 out of 3072
snd_pcm_writei short write: 1881 out of 3072
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 3072 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
guid set to WdzcnUkXRog
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable

It goes on to repeat those last few lines many many times, until I just exited the game.  What do I need to do to get the sound back to where it was?  

I'm wondering if there's a way where I don't have to run 'killall esd' every time I want to run the game in order to have sound, also.  I know I somehow got that to work just fine on Hoary.  After switching to Breezy, I haven't quite fixed my sound problems yet.

Thanks.

---

### Post by Gaming_Junkie on 2005-11-03
I fixed the problem.  I went back to my sound files and changed them back to where they were when I installed Breezy.  My sound system selectors are as follows:  ALSA for sound output, and Silence for source.  This seems to work well.

Doom 3 sound is now back to normal.

---

### Post by Zyphrexi on 2005-11-06
eh i'm having that prob too (on dapper though), what did you do?

---

### Post by gpw797 on 2005-11-07
I changed sound in doom config to OSS and it fixed mine.. works great now  :)

---

### Post by Gaming_Junkie on 2005-11-07
[QUOTE=Zyphrexi]eh i'm having that prob too (on dapper though), what did you do?[/QUOTE]

I had screwed with the audio settings, namely creating an asound.conf file.  What I did to fix this problem is just simply erase the asound.conf file.  In order to do that, type in this command:  sudo gedit /etc/asound.conf
After getting there, simply erase the file and save.  It will bring back the original settings for the most part.  After all, asound.conf isn't a default file.

After that, I changed my sound settings to:
Output: ALSA
and Source:  Silence

Doom 3 settings are at ALSA.  Seems to work just great.

Oh, and before I play, I type 'sudo killall esd' into the terminal.

Still not sure how not to have to type that in before I play...

Sorry for the late reply.

---

### Post by dbloom on 2005-11-10
Gaming_Junkie, how did you set the "source" to "Silence"?  i've been having the same sound issue.  i just can't find where to set this...

thx!

---

### Post by Gaming_Junkie on 2005-11-16
[QUOTE=dbloom]Gaming_Junkie, how did you set the "source" to "Silence"?  i've been having the same sound issue.  i just can't find where to set this...

thx![/QUOTE]

Under Multimedia Systems Selector, right under where it says default source.  Click on the dropbox and select silence.

---

### Post by Ranime on 2005-11-19
you can also use this script to put esd to sleep:
```

esdctl off
sleep 2
doom3
esdctl on

```

paste it in a text editor (gedit e.g.) and save it as *doom3.sh* in your home directory.

from a terminal you just type
```
$ sh doom3.sh
```
And the game will run, putting esd to sleep first. when you exit the game, esd will be restored to normal.

This code can also be used for games like Quake and SDL based games.

If you want to make a starter, just put *sh /home/username/doom3.sh* in the command field.

*Happy fraggin'*
:cool:

---

### Post by Zingam on 2005-11-20
how do I get esdctl command?

---

### Post by Ranime on 2005-11-27
Try this howto:
[http://www.ubuntuforums.org/showthread.php?t=79959](http://www.ubuntuforums.org/showthread.php?t=79959)

;)

---

