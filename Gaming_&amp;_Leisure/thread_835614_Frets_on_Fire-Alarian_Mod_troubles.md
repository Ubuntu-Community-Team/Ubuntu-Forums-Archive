---
title: "Frets on Fire-Alarian Mod troubles"
date: 2008-06-20
forum: Gaming &amp; Leisure
---

### Post by ucal on 2008-06-20
Frets on fire is impressive, but it is rather underwhelming graphically (compared to its other Guitar game brothers).  Alarian seems to fix that though, as well as add drum support.  I can't run it though.  I downloaded the latest linux version from the forums but whenever I open the FretsOnFire-run in the terminal, the terminal closes after about a second of no output.  Any ideas? I'm sure its just a very n00b mistake on my part.  Can't wait to play it though.

:guitar:

---

### Post by Zeotronic on 2008-06-21
I hadn't heard about it until this thread... quite nice... really, it seems to work for me even better than Frets on Fire itself did (I always had the buggiest experiance with FoF). Here: [http://fretsonfire.wikidot.com/ds-alarian-mod]("http://fretsonfire.wikidot.com/ds-alarian-mod")... this is where I got it from.

Edit:
I just use 'FretsOnFire'... not 'FretsOnFire-run'... which doesn't seem to do anything for me either.

---

### Post by ucal on 2008-06-21
Okay, I'll try that out as soon as I get back on my linux computer.

---

### Post by ucal on 2008-06-23
Nope that didn't work.  Or at least, I couldn't find a just "fretsonfire" file in the Alarian folder that wasn't a .run.  I downloaded it from the wiki as well. 

A side note:  How on earth do I get a 360 or PS2 (with usb adapter) guitar to work on my linux box? I've looked at the help topics, some updated a week ago, but I ran into quite a few problems with the terminal commands.

---

### Post by DoktorSeven on 2008-06-23
Make sure you have the right download: the file from [this post](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20933&st=1240#entry217499), first link ("2.63 MFH Hotfix 8 (full release)").

Extract using lzma (**sudo apt-get install lzma**): lzma -d *downloaded-file* (replace downloaded-file with the actual filename) then tar xfv the file it generates (same filename minus the .lzma at the end); it's possible that file-roller or ark can decompress this as well as long as lzma/7z is installed, but I didn't try it.

There's another hotfix to download but I didn't try that.

*Important: if you have a ~/.fretsonfire/fretsonfire.ini file from the normal Frets on Fire program, move it elsewhere or delete it.*

You should be able to run ./FretsOnFire (mind the capitalization) from the Alarian directory it made.

If you still have problems, post any output.  I recall I had to rename data/themes/Gh3 to GH3 to get it to run.

---

### Post by ucal on 2008-06-25
Thanks.  That worked perfectly.  

Any ideas on the guitar thing?

---

### Post by doorknob60 on 2008-06-28
Anyone get it working in 64 bit? I used getlibs and eveyrhting works except for the guitar.ogg file :( The other ogg's play fine however. I have the latest version, and eveyrthing else in the game works too (2.825 or something like that).

---

### Post by ucal on 2008-06-28
I've run into another problem.  Whenever I try and load a song, I am confronted with nothing but a black screen.

The songs are in my Frets on Fire Directory, and not the Alarian directory.  Could that be causing a problem?

---

### Post by DoktorSeven on 2008-06-29
Yes, the songs need to be in your Alarian/data/songs directory. 

Though you can create a symlink from your Frets on Fire directory.  Say Frets on Fire is installed in $HOME/FretsOnFire and Alarian in $HOME/alarian ($HOME = your home directory). 

Make sure you don't have a data/songs directory in alarian (if I recall, it doesn't by default), open a terminal and do:
```

cd ~/alarian/data/
ln -s ~/FretsOnFire/data/songs/

```

Now all songs in Frets On Fire are also available to Alarian.  Of course, you should change the paths above if they're installed elsewhere.

---

### Post by ucal on 2008-06-29
Okay, I moved the songs to the alarian/data/songs folder, changed the song library settings in game, but am still confronted with a black screen.  The game just won't load the songs.  Now I'm thinking a video driver error or something.

Ran it in the terminal, and got this upon trying to play a song.

```
Traceback (most recent call last):
  File "src/Session.py", line 66, in signalMessage
  File "src/Session.py", line 87, in handleMessage
  File "src/World.py", line 248, in handleSceneCreated
  File "src/SceneFactory.py", line 40, in create
  File "src/Scene.py", line 223, in __init__
  File "src/GuitarScene.py", line 94, in createClient
  File "src/Guitar.py", line 201, in __init__
  File "src/GameEngine.py", line 458, in loadImgDrawing
  File "src/Data.py", line 182, in loadImgDrawing
  File "src/Resource.py", line 221, in load
  File "src/Resource.py", line 109, in load
  File "src/Data.py", line 182, in <lambda>
  File "src/Svg.py", line 539, in __init__
  File "src/Texture.py", line 202, in __init__
  File "src/Texture.py", line 206, in loadFile
  File "src/Texture.py", line 214, in loadImage
  File "src/Texture.py", line 281, in loadRaw
GLerror: [Errno 1280] invalid enumerant


```

---

### Post by ucal on 2008-07-02
bump.

---

### Post by DoktorSeven on 2008-07-02
Just a wild guess, but do you have OpenGL / your video drivers working?

This should return "direct rendering: Yes" if you type it into a terminal:
```
glxinfo | grep direct

```

---

### Post by jnuz on 2008-07-02
hey guys. I'm the one who compiles the Alarian Mod binaries. If you have any questions please ask. I also would recommend getting the newest MFH alarian mod 2.8 at least.

---

### Post by ucal on 2008-07-02
> **DoktorSeven said:**
> Just a wild guess, but do you have OpenGL / your video drivers working?

This should return "direct rendering: Yes" if you type it into a terminal:
```
glxinfo | grep direct

```

It returned yes.  I'll just use the latest binaries and see if that works for now.

---

### Post by doorknob60 on 2008-07-03
> **jnuz said:**
> hey guys. I'm the one who compiles the Alarian Mod binaries. If you have any questions please ask. I also would recommend getting the newest MFH alarian mod 2.8 at least.

64 bit version please? The 32 bit one doesn't play guitar.ogg properly

---

### Post by jnuz on 2008-07-03
I don't have plans to compile 64-bit code as I do not have a 64-bit linux installation. I would, however, be more than happy to send you the source code. I may eventually compile a 64-bit binary, but with my new job it's not in the forseeable future.

---

### Post by Coolit on 2008-07-04
I'd give this a go also if my GH3 guitar could be used, unfortunately it looks like the PC wireless adapter made by M$ doesn't work in linux (yet).

The BIG advantage this has over GH3/Rockband is that you can have endless content, any track is potentially convertible. :guitar:

---

### Post by doorknob60 on 2008-07-09
> **jnuz said:**
> I don't have plans to compile 64-bit code as I do not have a 64-bit linux installation. I would, however, be more than happy to send you the source code. I may eventually compile a 64-bit binary, but with my new job it's not in the forseeable future.

Okay, the source is good enough :-) If it works well I'll maybe post a binary of it.

---

### Post by doorknob60 on 2008-07-29
*cough* Still not working...

---

### Post by Christopherius on 2008-10-01
i'm also having trouble with guitar.ogg not playing on some songs. any fix for it?

---

### Post by C0MM4NDER on 2008-10-09
Hi Ubuntu and Frets on Fire users....
First of all im kinda a newb to linux....

Anyway, i play frets on fire alarian mod now named MFH Mod 3.05
i play the windows version under wine.


My question is, could someone give a better mirror for the linux version because i live in Sweden and the maximum download speed from that us mirror is 5kb/s 

playing in Wine it works kinda good exept some kernel crashes happening from time to time. = everything freezes with wierd colors and computer not responding (hard reboot needed)

my other question is how do i fix this graphical erros = [http://www.youtube.com/watch?v=b6ch3n6H2r0&feature=related](http://www.youtube.com/watch?v=b6ch3n6H2r0&feature=related)

i dont have exactly the same problem but the colors spins arround like that.


Using Ubuntu Hardy Heron with Wubi.
Laptop = Compaq/HP 6510b (965 express chipset using standard drivers that installs when ubnutu starts)
latest Wine 1.0 i think
latest frets and mod.

havent tried the linux version yet if it fixes the kernel crash or the graphical glich because 5kb/s estimates several weeks of downloading 

Best regards Commander, a new ubuntu user.

---

### Post by supergeek321 on 2010-09-05
> **ucal said:**
> Thanks.  That worked perfectly.  

Any ideas on the guitar thing?

it works with a rock band controller for ps2

---

