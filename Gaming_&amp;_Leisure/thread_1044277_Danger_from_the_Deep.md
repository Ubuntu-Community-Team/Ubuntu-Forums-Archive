---
title: "Danger from the Deep"
date: 2009-01-19
forum: Gaming &amp; Leisure
---

### Post by Affrikka on 2009-01-19
Hey everyone,

I'm a linux newb, and stumbled upon the game "Danger form the Deep"
After instillation I tried running it in the terminal and it said that I'm missing "libSDL_image-1.2.so.0"
I browsed the forums in search of a cure and found one that said to install all libSDL -dev files from synaptic. I tried that but still get the same error message.

what do I do?

thanks,

-Mathieu

---

### Post by s|fr on 2009-01-19
Hi,

So the error literally means that its unable to find the image shared library from the SDL package. I would say check your lib folders to confirm whether you have a file call libSDL_image.so.something.

1) If you can't find anything then just do :
```

sudo apt-get install libsdl*

```

That should install everything libsdl. (As i am at work I cannot rem the specific package. :D). Check for the file again and read below if you find it.

 ------  OR  ------

2) If you do find something and its called something different for.eg: libSDL_image-1.2.so.0.12 instead of libSDL_image-1.2.so.0, then create a link to that file under the same lib folder and call it what the game is looking for something like:

```

ln -s /usr/lib/SDL/libSDL_image=1.2.so.0.12 /usr/lib/SDL/libSDL_image-1.2.so.0

```

This should fix the problem. Hope that helps.

---

### Post by Affrikka on 2009-01-19
okay I just did the top one you said, because I'm almsot positive that it isn't called anything else, and I still get this exact message:

```
dangerdeep: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

so i guess i'll try the second one.

EDIT: this is what I get for the second one:
```
ln: creating symbolic link `/usr/lib/SDL/libSDL_image-1.2.so.0': No such file or director
```

---

### Post by s|fr on 2009-01-19
Hi Afrikka,

When I said try #2 that was based upon whether you find the file or not. Anyway, I just got home and checked the repository. The package that you are looking for is libsdl-image1.2. install it like so:

```

sudo apt-get install libsdl-image1.2

```

After this you will have the file that you are looking for installed. Just run the application.

hth.

---

### Post by s|fr on 2009-01-19
Hi Afrikka,

I just confirmed. After installing that package The game loads and works fine and it actually looks interesting. I may just start playing it myself. :)

---

### Post by Affrikka on 2009-01-19
is there something I did wrong then? I did exactaly what oyu said and it STILL has that same error message... all I did prior to this was go trough all the defaults in the install, then installed this package and it gets that same error message.
Maybe I'm putting something somewhere I shouldn't be?

---

### Post by s|fr on 2009-01-19
Note: The files is supposed to be under /usr/lib/ and not /usr/lib/SDL.

hmm. That is strange indeed. Can you paste here the output of:

```

ls /usr/lib/libSDL*

```

---

### Post by snova on 2009-01-19
Well, it depends on a library in /usr/lib/SDL/, which doesn't exist (they're all in /usr/lib). So, make sure the 'libsdl-image1.2' package is installed, and try this:

```
sudo mkdir /usr/lib/SDL
sudo ln -s /usr/lib/libSDL_image-1.2.so.0 /usr/lib/SDL/libSDL_image-1.2.so.0
```

---

### Post by s|fr on 2009-01-19
> **snova said:**
> Well, it depends on a library in /usr/lib/SDL/, which doesn't exist (they're all in /usr/lib). So, make sure the 'libsdl-image1.2' package is installed, and try this:

```
sudo mkdir /usr/lib/SDL
sudo ln -s /usr/lib/libSDL_image-1.2.so.0 /usr/lib/SDL/libSDL_image-1.2.so.0
```

snova: The problem doesnt seem to be that the app is looking for the lib under /usr/lib/SDL but that after the package is installed (under /usr/lib) the app cannot seem to find it. I should also point out that I repeated the process on my machine and it seems to work just fine with the library under /usr/lib.

---

### Post by Affrikka on 2009-01-19
```
/usr/lib/libSDL-1.2.so.0            /usr/lib/libSDL_mixer.la
/usr/lib/libSDL-1.2.so.0.11.1       /usr/lib/libSDL_mixer.so
/usr/lib/libSDL.a                   /usr/lib/libSDL_net-1.2.so.0
/usr/lib/libSDL_console.a           /usr/lib/libSDL_net-1.2.so.0.0.7
/usr/lib/libSDL_console.so          /usr/lib/libSDL_net.a
/usr/lib/libSDL_console.so.1        /usr/lib/libSDL_net.la
/usr/lib/libSDL_console.so.1.3      /usr/lib/libSDL_net.so
/usr/lib/libSDL_gfx.a               /usr/lib/libSDL_Pango.a
/usr/lib/libSDL_gfx.la              /usr/lib/libSDL_Pango.so
/usr/lib/libSDL_gfx.so              /usr/lib/libSDL_Pango.so.1
/usr/lib/libSDL_gfx.so.4            /usr/lib/libSDL_Pango.so.1.1.0
/usr/lib/libSDL_gfx.so.4.9.0        /usr/lib/libSDL.so
/usr/lib/libSDL_image-1.2.so.0      /usr/lib/libSDL_sound-1.0.so.1
/usr/lib/libSDL_image-1.2.so.0.1.5  /usr/lib/libSDL_sound-1.0.so.1.0.0
/usr/lib/libSDL_image.a             /usr/lib/libSDL_sound.a
/usr/lib/libSDL_image.la            /usr/lib/libSDL_sound.la
/usr/lib/libSDL_image.so            /usr/lib/libSDL_sound.so
/usr/lib/libSDL.la                  /usr/lib/libSDL_ttf-2.0.so.0
/usr/lib/libSDLmain.a               /usr/lib/libSDL_ttf-2.0.so.0.6.3
/usr/lib/libSDL_mixer-1.2.so.0      /usr/lib/libSDL_ttf.a
/usr/lib/libSDL_mixer-1.2.so.0.2.6  /usr/lib/libSDL_ttf.la
/usr/lib/libSDL_mixer.a             /usr/lib/libSDL_ttf.so

```

okay well this is weird, you can see the exact file right there!

```
/usr/lib/libSDL-1.2.so.0            /usr/lib/libSDL_mixer.la
/usr/lib/libSDL-1.2.so.0.11.1       /usr/lib/libSDL_mixer.so
/usr/lib/libSDL.a                   /usr/lib/libSDL_net-1.2.so.0
/usr/lib/libSDL_console.a           /usr/lib/libSDL_net-1.2.so.0.0.7
/usr/lib/libSDL_console.so          /usr/lib/libSDL_net.a
/usr/lib/libSDL_console.so.1        /usr/lib/libSDL_net.la
/usr/lib/libSDL_console.so.1.3      /usr/lib/libSDL_net.so
/usr/lib/libSDL_gfx.a               /usr/lib/libSDL_Pango.a
/usr/lib/libSDL_gfx.la              /usr/lib/libSDL_Pango.so
/usr/lib/libSDL_gfx.so              /usr/lib/libSDL_Pango.so.1
/usr/lib/libSDL_gfx.so.4            /usr/lib/libSDL_Pango.so.1.1.0
/usr/lib/libSDL_gfx.so.4.9.0        /usr/lib/libSDL.so
*****/usr/lib/libSDL_image-1.2.so.0*****      /usr/lib/libSDL_sound-1.0.so.1
/usr/lib/libSDL_image-1.2.so.0.1.5  /usr/lib/libSDL_sound-1.0.so.1.0.0
/usr/lib/libSDL_image.a             /usr/lib/libSDL_sound.a
/usr/lib/libSDL_image.la            /usr/lib/libSDL_sound.la
/usr/lib/libSDL_image.so            /usr/lib/libSDL_sound.so
/usr/lib/libSDL.la                  /usr/lib/libSDL_ttf-2.0.so.0
/usr/lib/libSDLmain.a               /usr/lib/libSDL_ttf-2.0.so.0.6.3
/usr/lib/libSDL_mixer-1.2.so.0      /usr/lib/libSDL_ttf.a
/usr/lib/libSDL_mixer-1.2.so.0.2.6  /usr/lib/libSDL_ttf.la
/usr/lib/libSDL_mixer.a             /usr/lib/libSDL_ttf.so
```

so now what? 
it's not in /usr/lib/libSDL, it's just in /usr/lib

---

### Post by s|fr on 2009-01-19
The location of the file is correct. That is exactly where it is supposed to be.

Tell me the output of 

```

ls -lsh /usr/lib/libSDL_image*

```

and just so that I dont have to ask for it again tell me the output when you run the game.

---

### Post by Affrikka on 2009-01-19
```
   0 lrwxrwxrwx 1 root root  25 2009-01-18 16:38 /usr/lib/libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.1.5
 48K -rwxrwxrwx 1 root root 48K 2009-01-18 16:38 /usr/lib/libSDL_image-1.2.so.0.1.5
 84K -rw-r--r-- 1 root root 80K 2008-02-11 22:20 /usr/lib/libSDL_image.a
4.0K -rw-r--r-- 1 root root 931 2008-02-11 22:20 /usr/lib/libSDL_image.la
   0 lrwxrwxrwx 1 root root  25 2009-01-18 22:52 /usr/lib/libSDL_image.so -> libSDL_image-1.2.so.0.1.5

```

and when I try to run the game:

```
dangerdeep: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

---

### Post by Perfect Storm on 2009-01-20
any chance that you're running 64-bit?

---

### Post by Affrikka on 2009-01-20
yes I am running 64-bit 8.04

---

### Post by Perfect Storm on 2009-01-20
ok, you properly need to install the 32-bit version of libSDL_image-1.2.so.0 AFAIK this libs doesn't exist as an easy package.

You need to take a look at getlibs; [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by Affrikka on 2009-01-20
awesome! we're making progress!

Now I'm missing some other file, and, I installed it, now it works!
well.. almost.
(i think this game doesn't like me)
it starts up, then crashes, and the terminal displays this LONG huge mess of stuff, mainly GL_stuff, but at the end it shows this:

```
SIGSEGV caught!
Stack trace: (12 frames)
0x8070202 in dangerdeep at ??:0
0x805d560 in dangerdeep at ??:0
0xffffe500 in [0xffffe500] at ??:0
0xf7a8154c in memcpy at ??:0
0xf7c215a0 in std::string::append(std::string const&) at ??:0
0x806f72d in std::basic_string<char, std::char_traits<char>, std::allocator<char> > std::operator+<char, std::char_traits<char>, std::allocator<char> >(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) at ??:0
0x8156807 in dangerdeep at ??:0
0x806ac5e in dangerdeep at ??:0
0x806d3b2 in dangerdeep at ??:0
0x806d4f1 in dangerdeep at ??:0
0xf7a23450 in __libc_start_main at ??:0
0x804e6a1 in dangerdeep at ??:0
Aborting program.
Aborted

```

---

### Post by Perfect Storm on 2009-01-20
```
lspci | grep VGA
```


also can you **ldd** the binary file of danger of the deep?

---

### Post by Affrikka on 2009-01-20
how do you ldd stuff?

here's the lcpsi thing:

```
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)

```

---

### Post by snova on 2009-01-20
> **Affrikka said:**
> how do you ldd stuff?

here's the lcpsi thing:

```
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)

```

Run the **ldd** program on it. :)

```
ldd dangerdeep
```

It lists shared library dependencies.

---

### Post by Affrikka on 2009-01-20
well i figured that, but I did and it just sayd

```
ldd: ./dangerdeep: No such file or directory

```


EDIT:

okay I'm smart now :)
I cd'd into /usr/games and **ldd**'d on dangerdeep, this is what it came up with:

```
	linux-gate.so.1 =>  (0xffffe000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7efe000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7e7b000)
	libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7deb000)
	libSDL_image-1.2.so.0 => /usr/lib32/libSDL_image-1.2.so.0 (0xf7dd0000)
	libSDL_mixer-1.2.so.0 => /usr/lib32/libSDL_mixer-1.2.so.0 (0xf7d46000)
	libSDL_net-1.2.so.0 => /usr/lib32/libSDL_net-1.2.so.0 (0xf7d42000)
	libfftw3f.so.3 => /usr/lib32/libfftw3f.so.3 (0xf7c5d000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7b69000)
	libm.so.6 => /lib32/libm.so.6 (0xf7b44000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7b39000)
	libc.so.6 => /lib32/libc.so.6 (0xf79ea000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6ed5000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6ed3000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6ec4000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6ddd000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6dd9000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf6d16000)
	libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf6cb3000)
	libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf6caa000)
	libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf6c97000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf6c7f000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6c5c000)
	libjpeg.so.62 => /usr/lib32/libjpeg.so.62 (0xf6c3c000)
	libtiff.so.4 => /usr/lib32/libtiff.so.4 (0xf6be8000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6bd3000)
	/lib/ld-linux.so.2 (0xf7fb6000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6bd0000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6bce000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6bb6000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6bb0000)

```

that's a lot of mumbo jumbo IMO.... but i'm not a linux guru :(

---

