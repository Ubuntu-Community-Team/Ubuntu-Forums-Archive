---
title: "Marathon (AlephOne) issues"
date: 2007-09-28
forum: Gaming &amp; Leisure
---

### Post by Nerfperson on 2007-09-28
Played this game way back on the mac when it came out; since it is now open source would love to play it again.

Installed fine, moved the correct files into the /usr/local/share/AlephOne folder, try to run the program and I get the:

"FATAL ERROR: can't find the game files" (paraphrased, of course)

I have double checked. the files ARE in the correct folder.

The only thing I can think of is I'm not starting the game correctly. I just cd into the downloaded alephone folder and type "alephone". I assume that is right, but am not sure.

Still somewhat of a newbie to Linux, anyone with more experiance know what my problem is?

---

### Post by cogadh on 2007-09-28
I only ask this because you said you are a Linux newbie, but did you actually compile the game or did you just download it, unarchive it and copy files to the directory?

---

### Post by Nerfperson on 2007-09-28
It is compiled (don't think it would create the /usr/local/share/AlephOne directory if it wasn't).

---

### Post by cogadh on 2007-09-28
Okay, I just finished compiling and installing it myself and it worked fine. This is what I did:
[LIST=1]
[*]Install the libsdl, boost, lua and speex dev packages (the build-essential package was already installed)
[*]Download and extract the AlephOne files
[*]In a terminal, cd to the extracted AlephOne-20070819 directory  and run "./configure"
[*]Run "make"
[*]Run "sudo make install"
[*]Download and extract the Marathon (M1A1) data files
[*]Change directories to the extracted M1A1 files and run "sudo cp -r * /usr/local/share/AlephOne"
[/LIST]
You might want to try verifying the steps you took by following these steps.

---

### Post by Nerfperson on 2007-09-28
I believe the only thing I did differently was sudo mv the files instead of copy.

Edit:Alright, either it was the cp instead of mv, or moving all the files instead of just the ones they told you to move, it works now. Thanks!

---

### Post by EDX on 2007-10-03
Excuse me, I am trying to install this program as well. When I try to compile, I get this error:

checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: You need SDL_net to run Aleph One.

I went to [http://www.libsdl.org/projects/SDL_net/](http://www.libsdl.org/projects/SDL_net/) and compiled from the source... And still I get that error... Have any ideas? Any help at all will be appreciated.

---

### Post by Perfect Storm on 2007-10-04
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev bcp libsmpeg-dev libmad0-dev libsndfile1-dev libvorbis-dev libspeex-dev libasound2-dev libgl1-mesa-dev liblua50-dev lua50
```

Download source (no libs) to Desktop;

```
cd ~/Desktop
tar jxfv AlephOne-20070819-nolibs.tar.bz2
cd AlephOne-20070819
./configure --enable-opengl --enable-mad --enable-sndfile --enable-vorbis --enable-lua
make
sudo checkinstall

```

Download Marathon Scenario to Desktop;

```
cd ~/Desktop
unzip M1A1.zip
cd M1A1
sudo cp -r * /usr/local/share/AlephOne
```

You can choose others from their site if you want another plugin/scenario etc.

Launch:
```
alephone
```

Going to write my guide into our game guide database.
(tested on feisty i386 - 32bit

---

### Post by Perfect Storm on 2007-10-05
Guide made: [http://gaming.gwos.org/doku.php/guides:alephone](http://gaming.gwos.org/doku.php/guides:alephone)

---

### Post by EDX on 2007-10-05
Alright, I will try it all when I get home today.:)

---

### Post by EDX on 2007-10-08
Thanks for teh guide... However, when I tried to install it, I got this error instead, and I have all repositories enabled.

checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need SDL 1.2 to run Aleph One.

---

### Post by cogadh on 2007-10-08
You need to run that first bunch of commands that AI listed in order to install the SDL dev packages that the configure script is looking for.

---

### Post by executorvs on 2009-04-22
SO I was trying to follow this tutorial on intrepid and my install fails.
this is my first time deviating from simply using apt-get and installing prepreped packages so I'm not quite sure what to look for in order to fix this.
I'm attaching a summary of my checkinstall output if that helps.

---

