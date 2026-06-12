---
title: "Penumbra Collection on Karmic - horrible crackly audio"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2009-11-01
Decided to install my Penumbra Collection on my 64 bit Karmic today, but sadly for some reason there's some audio issues. Basically, it's intermittently giving me this crackly and scratchy type of feedback noise on occasion. I've had a good Google about the place, but to no avail. There are some posts about the issue some years ago on Feisty, but nothing for Karmic. Does anyone here know of a fix for this? I'm using 64 bit Karmic, bit I have ia32libs installed.

Many thanks! :)

---

### Post by amauk on 2009-11-03
Hey,
had similar issues

There's a beta upgrade for the collection
Patch here - [http://rapidshare.com/files/276633619/PenumbraCollectionUpgrade-1.0.1-2995.sh](http://rapidshare.com/files/276633619/PenumbraCollectionUpgrade-1.0.1-2995.sh)
thread here - [http://www.frictionalgames.com/forum/showthread.php?tid=3108&page=1](http://www.frictionalgames.com/forum/showthread.php?tid=3108&page=1)

This patch allows you to specify what audio system is used
OSS works great for me, with none of the crackling that ALSA gave

---

### Post by BigSilly on 2009-11-03
That's absolutely magic! Thanks very much for posting that up. :)

EDIT: Bugger. The Rapidshare link is only for premium members, and none of the other links work. :(

---

### Post by Brebs on 2009-11-03
> **BigSilly said:**
> crackly and scratchy type of feedback noise

I suggest --disable-assembly
See [thread](http://www.dxx-rebirth.com/smf/index.php?topic=591.15).

---

### Post by alanwalterthomas on 2009-11-05
I'm having the same problem except that I bought each game separately earlier (& paid a lot more for them too! :[  ) I downloaded a patch for overture but it didn't help at all
Besides sound there are also new Graphics glitches:
I think I remember the hand being visible most/all of the time. Now it's only visible if it's directly in front of something that it can interact with.
Didn't bother going far, but the snowy ground around the pit by the entrance at the beginning of overture is gone - transparent.

I need a little more explanation. The --disable-assembly thread tells me to:

./configure --disable-assembly in the SDL package

export SDL_AUDIODRIVER=alsa

Um, PLEASE, explain how/where to do that for us noobs. (line by line copy/paste terminal commands)

---

### Post by Brebs on 2009-11-05
The export line goes in ~/.bashrc

I don't use Debian/Ubuntu, so figure out the package recompilation yourself.

---

### Post by alanwalterthomas on 2009-11-06
Ok, Let me write what I have & have not understood before I go do BAD THINGS, & maybe someone can fill in the ?? blanks & correct my mistakes.

I edit ~/.bashrc

?? Then I tack on "export SDL_AUDIODRIVER=alsa" at the end of the file, or anywhere.
I can quickly & easily do that with cat "export SDL_AUDIODRIVER=alsa" >> ~/.bashrc
right?

Then I'll look for some SDL source tarball, unpack it, cd into the folder then do:
./configure --disable-assembly
make -j
make install

I looked at synaptic for a moment & SDL is all over the place. Please let me know exactly what SDL I'm looking for.
I'm sure there are mistakes in the above but that's as far as my knowledge goes.
Help's very welcome.

---

### Post by Brebs on 2009-11-06
Edit the [libsdl1.2 package](http://packages.ubuntu.com/source/karmic/libsdl1.2).

Look at line 1741 of [libsdl1.2_1.2.13-4ubuntu4.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13-4ubuntu4.diff.gz)

```
+confflags = --prefix=/usr
+confflags += --disable-rpath --enable-dlopen \
+	     --enable-dependency-tracking \
+	     --enable-arts-shared=no --enable-arts=no --enable-alsa-shared=no \
+	     --enable-esd-shared=no --enable-pulseaudio-shared=no
+all_confflags = --disable-video-ggi \
+		--enable-video-aalib --enable-video-directfb \
+		--enable-video-caca
+udeb_confflags = --enable-video-directfb --disable-video-ggi \
+		 --disable-video-svga --disable-video-x11 \
+		 --disable-video-aalib --disable-dga --disable-video-photon \
+		 --disable-video-fbcon --disable-video-ps2gs \
+		 --disable-video-opengl --disable-video-xbios \
+		 --disable-video-gem --disable-video-caca \
+		 --disable-audio --disable-audio-arts --disable-audio-esd \
+		 --disable-audio-oss --disable-audio-nas --disable-audio-alsa \
+		 --disable-pulseaudio
```

Add --disable-assembly to that, then recompile & install.

---

### Post by alanwalterthomas on 2009-11-07
Huh, that didn't do it.
I downloaded 
[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13-4ubuntu4.dsc](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13-4ubuntu4.dsc)
[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13.orig.tar.gz)
[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13-4ubuntu4.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.13-4ubuntu4.diff.gz)
& put all the .gz contents in the same folder. I edited the .diff file as told. Then
./configure
make
sudo make install

The audio's still crackling.

Now I ran sudo make uninstall. That should put everything back the way it was before right?

Any other ideas?

---

### Post by Brebs on 2009-11-08
You need to do the package modification, recompilation and reinstallation "the Debian way" - read up on it.

You have currently got the classic vs Debian installation methods horribly confused.

---

### Post by alanwalterthomas on 2009-11-08
The debian way, of course!
A google search for that & package modification gives no useful results (actually, this thread is ~5th result)
I don't mind a bit of reading, but it helps to know what to read. The Internet isn't exactly a small bookshelf.
.configure make make install is the only way I've ever heard of to remake packages.
I can only guess that the debian way is to make my own package?
Some real guidance would be very much appreciated.

---

### Post by frigginacky on 2009-11-20
I had this problem with Penumbra also.  I was able to fix it by simply stopping the pulseaudio daemon while playing.  A howto if you need it:

First, you have to tell pulseaudio not to restart itself.  Add this line to your ~/.pulse/client.conf (create the file if doesn't exist):
```
autospawn = no
```

Then kill pulseaudio:
```
killall pulseaudio
```

Now you can play Penumbra with lovely, non-crackly sound!

To turn pulseaudio back on when you're done:
```
pulseaudio -D
```

Hope it works for you!

---

### Post by alanwalterthomas on 2009-11-21
Absolutely Amazing!

THANK YOU!

---

### Post by BigSilly on 2009-11-21
> **frigginacky said:**
> I had this problem with Penumbra also.  I was able to fix it by simply stopping the pulseaudio daemon while playing.  A howto if you need it:

First, you have to tell pulseaudio not to restart itself.  Add this line to your ~/.pulse/client.conf (create the file if doesn't exist):
```
autospawn = no
```

Then kill pulseaudio:
```
killall pulseaudio
```

Now you can play Penumbra with lovely, non-crackly sound!

To turn pulseaudio back on when you're done:
```
pulseaudio -D
```

Hope it works for you!

That's absolutely excellent! Thanks very much. :D

Out of interest, is there a GUI way to do this? To turn Pulseaudio on and off at will? Don't get me wrong, I'm absolutely fine with the terminal, but I'm just thinking about the newbies. Thanks.

---

### Post by frigginacky on 2009-11-22
> **alanwalterthomas said:**
> Absolutely Amazing!

THANK YOU!

> **BigSilly said:**
> That's absolutely excellent! Thanks very much. :D

Out of interest, is there a GUI way to do this? To turn Pulseaudio on and off at will? Don't get me wrong, I'm absolutely fine with the terminal, but I'm just thinking about the newbies. Thanks.

You're both welcome. :)  I'm not aware of any GUI method to do this, but that doesn't mean it doesn't exist.

---

### Post by Elwro on 2010-05-05
Please help :-( After I "killall pulseaudio", the game runs in complete silence. When I "pulseaudio -D", the game runs with horrible crackly noises. I even did the "remove various libraries" trick suggested [here](http://support.frictionalgames.com/entry/64/), to no avail. Any ideas on what I could do?

edit: got the official support: [http://www.frictionalgames.com/forum/thread-3049.html](http://www.frictionalgames.com/forum/thread-3049.html) Works!

---

### Post by BigSilly on 2010-05-05
Are you still on Karmic Koala? I'm having none of these problems now on Lucid.

Thank God!

EDIT: I see you are. Might be worth upgrading if you can...

---

### Post by Elwro on 2010-05-05
> **BigSilly said:**
> Are you still on Karmic Koala? I'm having none of these problems now on Lucid.

Thank God!

EDIT: I see you are. Might be worth upgrading if you can...Yeah, thankfully the solution from the official support forum worked for me. I upgraded my second computer to 10.04 and it lost the ability to print :-( But that's a story for a different thread. Thanks for the positive comment about the upgrade, I'll do it with my main computer in a few days, when the initial bugs will have been ironed out.

---

