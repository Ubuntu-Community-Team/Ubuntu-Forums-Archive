---
title: "So I found my Quake CDs..."
date: 2006-12-02
forum: Gaming &amp; Leisure
---

### Post by deethree on 2006-12-02
I found my quake cds and I've tried to install Quake. Thought I'd take it easy since its been around for a while. I read a thread that talks about JoeQuake and I've given it a whirl. Heck I gave up on "the q" and installed ut2k4 using the loki installer faster then silly ole Q1. So I was wondering if anyone would be kind enouhg to point me in perhaps a better direction to figure out how to install Qukae. Yes, I'm new, just don't stone me yet ;).

Thanks for your time to even just read this thread...

d3.

---

### Post by deethree on 2006-12-02
Let me add, that I'm really suffering from Q1 withdrawls. :D Out of all the people I have gamed with, only one other still played Q1. *sigh* I guess I'm from ye olde shool.

d3.

---

### Post by billyfoxtrot on 2006-12-02
There are quite a few ways to install Quake on Linux.  Because the game engine is open source, there are a lot of updated engines out there to choose from.  The best site explaining how to install Quake with descriptions of each engine is this [Linux Quake How-To]("http://tldp.org/HOWTO/Quake-HOWTO.html").  I don't see JoeQuake listed in the engines section of this How-To, but there are a bunch of others to choose from.  I personally use DarkPlaces.

If you're set on using JoeQuake, I'll try and figure it out and post back on how to install it.

---

### Post by deethree on 2006-12-03
I'm not set on any one version of Quake, just looking to get it going. I'll checkout the link you posted and get into it...

Back in my windows days I used to use Darkplaces as well. :D

d3.

---

### Post by Carbon Based on 2006-12-03
eQuake is how I installed it, it's very easy to do, basically just unzip everything and run the executable. Everything is preconfigured, although I did have to comment out one line in a startup script because it was messing things up. Other than that its ran fine.

[http://equake.quakeworld.nu/](http://equake.quakeworld.nu/)

---

### Post by deethree on 2006-12-06
> **billyfoxtrot said:**
> I personally use DarkPlaces.


Yeah, maybe I should have posted this in the beginners forum, cuz I've tried to figure out what to do, sudo etc and I'm no farther then I was before, willing to put up a guideline so  a new old fragger can get it? ;)

---

### Post by billyfoxtrot on 2006-12-08
> **deethree said:**
> Yeah, maybe I should have posted this in the beginners forum, cuz I've tried to figure out what to do, sudo etc and I'm no farther then I was before, willing to put up a guideline so  a new old fragger can get it? ;)

Okay, let's see... It's been a while since I installed it, but I'll try to walk you through it.  As a warning, this is how I personally got it working, I'm not really an expert and so others may have done it differently.

First, download the Darkplaces engine from [here]("http://icculus.org/twilight/darkplaces/download.html").  Make sure you download the engine and not the mod.

Then create a quake folder in your /usr/local/games directory by opening up a terminal window and using the command:

```
sudo mkdir /usr/local/games/quake
```

Also, you'll need an id1 folder to store all the Quake data, so create that now too:

```
sudo mkdir /usr/local/games/quake/id1
```

In case you're not sure what any of that means, sudo is a command to allow you to do things you normally wouldn't have permission to do.  mkdir is a command to make a new directory.

Now open the DarkPlaces engine zip file that you downloaded and save the file called "darkplaces-linux-686-glx" that is inside of it to your Desktop.  You have to move this file to your newly created quake folder by issuing this command:

```
sudo mv ~/Desktop/darkplaces-linux-686-glx /usr/local/games/quake/
```

Note that you're putting it in your quake folder and not your id1 folder.

This is where it gets tricky because I'm not sure which Quake CD you have and how the data is stored on that disc.  Basically, there *should* be a folder called "id1" or "ID1" somewhere on your Quake CD.  You'll want to find it and move all of its contents to the id1 folder you created in /usr/local/games/quake.  I have the Ultimate Quake pack that comes with Quake, Quake II, and Quake III: Arena.  If you also have this edition you'd use the command:

```
sudo cp /media/cdrom0/Setup/ID1/* /usr/local/games/quake/id1/
```

And that should be it.  To run the game, you'd open a terminal window and move into the quake directory by using the command: 

```
cd /usr/local/games/quake
```

and then running the DarkPlaces binary by using:

```
./darkplaces-linux-686-glx
```

I hope this helps!  Let me know if it doesn't and we'll figure it out. :)

---

### Post by deethree on 2006-12-09
Well, some progress is better then none right?

Loads up, changes my resolution but no game, I have to change the screen res twice to get it back where it should be. *sigh* 

Don't know if it matters but I do have an ATi gfx card, installed the drivers (ut2k4 can attest to that).

```

d3@d3:~$ cd /usr/local/games/quake
d3@d3:/usr/local/games/quake$ ./darkplaces-linux-686-glx
^7DarkPlaces-Quake Linux 22:39:12 Jul 25 2006
^7Trying to load library... "libz.so.1" - loaded.
^7Compressed files support enabled
^7Added packfile id1/pak0.pak (339 files)
^7Added packfile id1/pak1.pak (85 files)
^7Console initialized.
^7Playing registered version.
^7Trying to load library... "libcurl.so.3" - loaded.
^7cURL support enabled
^7Initializing client
^7Trying to load library... "libvorbis.so.0" - loaded.
^7Trying to load library... "libvorbisfile.so.3" - loaded.
^7Ogg Vorbis support enabled
^7couldn't exec config.cfg
^7couldn't exec autoexec.cfg
^73 demo(s) in loop
^7Client using port 0
^7Client opened a socket on address local:2
^7Client opened a socket on address 0.0.0.0:34301
^7Playing demo from demo1.dem.
^7Starting video system
^7Video: fullscreen 640x480x32x60hz
^7Loading OpenGL driver libGL.so.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
^7checking for GLX_ARB_get_proc_address...  not detected
^7checking for GLX_SGI_swap_control...  not detected
^7checking for OpenGL 1.1.0...  enabled
^7GL_VENDOR: Mesa project: www.mesa3d.org
^7GL_RENDERER: Mesa GLX Indirect
^7GL_VERSION: 1.2 (1.5 Mesa 6.5.1)
^7GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
^7GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_multisample 
^7Checking OpenGL extensions...
^7checking for glDrawRangeElements...  enabled
^7checking for GL_ARB_multitexture...  enabled
^7checking for GL_ARB_texture_env_combine...  enabled
^7checking for GL_ARB_texture_env_dot3...  enabled
^7checking for GL_EXT_texture3D...  not detected
^7checking for GL_ARB_texture_cube_map...  enabled
^7checking for GL_EXT_compiled_vertex_array...  not detected
^7checking for GL_EXT_texture_edge_clamp...  not detected
^7checking for GL_SGIS_texture_edge_clamp...  not detected
^7checking for GL_EXT_texture_filter_anisotropic...  not detected
^7checking for GL_EXT_stencil_two_side...  not detected
^7checking for GL_ARB_shader_objects...  not detected
^7OpenGL Backend starting...
^7glDrawRangeElements detected (max vertices 2147483647, max indices 2147483647)
^7multitexture detected: texture units = 8
^7OpenGL backend started.
^7Trying to load library... "libjpeg.so.62" - loaded.
^7JPEG support enabled
^7Trying to load library... "libpng12.so.0" - loaded.
^7PNG support enabled
^7Draw_CachePic: failed to load gfx/crosshair7
^7Draw_CachePic: failed to load gfx/crosshair8
^7Draw_CachePic: failed to load gfx/crosshair9
^7Draw_CachePic: failed to load gfx/crosshair10
^7Draw_CachePic: failed to load gfx/crosshair11
^7Draw_CachePic: failed to load gfx/crosshair12
^7Draw_CachePic: failed to load gfx/crosshair13
^7Draw_CachePic: failed to load gfx/crosshair14
^7Draw_CachePic: failed to load gfx/crosshair15
^7Draw_CachePic: failed to load gfx/crosshair16
^7Draw_CachePic: failed to load gfx/crosshair17
^7Draw_CachePic: failed to load gfx/crosshair18
^7Draw_CachePic: failed to load gfx/crosshair19
^7Draw_CachePic: failed to load gfx/crosshair20
^7Draw_CachePic: failed to load gfx/crosshair21
^7Draw_CachePic: failed to load gfx/crosshair22
^7Draw_CachePic: failed to load gfx/crosshair23
^7Draw_CachePic: failed to load gfx/crosshair24
^7Draw_CachePic: failed to load gfx/crosshair25
^7Draw_CachePic: failed to load gfx/crosshair26
^7Draw_CachePic: failed to load gfx/crosshair27
^7Draw_CachePic: failed to load gfx/crosshair28
^7Draw_CachePic: failed to load gfx/crosshair29
^7Draw_CachePic: failed to load gfx/crosshair30
^7Draw_CachePic: failed to load gfx/crosshair31
^7Draw_CachePic: failed to load gfx/crosshair32
^7SndSys_Init: using the ALSA module
^7Sound format: 48000Hz, 2 channels, 16 bits per sample
^7ioctl CDROMREADTOCHDR failed
^7CDAudio_Init: No CD in player.
^7Initial CD volume: 1
^7CD Audio Initialized
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  2 (XF86DGADirectVideo)
  Serial number of failed request:  693
  Current serial number in output stream:  694

```

Thanks again peoples.

d3.

[edit: d3@d3:~$ cd /usr/local/games/quake
d3@d3:/usr/local/games/quake$ ./darkplaces-linux-686-glx -width 800 -height 600 -fullscreen -nosound

produced the same results.]

---

### Post by billyfoxtrot on 2006-12-09
Hmmm, from the looks of things, it's not detecting your graphics card drivers.

> ^7GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
^7GL_RENDERER: Mesa GLX Indirect
^7GL_VERSION: 1.2 (1.5 Mesa 6.5.1)

This means it's using the Mesa driver instead of your ATi driver.  I know very little about ATi graphics cards, I've just heard they don't always work as nicely with Linux as nVIDIA drivers do.

What does your /etc/X11/xorg.conf file say?  You're sure you configured it correctly when you installed the ATi drivers?

---

### Post by deethree on 2006-12-09
I'm looking into it as I type. I thought I had installed them from the add/remove apps list in applications, seems that it is not the case.  *sigh*

Update in a few hours. 

d3.

Holy crap, 3 different threads across 2 forums, 5 different ways, a HD issue and still mesa. yeah, won't be quaking anytime soon I think *sigh*

---

### Post by leilei on 2006-12-10
Hello

After obtaining the fglrx driver and installing it with aticonfig --initial, try typing this in bash
```

sudo aticonfig --overlay-type=Xv

```
Also, add this at the end of /etc/X11/xorg.conf
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

Give it a nice reboot and something should start working. :)

Also another note, eQuake [is highly non-free](http://mancubus.net/~cheapy/equake), so please remove that link.

---

### Post by deethree on 2006-12-10
I wish it was that easy.

I've followed:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
and..
[http://ubuntuforums.org/showthread.php?p=1866287](http://ubuntuforums.org/showthread.php?p=1866287)

With no luck. I'm holding out that the 3rd link is my issue because there are 2 other people with the same issue as me.  I'm almost to the point of going out and buying that ultimate quake in the hopes that getting this new version might increase my odds of this working. (maybe they differ from the origional games in some way shape or form.)

d3.

---

### Post by deethree on 2006-12-10
[http://www.ubuntuforums.org/showthread.php?t=305665](http://www.ubuntuforums.org/showthread.php?t=305665)

^^^^

WORKED!

wtf only 354FP? thats bunk ;D

---

### Post by Shpongled303 on 2007-07-22
> **billyfoxtrot said:**
> Okay, let's see... It's been a while since I installed it, but I'll try to walk you through it.  As a warning, this is how I personally got it working, I'm not really an expert and so others may have done it differently.

First, download the Darkplaces engine from [here]("http://icculus.org/twilight/darkplaces/download.html").  Make sure you download the engine and not the mod.

Then create a quake folder in your /usr/local/games directory by opening up a terminal window and using the command:

```
sudo mkdir /usr/local/games/quake
```

Also, you'll need an id1 folder to store all the Quake data, so create that now too:

```
sudo mkdir /usr/local/games/quake/id1
```

In case you're not sure what any of that means, sudo is a command to allow you to do things you normally wouldn't have permission to do.  mkdir is a command to make a new directory.

Now open the DarkPlaces engine zip file that you downloaded and save the file called "darkplaces-linux-686-glx" that is inside of it to your Desktop.  You have to move this file to your newly created quake folder by issuing this command:

```
sudo mv ~/Desktop/darkplaces-linux-686-glx /usr/local/games/quake/
```

Note that you're putting it in your quake folder and not your id1 folder.

This is where it gets tricky because I'm not sure which Quake CD you have and how the data is stored on that disc.  Basically, there *should* be a folder called "id1" or "ID1" somewhere on your Quake CD.  You'll want to find it and move all of its contents to the id1 folder you created in /usr/local/games/quake.  I have the Ultimate Quake pack that comes with Quake, Quake II, and Quake III: Arena.  If you also have this edition you'd use the command:

```
sudo cp /media/cdrom0/Setup/ID1/* /usr/local/games/quake/id1/
```

And that should be it.  To run the game, you'd open a terminal window and move into the quake directory by using the command: 

```
cd /usr/local/games/quake
```

and then running the DarkPlaces binary by using:

```
./darkplaces-linux-686-glx
```

I hope this helps!  Let me know if it doesn't and we'll figure it out. :)

billyfoxtrot:

I just wanted to thank you for your DarkPlaces installation post. I just read it today and it helped me install it so easily. I didn't even have to compile anything ??? Almost too easy. :)

I'm just having a little problem, I made a Launcher that points to darkplaces-linux-686-glx in my main menu but it doesn't seem to work? But if I double-click the darkplaces-linux-686-glx icon in /usr/local/games/quake it works fine.

I tried making the launcher "Application" as well as "Application in Terminal" but both didn't work.

Any ideas?

Thanks,
Shpongled

P.S. If I were to want to compile a lot of these helpful guides and post them somewhere, where would I post them? Here in the forum, on a Wiki, or something like that?

---

### Post by cjl2301 on 2007-08-19
Hey, I had the same problem with the launcher.  The problem is that the DarkPlaces engine needs to run from the install directory.

This is what I did to fix it.

I created a text file called "quake.sh" in the "/usr/local/games/quake" directory.   Here is the contents of that file:

```
#!/bin/sh
cd /usr/local/games/quake
./darkplaces-linux-686-glx
```

Now have your launcher launch "quake.sh" instead of "darkplaces-linux-686-glx".

Oh and BillyFoxTrot you have my thanks as well!   Your post made it very simple to get Quake running and the game still plays very well, especially with the Darkplaces engine!

---

### Post by Wobblybob on 2009-06-22
> **billyfoxtrot said:**
> Okay, let's see... It's been a while since I installed it, but I'll try to walk you through it.  As a warning, this is how I personally got it working, I'm not really an expert and so others may have done it differently.

First, download the Darkplaces engine from [here]("http://icculus.org/twilight/darkplaces/download.html").  Make sure you download the engine and not the mod.

Then create a quake folder in your /usr/local/games directory by opening up a terminal window and using the command:

```
sudo mkdir /usr/local/games/quake
```

Also, you'll need an id1 folder to store all the Quake data, so create that now too:

```
sudo mkdir /usr/local/games/quake/id1
```

In case you're not sure what any of that means, sudo is a command to allow you to do things you normally wouldn't have permission to do.  mkdir is a command to make a new directory.

Now open the DarkPlaces engine zip file that you downloaded and save the file called "darkplaces-linux-686-glx" that is inside of it to your Desktop.  You have to move this file to your newly created quake folder by issuing this command:

```
sudo mv ~/Desktop/darkplaces-linux-686-glx /usr/local/games/quake/
```

Note that you're putting it in your quake folder and not your id1 folder.

This is where it gets tricky because I'm not sure which Quake CD you have and how the data is stored on that disc.  Basically, there *should* be a folder called "id1" or "ID1" somewhere on your Quake CD.  You'll want to find it and move all of its contents to the id1 folder you created in /usr/local/games/quake.  I have the Ultimate Quake pack that comes with Quake, Quake II, and Quake III: Arena.  If you also have this edition you'd use the command:

```
sudo cp /media/cdrom0/Setup/ID1/* /usr/local/games/quake/id1/
```

And that should be it.  To run the game, you'd open a terminal window and move into the quake directory by using the command: 

```
cd /usr/local/games/quake
```

and then running the DarkPlaces binary by using:

```
./darkplaces-linux-686-glx
```

I hope this helps!  Let me know if it doesn't and we'll figure it out. :)

Thanks for this mate, worked 1st time on Quake One, now catching up of some old style shoot em up

Martin

---

### Post by xiongnu on 2009-11-22
> **billyfoxtrot said:**
> Okay, let's see... It's been a while since I installed it, but I'll try to walk you through it.  As a warning, this is how I personally got it working, I'm not really an expert and so others may have done it differently.

First, download the Darkplaces engine from [here]("http://icculus.org/twilight/darkplaces/download.html").  Make sure you download the engine and not the mod.

Then create a quake folder in your /usr/local/games directory by opening up a terminal window and using the command:

```
sudo mkdir /usr/local/games/quake
```

Also, you'll need an id1 folder to store all the Quake data, so create that now too:

```
sudo mkdir /usr/local/games/quake/id1
```

In case you're not sure what any of that means, sudo is a command to allow you to do things you normally wouldn't have permission to do.  mkdir is a command to make a new directory.

Now open the DarkPlaces engine zip file that you downloaded and save the file called "darkplaces-linux-686-glx" that is inside of it to your Desktop.  You have to move this file to your newly created quake folder by issuing this command:

```
sudo mv ~/Desktop/darkplaces-linux-686-glx /usr/local/games/quake/
```

Note that you're putting it in your quake folder and not your id1 folder.

This is where it gets tricky because I'm not sure which Quake CD you have and how the data is stored on that disc.  Basically, there *should* be a folder called "id1" or "ID1" somewhere on your Quake CD.  You'll want to find it and move all of its contents to the id1 folder you created in /usr/local/games/quake.  I have the Ultimate Quake pack that comes with Quake, Quake II, and Quake III: Arena.  If you also have this edition you'd use the command:

```
sudo cp /media/cdrom0/Setup/ID1/* /usr/local/games/quake/id1/
```

And that should be it.  To run the game, you'd open a terminal window and move into the quake directory by using the command: 

```
cd /usr/local/games/quake
```

and then running the DarkPlaces binary by using:

```
./darkplaces-linux-686-glx
```

I hope this helps!  Let me know if it doesn't and we'll figure it out. :)


I've followed the instructions to install darkplaces quake 1 engine on my old dell pc. installation was just fine.  when i tried to
launch it by using './darkplaces-linux-686-glx'. game first gets loaded, but moments later the game screen changed to windowed mode, then
ubuntu exits. No error was given. I have tried several times but every time it ended like this. I'm not sure what caused this. any ideas?

My machine specs is as follows:
Dell Dimension PIII 600MHZ PC/320M RAM/ATI Rage Pro 16M Video Card
Ubuntu 7.04
pk0, pk1 is copied to /usr/local/games/dosgames/quake/id1/ directory, run './darkplaces-linux-686-glx' from /usr/local/games/dosgames/quake/ directory.

thanks

---

### Post by swimb on 2009-11-22
Try running it with darkplaces-linux-x86_64-glx or darkplaces-linux-x86_64-sdl. The 686 executables dont work for me either, but it works with the x86_64 ones.

---

### Post by xiongnu on 2009-11-26
> **swimb said:**
> Try running it with darkplaces-linux-x86_64-glx or darkplaces-linux-x86_64-sdl. The 686 executables dont work for me either, but it works with the x86_64 ones.

i tried.  still no success...

erdos@erdos-desktop:/usr/local/games/quake/darkplaces$ ./darkplaces-linux-x86_64-glx
bash: ./darkplaces-linux-x86_64-glx: cannot execute binary file

same for 'darkplaces-linux-x86_64-sdl'

However, I can run darkplaces Quake on my Xandros Thinkpad box, though game is very slow since the graphics card is very old.

---

