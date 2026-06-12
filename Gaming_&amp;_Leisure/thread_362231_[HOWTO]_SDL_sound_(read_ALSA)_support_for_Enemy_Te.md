---
title: "[HOWTO] SDL sound (read: ALSA) support for Enemy Territory"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by nullkey on 2007-02-15
**[UP-TO-DATE INFORMATION IS AVAILABLE HERE](http://nullkey.ath.cx/~stuff/et-sdl-sound/)**

**about**
et-sdl-sound provides SDL-based replacement for deprecated OSS-based sound systems of Enemy Territory, Return to Castle Wolfenstein and Quake III Arena. To put it short, et-sdl-sound is a working ALSA support hack for ET, RTCW and Q3 (and all mods for those binaries).

 Since modifying binary directly makes game unplayable, this is accomplished via replacing standard sound system functions in run-time by forcing dynamic linker to load an additional dynamic library to the process (so-called LD_PRELOAD trick).

This library currently supports **ET 2.60b, ET 2.60, ET 2.56, ET 2.55, RTCW SP 1.41, RTCW MP 1.41 Quake3 1.31, Quake3 1.32, Quake3 1.32b and Quake3 1.32c**.

**installation and usage**
Make sure you have core SDL library installed
```
sudo apt-get install libsdl1.2debian-alsa
```

[et-sdl-sound](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz) script contains everything you need to launch Enemy Territory with SDL audio support. The fastest way to install the script is to execute following command line:
```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
```
Now you can start Enemy Territory with SDL sound support by running ./et-sdl-sound

There are also specific launcher scripts for RTCW SP ([wolfsp-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/wolfsp-sdl-sound.gz)), RTCW MP ([wolf-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/wolf-sdl-sound.gz)) and Quake 3 ([quake3-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz)). 

**[download](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.tar.gz)**
Please use this download link as it contains the most recent version.

PS. I posted this first to gentoo forums but then tought that ubuntu users could also find this useful... :)

---

### Post by Xzallion on 2007-02-16
Neither one worked for me.  The static version gave a segmentation fault, and the first one said I don't have libSDL_sound or something or another.

---

### Post by nullkey on 2007-02-16
> **Xzallion said:**
> Neither one worked for me.  The static version gave a segmentation fault, and the first one said I don't have libSDL_sound or something or another.
Could you please provide some information about your system? Giving output of following commands would help. And does "et-sdl-sound.so" segfault if you install libsdl-sound1.2 package?
```

strings /path/to/et.x86 | grep "ET 2"
uname -a
gcc -v

```

---

### Post by nullkey on 2007-02-16
Oops, it seems that I don't need to link it with SDL_sound. I attached the updated version which **does not need SDL_sound**. Download link is also updated. I hope this solves some problems :)

---

### Post by Yeeha on 2007-02-17
worked for me without any problems.

---

### Post by jrohde on 2007-02-17
Hi,

I must be missing something. If I run:

LD_PRELOAD=/tmp/et-sdl-sound/et-sdl-sound.so /home/jakob/enemy-territory/et.x86

I get this response:

 "You are not running Enemy Territory 2.60b!"

I don't know exactly what version I'm running, but it should be the newest.

Any suggestions?

Jakob

---

### Post by nullkey on 2007-02-18
> **jrohde said:**
> 
 "You are not running Enemy Territory 2.60b!"

Please update your et.x86. You can get the update from **[3D Gamers](http://www.3dgamers.com/dlselect/games/wolfensteinet/et-2.60b.zip.html)** for example. 2.60b just fixes some buffer overflows and actual protocol is not modified, so servers don't make difference between 2.60 and 2.60b (in fact there are even 2.60c and 2.60d for OS X :) ).

If you face some PunkBuster kicks after upgrade, you should update PunkBuster by copying **[pbsec.htm](http://www.punkbuster.com/downloads/et/pbsec.htm)** to /path/to/et/pb/ and **[lc001298.htm](http://www.punkbuster.com/downloads/et/lc001298.htm)** & **[la001377.htm](http://www.punkbuster.com/downloads/et/la001377.htm)** to /path/to/et/pb/htm

---

### Post by octavio on 2007-02-18
Hi, i have don all you say but i get this error.

```

$> LD_PRELOAD=/home/octavio/Desktop/et-sdl-sound/et-sdl-sound.so /usr/local/games/enemy-territory/et.x86

...

----------------------
271 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?

```

When i run et there is no problem, but no sound.

Do you know what it may be? And how to get this work of course?

Thanks.

---

### Post by nullkey on 2007-02-18
> **octavio said:**
> 
When i run et there is no problem, but no sound.

Do you know what it may be? And how to get this work of course?

I should have made myself a little bit more clear about this. Every time you want to use the new SDL sound system, you should run ET with provided LD_PRELOAD... -command. To make this easier, make following script and put it somewhere safe, for example where you put et-sdl-sound.so.
```

#!/bin/bash

# path to enemy territory installation directory
cd /path/to/enemy-territory/

# path to et-sdl-sound(-static).so
export LD_PRELOAD=/path/to/et-sdl-sound(-static).so

./et.x86 $*

unset LD_PRELOAD

```
Then make the script executable and point your ET shortcut to this script.

```

Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?

```
That means your working directory is not the directory where you have installed Enemy Territory. That's why my script has line "cd /path/to/enemy-territory/".

---

### Post by octavio on 2007-02-18
Now it loads at first. But i still have no sound.

Sound works fine in my system. But i'm getting mad with this game.

Thank you very much.

I hope anybody find a solution someday.

---

### Post by nullkey on 2007-02-18
> **octavio said:**
> Now it loads at first. But i still have no sound.

Sound works fine in my system. But i'm getting mad with this game.
I'm still willing to help ;). I can think a few factors that can affect the sound (or it's absence).

Are you running a sound server (like arts or esd) in the background blocking access to the sound device from anyone but applications using an API provided by that server? If "mplayer -ao alsa somefile" produces sound, this is not the case.

It might also be problem in SDL libraries. Does any other application using SDL audio (neverball for example) work? If et-sdl-sound is working properly, the following text should appear in the console output
```

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
WARNING: sdlmixsamps wasn't a power of two (18800) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x95ddbb0 dma buffer
No background file.
----------------------

```

And please post the whole console output of Enemy Territory.

---

### Post by octavio on 2007-02-18
i have checked my daemons, and this time the sound works.

This is the output:

```


------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "dsp"
WARNING: sdlmixsamps wasn't a power of two (20480) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x96de140 dma buffer
No background file.
----------------------

```

Thanks really much. Is great to be in a comunity with people like you. 

I'm going to check if it works propertly and post here the results.

Thanks.

---

### Post by octavio on 2007-02-18
As long as i have been useing this, the sound works great.

As i said, thank you very much.

---

### Post by nullkey on 2007-02-19
> **octavio said:**
> 
```

...
SDL audio driver is "dsp"
...

```
It seems like your SDL libs prefer OSS over ALSA, so you gain currently nothing from this library. I will look at this later today.

Edit: Does it still use OSS/dsp if you use the "et-sdl-sound-static.so"?

---

### Post by octavio on 2007-02-19
The result that i posted before is with static on. But here you have two executions.

The results of both excutions:

```

$> with_static.sh

...
------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "dsp"
WARNING: sdlmixsamps wasn't a power of two (20480) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x96fd340 dma buffer
No background file.
----------------------
...


```

```


$> without_static.sh

------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
SDL audio driver is "(UNKNOWN)"
SDL_OpenAudio() failed: No available audio device
------------------------------------



```

---

### Post by nullkey on 2007-02-19
> **octavio said:**
> 
```

...
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
...

```
Looks bad, very bad :( . Your alsa installation is either broken or your alsa library is too old. Quick googling with that error message bring up [this thread about flash 9 ALSA problems](http://ubuntuforums.org/showthread.php?t=314718). You could try some of the solutions posted to that thread, especially:

> **CPtAJ said:**
> 
The fix is this: Use the asoundconf utility...
```
asoundconf list
asoundconf set-default-card <card name>
```

Replace the <card name> with the right card out of the ones shown by the list command. It should make everything in ubuntu go to that sound card first.

Hope that helps some of you...

Another trick mentioned was to "mv /etc/asound.conf /etc/asound.conf.bak". Of course if that does not work, you should "mv /etc/asound.conf.bak /etc/asound.conf" to make sure the problem doesn't get worse.

If none of the fixes presented in that thread don't work, it might be incompability between my cutting-edge gentoo ~x86 ALSA libraries and your system. I attached a version which is compiled on Kubuntu 6.06. Of course you can try to compile your own, just "apt-get install build-essential libsdl1.2-dev" and run "make" in et-sdl-sound/.

---

### Post by octavio on 2007-02-19
I think this was only my fault.

Now i have this output for both executions.

```

$> without_static.sh

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
WARNING: sdlmixsamps wasn't a power of two (20480) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x9701318 dma buffer
No background file.
----------------------


```

```

$> with_static.sh

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "dsp"
WARNING: sdlmixsamps wasn't a power of two (20480) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x96fff40 dma buffer
No background file.
----------------------

```

As you see  now with static keeps dsp but load alsa without static.

My problem, i post it for other people was that my asound.conf doesn't exist. I use ubuntu 6.10 and i had problems with my sound since the begining. Now i use this script i take from a forum:

```

#asound.conf
pcm.!default{
        type hw
        card IXP
}
ctl.!default{
        type hw
        card IXP
}

```

change IXP with the output of "asoundconf list" if you have more than one output, as i had (because my modem appears as a sound card you may blacklisted it in /etc/modprobe.d and there edit the blacklist-modem)

Thanks for all.

---

### Post by v3rtigo on 2007-02-23
I have a problem too, i can run et with sound w/o a problem but my problem is that 
My card doesn't have hardware mixing support by alsa so i can run TS+ET...

I tried your thing and it worked for the first time, but when i tried to run it again in the next day it didn't worked anymore i don't remember what i did except echo'ing et.x86 disable/direct to /proc/asound/card0...

when i run et with TS on i get this error
```

------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
SDL audio driver is "(UNKNOWN)"
SDL_OpenAudio() failed: No available audio device

```

with both static and the reguler.

Without TS it runs just fine... any solution?

---

### Post by nullkey on 2007-02-23
> **v3rtigo said:**
> 
```

------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
SDL audio driver is "(UNKNOWN)"
SDL_OpenAudio() failed: No available audio device

```
Octavio had similar error (read a few previous messages) and in his case and in your case this is a symptom of broken ALSA configuration. Please see [this thread](http://ubuntuforums.org/showthread.php?t=314718). The internal state of the ALSA system does reset in reboot and some abnormality could cause init scripts not to load some aspects of the configuration at boot, which results broken ALSA in some cases. I'm not an *ubuntu user, so I have no idea what it might be... :-|

If you don't run TS, the sound card is free and because ALSA does not work, SDL decides to use traditional OSS (you should see "SDL audio driver is ""dsp""). When using TS sound card is obviously not free and SDL fails because both ALSA and OSS fail.

---

### Post by v3rtigo on 2007-02-23
I'm also using arch and not ubuntu but i had same problem in ubuntu...

maybe it's because TS using oss and not alsa?

---

### Post by nullkey on 2007-02-23
> **v3rtigo said:**
> maybe it's because TS using oss and not alsa?
I've never used TS, so I didn't know this. So TS definetly conflicts with ET, even when ET is using ALSA. Fortunately you may have a chance of getting TS to work with ALSA using aoss (if TS doesn't use mmap it should work fine).

---

### Post by v3rtigo on 2007-02-23
It does work with aoss, that problem is that it makes the qulity of the sound really really bad
There is no chance to understand something with aoss.

---

### Post by nullkey on 2007-02-24
> **v3rtigo said:**
> It does work with aoss, that problem is that it makes the qulity of the sound really really bad
There is no chance to understand something with aoss.
That's sad but maybe there is an another VoIP conferencing application that fulfills your demands. I don't currently have any plans nor time to hack TS ALSA -compatible.

---

### Post by Quereller on 2007-02-26
Works great for me, thanks!

But I am not sure if the GPL is the right licence, would it not be better to use the LGPL?

---

### Post by nullkey on 2007-02-26
> **Quereller said:**
> But I am not sure if the GPL is the right licence, would it not be better to use the LGPL?
LGPL stands for Lesser General Public Lisence, not Library General Public License anymore. et-sdl-sound is an indipendent library (not a derivate of Enemy Territory) and borrows a few bits from Quake 3's source, which is released under GPL.

---

### Post by ins0mniac on 2007-03-05
Absolutely awesome!  I can hear ET and ventrilo via aoss+wine on my AC97.

Only problem is I cant get the mic working...

---

### Post by bravemosquito on 2007-03-12
One simple solution, taken from [http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

Create script etrun.sh with following lines:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
**sleep 3 - optional if u want to run ET within the script**
**et - optional if u want to run ET within the script**
```

Works fine on my u-boxes. When you exit ET and want to play TrueCombat: Elite, sound works well too - there's no need to run etrun.sh again, except after reboot

Edit: There is a little problem with this (probably only with me) - the 2 lines after **killall esd** must save the settings, but won't work for me. Another strange behavior is when I try to play ET with non-privileged user, the in-game settings won't remember - after closing and opening ET setting are 'defaults'. Chmoding 1777 the game dir didn't helps very much

Edit2: There is another bug (again on my box), associated with Firestarter - when Firestarter is stared I cannot play on Inernet and local servers.

---

### Post by peterhaagerup on 2007-03-20
I never got sound working until this. I can hear the sound, but it's lagging. My sound card is HDA Intel found in the 13,3" MacBook's. Any solutions to this?

---

### Post by bravemosquito on 2007-03-21
> **peterhaagerup said:**
> I never got sound working until this. I can hear the sound, but it's lagging. My sound card is HDA Intel found in the 13,3" MacBook's. Any solutions to this?

Which driver is used - OSS or ALSA?

---

### Post by sirniemi on 2007-05-06
Thank you so much for this.. thing!

Now I can play music, chat in ventrilo and play ET at the same time, and with SOUNDS!

Though I faced some problems with libSDL.so not found I got it working by doing this:

```

sudo apt-get install libsdl1.2-dev

```

Sound card is integrated ALC850 in nForce4-SLI motherboard (Asus A8N-SLI)
Using Ubuntu Feisty.

---

### Post by TheFuzzy0ne on 2007-05-20
You're a star! Uber-thanks! Worked a treat. :D

---

### Post by userundefine on 2007-05-27
Fantastic howto and work!  But it took a few minutes to figure out that I didn't have libsdl installed.  Post above cleared that up.  You should think about adding that to the first post.

---

### Post by nullkey on 2007-05-28
> **userundefine said:**
> Fantastic howto and work!  But it took a few minutes to figure out that I didn't have libsdl installed.  Post above cleared that up.  You should think about adding that to the first post.
Done. Does ubuntu have run-time only package for SDL? Since precompiled binary is provided, development libraries aren't really needed.

---

### Post by userundefine on 2007-05-28
I checked and was given a myriad of options so I just went with the one listed.  Here's what I got when I just dropped the -dev:

```
userundefine@nomadsland:~$ sudo apt-get install libsdl1.2
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libsdl1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl1.2debian-nas libsdl1.2debian-arts libsdl1.2debian-oss libsdl1.2debian-esd libsdl1.2debian-alsa
  libsdl1.2debian-all
E: Package libsdl1.2 has no installation candidate
```

---

### Post by nullkey on 2007-05-28
> **userundefine said:**
> I checked and was given a myriad of options so I just went with the one listed.  Here's what I got when I just dropped the -dev:
Oh, I see ;). I think libsdl1.2debian-alsa should do. At least it's name refers to alsa support.

---

### Post by fakie_flip on 2007-06-04
This got sound working in et running with 64 bit Ubuntu Feisty. Thanks!

---

### Post by transfix on 2007-07-09
Works great on my system!

---

### Post by Arrdee on 2007-07-22
This was the only thing that could get the sound working on my computer! Just had to change the script where it says "libSDL.so" to "libSDL-1.2.so". Thanks a bunch!

---

### Post by Haz13r on 2007-07-22
All i type is in terminal 

sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

Then i open Enemy Territory. Although the problem is every time you restart your computer, you type that in.

---

### Post by h2z on 2007-07-24
```

./et.x86: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/local/games/enemy-territory/et-sdl-sound/et-sdl-sound.so)

```

This is what I get when trying to run the script...I'm a total newbie but I think it has something to do with me running a 64bit version of fiesty?

---

### Post by nullkey on 2007-07-24
> **h2z said:**
> ```

./et.x86: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/local/games/enemy-territory/et-sdl-sound/et-sdl-sound.so)

```
Have you tried the latest **r16** version ([et-sdl-sound-r16.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/old/et-sdl-sound-r16.tar.gz)) or compiling from source (just run "make" in et-sdl-sound/)?

---

### Post by h2z on 2007-07-24
This is what i get when trying to make r16 (or any other version):

```

stefan@stefan-linux:/usr/local/games/enemy-territory/et-sdl-sound$ sudo make
g++ -m32 -O2 -fomit-frame-pointer -Wall -fPIC -D__SDL -D__DLOPEN_SDL -D__DEFAULT_BACKEND=SDL -c etsdl.cpp
In file included from etsdl.cpp:20:
etsdl.hpp:23:21: error: SDL/SDL.h: No such file or directory
In file included from /usr/include/features.h:346,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/x86_64-linux-gnu/32/bits/os_defines.h:39,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/x86_64-linux-gnu/32/bits/c++config.h:35,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/iostream:43,
                 from etsdl.cpp:21:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
etsdl.cpp:24:27: error: SDL/SDL_audio.h: No such file or directory
etsdl.hpp:39: error: &#8216;Uint8&#8217; has not been declared
etsdl.hpp:46: error: &#8216;Uint32&#8217; has not been declared
etsdl.hpp:47: error: expected identifier before &#8216;*&#8217; token
etsdl.hpp:47: error: &#8216;Uint32&#8217; has not been declared
etsdl.hpp:47: error: ISO C++ forbids declaration of &#8216;Uint32&#8217; with no type
etsdl.hpp:47: error: &#8216;Uint32&#8217; declared as function returning a function
etsdl.hpp:49: error: &#8216;Uint32&#8217; is not a type
etsdl.hpp:52: error: &#8216;SDL_AudioSpec&#8217; has not been declared
etsdl.hpp:52: error: &#8216;SDL_AudioSpec&#8217; has not been declared
etsdl.cpp: In member function &#8216;qboolean EtSDL::init()&#8217;:
etsdl.cpp:54: error: &#8216;SDL_AudioSpec&#8217; was not declared in this scope
etsdl.cpp:54: error: expected `;' before &#8216;desired&#8217;
etsdl.cpp:66: error: &#8216;SDL_INIT_AUDIO&#8217; was not declared in this scope
etsdl.cpp:66: error: &#8216;__SDL_WasInit&#8217; was not declared in this scope
etsdl.cpp:78: error: &#8216;desired&#8217; was not declared in this scope
etsdl.cpp:79: error: &#8216;obtained&#8217; was not declared in this scope
etsdl.cpp:87: error: &#8216;AUDIO_U8&#8217; was not declared in this scope
etsdl.cpp:89: error: &#8216;AUDIO_S16SYS&#8217; was not declared in this scope
etsdl.cpp:92: error: &#8216;Uint16&#8217; was not declared in this scope
etsdl.cpp:92: error: expected `;' before &#8216;sdldevsamps&#8217;
etsdl.cpp:103: error: expected primary-expression before &#8216;void&#8217;
etsdl.cpp:103: error: expected `)' before &#8216;void&#8217;
etsdl.cpp:106: error: &#8216;SDL_GetError&#8217; was not declared in this scope
etsdl.cpp: In member function &#8216;void EtSDL::shutdown()&#8217;:
etsdl.cpp:150: error: &#8216;SDL_INIT_AUDIO&#8217; was not declared in this scope
etsdl.cpp: At global scope:
etsdl.cpp:161: error: &#8216;Uint8&#8217; has not been declared
etsdl.cpp: In member function &#8216;bool EtSDL::loadSDLLib()&#8217;:
etsdl.cpp:257: error: expected primary-expression before &#8216;int&#8217;
etsdl.cpp:257: error: expected `)' before &#8216;int&#8217;
etsdl.cpp:258: error: expected `)' before &#8216;if&#8217;
etsdl.cpp:259: error: expected `)' before &#8216;if&#8217;
make: *** [etsdl.o] Error 1

```



I've installed the stdlib dev thingy and now this is what I get when trying to make:

```

stefan@stefan-linux:/usr/local/games/enemy-territory/et-sdl-sound$ sudo make
g++ -m32 -O2 -fomit-frame-pointer -Wall -fPIC -D__SDL -D__DLOPEN_SDL -D__DEFAULT_BACKEND=SDL -c etsdl.cpp
In file included from /usr/include/features.h:346,
                 from /usr/include/sys/types.h:27,
                 from /usr/include/SDL/SDL_stdinc.h:32,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from etsdl.hpp:23,
                 from etsdl.cpp:20:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [etsdl.o] Error 1

```

---

### Post by nullkey on 2007-07-24
> **h2z said:**
> This is what i get when trying to make r16 (or any other version):
You are still missing some essential packages or feisty has very broken glibc headers...

The error about "GLIBCXX_3.4.9" hints that my ~amd64 gentoo glibc/gcc might be just too bleeding edge :cool: (or broken...), so I compiled the latest version on (k)ubuntu 6.06: [et-sdl-sound-r16-ubuntu606.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/old/et-sdl-sound-r16-ubuntu606.tar.gz).

---

### Post by h2z on 2007-07-24
You are my hero! works like a charm now. :)

BTW, I highly doubt gcc is broken since I only recently installed fiesty (2 days ago) and apart from adding some essential updates, I haven't removed anything. Is there a way for me to check those lib's integrity/functionality?

---

### Post by pofigster on 2007-07-24
Ok, I really don't know what's wrong, so, I'll post everything I've done.

I've tried the killall esd command and something else...the two line command that involves oss somehow...anyway, the two standard methods of fixing no sound.

My alsa drivers are installed and running fine.  I downloaded the files you provided and wrote the script.  I have the folder from the .zip file on my desktop.  The script is also on my desktop.  The content of my script is as follows:

> #!/bin/bash

cd /usr/local/games/enemy-territory/
export LD_PRELOAD=/home/mark/Desktop/et-sdl-sound/et-sdl-sound.so 
./et.x86 $*

unset LD_PRELOAD

Ok, now, when it runs I get the following output (there's actually more than this, I've trimmed to what I think is necessary)

> $ sh etscript
etscript: line 3: cd: /usr/loca/games/enemy-territory/: No such file or directory
etscript: line 5: ./et.x86: No such file or directory
mark@mark-desktop:~/Desktop$ sh etscript
**et-sdl-sound loaded.**
ET 2.60 linux-i386 Mar 10 2005
...
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/mark/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/mark/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/mark/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaddedf40  
Sys_LoadDll(ui) succeeded!

Everytime I run ET I get that line:
/dev/dsp: Device or resource busy

I'm not running anything that takes sound (as far as I'm aware) although I do have pidgin running with sounds disabled.

Any help would be appreciated, the game is fun, but I'm sure it's more fun with sound.  :guitar:

Thanks!

---

### Post by nullkey on 2007-07-25
> **h2z said:**
> BTW, I highly doubt gcc is broken since I only recently installed fiesty (2 days ago) and apart from adding some essential updates, I haven't removed anything. Is there a way for me to check those lib's integrity/functionality?
I meant that it is probably my glibc/gcc which is broken ;)

> **pofigster said:**
> Everytime I run ET I get that line:
/dev/dsp: Device or resource busy
Really strange, are you sure it doesn't say something like "SDL audio driver initializing..."? Could you post the full console output to pastebin.com for example.

BTW, the recommended launcher script ([@et-sdl-sound home page](http://nullkey.ath.cx/~stuff/et-sdl-sound/)) is:
```
#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /path/to/enemy-territory/
LD_PRELOAD="/path/to/et-sdl-sound.so" ./et.x86 $*
```

---

### Post by pofigster on 2007-07-25
Ok, so I changed the script to reflect what you posted, it's now exactly the same.  However, I still don't get sound, so I copied the entire output and put it in pastebin.com - the link is [http://pastebin.com/m5dcf5f7f]("http://pastebin.com/m5dcf5f7f")

This time it didn't say that the device was busy, it said there was an I/O error.

---

### Post by nullkey on 2007-07-25
> **pofigster said:**
> Ok, so I changed the script to reflect what you posted, it's now exactly the same.  However, I still don't get sound, so I copied the entire output and put it in pastebin.com - the link is [http://pastebin.com/m5dcf5f7f]("http://pastebin.com/m5dcf5f7f")

This time it didn't say that the device was busy, it said there was an I/O error.
Still et-sdl-sound doesn't load properly. Are results any different if you execute
```
LD_PRELOAD=/home/mark/Desktop/et-sdl-sound/et-sdl-sound.so ./et.x86
``` in /usr/local/games/enemy-territory/? And please post md5 and crc32 sums for your et.x86:
```
md5sum /usr/local/games/enemy-territory/et.x86
crc32 /usr/local/games/enemy-territory/et.x86
```

---

### Post by pofigster on 2007-07-26
Ok, I moved the script as it was to /usr/local/games/enemy-territory and ran it - no sound.
I also changed the script since what you had posted didn't have the quotes and was missing the $* - that also didn't enable sound.

The md5sum is cfad12854e77fcde002a8f5327177172
the crc32 is 3b18a889

I really appreciate all your effort in helping me figure this out.

---

### Post by nullkey on 2007-07-26
Please try the attached binary and post the full output. I added some additional debugging code which will hopefully provide some additional information. I'm soon out of ideas :( (and time, it is holiday trip time again...)

---

### Post by kr0n1x on 2007-07-26
```
pasquale@pasquale-desktop:/usr/local/games/enemy-territory$ ./et_con_alsa 
./et.x86: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/local/games/et-sdl-sound.so)
pasquale@pasquale-desktop:/usr/local/games/enemy-territory$
```

any solution? what package i need?

i'm using Ubuntu Feisty desktop32bit

ps: i've noticed i'm not the first with this error. i need to try 606 version??

---

### Post by nullkey on 2007-07-26
> **kr0n1x said:**
> 
ps: i've noticed i'm not the first with this error. i need to try 606 version??
Exactly.

---

### Post by kr0n1x on 2007-07-26
now works perfectly :)

great work nullkey ;) thank!

bye

---

### Post by pofigster on 2007-07-26
> **nullkey said:**
> Please try the attached binary and post the full output. I added some additional debugging code which will hopefully provide some additional information. I'm soon out of ideas :( (and time, it is holiday trip time again...)
Ok, so I downloaded and installed the new binary you posted.  There was no change, still no sound.  However, the output does look different, it's complaining that libSDL.so doesn't exist.  The code is posted at [http://pastebin.com/d69d34b4b]("http://pastebin.com/d69d34b4b")

If this is because I didn't download something or some other stupid n00b mistake, I'm gonna shoot myself.

And thanks again for your help, you deserve a great vacation.

---

### Post by nullkey on 2007-07-28
> **pofigster said:**
> However, the output does look different, it's complaining that libSDL.so doesn't exist.  The code is posted at [http://pastebin.com/d69d34b4b]("http://pastebin.com/d69d34b4b")
That pastebin entry doesn't exist. But given that error I can guess something. Install SDL libs and modify ETSDL_SDL_LIB to point to the the correct libSDL.so, f.ex. /usr/lib/libSDL.so.1.2

---

### Post by pofigster on 2007-07-28
Hey!  That fixed it!  Thanks a million man!  If there was a kudos system here, you'd get all my kudos.

---

### Post by Malvolio on 2007-07-28
There's alot of methods floating around this thread and not alot of posts point back at what methods people used to get it to work.  I assume this process is to permanently fix the sound issues.  I've been using-

sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

-and I get sound working but, as said earlier, it's a session-specific fix.  I'm running Dell's Ubuntu install on a laptop and have it as up-to-date as I can figure.  What method shown on this thread is the best for my install?

---

### Post by pofigster on 2007-07-28
Well, for me, that didn't work.  So I downloaded the binaries provided here and copied the script that's also provided here.  Then I installed the SDL libraries and now I just run the script and it enables sound.  When I'm done, other sounds work fine.  So, it's just a new way of launching the game that gets rid of typing stuff into the terminal all the time.

---

### Post by nullkey on 2007-07-29
> **Malvolio said:**
> sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
That trick fixes ALSA's OSS emulation, so it is fine as long as you don't need software mixing or your sound card supports hardware mixing (probably not). If you want to play other audio streams (music or TS f.ex.) while playing ET, you need et-sdl-sound.

---

### Post by zuzuzzzip on 2007-07-31
this fixed my sound :D

I thought it was a linux32 problem, but seams it is not. Still can't get any sound in skype though :S

edit: so it worked, but not anymore :( 
I get this in console:
```
/dev/dsp: Device or resource busy
Could not open /dev/dsp
```with or without the script.. 
and with or without the kill esd, it says there's nothing to be killed, but that's what did the trick before...
need help :P
sound used to work in wine, now i get this when i do **winecfg**:
```
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: &#65533;&#65533;Z&#65533;: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: &#65533;&#65533;Z&#65533;: No such file or directory
ALSA lib pcm_dsnoop.c:588:(snd_pcm_dsnoop_open) unable to connect client
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer

```

---

### Post by Zexter on 2007-07-31
i have no sound... here is the read out of when i start the game from the script.


zexter@zexter-desktop:~$ #!/bin/bash
zexter@zexter-desktop:~$ export ETSDL_SDL_LIB="libSDL.so"
zexter@zexter-desktop:~$ export SDL_AUDIODRIVER="alsa"
zexter@zexter-desktop:~$ cd /usr/local/games/enemy-territory
zexter@zexter-desktop:/usr/local/games/enemy-territory$ LD_PRELOAD="/home/zexter" ./et.x86 $*
ERROR: ld.so: object '/home/zexter' from LD_PRELOAD cannot be preloaded: ignored.
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/zexter/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Zexter' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Zexter/etconfig.cfg
r_smp is unsafe. Check com_crashed.
r_mode is unsafe. Check com_crashed.
r_depthbits is unsafe. Check com_crashed.
r_stencilbits is unsafe. Check com_crashed.
r_stereo is unsafe. Check com_crashed.
r_colorbits is unsafe. Check com_crashed.
r_texturebits is unsafe. Check com_crashed.
r_clampToEdge is unsafe. Check com_crashed.
r_ext_texture_env_add is unsafe. Check com_crashed.
r_nv_fogdist_mode is unsafe. Check com_crashed.
r_ext_NV_fog_dist is unsafe. Check com_crashed.
r_ext_texture_filter_anisotropic is unsafe. Check com_crashed.
r_ati_fsaa_samples is unsafe. Check com_crashed.
r_ati_truform_pointmode is unsafe. Check com_crashed.
r_ati_truform_normalmode is unsafe. Check com_crashed.
r_ati_truform_tess is unsafe. Check com_crashed.
r_ext_ATI_pntriangles is unsafe. Check com_crashed.
r_glIgnoreWicked3D is unsafe. Check com_crashed.
r_ext_compiled_vertex_array is unsafe. Check com_crashed.
r_ext_multitexture is unsafe. Check com_crashed.
r_ext_gamma_control is unsafe. Check com_crashed.
r_ext_compressed_textures is unsafe. Check com_crashed.
r_allowExtensions is unsafe. Check com_crashed.
r_glDriver is unsafe. Check com_crashed.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: RADEON XPRESS Series
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON XPRESS Series
GL_VERSION: 2.0.6334 (8.34.8)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_pixel_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ARB_draw_buffers GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/zexter/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/zexter/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/zexter/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa9a1bf40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: zexter-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
Couldn't write profiles/Zexter/etconfig.cfg.
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951


and also when i try to join a server it says cannot write to hunkusage.dat

---

### Post by zuzuzzzip on 2007-07-31
my sound works now using this!
[http://ubuntuforums.org/showthread.php?t=30302](http://ubuntuforums.org/showthread.php?t=30302)

but this sdl thing doesn't but will figure that out later :D

---

### Post by nullkey on 2007-08-01
> **Zexter said:**
> 
zexter@zexter-desktop:/usr/local/games/enemy-territory$ LD_PRELOAD="/home/zexter" ./et.x86 $*
ERROR: ld.so: object '/home/zexter'
```
LD_PRELOAD="/home/zexter/et-sdl-sound.so" ./et.x86 $*
```

---

### Post by zuzuzzzip on 2007-08-01
I get this error:
```
------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: &#65533;&#65533;Z&#65533;: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
SDL audio driver is "(UNKNOWN)"
Received signal 11, exiting...
et.pl: line 5: 10030 Segmentation fault      (core dumped) LD_PRELOAD="/usr/local/games/enemy-territory/et-sdl-sound.so" ./et.x86
zuzuzzzip@ZuzuPC-ubuntu:~$ cd /usr/local/games/enemy-territory/

```
That's with rhytmbox running, without rythmbox running it works (duh) but the idea is to let it work at the same time, right? :p

---

### Post by nullkey on 2007-08-01
> **zuzuzzzip said:**
> ```
------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: Z: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
SDL audio driver is "(UNKNOWN)"
Received signal 11, exiting...
et.pl: line 5: 10030 Segmentation fault      (core dumped) LD_PRELOAD="/usr/local/games/enemy-territory/et-sdl-sound.so" ./et.x86
zuzuzzzip@ZuzuPC-ubuntu:~$ cd /usr/local/games/enemy-territory/

```
et-sdl-sound is working, your ALSA is not. I'm sorry but I can't currently help (mobile phones aren't ideal web browsers so googling around about that error message wouldn't be a pleasant experience :D).

---

### Post by nullkey on 2007-08-01
> **zuzuzzzip said:**
> ```
/dev/dsp: Device or resource busy
Could not open /dev/dsp
```
```
export SDL_AUDIODRIVER="alsa"
```
> **zuzuzzzip said:**
> ```
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: Z: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: Z: No such file or directory
ALSA lib pcm_dsnoop.c:588:(snd_pcm_dsnoop_open) unable to connect client
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer

```
Another happy owner of a problematic ALSA installation :/

---

### Post by redhat24 on 2007-08-03
Hiho!

I've read all the posts, and it's working for everybody but not for me... :(

[http://pastebin.com/m411fda84](http://pastebin.com/m411fda84)

I've done everything what you wrote, tried every aspect of script file, but it keep saying:
```

ERROR: ld.so: object 'et-sdl-sound.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'et-sdl-sound.so' from LD_PRELOAD cannot be preloaded: ignored.

```

First time i was used the oss-forcing method, it worked once, not anymore, and i would like to play with et-sdl-sound, but it doesnt load :S

---

### Post by nullkey on 2007-08-05
**UPDATE!**: New self-containing launcher script! No more complex scripts or environment variables!

Just
```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
```
and run ./et-sdl-sound

---

### Post by redhat24 on 2007-08-05
```

[et-sdl-sound] info   : Enemy Territory is installed to /usr/local/games/enemy-territory
[et-sdl-sound] info   : 32-bit libSDL.so is installed to /home/balint/games/armyops/System/libSDL-1.2.so.0
[COLOR="Red"]./et-sdl-sound: line 61: base64: command not found[/COLOR]

gzip: stdin: unexpected end of file
[et-sdl-sound] error  : can't write /tmp/et-sdl-sound.so

```

which package should i install to have base64 encode/decode?

---

### Post by nullkey on 2007-08-05
> **redhat24 said:**
> which package should i install to have base64 encode/decode?
et-sdl-sound-r19 should no longer need base64 so that problem should be fixed :)

---

### Post by zuzuzzzip on 2007-08-05
```
[et-sdl-sound] info   : Enemy Territory is installed to /usr/local/games/enemy-territory
[et-sdl-sound] error  : can't locate libSDL.so

```

[IMG]http://student.khleuven.be/%7E500182/fun/libSDL.png[/IMG]

---

### Post by nullkey on 2007-08-06
> **zuzuzzzip said:**
> ```
[et-sdl-sound] info   : Enemy Territory is installed to /usr/local/games/enemy-territory
[et-sdl-sound] error  : can't locate libSDL.so

```]
I'm not very good at night-coding, sorry about that bug ;). **r20** should have a fix and even tested (how often this is forgotten...) on ubuntu 6.06.

---

### Post by redhat24 on 2007-08-08
> **nullkey said:**
> et-sdl-sound-r19 should no longer need base64 so that problem should be fixed :)

Oh man! You're the best! It's working!!!!
```

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
WARNING: sdlmixsamps wasn't a power of two (18800) so we made it one (32768).
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x98ca810 dma buffer
No background file.
----------------------

```

Now I can listen to music while i'm killing my enemy :)

---

### Post by Theimon on 2007-08-22
Joy to the world for this brilliant piece of software. Absolutely fabulous. On my old hardware setup I was able to play mp3s and play the game at the same time, but somehow my new setup didn't seem to manage that (the newer, the better? errr). 
But I stumbled across this thread, I tried it (why not, I tried everything else...) and it just bloody works, Hurray! 
Cheers!

---

### Post by zuzuzzzip on 2007-08-22
> **nullkey said:**
> I'm not very good at night-coding, sorry about that bug ;). **r20** should have a fix and even tested (how often this is forgotten...) on ubuntu 6.06.
is r20 finished? :)

---

### Post by nullkey on 2007-08-22
> **zuzuzzzip said:**
> is r20 finished? :)
[The official homepage](http://nullkey.ath.cx/~stuff/et-sdl-sound/) states that the latest release is **r23**, which introduces support for **Quake III Arena**.

---

### Post by yekim on 2007-08-25
I've spent two days trying everything I could find in the forums to  fix my sound, finally found this post and worked automagically.  Thanks OP!

---

### Post by krak on 2007-09-03
THX nice HOWTO worked 100%

now I can play :>
:-({|=:guitar::popcorn:=D>

---

### Post by Lord C on 2007-10-20
Worked great, thanks :)

---

### Post by Sotamato on 2007-10-25
Thank you very much. I tried at least everything, but this finally works.

---

### Post by kr0n1x on 2007-10-25
i tried the new and the old methods but it hasn't helped me.

i'm on Ubuntu Gutsy 64 bit, maybe you know how to solve the problem? :(

ps: sorry my english

---

### Post by nullkey on 2007-10-25
> **kr0n1x said:**
> i tried the new and the old methods but it hasn't helped me.

i'm on Ubuntu Gutsy 64 bit, maybe you know how to solve the problem? :(
Could you post et-sdl-sound console output somewhere?

---

### Post by kr0n1x on 2007-10-25
i'm trying to compile my et-sdl-sound.so

when i write "make", i've this in console:
```

pasquale@pasquale-desktop:~/et-sdl-sound$ make
g++ -m32 -shared build/mainlib.o build/etsdl.o build/hooks.o -o et-sdl-sound.so
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [et-sdl-sound.so] Error 1
pasquale@pasquale-desktop:~/et-sdl-sound$ 

```

what i need to complete my "make"?

i used apt-file search for find some files i needed (like SDL.h) but now i don't know what package i need to download and install...
can you help me?

anyway here is my output: [http://pastebin.com/f38ece77a](http://pastebin.com/f38ece77a)

and this is my starter file:
```
#!/bin/bash
export ETSDL_SDL_LIB="/usr/lib/libSDL-1.2.so.0"
export SDL_AUDIODRIVER="alsa"
cd /usr/local/games/enemy-territory/
LD_PRELOAD="/usr/local/games/enemy-territory/et-sdl-sound.so" ./et.x86 $*
```

and here is where i can find my libSDL-1.2.so.0:
```
pasquale@pasquale-desktop:~$ locate libSDL-1.2
/usr/lib32/libSDL-1.2.so.0.11.0
/usr/lib32/libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0.11.0
/usr/lib/libSDL-1.2.so.0
pasquale@pasquale-desktop:~$ 

```

thx bye :) if you need more info ask to me

---

### Post by nullkey on 2007-10-26
> **kr0n1x said:**
> i'm trying to compile my et-sdl-sound.so

when i write "make", i've this in console:
You don't need to compile et-sdl-sound just because you are running x86-64. ET is still 32-bit application and my precompiled library should work. That error is about missing 32-bit development libraries (libstdc++).

The real problem is however
```

------- sound initialization -------
Could not open /usr/lib/libSDL-1.2.so.0: /usr/lib/libSDL-1.2.so.0: wrong ELF class: ELFCLASS64
Please check that ETSDL_SDL_LIB environment variable points to valid 32-bit SDL library.
------------------------------------

```
You need to install 32-bit sdl libraries (not sure what is correct package name for 'em, I'll try to find out). Those 32-bit versions will install to /usr/lib**32** and you need to modify ETSDL_SDL_LIB. I think et-sdl-sound script bugs you about missing 32-bit SDL since it does check whether found libraries are x86 or x86_64.

The reason why this is so complex is that 32- and 64-bit code can't coexist in same process. The application and all its dependencies (libraries) need to be either x86 or x86_64. Enemy Territory is 32-bit application and needs 32-bit libraries.

---

### Post by gav616 on 2007-10-26
do i need to use this script when lauching TC: E, beacuse it comes with its own lauch script, it contains;

```
#!/bin/sh
###############################################################################
#
## LIFLG Startup Script
#
# Copyright (C) 2004-2007  Team LIFLG http://www.liflg.org/
#
#
# This script is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
###############################################################################
#
# The game binary
GAME_BINARY="et.x86"

# Subdirectory
SUBDIR="."

# Library directory
LIBDIR=""

# Additional commandline options for mods etc.
CMD_ARGS="+set fs_game tcetest +set com_hunkMegs 512 +set com_soundMegs 64 +set com_zoneMegs 64"

# Set the sdl audio driver (default: oss)
# More at http://icculus.org/lgfaq/#setthatdriver
SDL_AUDIODRIVER="alsa"

# Use US keyboard layout
USLAYOUT="false"

# Set gamma for the game
GAMMA="1.25"

# If you want to start the game on a second X server
# comment out the XSERVER* options.
# Useful if you run Xgl ;-)
#XSERVER="Xorg"

# for options run Xorg -help
#XSERVER_OPTIONS="-reset -terminate -br -quiet -nolisten tcp -to 30"

# display number
#XSERVER_DISPLAY=":1.0"

###############################################################################
## DO NOT EDIT BELOW THIS LINE
###############################################################################
export LANG="POSIX"

test -n "${SDL_AUDIODRIVER}" && export SDL_AUDIODRIVER
if [ -n "${XSERVER_DISPLAY}" ]; then
	DISPLAY=${XSERVER_DISPLAY}
	export DISPLAY
fi

# readlink replacement for older bash versions
readlink() {
	path=$1
 
	if [ -L "$path" ]
	then
		ls -l "$path" | sed 's/^.*-> //'
	else
		return 1
	fi
}

setuslayout() {
	setxkbmap -model pc101 us -print | xkbcomp - ${DISPLAY} 2>/dev/null
}
trap setxkbmap EXIT

resetgamma() {
	if [ -n "${XGAMMA}" ]
	then
		exec ${XGAMMA}
	fi
}
trap resetgamma EXIT

SCRIPT="$0"
COUNT=0
while [ -L "${SCRIPT}" ]
do
	SCRIPT=$(readlink ${SCRIPT})
	COUNT=$(expr ${COUNT} + 1)
	if [ ${COUNT} -gt 100 ]
	then
		echo "Too many symbolic links"
		exit 1
	fi
done
GAMEDIR=$(dirname ${SCRIPT})

# start second X server
if [ -n "${XSERVER}" ]; then
	${XSERVER} ${XSERVER_OPTIONS} ${XSERVER_DISPLAY} 2>/dev/null &
	xterm -e sleep 5 &
fi

#games are better played with us keyboard layout
if [ "${USLAYOUT}" = "true" ]; then
	setuslayout
fi

# save gamma value and set wanted
if [ -n "${GAMMA}" ]; then
	XGAMMA=$(xgamma 2>&1 | sed -e "s/.*Red \(.*\), Green \(.*\), Blue \(.*\)/xgamma -rgamma\1 -ggamma\2 -bgamma\3/")
	xgamma -gamma ${GAMMA}
fi

cd ${GAMEDIR}
cd ${SUBDIR}

# export game library directory
test -n "${LIBDIR}" && export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:${GAMEDIR}/${LIBDIR}"

# start the game
./${GAME_BINARY} ${CMD_ARGS} "$@"
EXITCODE="$?"

if [ "${USLAYOUT}" = "true" ]; then
	# reset kb layout
	setxkbmap >/dev/null 2>&1

	# reset xmodmap
	test -r ${HOME}/.Xmodmap && xmodmap ${HOME}/.Xmodmap >/dev/null 2>&1
fi

# reset gamma
resetgamma

exit ${EXITCODE}

```

```
SDL_AUDIODRIVER="alsa"
```
will setting ^ be enough to enable alsa (providing i have the package installed?)

---

### Post by nullkey on 2007-10-26
> **gav616 said:**
> 
```
SDL_AUDIODRIVER="alsa"
```
will setting ^ be enough to enable alsa (providing i have the package installed?)
Try it... I guess it will just use OSS (unless TC:E has been ported to some enchanced version of Q3 engine with SDL/ALSA support). I think that the author of that script has absolutely no clue about SDL/ALSA/OSS/ET.

However if you want to make it work with et-sdl-sound (it is actually a **library**, script is just for convinience), extract [et-sdl-sound.tar.gz](http://nullkey.ath.cx/et-sdl-sound/et-sdl-sound.tar.gz), copy et-sdl-sound**.so** somewhere and add
```

export ETSDL_SDL_LIB="libSDL.so"
export LD_PRELOAD="/<path to>/et-sdl-sound.so"

```
after that SDL_AUDIODRIVER="alsa" -line. If that does not work, try et-sdl-sound script with +fs_game tcetest argument:
```

./et-sdl-sound +fs_game tcetest

```

---

### Post by gav616 on 2007-10-27
from what ive tryed both dont work,
how to i check its on or off in TCE?

---

### Post by nullkey on 2007-10-27
> **gav616 said:**
> from what ive tryed both dont work,
how to i check its on or off in TCE?
Run ```
./et-sdl-sound
``` in console and post everything it prints out.

If it is using SDL audio, it says something like
```

et-sdl-sound-r25 (...) loaded.
...
------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
SDL audio initialized.
------------------------------------

```

---

### Post by gav616 on 2007-10-27
says it can't find et.x86

---

### Post by nullkey on 2007-10-28
> **gav616 said:**
> says it can't find et.x86
et-sdl-sound script tries to search et.x86 in /usr/local/games/enemy-territory, /opt/enemy-territory, /usr/games/enemy/territory, /home/username/enemy-territory and if all of those fails, it tries "locate et.x86" and then "find /opt/ /usr/ -type f -name et.x86". Try running "updatedb" as root or symlink your enemy territory installation path to ~/enemy-territory. 

If nothing works, please tell me where you actually have et.x86 and I'll add that to the script.

---

### Post by kr0n1x on 2007-10-28
i solved my problem (gutsy 64 bit):

[http://ubuntuforums.org/showthread.php?t=425327](http://ubuntuforums.org/showthread.php?t=425327)

all i need to do was installi [this]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") package

thanks Kilz ;) and nullkey in msn :D

---

### Post by PissedApache on 2007-11-16
The script worked a treat for me! thanks :)

ET & ETQW! joy\\:D/

---

### Post by popey on 2007-11-21
Hi, I wonder if you can help me, I'm having problems here:-

Ubuntu 7.10 x86

Binary ET file looks good.
```

$ crc32 /usr/local/games/enemy-territory/et.x86 
3b18a889

```

Compiling looks okay.
(Tried using your pre-built binaries, also tried compiling myself)
```

$ make
mkdir -p build
g++ -m32 -O2 -fomit-frame-pointer -Wall -fPIC -D__SDL -D__DLOPEN_SDL -D__DEFAULT_BACKEND=SDL -c mainlib.cpp -o build/mainlib.o
g++ -m32 -O2 -fomit-frame-pointer -Wall -fPIC -D__SDL -D__DLOPEN_SDL -D__DEFAULT_BACKEND=SDL -c etsdl.cpp -o build/etsdl.o
g++ -m32 -O2 -fomit-frame-pointer -Wall -fPIC -D__SDL -D__DLOPEN_SDL -D__DEFAULT_BACKEND=SDL -c hooks.cpp -o build/hooks.o
g++ -m32 -shared build/mainlib.o build/etsdl.o build/hooks.o -o et-sdl-sound.so
sed 's/--script-name--/et-sdl-sound/g;s/--game-bin--/et.x86/g;s/--game-dir--/enemy-territory/g' launcher-script.in > et-sdl-sound
./embed-lib et-sdl-sound et-sdl-sound --et-sdl-sound-lib-- et-sdl-sound.so wrap
chmod a+x et-sdl-sound
sed 's/--script-name--/wolf-sdl-sound/g;s/--game-bin--/wolf.x86/g;s/--game-dir--/rtcw/g' launcher-script.in > wolf-sdl-sound
./embed-lib wolf-sdl-sound wolf-sdl-sound --et-sdl-sound-lib-- et-sdl-sound.so wrap
chmod a+x wolf-sdl-sound
sed 's/--script-name--/wolfsp-sdl-sound/g;s/--game-bin--/wolfsp.x86/g;s/--game-dir--/rtcw/g' launcher-script.in > wolfsp-sdl-sound
./embed-lib wolfsp-sdl-sound wolfsp-sdl-sound --et-sdl-sound-lib-- et-sdl-sound.so wrap
chmod a+x wolfsp-sdl-sound
sed 's/--script-name--/quake3-sdl-sound/g;s/--game-bin--/quake3.x86/g;s/--game-dir--/quake3/g' launcher-script.in > quake3-sdl-sound
./embed-lib quake3-sdl-sound quake3-sdl-sound --et-sdl-sound-lib-- et-sdl-sound.so wrap
chmod a+x quake3-sdl-sound

```

libSDL is installed:-
```

$ dpkg -l libsdl1.2debian-alsa | grep ^ii
ii  libsdl1.2debian-alsa 1.2.11-9ubuntu2 Simple DirectMedia Layer (with X11 and ALSA options)
alan@wopr:~/et/et-sdl-sound$ 

```

Confirmed:-
```

$ ls -l /usr/lib/libSDL.so
lrwxrwxrwx 1 root root 20 2007-10-16 14:45 /usr/lib/libSDL.so -> libSDL-1.2.so.0.11.0

```

Script is written:-
```

$ cat goet
#!/bin/bash
export ETSDL_SDL_LIB="/usr/lib/libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /usr/local/games/enemy-territory
LD_PRELOAD="/home/alan/et/et-sdl-sound/et-sdl-sound.so" ./et.x86 $*

```

When I run it however:-
```

$ ./goet 
Read /usr/local/games/enemy-territory/et.x86 (1538888 bytes)
0x817d6c0: e9 2b 2e e3 af 
0x817dce0: e9 cb 27 e3 af 
0x817dd70: e9 fb 26 e3 af 
0x817dd90: e9 9b 26 e3 af 
0x817dd80: e9 6b 26 e3 af 
Found ET 2.60 (CRC32 = 0x3b18a889)
Using SDL backend.
et-sdl-sound-r25 (Nov 21 2007 14:08:28, 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) loaded.
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----

```

...then...

```


------- sound initialization -------
SDL audio driver initializing...
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
SDL audio driver is "(UNKNOWN)"
./goet: line 5:  8808 Segmentation fault      (core dumped) LD_PRELOAD="/home/alan/et/et-sdl-sound/et-sdl-sound.so" ./et.x86 $*


```


Any suggestions?

Just for your information I am using a USB-attached soundblaster extigy which works fine in rhythmbox and the test tool in sound preferences.


```

$ ls -l /proc/asound/Extigy
lrwxrwxrwx 1 root root 5 2007-11-21 14:14 /proc/asound/Extigy -> card1


```

---

### Post by nullkey on 2007-11-21
> **popeydc said:**
> 
```

------- sound initialization -------
SDL audio driver initializing...
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
SDL audio driver is "(UNKNOWN)"
./goet: line 5:  8808 Segmentation fault      (core dumped) LD_PRELOAD="/home/alan/et/et-sdl-sound/et-sdl-sound.so" ./et.x86 $*

```

SDL tries to use non-existing sound device, are you sure other SDL apps work fine?

> **popeydc said:**
> 
```

$ ls -l /proc/asound/Extigy
lrwxrwxrwx 1 root root 5 2007-11-21 14:14 /proc/asound/Extigy -> card1

```
That seems to link to card**1** and I guess card**0** is considered the default one (at least on my system card0 is symlink to default device). You need to either tell SDL to use card1 or reconfigure your ALSA to map Extigy to card0.

---

### Post by popey on 2007-11-21
No, other SDL apps do not work. Neverball for example gives no sound.

The onboard sound is disabled so card1 is the _only_ audio card in the system. There is no card0.

---

### Post by popey on 2007-11-21
Yay. Editing /etc/modprobe.d/alsa-base to allow the external card to be card0 worked! Thanks for the tip!

---

### Post by henriquemaia on 2007-12-12
Thanks a lot for this howto. Now I can play TC:E again with sound. 

:D

---

### Post by KindredCharles on 2007-12-29
------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)"
./et-sdl-sound: line 1582: 19516 Segmentation fault      (core dumped) LD_PRELOAD="$TMP_DIR/et-sdl-sound.so" ./$GAME_BIN $*
[et-sdl-sound] info   : done
charles@THX1138:~$ 




I'm not sure what my problem is i was told et-sdl-sound was the fix for ts et sound conflict but when i run it i get this error

---

### Post by nullkey on 2007-12-29
> **KindredCharles said:**
> I'm not sure what my problem is i was told et-sdl-sound was the fix for ts et sound conflict but when i run it i get this error
It is a proper fix for enemy territory sound issues (besides being a cure for cancer) but first you must fix your ALSA. I think I've seen that error before... I strongly suggest using the almighty "search" -feature.

---

### Post by Uriziel on 2007-12-31
I've got sound in Et (Ubuntu 7.10) but I can't listen to music when I'm playing... I've tried to use both versions of sdl (static and non-static) but it don't work.
 In non-static i have 
```

uriziel@uriziel-desktop:~$ ./et-sdl-sound
[et-sdl-sound] info   : et.x86 is installed to /home/uriziel/.etwolf
[et-sdl-sound] info   : 32-bit libSDL.so is installed to /usr/lib/libSDL-1.2.so.0.11.0
[et-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
[et-sdl-sound] info   : launching the game...
Read /home/uriziel/.etwolf/et.x86 (1604328 bytes)
0x8188250: e9 5b 32 e3 af 
0x8188840: e9 ab 2c e3 af 
0x81888d0: e9 5b 2c e3 af 
0x81888f0: e9 7b 2c e3 af 
0x81888e0: e9 cb 2c e3 af 
Found ET 2.60b (CRC32 = 0x6ab49f82)
Using SDL backend.
et-sdl-sound-r25 (Sep 15 2007 10:29:23, 3.4.6 (Gentoo 3.4.6-r2 p1.5, ssp-3.4.6-1.0, pie-8.7.10)) loaded.
(...)
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?
[et-sdl-sound] info   : done

```
Shouldn't it use et.x86 from /home/uriziel/enemy-territory/ ?
If i use static version with 
```

#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /home/uriziel/enemy-territory/
LD_PRELOAD="/home/uriziel/enemy-territory/et-sdl-sound.so" ./et.x86 $*

```
I've got:
```

------- sound initialization -------
Could not open libSDL.so: libSDL.so: cannot open shared object file: No such file or directory
Please check that ETSDL_SDL_LIB environment variable points to valid 32-bit SDL library.

```
w/o script I have:
```

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x80a53000 dma buffer
No background file.
----------------------

```
With amarok I have
```
 ------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

```


Btw.
```

uriziel@uriziel-desktop:~$ sudo apt-get install libsdl1.2debian-alsa
(...)
libsdl1.2debian-alsa jest ju&#380; w najnowszej wersji // libsdl1.2debian-alsa is in newest version

```
```

uriziel@uriziel-desktop:~$ md5sum /home/uriziel/enemy/et.x86
e612c922bec7d8f4d7a8dfbbea3dade3  /home/uriziel/enemy/et.x86
uriziel@uriziel-desktop:~$ crc32 /home/uriziel/enemy/et.x86
6ab49f82

```

---

### Post by bharadwaj on 2007-12-31
nullkey: you have any idea how to customize my video interface mine is very sluggish interface
[http://ubuntuforums.org/showthread.php?t=607494](http://ubuntuforums.org/showthread.php?t=607494)

---

### Post by nullkey on 2008-01-02
> **Uriziel said:**
> 
Shouldn't it use et.x86 from /home/uriziel/enemy-territory/ ?

You have ET installed into non-standard path and thus et-sdl-sound script must rely on `locate` or `find` to find out where it is installed and somehow your ~/.etwolf/ directory contains et.x86. Remove it and run updatedb as root. After that et-sdl-sound script should find correct one.

> **Uriziel said:**
> 
```

#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /home/uriziel/enemy-territory/
LD_PRELOAD="/home/uriziel/enemy-territory/et-sdl-sound.so" ./et.x86 $*

```
```

...
export ETSDL_SDL_LIB="/usr/lib/libSDL-1.2.so.0.11.0"
...

```

---

### Post by Uriziel on 2008-01-04
It work with amarok, it dont with TS, with ts i have ```
------- sound initialization -------
SDL audio driver initializing...
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
SDL audio driver is "(UNKNOWN)"
Received signal 11, exiting...
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 1419
./etsdl: line 5:  7765 Segmentation fault      (core dumped) LD_PRELOAD="/home/uriziel/enemy/et-sdl-sound.so" ./et.x86 $*

```

---

### Post by nullkey on 2008-01-05
> **Uriziel said:**
> It work with amarok, it dont with TS, with ts i have
Teamspeak uses OSS, which interferes with ALSA (as it was with Enemy Territory before et-sdl-sound) so you need to run it through alsa-oss (aoss) wrapper which translates OSS calls into ALSA:
```
aoss teamspeak
```

---

### Post by Lameismyname on 2008-02-24
Works fine for me except one little thingie. On etpro servers in /cheaters menu my system is [???] when using your toll nullkey. I'm wondering is there any method available to "repair" this bug (installing older version or smthng). It's very important for me. Plz help and thx in advance.

---

### Post by nullkey on 2008-02-24
> **Lameismyname said:**
> Works fine for me except one little thingie. On etpro servers in /cheaters menu my system is [???] when using your toll nullkey. I'm wondering is there any method available to "repair" this bug (installing older version or smthng). It's very important for me. Plz help and thx in advance.
It is actually possible since real hacks do that. It would require hooking deeper into ET and modifying etpro binary code. et-sdl-sound 'aint a hack so I'm reluctant to implement such feature.

---

### Post by Lameismyname on 2008-02-24
Ok I understand, I'm not talking about spoofing this information but just to show the real one  
wchich is generated by ET. I don't know is it because of program/driver or whatever. And another question - is everyone using this toll having same problem with [???] system? Please give me an advice what to do cause I don't know anyone who could help me with this....

---

### Post by nullkey on 2008-02-24
> **Lameismyname said:**
> Ok I understand, I'm not talking about spoofing this information but just to show the real one  
wchich is generated by ET. I don't know is it because of program/driver or whatever. And another question - is everyone using this toll having same problem with [???] system? Please give me an advice what to do cause I don't know anyone who could help me with this....
etpro does some additional code integrity checks which do not pass since et-sdl-sound has to modify ET binary code directly. Your best option is to explain the admins that you are using et-sdl-sound and that causes [???]. If you were using real hack, it would spoof the information so [???] is actually "better" than spoofed information.

---

### Post by Lameismyname on 2008-02-24
Ok thank you. Just a shame there isn't any solution for this.... life :)

---

### Post by came2die on 2008-04-15
It works for me too :) 

Thank you very much :)!

---

### Post by Dingo_aus on 2008-05-19
THanks Nullkey worked first go for me - saved a lot of hair pulling :)

---

### Post by MattThLinuxNewb on 2008-05-25
Hi this is what I get in the console:
```

-e [et-sdl-sound] info   : et.x86 is installed to /usr/local/games/enemy-territory
-e [et-sdl-sound] info   : 32-bit libSDL.so is installed to /usr/lib/libSDL-1.2.so.0.11.1
-e [et-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
-e [et-sdl-sound] info   : launching the game...
ERROR: ld.so: object '/tmp/et-sdl-sound.so' from LD_PRELOAD cannot be preloaded: ignored.
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/matt/.etwolf/etmain/xposed.pk3 (75 files)
/home/matt/.etwolf/etmain/Warbell.pk3 (242 files)
/home/matt/.etwolf/etmain/vengeance_te_final.pk3 (108 files)
/home/matt/.etwolf/etmain/transmitter.pk3 (143 files)
/home/matt/.etwolf/etmain/TDM_Close_Combat.pk3 (129 files)
/home/matt/.etwolf/etmain/tc_venice_rc2.pk3 (324 files)
/home/matt/.etwolf/etmain/tc_base.pk3 (63 files)
/home/matt/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
/home/matt/.etwolf/etmain/sw_goldrush_te.pk3 (48 files)
/home/matt/.etwolf/etmain/sw_cathedral_b7.pk3 (82 files)
/home/matt/.etwolf/etmain/supplydepot.pk3 (46 files)
/home/matt/.etwolf/etmain/streets_a2.pk3 (19 files)
/home/matt/.etwolf/etmain/streets_a1.pk3 (14 files)
/home/matt/.etwolf/etmain/sp_delivery2.pk3 (39 files)
/home/matt/.etwolf/etmain/rommel_ga.pk3 (129 files)
/home/matt/.etwolf/etmain/quotidian_b2.pk3 (212 files)
/home/matt/.etwolf/etmain/orcon5.pk3 (9 files)
/home/matt/.etwolf/etmain/mml_helmsdeep_b4.pk3 (185 files)
/home/matt/.etwolf/etmain/karsiah_te2.pk3 (41 files)
/home/matt/.etwolf/etmain/intel_center_b2.pk3 (190 files)
/home/matt/.etwolf/etmain/industry2_final.pk3 (85 files)
/home/matt/.etwolf/etmain/hillclimb_a2.pk3 (14 files)
/home/matt/.etwolf/etmain/graverob_b1.pk3 (95 files)
/home/matt/.etwolf/etmain/ga_cmp_090805.pk3 (9 files)
/home/matt/.etwolf/etmain/Frostbite.pk3 (99 files)
/home/matt/.etwolf/etmain/et_village.pk3 (58 files)
/home/matt/.etwolf/etmain/et_ice.pk3 (61 files)
/home/matt/.etwolf/etmain/et_beach.pk3 (177 files)
/home/matt/.etwolf/etmain/et6mapcycle.pk3 (3 files)
/home/matt/.etwolf/etmain/eftetpub0208.pk3 (2 files)
/home/matt/.etwolf/etmain/caen2.pk3 (85 files)
/home/matt/.etwolf/etmain/bremen_b2.pk3 (82 files)
/home/matt/.etwolf/etmain/braundorf_b4.pk3 (51 files)
/home/matt/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
6727 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/MattMurdock/etconfig.cfg
execing autoexec.cfg
execing mg
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Unknown command "+attack"
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Unknown command ""
Unknown command "cpm"
Unknown command "cpm"
Unknown command "cpm"
Unknown command "cpm"
Unknown command "cpm"
Unknown command "cpm"
Unknown command "cpm"
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8600 GT/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/matt/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/matt/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/matt/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa9d42f40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: matt-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master6.evenbalance.com
^5PunkBuster Client: Resolved to [69.59.138.4]
^5PunkBuster Client: PunkBuster Client (v2.042 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60b linux-i386 May  8 2006]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
-e [et-sdl-sound] info   : done

```
I'm guessing this is the problem ->
```

ERROR: ld.so: object '/tmp/et-sdl-sound.so' from LD_PRELOAD cannot be preloaded: ignored.
```
How can I fix this? :(
Thanks, Matt

---

### Post by nullkey on 2008-05-25
> **MattThLinuxNewb said:**
> 
I'm guessing this is the problem ->
```

ERROR: ld.so: object '/tmp/et-sdl-sound.so' from LD_PRELOAD cannot be preloaded: ignored.
```
How can I fix this? :(
Thanks, Matt
It certainly is. Make sure you can actually write file named /tmp/et-sdl-sound.so and make it executable. Try this:
```

echo -e "#\!bin/sh\necho \"Working\"" > /tmp/et-sdl-sound.so
chmod a+x /tmp/et-sdl-sound.so
/tmp/et-sdl-sound.so
rm /tmp/et-sdl-sound.so
```
It should print out "Working". Problem might be that your /tmp is mounted with noexec flag (paste your `mount` output here) or there is already et-sdl-sound.so file you can't overwrite.

---

### Post by MattThLinuxNewb on 2008-05-25
Wow, fast reply! Here' the output:

```
matt@matt-desktop:/usr/local/games/enemy-territory$ echo -e "#\!bin/sh\necho \"Working\"" > /tmp/et-sdl-sound.so
matt@matt-desktop:/usr/local/games/enemy-territory$ chmod a+x /tmp/et-sdl-sound.so
matt@matt-desktop:/usr/local/games/enemy-territory$ /tmp/et-sdl-sound.so
Working
matt@matt-desktop:/usr/local/games/enemy-territory$ rm /tmp/et-sdl-sound.so

```

---

### Post by nullkey on 2008-05-25
> **MattThLinuxNewb said:**
> Wow, fast reply! Here' the output:
Instant email notifications FTW! And it seems that your /tmp has correct permissions. I can't yet figure out the problem with so little information available but let's acquire more ;)

Try changing ONLY_EXTRACT variable in et-sdl-sound script to "yes":
```

# Just extract et-sdl-sound.so
ONLY_EXTRACT="no"

```
and run et-sdl-sound. It wont launch ET this time but instead just extract et-sdl-sound.so to /tmp/. Now we need to check if such file is created properly; post the output of the following commands here:
```

stat /tmp/et-sdl-sound.so
file /tmp/et/sdl-sound.so
LD_PRELOAD=/tmp/et-sdl-sound.so glxgears

```

---

### Post by MattThLinuxNewb on 2008-05-25
Ok I got it working... music and ET finally! Yesss!
Turns out LD_PRELOAD fails on binaries owned by the root user for "security reasons". (Found this out after some googling on ls.so) So to fix it I entered:
```

cd /usr/local/games/
sudo chown -R matt enemy-territory

```
Not sure why et was owned by root come to think of it.

Anyway thanks for your fast response. And et-sdl-sound of course. Cheers!

---

### Post by nullkey on 2008-05-25
> **MattThLinuxNewb said:**
> Ok I got it working... music and ET finally! Yesss!
Turns out LD_PRELOAD fails on binaries owned by the root user for "security reasons". (Found this out after some googling on ls.so) So to fix it I entered:
That's really strange. I know LD_PRELOAD fails on SUID binaries (chmod +s) but it certainly shouldn't fail when binary is just owned by root. I'd like to see source for that information.

---

### Post by MattThLinuxNewb on 2008-05-25
> I know LD_PRELOAD fails on SUID binaries
Yeah that's what I read in some page about "fakeroot".
> ... This is due to the fact that mount is an suid root binary, and for security reasons LD_PRELOAD is disabled on suid binaries.
I'm relatively new to linux and just assumed SUID binaries were binaries owned by root? So there's a difference? Hmm well it works now in any case.

---

### Post by nullkey on 2008-05-25
> **MattThLinuxNewb said:**
> 
I'm relatively new to linux and just assumed SUID binaries were binaries owned by root? So there's a difference? Hmm well it works now in any case.
SUID bits means that binary is executed under file owner permissions. For example /bin/passwd has SUID bit set and owned by root so it is executed always under root permissions (otherwise it wouldn't be able to modify your account information). You can set suid by `chmod +s` and clear it with `chmod -s`. Try `stat /bin/passwd` and you should see something like "Access: (4711/-rw**s**--x--x)".

---

### Post by dyntryx on 2008-05-25
Hi all!

Just popped in to say this script fixed my no-sound issues in Urban Terror 4.1 after upgrading to (K)ubuntu Hardy (8.04).

I simply used the commands outlined in the original post and modified the script to run Urban Terror instead of Enemy Territory.

Thank you very much for your help and support [nullkey]("http://ubuntuforums.org/member.php?u=239357")!  Also, might I suggest that you add a script for Urban Terror to [your homepage]("http://nullkey.ath.cx/~stuff/et-sdl-sound/")?  The only problem I see with this is there is no official installation package for the Ubuntu folks, so the location of the game is decided by the user.  However, there could still be an 'urt-sdl-sound' script with the correct binaries (ioUrbanTerror.i386 or ioUrbanTerror.x86_64) and default directory name (UrbanTerror).  Then all the user has to do is edit the GAME_PATH variable, which would be very simple to explain and accomplish, even for a new user.

Also, from my experience, Ubuntu uses /usr/share/games/ to store most files for games, and /usr/games/ as the directory for the binary to run the game (which occasionally can be a script that points to /usr/share/games/).  To improve the Ubuntu experience it may be a good idea to add /usr/share/games/ as one of the default directories to search for game *folders* and /usr/games/ to search for game *binaries*.  Then again, teaching users to edit the GAME_PATH variable may be the easier solution.

As always, your mileage may vary and thanks again!

---

### Post by oaXman on 2008-06-02
Thanks nullkey for fixing my sound issue! Now I can use amarok / ventrilo while playing et. I'm just having a minor 'problem' left.

I can only run the script by typing ./et-sdl-sound @ terminal.
I'd like to know that what do I need to do to run the script in command line. Or how to set XQF to start ET through that script. (XQF starts games with command line commands) If I insert "et-sdl-sound" or "./et-sdl-sound" to XQF, it fails. Normally, without the script, the command is "et".

Current settings:
XQF-Preferences-Games-Enemy Territory
Invoking
Command line: **et**
Working directory: /usr/local/games/enemy-territory
Custom CFG: autoexec.cfg

Thx in advance.

---

### Post by nullkey on 2008-06-02
> **oaXman said:**
> Thanks nullkey for fixing my sound issue! Now I can use amarok / ventrilo while playing et. I'm just having a minor 'problem' left.

I can only run the script by typing ./et-sdl-sound @ terminal.
I'd like to know that what do I need to do to run the script in command line. Or how to set XQF to start ET through that script. (XQF starts games with command line commands) If I insert "et-sdl-sound" or "./et-sdl-sound" to XQF, it fails. Normally, without the script, the command is "et".

Current settings:
XQF-Preferences-Games-Enemy Territory
Invoking
Command line: **et**
Working directory: /usr/local/games/enemy-territory
Custom CFG: autoexec.cfg

Thx in advance.
You need to change working directory into correct one. For example if you have et-sdl-sound in /home/user/Desktop, set Working directory to "/home/user/Desktop" and command line to "et-sdl-sound".

---

### Post by abelthorne on 2008-07-19
Hello,
I've just tried using your script with Enemy Territory, but it doesn't work.
I'm using Ubuntu Hardy, which includes PulseAudio (I guess it might be related to my problems).

I installed ET as normal user, in ~/games/enemy-territory and copied et-sdl-sound and et-sdl-sound.so in that directory.
Also, I created a script as explained before (with the "LD_PRELOAD" stuff).

When I launched ET, either with et-sdl-sound or with the script I created, I had no sound. After looking in the log, I had an error message for the sound part, claiming that it could not find a given library. I don't remember its name but I tracked it down with Google and found that it was in libasound2-plugins, which I installed.

Since then, when I launch ET, I still don't have sound but when I quit, it "freezes" Ubuntu (the et process is eating 100% CPU) and I have to restart X.

Any idea on what I should do/try/fix ?

EDIT : in fact, it seems that SDL has broke on my system : if I start ScummVM, I don't get any sound (error message at startup "no available audio device" and it ends up taking 100% CPU too. I guess et-sdl-sound has nothing to do with my problems. :/

---

### Post by nullkey on 2008-07-19
> **abelthorne said:**
> ...
I'm using Ubuntu Hardy, which includes PulseAudio (I guess it might be related to my problems).
...
See [pulseaudio wiki](http://www.pulseaudio.org/wiki/PerfectSetup). You need to change SDL_AUDIODRIVER variable in et-sdl-sound script to
```

SDL_AUDIODRIVER=esd
```

---

### Post by abelthorne on 2008-07-19
Well, I had seen that but I didn't understand where it had to be changed. Thanks. :)

Anyway, it still doesn't work and I've messed thing up a little bit more.

As ScummVM crashed too, I installed libsdl1.2debian-pulseaudio, which removes libsdl1.2devian-alsa. Now ScummVM works and has sound but et-sdl-sound cant't find anything :

------- sound initialization -------
SDL audio driver initializing...
SDL_AudioDriverName() = NULL
------------------------------------

I guess it's because that it relies on libsdl1.2debian-alsa, which seems to crash SDL apps on my system. :/

EDIT : ok, removed libsdl1.2debian-pulseaudio and installed libsdl1.2debian-all. ET now starts with sound !

Now I'll have to find how I can fix the problem with ScummVM (and probably other SDL apps too), but it has nothing to do with this thread. Thanks a lot. :)

---

### Post by nullkey on 2008-07-19
> **abelthorne said:**
> 
------- sound initialization -------
SDL audio driver initializing...
SDL_AudioDriverName() = NULL
------------------------------------

You can try removing that SDL_AUDIODRIVER-line completely but then SDL might prefer oss over alsa (and that's the reason I originally put it there).

---

### Post by abelthorne on 2008-07-19
Well, I've removed libsdl-all and reinstalled libsdl-alsa (needed by another SDL app) and I have no sound in ET. Tried to set SDL_AUDIODRIVER to "oss" or commenting the line in et-sdl-sound to no avail.

I guess I really need to set SDL_AUDIODRIVER to "esd" and install libsdl-esd (or libsdl-all which includes it). Is that correct or am I mistaken with the libsdl-esd part ? Is your script supposed to work with libsdl-alsa only when used with PulseAudio (sorry, this might sound dumb but these sound server problems are new to me) ?

---

### Post by nullkey on 2008-07-19
> **abelthorne said:**
> 
I guess I really need to set SDL_AUDIODRIVER to "esd" and install libsdl-esd (or libsdl-all which includes it). Is that correct or am I mistaken with the libsdl-esd part ? Is your script supposed to work with libsdl-alsa only when used with PulseAudio (sorry, this might sound dumb but these sound server problems are new to me) ?
I think you are fine with that "esd" driver. AFAIK pulseaudio is rewritten esd (enlightement sound daemon) and also maintains old api for old esd applications. But as I suggested in previous reply, leaving SDL_AUDIODRIVER completely out (not setting to anything, just remove it) gives SDL possibility to choose (hopefully) best audio driver for your system.

---

### Post by tromort on 2008-07-31
that link seems to be broken.

---

### Post by 3togo on 2008-08-04
I am currently using Hardy(AMD64)
If I change a line inside et-sdl-sound
SDL_AUDIODRIVER="esd" 
or
SDL_AUDIODRIVER="pulse"

I will get the following error
------- sound initialization -------
SDL audio driver initializing...
SDL_AudioDriverName() = NULL
------------------------------------

If I stick to 
SDL_AUDIODRIVER="alsa"
then I get

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x95aebb8 dma buffer
No background file.
----------------------


Either way will start et without any sound.

:(

---

### Post by abelthorne on 2008-08-04
You need to have the corresponding libSDL package installed. If you have libsdl-alsa, SDL apps will use ALSA output (but ALSA support is broken when using PulseAudio as sound system). To use ESD or PulseAudio in SDL apps, you'll need libsdl-esd ou libsdl-pulseaudio, respectively.
Also, you can install libsdl-all to have all sound outputs, but unless you specify it with the SDL_AUDIODRIVER variable (as does ET-SDL), the default system used will be ALSA.

Currently, there are issues with SDL and PulseAudio :
- if you use ALSA output (SDL_AUDIODRIVER="alsa"), applications will crash
- if you use PulseAudio (SDL_AUDIODRIVER="pulse"), some applications will have sound issues
- if you use ESD (SDL_AUDIODRIVER="esd"), the sound will be ok in most apps but some won't output sound at all (they need SDL_AUDIODRIVER set to "pulse")
Moreeover, PulseAudio sets an OSS emulation that can be used with some apps.

If you stick with PulseAudio in Hardy, you have three possibilities for SDL apps :
- install libsdl-all and manually set SDL_AUDIODRIVER to the most suited output (i.e. for ET use "esd", for ScummVM use "pulse") ; this can be a pain, as you'll have to set the variable for each app you use or they'll use ALSA by default and will crash in most case
- install libsdl-pulseaudio and set SDL_AUDIODRIVER to "pulse" if needed (e.g. ET) ; apps won't crash and you should have sound all the time but in a lot of apps (including ET) you'll have bad sound
- install libsdl-esd and set SDL_AUDIODRIVER to "esd" if needed in order to use the ESD emulation ; apps won't crash, you'll have nice sound but a few apps won't output sound at all

Note : I write libsdl-all (-esd, etc.) because it is shorter. If you search for the packages in Synaptic, the exact name is libsdl1.2debian-all (or -esd, etc.).

---

### Post by nullkey on 2008-08-06
> **tromort said:**
> that link seems to be broken.
It **was** broken. I've moved to another city and thus had to move my server also ;)

---

### Post by billybag on 2008-08-17
i completely give up

---

### Post by Kubunteando on 2008-08-29
This worked for me in Kubuntu 8.04:

[http://gentoo-wiki.com/HOWTO_Quake_III_Arena_/_Enemy_Territory#Enable_Sound](http://gentoo-wiki.com/HOWTO_Quake_III_Arena_/_Enemy_Territory#Enable_Sound)

I used the ALSA part.

Perfect sound in Enemy Territory!

---

### Post by brightsim on 2008-10-25
Hi!

Finally i got my sound working on ET using the SDL sound script + Pulseaudio but unfortunately i am experiencing a slight delay (about 1 second) of the sound output. 
can anyone tell me what can be done about this issue? :/

---

### Post by Azure.Rise on 2008-10-25
brightsim, go into the options, then settings, and uncheck "Use Compressed Sounds".

---

### Post by gcbzzzz on 2008-11-17
this worked just fine in 8.04 (well, i had to close gaim and firefox to have sound...)

now updating to 8.10 and it wont work. i've already followed all steps in several twikis around.

i'm just not crazy enough to download scripts with binary data in it :)

---

### Post by michelino on 2009-02-13
hi nullkey,

i'm on intrepid.

while i'm playing with ET, the game quit with this error:

> /usr/local/games/enemy-territory/et-sdl-sound: line 1582: 22689 Segmentation fault      LD_PRELOAD="${LD_PRELOAD}:${TMP_DIR}/et-sdl-sound.so" ./$GAME_BIN $*

:confused:

tnx

---

### Post by michelino on 2009-02-15
:popcorn:

---

### Post by Dizzle7677 on 2009-02-17
This is what works for me:
Set everything in Sys->Prefs->Sounds to ALSA
Killall PulseAudio

No problems. Since I build the kernel from source I get any new patches,etc for alsa with no need to muck about with seperate alsa driver installs for my hardware.

---

### Post by thumb on 2009-02-21
Thanks, this worked for me. I get some static when its loading up for some reason but it doesn't last for long. I had this problem in ET where if I press the CTRL key and then the number 3(crouching and then selecting the smg for example) the Escape menu would pop up.

There's a fix for this on the forums [here]("http://ubuntuforums.org/showthread.php?t=473297") so I just added that to this file to work with it, I've attached it here for anyone who has the same problem.

---

### Post by devilscemo on 2009-04-21
Hi i am new to Ubuntu and i have tried 2 read all the thread but sometimes i don't really understand what's going on... 
I have Ubuntu 8.04 and i installed pulseaudio plus the SDL-sound that was at the beginning of the topic. I have also installed the lib2.dev libraries and so on. Pulseaudio seems to work fine but when i start et there is just no sounds.
the only way for me 2 get ET to have sound is :
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

but that is very annoying since, from my understanding, it "steals" the sound from other software so it is impossible to play Et and have teamSpeak on at the same time... For example i have 2 close all my music software once i start ET...
what should I do?? Thank you for your time

---

### Post by Solvanora on 2009-04-23
So, did anything change with our brand spanking new Jaunty Jackalope?

I just installed 9.04 half an hour ago. ET 15 minutes ago, but still get the same error:

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp

Something did change with the sound, beccause im able to hear both the firefox sounds and rhytmbox at the same time (so its mixed).

Any thoughts, any news?

---

### Post by linux_lover69 on 2009-04-28
Thank you, It even worked with the new jaunty.

---

### Post by ogopogo on 2009-05-06
Ok really frustrated here.  Too many bugs in Jackalope and 8.04 Ubuntu studio so went to a regular 8.04.2 Hardy install.  3 hours later got the sound working in Flash, firefox, Vlc, Alsa is going well too. 

Sound Card is a USB v1.1 Edirol UA25.  So I know it is giving me trouble but I am determined.  

Now trying to get SDL audio (thanks Nullkey) to play Enemy Territory w sound.  Nothing works.  If I execute ./et-sdl-sound, the game won start and my desktop get zoomed in like 400% or something really wierd.  

here is the output,  seem like SDL is loading fine Is it a problem with NVIDIA.  Why me.  It`s just not fair!  Ubuntu is sweet and windows sucks!  But I`ll have to go back to it if this keeps up!  Not everyone is a Linux developer so this is just an impossible OS!

Please Help me!


_______________________________________________________
_______________________________________________________
mike@komputa:~$ ./et-sdl-sound
[et-sdl-sound] info   : et.x86 is installed to /usr/local/games/enemy-territory
[et-sdl-sound] info   : 32-bit libSDL.so is installed to /usr/lib/libSDL-1.2.so.0.11.1
[et-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
[et-sdl-sound] info   : launching the game...
Read /usr/local/games/enemy-territory/et.x86 (1538888 bytes)
0x817d6c0: e9 3b be d7 af 
0x817dce0: e9 5b b8 d7 af 
0x817dd70: e9 0b b8 d7 af 
0x817dd90: e9 2b b8 d7 af 
0x817dd80: e9 7b b8 d7 af 
Found ET 2.60 (CRC32 = 0x3b18a889)
Using SDL backend.
et-sdl-sound-r29 (Apr 13 2008 13:59:02, 3.4.6 (Gentoo 3.4.6-r2 p1.5, ssp-3.4.6-1.0, pie-8.7.10)) loaded.
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/mike/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6100 nForce 405/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6100 nForce 405/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x95a9740 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/mike/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/mike/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/mike/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad466f40  
Sys_LoadDll(ui) succeeded!
Received signal 11, exiting...
./et-sdl-sound: line 1582:  6472 Segmentation fault      LD_PRELOAD="${LD_PRELOAD}:${TMP_DIR}/et-sdl-sound.so" ./$GAME_BIN $*
[et-sdl-sound] info   : done

---

### Post by Uriziel on 2009-07-12
My friend has problem and I don't know how to help him
He has Ubuntu 9.04
He's useing this launch script:
```
#!/bin/bash
export ETSDL_SDL_LIB="/usr/lib/libSDL-1.2.so.0.11.2"
export SDL_AUDIODRIVER="alsa"
cd /home/arek/gry/et/
LD_PRELOAD="/home/arek/gry/et/et-sdl-sound.so"  ./et.x86 +connect $
```
And he's got first like after runing et:
```
ERROR: ld.so: object '/home/arek/gry/et/et-sdl-sound.so ' from LD_PRELOAD cannot be preloaded: ignored.
```

/home/arek/gry/et/et-sdl-sound.so exists for sure
We've tried sudo chown -R arek:arek ~/gry/
And even sudo chmod -R -s ~/gry/et/
But didn't work

---

### Post by beefjerkymonster on 2009-07-21
Why is there no solution for this?  ](*,)

Sure, there's the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" thing, but that involves root privlidges and such.

There's also the script posted early in the thread, but I'm having this problem with other games.

Why can't this work out of the box? Ubuntu is a really mature distro imho, I've been using it for a while. Very stable, things just work. But this problem has been around for so long..? #-o

---

### Post by shrndegruv on 2009-08-10
the echo trick does not work for me:(...any other suggestions?

---

### Post by Stosskraft on 2009-10-06
I'm having a similar problem. Here's what is output when I run 
killall esd; et; esd 

```
------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0xed7cf000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/yanek/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/yanek/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/yanek/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xebc3df40  
Sys_LoadDll(ui) succeeded!
```

Having a bit of problems, any suggestions. Tried the steps above, correctly as far as I know and still no joy. Would appreciate a leg-up.

---

### Post by Stosskraft on 2009-10-08
does anyone have ET working with 9.04, are we barking up the wrong tree?

---

### Post by Stosskraft on 2009-10-11
*bump*

---

### Post by Tobis87 on 2009-10-24
Hi,

I already send a mail to the maintainer of et-sound-sdl, but I didn't get an answer.

Could you please add the hooks for Rtcw 1.41b in et-sdl-sound,
```
Read /daten/Spiele/ID/Return to Castle Wolfenstein/wolf.x86 (1496148 bytes)
You are not running a recognized version of Enemy Territory or RTCW (CRC32 = 0xfb070fcf)
Wolf 1.41b-MP linux-i386 May  8 2006
```

as well as the hooks for Quake 3 smp?
```
Read /daten/Spiele/ID/Quake III Arena/quake3-smp.x86 (1295316 bytes)
You are not running a recognized version of Enemy Territory or RTCW (CRC32 = 0x2baa1)
Q3 1.32c linux-i386 May  8 2006
```

Thanks in advance.

---

### Post by abelthorne on 2009-12-16
Hello,
Although the hack works fine with ET on my system, I can't get it to work for RTCW: the game runs fine but I have no sound at all. Any idea?

---

### Post by davygrvy on 2009-12-31
```
$ ./et-sdl-sound
[et-sdl-sound] info   : et.x86 is installed to /usr/share/games/enemy-territory
[et-sdl-sound] info   : 32-bit libSDL.so is installed to /usr/lib32/libSDL-1.2.so.0.11.2
[et-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
[et-sdl-sound] info   : launching the game...
Read /usr/share/games/enemy-territory/et.x86 (1599964 bytes)
You are not running a recognized version of Enemy Territory or RTCW (CRC32 = 0xbeaf33c4)
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
...
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
...

```

Oh so close..  I tried editing hooks.cpp and adding 0xbeaf33c4 to the main switch for et2.60b, but no luck getting it to work.

If I load et.x86 into a debugger, what addresses should I be searching for?

EDIT: Umm..  no symbols.  My God, how in the world did you hack these apps?
```
$ nm -A /usr/share/games/enemy-territory/et.x86 
nm: /usr/share/games/enemy-territory/et.x86: no symbols
```

---

### Post by Jestersage on 2010-01-08
The new update from Playdeb seems to have fix the issue. Go and update/get the ET from there; no need to fiddle with all these hacks now.

Of course, you will have to fix the PB, but that's a different story. Playing it on that HDTV is... awesome.

---

### Post by davygrvy on 2010-01-08
The executable is no different.  CRC32 = 0x6ab49f82, same as before.  It is still not compiled against SDL like ioQuake.   Also, it's still a 32-bit app.

BUT....  sound is working..  wtf?

There's no changelog, So I have no clue why it is working.

---

### Post by ViperScull on 2010-01-08
The opposite. Installig via playdeb worked fine without doing anything. 

With the latest uptade by playdeb yesterday, sound stops working after 15 or 20 minutes and the game crashes when i try to exit.

Is there any way to remove the latest update??

---

### Post by trajo on 2010-08-29
WOW! It works for me ty!


But I have 1 question... is this compatible with Punkbuster? It will be detect et-sdl-sound like a cheat?

---

### Post by lyka on 2010-09-16
To fix sound on Ubuntu lucid lynx you can also install libsdl1.2debian-all and use et-sdl-sound:

> sudo aptitude install libsdl1.2debian-all

> 
cd /pathto/enemy-territory
wget -q -O - [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound

launch with 
> et-sdl-sound

installing libsdl1.2debian-all will remove libsdl1.2debian-pulseaudio and metapackage ubuntu-desktop.

On lucid i couldn't find a better solution.

---

### Post by Devport on 2010-09-30
On amd64 to make sound work again on Maverick with getdeb et I manually downloaded and extracted libsdl1.2debian-alsa

[http://packages.debian.org/sid/i386/libsdl1.2debian-alsa/download](http://packages.debian.org/sid/i386/libsdl1.2debian-alsa/download)

and copied usr/lib/libSDL-1.2.so.0.11.3 to /usr/lib32 and set the driver to alsa in /usr/games/et :

export SDL_AUDIODRIVER="alsa"

---

### Post by LeoEvs on 2010-11-21
Hi. i'm using ubuntu 10.10, and the ET continues without sound.
Then when i use the command ./et-sdl-sound i don't have any error but do not loads sound, which appears as follows: 

------- sound initialization -------
SDL audio driver initializing...
SDL_AudioDriverName() = NULL
------------------------------------

Obs. using alsa 1.0.23. and card VIA8237.

Anyone have any ideas to fix this?
thnx

---

### Post by LeoEvs on 2010-11-22
Ok. I solved the problem just changing a line # SDL audio driver inside et-sdl-sound of "alsa" to "pulse"

SDL_AUDIODRIVER="pulse"
:popcorn:

---

### Post by azurehoney on 2011-06-17
Odd that the author has not updated his post with latest info.

1.
et-sdl-sound has moved, new web site address is:

[http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)

2.
packages you need to install:
[FONT="Courier New"]libsdl-sound1.2
libsdl1.2-dev
libsdl1.2-debian-all[/FONT]

3.
for 64bit I run into problem:
[FONT="Courier New"]------- sound initialization -------
Could not open libSDL.so: libSDL.so: wrong ELF class: ELFCLASS64
Please check that ETSDL_SDL_LIB environment variable points to valid 32-bit SDL library.
------------------------------------[/FONT]

I had to change "export ETSDL_SDL_LIB" line from:

[FONT="Courier New"]export ETSDL_SDL_LIB="libSDL.so"
[/FONT]
to:
[FONT="Courier New"]export ETSDL_SDL_LIB="/usr/lib32/libSDL-1.2.so.0.11.3"[/FONT]


My complete executable bash script that launches the game with etpro mod:

```
#!/bin/bash
export ETSDL_SDL_LIB="/usr/lib32/libSDL-1.2.so.0.11.3"
export SDL_AUDIODRIVER="alsa"
cd /home/myname/et
LD_PRELOAD="${LD_PRELOAD}:/home/myname/et/et-sdl-sound.so" ./et.x86 +set fs_game etpro $*
```

---

### Post by Perfect Storm on 2011-06-17
> Odd that the author has not updated his post with latest info.

He haven't been active on UF since 2008.
If you wish, you can start a new thread for this subject and maintain it, and I'll close this old thtread.

---

### Post by OakRaider4Life on 2011-06-28
Help!

After running

```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.gz | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
```

My Terminal returns the following error


```
gzip: stdin: unexpected end of file
```

I am a brand new linux convert, so any help which can be offered is greatly appreciated!

Just FYI, I'm running 64-bit Natty and have tried options 1-3 on this instruction page ([https://help.ubuntu.com/community/EnemyTerritory#Method%204](https://help.ubuntu.com/community/EnemyTerritory#Method%204)) so getting this step to work is my last hope!

---

