---
title: "Duke Nukem 3d"
date: 2008-06-06
forum: Gaming &amp; Leisure
---

### Post by thedevnull on 2008-06-06
Hey Everyone,

Anyone get Duke Nukem 3d running in 8.04?  I know there are a few avenues to getting it going but I wanted to hear what people have done first before I go down roads riddled with potholes.  Ofcourse there is no deb package in the repos.  =P  

I so miss my Duke Nukem 3d. =(  


It's time to kick *** and chew bubble gum people!

---

### Post by eragon100 on 2008-06-06
dosBOX, it's a dos game, right! :)

---

### Post by Cappy on 2008-06-06
> **thedevnull said:**
> 
It's time to kick *** and chew bubble gum people!

And I'm all out of gummmm

---

### Post by DoktorSeven on 2008-06-06
Actually, there's some native ports floating around since the engine was open-sourced.  I used [this engine](http://www.jonof.id.au/index.php?p=jfduke3d) but I remember it being a real pain to compile, though maybe someone has a package or binary already created from it somewhere.

---

### Post by Pulsar007 on 2008-06-06
You could always just the windows version from [here]("http://jonof.edgenetwork.org/index.php?p=jfduke3d") and run it thru wine. Works well on the Atomic Edition for me.

---

### Post by DoktorSeven on 2008-06-06
But that version also can be compiled into a native binary.

Here, try this: [jfduke3d.tar.gz](http://sdcofer.googlepages.com/jfduke3d.tar.gz).  Works on my system (32-bit Hardy) but I have no idea if they will translate over or work on anything else (try at your own risk).  It's just a tarball of the binaries (duke3d the game and build the editor) created from jfduke3d sources on that site.  You'll need the .grp file from Duke3d of course (it's the data files, just put it in the same directory) and run ./duke3d to start.  

If it says it's missing a library, just search for the name in synaptic or with apt-cache search and install the most likely candidate.

(Note: you'll have to look through the options menus to get fullscreen.)

---

### Post by mister_k81 on 2008-06-06
> **DoktorSeven said:**
> But that version also can be compiled into a native binary.

Here, try this: [jfduke3d.tar.gz](http://sdcofer.googlepages.com/jfduke3d.tar.gz).  Works on my system (32-bit Hardy) but I have no idea if they will translate over or work on anything else (try at your own risk).  It's just a tarball of the binaries (duke3d the game and build the editor) created from jfduke3d sources on that site.  You'll need the .grp file from Duke3d of course (it's the data files, just put it in the same directory) and run ./duke3d to start.  

If it says it's missing a library, just search for the name in synaptic or with apt-cache search and install the most likely candidate.

(Note: you'll have to look through the options menus to get fullscreen.)


Another port worth checking out is EDuke32, which is a little more recent than JFDuke3D is... you can get the latest .deb file here: 

[http://ny00123.sitesled.com/files.html](http://ny00123.sitesled.com/files.html)

Plus that site also has a .deb file for JFDuke32 as well, if you want to try that one out instead. There are also instructions on how to use both ports there, too. 


Also, there's a high resolution texture and model pack that can be used for either EDuke32 or JFDuke32, that you can find here: 

[http://hrp.duke4.net/download.php](http://hrp.duke4.net/download.php)

And,  If you're going to try either port, I suggest downloading Timidity midi sequencer from the repositories...

---

### Post by TerminX on 2008-06-18
> **mister_k81 said:**
> Another port worth checking out is EDuke32, which is a little more recent than JFDuke3D is...
If by "a little more recent" you mean it has 3-4 more years of active development, you're correct.

Here's the newest version of the source, should build on 64-bit Linux as well (thanks to a lot of porting work by one of the DOSBox developers): [http://wiki.eduke32.com/stuff/eduke32_src_20080610.zip](http://wiki.eduke32.com/stuff/eduke32_src_20080610.zip)

---

### Post by fugazi32 on 2009-11-05
> **eragon100 said:**
> dosBOX, it's a dos game, right! :)

Works fine for me in DosBOX! ;)

---

### Post by LuigiAntoniol on 2009-11-05
3D Realms have released the source code for Duke Nukem.

[http://eduke32.com/](http://eduke32.com/)

To quote one paragraph from the website:

"EDuke32 is a source port of the classic PC first person shooter Duke Nukem 3D — Duke3D for short — to Windows, Linux and OS X, which adds a ton of awesome features and upgrades for regular players and an arsenal of editing functions and scripting extensions for mod authors and map makers."

Good luck!!

---

