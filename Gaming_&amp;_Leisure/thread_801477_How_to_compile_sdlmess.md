---
title: "How to compile sdlmess ?"
date: 2008-05-20
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-05-20
Hello, 

Has anyone sdlmess working? What are the required packages to avoid floating point error?

thanks:guitar::guitar:

---

### Post by rocky5051 on 2008-05-20
There are directions here:

[http://www.vg-network.com/sdl-mess](http://www.vg-network.com/sdl-mess)

The copy of MESS is availible in the repositories, so it really isn't necessary to compile it. The packages you'll need are xmess-sdl, xmess-common, xmess-x and all the libsdl packages.

---

### Post by frenchn00b on 2008-06-01
I could find this howto , damn no one post any information to install that sdlmess ... 

[B]what are all the directories to create in sdlmess/roms ??
[/B]
```
 SDLMESS

Systems: (Many Console Systems...)

Homepage: http://rbelmont.mameworld.info/?page_id=163

Version: 0.119

    * Download sdlmess119.zip
    * Create destination directory: 

$ sudo mkdir /usr/share/games/sdlmess

    * Extract zip to the above dir
    * Compile to produce executable called "mess" 

$ cd /usr/share/games/sdlmess
$ sudo make -f makefile.sdl

    * For 64-bit architectures substitute the above make command for the one below. 

$ sudo make -f makefile.sdl PTR64=1 //64-bit architectures only.

    * Generate a config file: 

$ mess -createconfig

    * Copy the config file to your user directory 

$ mkdir ~/.mess
$ cp mess.ini ~/.mess

    * Edit the config file 

$ sudo apt-get install leafpad  // lightweight GUI text editor great for mythtv installations
$ leafpad ~/.mess/mess.ini

    * Modify the following paths in the file to point to the sdlmess directory: 

rompath    /usr/local/share/games/sdlmess/roms
hashpath   /usr/local/share/games/sdlmess/hash
samplepath /usr/local/share/games/sdlmess/samples
artpath    /usr/local/share/games/sdlmess/artwork
ctrlrpath  /usr/local/share/games/sdlmess/ctrlr
inipath    /usr/local/share/games/sdlmess
fontpath   /usr/local/share/games/sdlmess

    * Create a symbolic link within your path (lets you run it from anywhere) 

$ cd /usr/games
$ sudo ln /usr/share/games/sdlmess/mess mess --symbolic

    * Create a directory structure for your ROMs (cpc464 is an example console) 

$ sudo mkdir /usr/local/share/games/sdlmess/
$ sudo mkdir /usr/local/share/games/sdlmess/roms/
$ sudo mkdir /usr/local/share/games/sdlmess/roms/cpc464

    * Place BIOS roms straight into the roms dir: 

$ mv cpc464.zip /usr/local/share/games/sdlmess/roms/

    * Place game roms in a suitable sub-directory: 

$ mv game.dsk /usr/local/share/games/sdlmess/roms/cpc464

    * test by executing mess using the appropriate parameters: 

$ cd /usr/local/share/games/sdlmess
$ mess cpc464 -flop1 "roms/cpc464/game.dsk"

```

---

### Post by frenchn00b on 2008-06-01
Here is my script to install sdlmess !!
Finally 
to be retrieved [here]("http://yellowprotoss.ye.funpic.org/games/sdlmame/sdlmame0122-installer-ubuntu.sh") 
you can run it from the console directly.

```
#!/bin/bash
mkdir -p /usr/share/games/
cd /usr/share/games/
wget -N http://ftp.plusline.de/FreeBSD/distfiles/sdlmess0122.zip
unzip sdlmess0122.zip
rm sdlmess0122.zip
mv sdlmess0122 sdlmess
cd /usr/share/games/sdlmess
make -f makefile.sd
beep
chmod ug+rx /usr/share/games/sdlmess -R
mkdir -p /usr/share/games/sdlmess/roms
echo "please put all the zip files into /usr/share/games/sdlmess/roms, like this"
rox & rox &
echo "I am waiting you do so with rox and please press enter"
read lfkdjdlfs
rm /usr/bin/sdlmess 
ln -s /usr/share/games/sdlmess/mess   /usr/bin/sdlmess 
chmod ug+rx /usr/share/games/sdlmess -R
chmod ug+rx /usr/bin/sdlmess
echo "to run a floppy game : mess cpc464 -flop1 renegade.dsk"
echo "to run a console game : mess n64 -cart mario64.n64"
echo "Enjoy !!"

```

---

