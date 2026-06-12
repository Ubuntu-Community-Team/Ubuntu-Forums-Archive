---
title: "UT2004 openAL alsa-dev"
date: 2005-07-14
forum: Gaming &amp; Leisure
---

### Post by DarkManX4lf on 2005-07-14
i read in this guide:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=40](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=40)

in section three if i use the openAL module suggested there, that i would get a performance boost when playing UT2004 and using openAL, and an Audigy card.  I then downloaded it, extracted, in terminal i wento the src dir, and typed make, to make the module (not sure if its a module) but i get this error

> gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_listener.c
In file included from al_listener.c:23:
alc_context.h:23:21: pthread.h: No such file or directory
alc_context.h:24:23: semaphore.h: No such file or directory
In file included from alc_context.h:30,
                 from al_listener.c:23:
alc_device.h:23:28: alsa/asoundlib.h: No such file or directory
In file included from alc_device.h:28,
                 from alc_context.h:30,
                 from al_listener.c:23:
al_source.h:23:28: alsa/asoundlib.h: No such file or directory
In file included from al_source.h:28,
                 from alc_device.h:28,
                 from alc_context.h:30,
                 from al_listener.c:23:
al_buffer.h:31: error: syntax error before "int32_t"
al_buffer.h:31: warning: no semicolon at end of struct or union
al_buffer.h:34: error: syntax error before '}' token
al_buffer.h:35: warning: type defaults to `int' in declaration of `AL_buffer'
al_buffer.h:35: warning: data definition has no type or storage class
al_buffer.h:37: error: syntax error before '*' token
al_buffer.h:37: warning: type defaults to `int' in declaration of `_alLockBuffer'
al_buffer.h:37: warning: data definition has no type or storage class
al_buffer.h:38: error: syntax error before '*' token
In file included from alc_device.h:28,
                 from alc_context.h:30,
                 from al_listener.c:23:
al_source.h:33: error: syntax error before "AL_buffer"
al_source.h:33: warning: no semicolon at end of struct or union
al_source.h:35: error: syntax error before '}' token
al_source.h:36: warning: type defaults to `int' in declaration of `AL_queue'
al_source.h:36: warning: data definition has no type or storage class
al_source.h:42: error: syntax error before "snd_pcm_t"
al_source.h:42: warning: no semicolon at end of struct or union
al_source.h:43: warning: type defaults to `int' in declaration of `vol_ctl'
al_source.h:43: warning: data definition has no type or storage class
al_source.h:44: error: syntax error before '*' token
al_source.h:44: warning: type defaults to `int' in declaration of `send_ctl'
al_source.h:44: warning: data definition has no type or storage class
al_source.h:50: error: syntax error before '*' token
al_source.h:50: warning: type defaults to `int' in declaration of `buffer'
al_source.h:50: warning: data definition has no type or storage class
al_source.h:51: warning: built-in function `index' declared as non-function
al_source.h:53: error: syntax error before '*' token
al_source.h:53: warning: type defaults to `int' in declaration of `first_q'
al_source.h:53: warning: data definition has no type or storage class
al_source.h:54: error: syntax error before '*' token
al_source.h:54: warning: type defaults to `int' in declaration of `last_q'
al_source.h:54: warning: data definition has no type or storage class
al_source.h:55: error: syntax error before '*' token
al_source.h:55: warning: type defaults to `int' in declaration of `current_q'
al_source.h:55: warning: data definition has no type or storage class
al_source.h:75: error: syntax error before '}' token
al_source.h:76: warning: type defaults to `int' in declaration of `AL_source'
al_source.h:76: warning: data definition has no type or storage class
al_source.h:78: error: syntax error before '*' token
al_source.h:79: error: syntax error before '*' token
In file included from alc_context.h:30,
                 from al_listener.c:23:
alc_device.h:34: error: syntax error before "snd_ctl_t"
alc_device.h:34: warning: no semicolon at end of struct or union
alc_device.h:39: error: syntax error before '}' token
alc_device.h:41: error: syntax error before '*' token
alc_device.h:42: error: syntax error before '*' token
In file included from al_listener.c:23:
alc_context.h:37: error: syntax error before "AL_source"
alc_context.h:37: warning: no semicolon at end of struct or union
alc_context.h:39: warning: type defaults to `int' in declaration of `thread'
alc_context.h:39: warning: data definition has no type or storage class
alc_context.h:40: error: syntax error before "mutex"
alc_context.h:40: warning: type defaults to `int' in declaration of `mutex'
alc_context.h:40: warning: data definition has no type or storage class
alc_context.h:41: error: syntax error before "cond"
alc_context.h:41: warning: type defaults to `int' in declaration of `cond'
alc_context.h:41: warning: data definition has no type or storage class
alc_context.h:49: error: syntax error before '*' token
alc_context.h:51: warning: type defaults to `int' in declaration of `AL_context'alc_context.h:51: warning: data definition has no type or storage class
alc_context.h:53: error: syntax error before '*' token
alc_context.h:53: warning: type defaults to `int' in declaration of `_alcCurrentContext'
alc_context.h:53: warning: data definition has no type or storage class
alc_context.h:58: error: syntax error before '*' token
alc_context.h:58: error: syntax error before '*' token
alc_context.h:58: warning: type defaults to `int' in declaration of `_alFindSource'
alc_context.h:58: warning: data definition has no type or storage class
alc_context.h:60: error: syntax error before '*' token
al_listener.c: In function `alListenerf':
al_listener.c:84: error: `ctx' undeclared (first use in this function)
al_listener.c:84: error: (Each undeclared identifier is reported only once
al_listener.c:84: error: for each function it appears in.)
al_listener.c:92: warning: implicit declaration of function `pthread_mutex_lock'al_listener.c:104: warning: implicit declaration of function `pthread_mutex_unlock'
al_listener.c: In function `alListener3f':
al_listener.c:109: error: `ctx' undeclared (first use in this function)
al_listener.c: In function `alListenerfv':
al_listener.c:141: error: `ctx' undeclared (first use in this function)
al_listener.c: In function `alGetListeneriv':
al_listener.c:194: error: `ctx' undeclared (first use in this function)
al_listener.c: In function `alGetListenerfv':
al_listener.c:261: error: `ctx' undeclared (first use in this function)
make: *** [al_listener.o] Error 1



i went to the linux-gamers forum, and it was stated there (from another person posting the similar problem) that i need alsa-dev package from my distro...but in synpatic i cant find it, and i cant apt-get install alsa-dev.... 

so basically i want to know how do i get this to work ?

---

### Post by DarkManX4lf on 2005-07-15
anyone know how to get this compiled properly?

---

### Post by evilghost on 2005-07-15
Before you go down this path, perhaps try running UT2004 with sound off, to see if recompiling ALSA would do anything for you?  Seems like a  lot of work that may have zero yield for you...


```

gedit ~/.ut2004/System/UT2004.ini
(Find line "UseSound=True" and change to UseSound="False" under [Engine.GameEngine])

```

Try running UT2004 then, with a "stat fps" and see if there's even a change.  On my system, there was none.  You could also rename/move the openal.so in the [UT2004 Installation Folder]/System directory if you don't trust UseSound=False. :)

---

### Post by DarkManX4lf on 2005-07-16
[QUOTE=evilghost]Before you go down this path, perhaps try running UT2004 with sound off, to see if recompiling ALSA would do anything for you?  Seems like a  lot of work that may have zero yield for you...


```

gedit ~/.ut2004/System/UT2004.ini
(Find line "UseSound=True" and change to UseSound="False" under [Engine.GameEngine])

```

Try running UT2004 then, with a "stat fps" and see if there's even a change.  On my system, there was none.  You could also rename/move the openal.so in the [UT2004 Installation Folder]/System directory if you don't trust UseSound=False. :)[/QUOTE]


 yep, i had to rename openal.so, it the sound would still be there if i set "usesound=false" also i did get a fps boost, almost +20fps

---

### Post by evilghost on 2005-07-16
Woah....I just did the UseSound=False, and it had no affect.  I renamed openal.so and saw about a 15 to 20 fps boost.  **Excellent**.  Now we just need to figure out how to recompile openal.so for our system.  I've got a Sound Blaster Live so we should be able to use the same openal.so module.

Today I'm going to try to get this figured out and will gladly share anything I've learned.

---

### Post by evilghost on 2005-07-16
Here you go:

```

sudo apt-get install alsa-source
sudo apt-get install alsa-headers
cd ~/openal-alsa-emu10k1-1.2/src
make

```

Now I get:

```

luser@400sc:~/openal-alsa-emu10k1-1.2/src$ make
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_listener.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_source.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_buffer.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_play.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_able.c
al_able.c:20:22: ansidecl.h: No such file or directory
al_able.c:24: error: syntax error before "ATTRIBUTE_UNUSED"
al_able.c: In function `alEnable':
al_able.c:25: error: number of arguments doesn't match prototype
../include/AL/al.h:72: error: prototype declaration
al_able.c: At top level:
al_able.c:29: error: syntax error before "ATTRIBUTE_UNUSED"
al_able.c: In function `alDisable':
al_able.c:30: error: number of arguments doesn't match prototype
../include/AL/al.h:74: error: prototype declaration
al_able.c: At top level:
al_able.c:34: error: syntax error before "ATTRIBUTE_UNUSED"
al_able.c: In function `alIsEnabled':
al_able.c:35: error: number of arguments doesn't match prototype
../include/AL/al.h:76: error: prototype declaration
make: *** [al_able.o] Error 1

```

Have to run, hopefully this will be enough to get us started down the path to a solution.  I hope to check back later in the afternoon, hopefully you've found a solution ;)

---

### Post by DarkManX4lf on 2005-07-16
nah i havent found any solution, but i do know that UT2004 comes with its own openal and libSDL-1.2.so.0 sources, im going to see if i can compile that.  i'm pretty new to linux so bear with me a bit :)



edit

yea it seems that i cant compile the openal-alsa-emu10k1-1.2, i get the same error as you do...but i can compile the one that UT2004 gives you, but that one only gave me a slight increase (2fps)

---

### Post by tomchuk on 2005-07-16
1st, Install the build-essential package
2nd, if you'd like an easy way to fix this youself in the future without blindly installing unnecessary packages, install apt-file and search for the missing includes:
```

$ apt-file search usr/include/pthread.h
libc6-dev: usr/include/pthread.h
$ apt-file search usr/include/semaphore.h
libc6-dev: usr/include/semaphore.h
$ apt-file search usr/include/alsa/asoundlib.h
libasound2-dev: usr/include/alsa/asoundlib.h
$ apt-file search usr/include/ansidecl.h
binutils-dev: usr/include/ansidecl.h

```
All you needed to install was libc6-dev, libasound2-dev and binutils-dev

---

### Post by evilghost on 2005-07-16
[QUOTE=tomchuk]1st, Install the build-essential package
2nd, if you'd like an easy way to fix this youself in the future without blindly installing unnecessary packages, install apt-file and search for the missing includes:
```

$ apt-file search usr/include/pthread.h
libc6-dev: usr/include/pthread.h
$ apt-file search usr/include/semaphore.h
libc6-dev: usr/include/semaphore.h
$ apt-file search usr/include/alsa/asoundlib.h
libasound2-dev: usr/include/alsa/asoundlib.h
$ apt-file search usr/include/ansidecl.h
binutils-dev: usr/include/ansidecl.h

```
All you needed to install was libc6-dev, libasound2-dev and binutils-dev[/QUOTE]

Wow, didn't even realize that.  After doing a "sudo apt-get install libc6-dev" I was able to successfully compile the package.  Thank you for your help.

```

luser@400sc:~/openal-alsa-emu10k1-1.2/src$ make
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_able.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_state.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_doppler.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_distance. c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_error.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_ext.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_vector.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_context. c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_speaker. c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_device.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_state.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_error.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alc_ext.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alut_main.c
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c alut_wav.c
gcc -shared -Wl,-soname,libopenal.so.0 -o libopenal.so.0.1.2 al_listener.o al_so urce.o al_buffer.o al_play.o al_able.o al_state.o al_doppler.o al_distance.o al_ error.o al_ext.o al_vector.o alc_context.o alc_speaker.o alc_device.o alc_state. o alc_error.o alc_ext.o alut_main.o alut_wav.o -lasound -lpthread -lm
luser@400sc:~/openal-alsa-emu10k1-1.2/src$ ls -la|grep -i openal
-rwxr-xr-x  1 luser luser 51585 2005-07-16 11:36 libopenal.so.0.1.2

```

Will let you know if I see an FPS decrease or increase.

---

### Post by DarkManX4lf on 2005-07-17
well i compiled it, and  even tho there were errors, it spat o ut a module, when i used that module i noticed an avg 10fps in crease and a max 20fps increase so i would say its good...maybe if we get rid of those errors we can get more performance.


EDIT

i just tested the new module, and it seems fine BUT the volume seems to be very low, even tho i turned it up high in UT2004, when using the older module this wasnt the case....and i had the same errors as the above posted....hopefully we can get t hem fixed.

---

### Post by rwabel on 2005-08-09
I've compiled the openal. What do I've to do now? Do I need to install them or load them in the kernel? How can I remove them later?

---

### Post by rpgcyco on 2005-08-13
> i just tested the new module, and it seems fine BUT the volume seems to be very low, even tho i turned it up high in UT2004, when using the older module this wasnt the case....and i had the same errors as the above posted....hopefully we can get t hem fixed.

Have you found a solution to this problem by any chance? This hardware accelerated OpenAL works wonders, but unfortuately doesn't work right itself, as you know. :(

> I've compiled the openal. What do I've to do now? Do I need to install them or load them in the kernel? How can I remove them later?

Rename the openal.so file in the UT2004 System directory (/usr/local/games/ut2004/System) and then copy the libopenal.so.0.1.2 to the UT2004 System directory as openal.so

- Rpg Cyco

---

### Post by DarkManX4lf on 2005-08-13
yea i havent found a fix to this problem yet, as i am new to linux...but hopefullysomeone on this board could help.

---

### Post by evilghost on 2005-08-13
Oddly enough, I'm not having the problem at all...

---

### Post by J.K.Makowka on 2005-08-13
Ok I did everything as described in this thread. The Source compiled fine with no errors (same output as evilghost).

The I put the renamed file into the ut2004/system directory (after renaming the old file), and set up a configuration file in /home/alsa-speakers as described in the readme.

But after doing all this, there is no sound at all in UT2004 :(

I am using a Audigy 2 ZS btw.

Anyone got an idea what could be causing this?

EDIT: Nevermind... I had to turn the PCM controls in alsamixer on. Now I have sound, but the volume is quite low, as others already complained.
But I am going to experiment with the alsamixer to see what happens, since there is something written about turning certain controls off in the readme.

EDIT2:
The low volume doesn't seem to have anything to do with the settings, but with the programs themselves, I guess.

I tried the new openallib with these games: UT2004, Glest and Warzone2100.

The first two have the low volume problem as soon as I replace the file, but Warzone2100 doesn't.

It is really a pity that is isn't worked on more, as Creative soundscards are pretty common, and the gain of hardware acceleration seems to be quite high.

Edit3: Hmmm, it seems that the low volume problem occurs only on Audigy1&2 cards but not on SBlive, as all people who responded to this thread with volume problems have a Audigy.
The only one who doesn't seem to have these volume problems is evilghost, who has a SBlive.

Maybe this is really a bug, since the readme states, that this was only tested on SB:Live cards, and not on Audigy cards.
I will try to contact the original Author and ask him if he has any idea.

---

### Post by rpgcyco on 2005-08-13
> The low volume doesn't seem to have anything to do with the settings, but with the programs themselves, I guess.

Have you noticed that the sound during the intro (the NVIDIA logo thing) is normal, until the menu loads and the volume then takes a dive?

> Maybe this is really a bug, since the readme states, that this was only tested on SB:Live cards, and not on Audigy cards.
I will try to contact the original Author and ask him if he has any idea.

Yeah, that's a good idea. I couldn't find an email address on the author's [website](http://www.lost.org.uk/openal.html), though maybe I am blind.

- Rpg Cyco

---

### Post by J.K.Makowka on 2005-08-13
His email adress was in one of the readmes that came with the source, but so far I haven't got a reply (ok it is just 5 hours ago that I send him a mail :D ).
But I also pointed him to this thread, so that he can read it himself.

Btw on my PC the volume is also quite low during the UT2004 Nvidia logo thing.

---

### Post by evilghost on 2005-08-13
I'm using an emu10k1-NEF card, and my brother-in-law is using a emu10k1-SEF.  Does this help at all?

I'm using a Sound Blaster Live 5.1 and a Sound Blaster Live 1024(?).  Either way, they are emu10k1.

I did just win an auction on Ebay for 10 EMU10k1 Sound Blaster Live 5.1's, since they are the panacea of a sound card in Linux.  If anyone wants one, $10 (which includes shipping).  Im still waiting for the seller to ship them.

I'm not trying to troll/make a profit, but rather, do what I can to support the Linux community.  The $10 is a break-even price.

---

### Post by rpgcyco on 2005-08-19
[QUOTE=J.K.Makowka]His email adress was in one of the readmes that came with the source, but so far I haven't got a reply (ok it is just 5 hours ago that I send him a mail :D ).
But I also pointed him to this thread, so that he can read it himself.

Btw on my PC the volume is also quite low during the UT2004 Nvidia logo thing.[/QUOTE]

Any response yet? I'm really interested in getting this to work correctly. :)

- Rpg Cyco

---

### Post by Drakx on 2005-08-31
[QUOTE=DarkManX4lf]well i compiled it, and  even tho there were errors, it spat o ut a module, when i used that module i noticed an avg 10fps in crease and a max 20fps increase so i would say its good...maybe if we get rid of those errors we can get more performance.


EDIT

i just tested the new module, and it seems fine BUT the volume seems to be very low, even tho i turned it up high in UT2004, when using the older module this wasnt the case....and i had the same errors as the above posted....hopefully we can get t hem fixed.[/QUOTE]
 Ok i have recompiled the module but what do i do with it now ?

---

### Post by evilghost on 2005-08-31
```

mv [/path/to/ut2004/installation]/System/openal.so [/path/to/ut2004/installation]/System/openal.so.bak
mv [compiled module] [/path/to/ut2004/installation]/System/openal.so

```

---

### Post by J.K.Makowka on 2005-09-02
In other words, rename the old one and copy the newone renamed to the original name to the UT2004 /system directory.

Btw, No reply from the original author :( I bet it is just a minor bug...

P.S.: When I said earlier that Warzone2100 work fine with the replaced libopenal.so I didn't take into account that the file was present, but not (little) used up until the newest Beta, which now officially supports OpenAL. I still need to check it it is now low volume also, but I guess it will be.

---

### Post by maxol on 2005-12-08
Hi,

I'm trying to compile this but I'm getting> max@Shiny:~/openal-alsa-emu10k1-1.2/src$ make
gcc -O2 -W -Wall -Wmissing-prototypes -Werror -fPIC -I../include -c al_state.c
cc1: warnings being treated as errors
al_state.c: In function ‘alGetString’:
al_state.c:191: warning: pointer targets in return differ in signedness
al_state.c:193: warning: pointer targets in return differ in signedness
al_state.c:195: warning: pointer targets in return differ in signedness
al_state.c:197: warning: pointer targets in return differ in signedness
al_state.c:199: warning: pointer targets in return differ in signedness
al_state.c:201: warning: pointer targets in return differ in signedness
al_state.c:203: warning: pointer targets in return differ in signedness
al_state.c:205: warning: pointer targets in return differ in signedness
al_state.c:207: warning: pointer targets in return differ in signedness
al_state.c:209: warning: pointer targets in return differ in signedness
make: *** [al_state.o] Error 1

Any ideas where I may be going wrong? I'd love to get this working.

---

### Post by maxol on 2005-12-12
Found a solution.

I removed "-Werror" from the make file and it worked.

I named the file openal.so and placed it in my /ut2004/System directory and it works but volume is low.

---

### Post by superm1 on 2006-01-04
It seems like current patched versions of the game no longer work with this file.  They just bitch about some missing capture symbols from the openal driver.  I read somewhere Chris had no intention of putting capture support in, so oh well for all of us I guess....

---

### Post by evilghost on 2006-01-04
[QUOTE=superm1]It seems like current patched versions of the game no longer work with this file.  They just bitch about some missing capture symbols from the openal driver.  I read somewhere Chris had no intention of putting capture support in, so oh well for all of us I guess....[/QUOTE]

Still works here, current version of UT2004, no problems.  Hoary 5.04, perhaps it's a Dapper issue if you're running it.

---

### Post by superm1 on 2006-01-04
[QUOTE=evilghost]Still works here, current version of UT2004, no problems.  Hoary 5.04, perhaps it's a Dapper issue if you're running it.[/QUOTE]
Well interesting I have to say then.  Actually, the machine I'm running it on is a gentoo box, but I have several other boxes running ubuntu so I regular both forums.  I'm gonna have to check and see if the gentoo ebuild for ut2004 does some funky stuff at all.  I mearly just dropped in my compiled openal-emu10k1 driver in the directory weeks ago, and after a new update it stopped working.  Thanks for the info :)

---

### Post by minisori on 2006-03-05
Looking how to fix some anoying sound errors with openal-alsa-emuk10k1, i found this page [http://dino.e4a.it/openal-alsa/](http://dino.e4a.it/openal-alsa/) 

Even if the programmer sais it works better the other one for emuk10k1, this one has solved my problem and seem to work very well.

---

