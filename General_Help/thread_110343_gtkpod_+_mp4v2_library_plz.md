---
title: "gtkpod + mp4v2 library plz"
date: 2005-12-30
forum: General Help
---

### Post by justinesalo on 2005-12-30
google is no help...i'm trying to get gtkpod to recognize m4a files to put on an ipod, but it says:
“fie type is known but analysis failed to convert m4a to mp3“
"m4a/m3p/m3b not supported without the mp4v2 library.  You must compile the gtkpod source together with the mp4v2 library."

the thing is, libmp4v2-0 is installed, as is gstreamer0.8-faad and i just ran gst-register-0.8...but it still says i don't have it. 

i've done all the stuff it says to do to get restricted formats on the ubuntu wiki.  

if it means anything, totem can play my m4a, it's just the gtkpod that has issues.  also, when i try to use audio-convert to convert m4a files to mp3, it says  i'm missing the faad codec, though gstreamer-0.8-faad is installed.  

>>so, how do i compile the gtkpod source together with the mp4v2 library that's already installed?  please?

---

### Post by Suger on 2005-12-30
Well, you could try recompiling the mp4v2 from source, then the gtkpod. I did that, it works :)

---

### Post by astoltz on 2005-12-30
There is a version with m4a support available already - it's called gtkpod-aac. see [this thread]("http://ubuntuforums.org/archive/index.php/t-93598.html") for reference.  I can tell you that gtkpod-aac still didn't work for me though.  I didn't try very hard to get it working  'cause most of my music is in mp3 anyway.

---

### Post by justinesalo on 2005-12-30
[QUOTE=Suger]Well, you could try recompiling the mp4v2 from source, then the gtkpod. I did that, it works :)[/QUOTE]

i give up--please enlighten me.  i've spent hours messing around with .tar.gz files:

is the mp4v2 that you recompiled the mpeg4ip-1.4.1 from here?:
[http://mpeg4ip.sourceforge.net/downloads/index.php](http://mpeg4ip.sourceforge.net/downloads/index.php)

if so...how'd you do it? i have no idea what i did, but now when i try to make, it gets stuck in a recursion that never ends.  any idea what that's about?  if i used make before, would it do that?

---

### Post by Suger on 2005-12-31
```

tar xvf mpeg4ip-1.4.1.tar.gz
cd mpeg4ip-1.4.1
./configure
make
sudo make install

```

If you encounter any errors doing that, give me the message.

---

### Post by cpreynolds on 2007-09-20
I was searching for a solution to this problem via google and ended up here. For all you kids that do the same thing, the solution for me was
```

$ sudo aptitude install gtkpod-aac

```

PS: I'm running feisty-x86

---

### Post by Mixmastermichael on 2007-12-12
So after you ran the command:

$ sudo aptitude install gtkpod-aac

Did the original gtk pod you were using become compatible with aac files, or did it install a new program strictly to import aac files to an ipod?

I still can't get mine to work even after I tried your solution.  I am using Gutsy right now.

Please respond at your earliest convenience.

---

### Post by redDEADresolve on 2007-12-13
gutsy version of gtkpod-aac is messed up, it will not let you upload mp4 videos to it. if you want to use gtkpod compile the newest version from the gtkpod site. [http://www.gtkpod.org](http://www.gtkpod.org)

---

### Post by cpreynolds on 2007-12-13
redDEADresolve seems to be correct with gutsy. I upgraded to gutsy a few months ago and have been too bogged down with work to do any ipoding...

---

### Post by Mixmastermichael on 2007-12-15
So I downloaded and compiled the newest GTK pod, but still no luck in adding mp4 files.

I don't so much care to use GTK pod just so long as there is another adaquate program.

I used Rhythm box for a while to add mp4 files to the pod, but it was incredibly slow to do so and often corrupted my ipod forcing me to reformat "back to original settings" on a windows machine in itunes.

There has to be another way to add mp4 files, any suggestions?

---

