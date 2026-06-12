---
title: "GLfrontier (elite2) problems"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by jonboy99 on 2006-06-14
Am having severe problems compiling this from source!

Found this page:
[http://soul-less.pwp.blueyonder.co.uk/glfrontier/](http://soul-less.pwp.blueyonder.co.uk/glfrontier/)

and downloaded the source, and attempted to compile it with the instructions for the i386 makefile in the readme, but just got a load of errors (see endo of post for printout).
The annoying thing was I managed to compile the previous version a few days ago, however I also had a load of errors comiling that, only when I checked the directory after a few times to my surprise I found an executable - i've no idea what I did to compile it, but when I tried it again today I couldn't compile that either  :(

Anyone else able to compile the source?  This is the original one I somehow did compile the one time only:

[old file]("www.jonbrookes.dsl.pipex.com/frontvm3-20060226.tar.bz2")


And this is the latest version which I can't compile at all.

[http://soul-less.pwp.blueyonder.co.uk/glfrontier/frontvm3-20060613.tar.bz2](http://soul-less.pwp.blueyonder.co.uk/glfrontier/frontvm3-20060613.tar.bz2)


This is the output from the terminal:

> jonboy99@xp24ubuntu:~/Desktop/frontvm3-20060613$ make -f Makefile-i386
make -C as68k/
make[1]: Entering directory `/home/jonboy99/Desktop/frontvm3-20060613/as68k'
gcc -O2 -g -Wall output.o output_c.o output_i386.o as68k.o dict.o -o as68k
make[1]: Leaving directory `/home/jonboy99/Desktop/frontvm3-20060613/as68k'
make -f Makefile-i386 fe2.s.o
make[1]: Entering directory `/home/jonboy99/Desktop/frontvm3-20060613'
make[1]: `fe2.s.o' is up to date.
make[1]: Leaving directory `/home/jonboy99/Desktop/frontvm3-20060613'
make -C src/
make[1]: sdl-config: Command not found
make[1]: Entering directory `/home/jonboy99/Desktop/frontvm3-20060613/src'
gcc -O2 -g -Wall -DOGG_MUSIC   -L/usr/X11R6/include -c audio.c
audio.c:10:17: error: SDL.h: No such file or directory
In file included from audio.c:13:
audio.h:4:23: error: SDL_types.h: No such file or directory
audio.c:32: error: syntax error before &#8216;Uint8&#8217;
audio.c:32: warning: no semicolon at end of struct or union
audio.c:36: error: syntax error before &#8216;}&#8217; token
audio.c:36: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;wav_stream&#8217;
audio.c:36: warning: data definition has no type or storage class
audio.c:38: error: syntax error before &#8216;sfx_buf&#8217;
audio.c:38: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;sfx_buf&#8217;
audio.c:38: warning: data definition has no type or storage class
audio.c:39: error: syntax error before &#8216;wav_channels&#8217;
audio.c:39: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;wav_channels&#8217;
audio.c:39: warning: data definition has no type or storage class
audio.c: In function &#8216;Call_PlayMusic&#8217;:
audio.c:111: warning: implicit declaration of function &#8216;SDL_LockAudio&#8217;
audio.c:128: warning: implicit declaration of function &#8216;SDL_UnlockAudio&#8217;
audio.c: In function &#8216;Call_PlaySFX&#8217;:
audio.c:170: error: request for member &#8216;buf_pos&#8217; in something not a structure or union
audio.c:171: error: request for member &#8216;buf_len&#8217; in something not a structure or union
audio.c:171: error: request for member &#8216;buf_len&#8217; in something not a structure or union
audio.c:172: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:172: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:173: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c:173: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c: At top level:
audio.c:182: error: syntax error before &#8216;Uint8&#8217;
audio.c: In function &#8216;Audio_CallBack&#8217;:
audio.c:184: error: &#8216;Sint8&#8217; undeclared (first use in this function)
audio.c:184: error: (Each undeclared identifier is reported only once
audio.c:184: error: for each function it appears in.)
audio.c:184: error: &#8216;pBuffer&#8217; undeclared (first use in this function)
audio.c:189: error: &#8216;pDestBuffer&#8217; undeclared (first use in this function)
audio.c:192: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:198: error: &#8216;len&#8217; undeclared (first use in this function)
audio.c:229: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:230: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:230: error: request for member &#8216;buf_pos&#8217; in something not a structure or union
audio.c:231: error: request for member &#8216;buf_pos&#8217; in something not a structure or union
audio.c:232: error: request for member &#8216;buf_pos&#8217; in something not a structure or union
audio.c:232: error: request for member &#8216;buf_len&#8217; in something not a structure or union
audio.c:234: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c:235: error: request for member &#8216;buf_pos&#8217; in something not a structure or union
audio.c:235: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c:237: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c: At top level:
audio.c:253: error: syntax error before &#8216;*&#8217; token
audio.c: In function &#8216;check_sample_format&#8217;:
audio.c:255: error: &#8216;Uint8&#8217; undeclared (first use in this function)
audio.c:255: error: &#8216;old_buf&#8217; undeclared (first use in this function)
audio.c:255: error: &#8216;buf&#8217; undeclared (first use in this function)
audio.c:259: error: &#8216;spec&#8217; undeclared (first use in this function)
audio.c:260: error: &#8216;filename&#8217; undeclared (first use in this function)
audio.c:261: warning: implicit declaration of function &#8216;SDL_FreeWAV&#8217;
audio.c:266: error: &#8216;AUDIO_U8&#8217; undeclared (first use in this function)
audio.c:267: error: &#8216;len&#8217; undeclared (first use in this function)
audio.c:274: error: &#8216;AUDIO_S16&#8217; undeclared (first use in this function)
audio.c: In function &#8216;Audio_Init&#8217;:
audio.c:291: error: &#8216;SDL_AudioSpec&#8217; undeclared (first use in this function)
audio.c:291: error: syntax error before &#8216;desiredAudioSpec&#8217;
audio.c:303: warning: implicit declaration of function &#8216;SDL_WasInit&#8217;
audio.c:303: error: &#8216;SDL_INIT_AUDIO&#8217; undeclared (first use in this function)
audio.c:305: warning: implicit declaration of function &#8216;SDL_InitSubSystem&#8217;
audio.c:307: warning: implicit declaration of function &#8216;SDL_GetError&#8217;
audio.c:307: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
audio.c:314: error: &#8216;desiredAudioSpec&#8217; undeclared (first use in this function)
audio.c:315: error: &#8216;AUDIO_S16&#8217; undeclared (first use in this function)
audio.c:321: warning: implicit declaration of function &#8216;SDL_OpenAudio&#8217;
audio.c:323: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
audio.c:333: warning: implicit declaration of function &#8216;SDL_LoadWAV&#8217;
audio.c:333: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:334: error: request for member &#8216;buf_len&#8217; in something not a structure or union
audio.c:334: warning: comparison between pointer and integer
audio.c:335: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
audio.c:336: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:338: error: request for member &#8216;buf&#8217; in something not a structure or union
audio.c:338: error: request for member &#8216;buf_len&#8217; in something not a structure or union
audio.c:341: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c:342: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c:343: error: request for member &#8216;loop&#8217; in something not a structure or union
audio.c: In function &#8216;Audio_UnInit&#8217;:
audio.c:362: warning: implicit declaration of function &#8216;SDL_CloseAudio&#8217;
audio.c: In function &#8216;Audio_EnableAudio&#8217;:
audio.c:375: warning: implicit declaration of function &#8216;SDL_PauseAudio&#8217;
make[1]: *** [audio.o] Error 1
make[1]: Leaving directory `/home/jonboy99/Desktop/frontvm3-20060613/src'
make: *** [default] Error 2


---

### Post by The Cosmic Hobo on 2006-06-14
I wish I could help you - you've brought me over all nostalgic, Frontier was one of my favourite Amiga games!

---

### Post by Perfect Storm on 2006-06-14
> ]audio.c:10:17: error: SDL.h: No such file or directory
In file included from audio.c:13:
audio.h:4:23: error: SDL_types.h: No such file or directory

check if you have libsdl1.2-dev and libsdl mixer and libsdl sound (and devs) installed.

Just compiled and it works.

---

### Post by jonboy99 on 2006-06-14
You are the man! Works great  :D   Damn pesky development files..

*soars gracefully in the clouds above planetary system Ross154 at 186fps*  :D

---

### Post by 23meg on 2006-06-14
Wow, thanks for the heads up. I've always wished it ran better on my Amiga 500; it choked badly even around Sirocco Station.. Compiling right now!

---

### Post by Perfect Storm on 2006-06-14
[QUOTE=jonboy99]You are the man! Works great  :D   Damn pesky development files..

*soars gracefully in the clouds above planetary system Ross154 at 186fps*  :D[/QUOTE]

My pleasure ^^

If you like The elite series, you might want to to check out 
Vega Strike (it's in the repo): [http://doc.gwos.org/index.php/Vega_Strike](http://doc.gwos.org/index.php/Vega_Strike)
Privateer Remake: [http://doc.gwos.org/index.php/Privateer_Remake](http://doc.gwos.org/index.php/Privateer_Remake)
OOlite (enhanced Elite clone): [http://doc.gwos.org/index.php/Oolite](http://doc.gwos.org/index.php/Oolite)

Edit: GLfrontier - usefull option:
```

--fullscreen            Try to use fullscreen mode.
--size w h            Start at specified window size.
```

---

### Post by 23meg on 2006-06-14
Anyone figured out how to exit fullscreen mode?

---

### Post by jonboy99 on 2006-06-15
[QUOTE=Artificial Intelligence]My pleasure ^^

If you like The elite series, you might want to to check out 
Vega Strike (it's in the repo): [http://doc.gwos.org/index.php/Vega_Strike](http://doc.gwos.org/index.php/Vega_Strike)
Privateer Remake: [http://doc.gwos.org/index.php/Privateer_Remake](http://doc.gwos.org/index.php/Privateer_Remake)
OOlite (enhanced Elite clone): [http://doc.gwos.org/index.php/Oolite](http://doc.gwos.org/index.php/Oolite)

Edit: GLfrontier - usefull option:
```

--fullscreen            Try to use fullscreen mode.
--size w h            Start at specified window size.
```[/QUOTE]

Cheers, but i've already got all those apart from privateer. Had a major elite nostalgia trip the last few days.  :D

As to full screen, I think the shortcut key is F11 but am not in front of my linux comp at the moment so can't be sure.  I think it tells you in the readme file.

---

