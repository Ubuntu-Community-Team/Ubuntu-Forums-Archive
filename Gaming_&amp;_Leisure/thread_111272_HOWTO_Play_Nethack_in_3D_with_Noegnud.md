---
title: "HOWTO: Play Nethack in 3D with Noegnud"
date: 2006-01-01
forum: Gaming &amp; Leisure
---

### Post by Dogmeat on 2006-01-01
**HOWTO: Play Nethack in 3D with Noegnud**

Noegnud is a semi-3D frontend for Nethack and Slash'EM. For more information visit [http://www.darkarts.co.za/projects/noegnud/]("http://www.darkarts.co.za/projects/noegnud/").

This HOWTO tries to address the issue of installing Noegnud with Nethack 3.4.3.

**PREREQUISITES:**

You should install these packages before continuing. You can open a terminal and type this line:

```
sudo apt-get install build-essential libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev
```

Or just select and install them in synaptic.

**DOWNLOAD NOEGNUD HERE:**

[http://www.darkarts.co.za/projects/noegnud/downloads/noegnud-0.8.3/noegnud-0.8.3_linux_src-full.tar.bz2]("http://www.darkarts.co.za/projects/noegnud/downloads/noegnud-0.8.3/noegnud-0.8.3_linux_src-full.tar.bz2")

Open a terminal if you haven't already. Go to wherever you put the downloaded file and extract Noegnud with the following command:

```
tar xjf noegnud-0.8.3_linux_src-full.tar.bz2
```

Now this package has a couple of problems. The first is it tries to download a file that no longer exists (I'll call this PROBLEM #1). The other one is it has a wrong line of code. Don't be afraid though, it's pretty simple to fix (This is PROBLEM #2).

**FIX FOR PROBLEM #1:**

NOTE: The link below was working when I posted this. If it no longer does, just google for nethack-343-src.tgz and download it into the noegnud-0.8.3/variants/tarballs directory. Do not extract it, just put it there.

After extracting Noegnud (see above), do this:

```
cd noegnud-0.8.3/variants/tarballs
wget http://blastwave.informatik.uni-erlangen.de/csw/users/michael/sources/sources/nethack-343-src.tgz

```
Wait until it downloads, then type this:

```
cd ..
make nh343

```
You should get this error now, and 'make'  should stop:

```
../win/noegnud/noegnud_gui.c: In function &#8216;noegnud_gui_create_button&#8217;:
../win/noegnud/noegnud_gui.c:635: error: invalid lvalue in assignment

```

This is the second problem I told you above. If you got another error, see if you have installed the required libraries (in the Prerequisites above). If for some reason you don't get this error or any others, skip the following fix.

**FIX FOR PROBLEM #2:**

```
cd nethack-3.4.3/win/noegnud
gedit noegnud_gui.c

```
Search for this line: 
```
				 (noegnud_gui_twidget *)button=(noegnud_gui_tbutton *)

```Replace it with:
```
				 button=(noegnud_gui_tbutton *)

```Save the file, close gedit and go back to the terminal. Type the following:

```
cd ../../../
make nh343

```
This time it should compile without errors. Now install it:

```
sudo make install_data install_nh343
```

To play, type: 

```
noegnud-nethack-3.4.3
```

Now you can play nethack in 3D! Despite it's name, I found the 'absurd' tileset to be actually pretty good and funny too (Your pet is bigger than you!). I hope this HOWTO worked for you, if not let me know where you're stuck and I'll update it! :)

---

### Post by meborc on 2006-01-02
thanks for the how-to... can't wait to go home to my ubuntu box and try it out.. nethack has been my great love, but we seldom meet these days... hope that will change that :D

---

### Post by Dogmeat on 2006-01-02
[QUOTE=meborc]thanks for the how-to... can't wait to go home to my ubuntu box and try it out.. nethack has been my great love, but we seldom meet these days... hope that will change that :D[/QUOTE]

You're welcome :) I used to play ADOM a lot, now i'll play Nethack a bit for a change. 

The problem with installing like this is that you have to manually uninstall it (rm -rf /usr/local/lib/noegnud* and rm -rf /usr/local/bin/noegnud*) if you want to update sometime in the future.

Let me know if it works for you, as I only tried this on my computer, maybe I missed a prerequisite or two.

---

### Post by forcesofhabit on 2006-11-07
I tried this, and I couldn't get it to work... I'm really not sure where I went wrong. I did use a different source file, as the one you gave is now broken.

Man a deb package would be nice for this...

---

### Post by roberto.tomas on 2010-06-06
the source is currently available at sourceforge -- [http://sourceforge.net/projects/noegnud/](http://sourceforge.net/projects/noegnud/)
[LEFT]
[/LEFT]

---

