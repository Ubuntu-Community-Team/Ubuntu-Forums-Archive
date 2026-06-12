---
title: "[SOLVED] No such file or directory ??  plez help"
date: 2008-03-01
forum: Desktop Environments
---

### Post by tropcky on 2008-03-01
i am trying to learn how to use linux so i trayed to install the vdrift game  i have the tar.bz2
and when install it i did thes steps 

tar xvjf filename .tarbz2
cd-/ destnation / file name 
./ configure  ( at thes steop i got      No such file or directory

i never mede it to that part :
make
sudo make install  

any help

---

### Post by kaens on 2008-03-01
There should be no space between ./ and configure. ./ means "the current directory"

---

### Post by justsomedude on 2008-03-01
> tar xvjf filename .tar.bz2

Right click your downloaded file and select 'extract here'.
> 
cd-/ destnation / file name 

/destnation/ file name = the name of the directory you just extracted. If in doubt, mark it in Nautilus location bar and paste it into the terminal. There should be no "-"  (minus) after cd.

Then execute 

```
./configure
```

---

### Post by tropcky on 2008-03-01
the same problem 

tropcky@tropcky-Linux:~/build$ ./configure
bash: ./configure: No such file or directory
tropcky@tropcky-Linux:~/build$

---

### Post by kaginken on 2008-03-01
If it still doesn't run, post the results of a listing of the directory containing your configure file like so:

```
ls -la configure
```

May be a permissions problem also, which can be fixed by chmod.

---

### Post by kaginken on 2008-03-01
may also need to sudo

sudo ./configure

---

### Post by kaens on 2008-03-01
Is build the only directory made by untarring the file? If so, and executing 
```

ls
``` 

does not show the configure file, but there is a configure.in file, you need to run autoconf

---

### Post by kaens on 2008-03-01
> **kaginken said:**
> may also need to sudo

sudo ./configure

I'm not aware of any situations in which you'd need to sudo ./configure. Only on the make install script - unless you extracted them as root.

A permissions problem would not stop you from seeing the file.

---

### Post by tropcky on 2008-03-01
> **justsomedude said:**
> Right click your downloaded file and select 'extract here'.


/destnation/ file name = the name of the directory you just extracted. If in doubt, mark it in Nautilus location bar and paste it into the terminal. There should be no "-"  (minus) after cd.

Then execute 

```
./configure
```
 i tryed but still :
tropcky@tropcky-Linux:~$ cd /home/tropcky/vdrift-2007-03-23-src
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$ ./configure
bash: ./configure: No such file or directory
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$

---

### Post by justsomedude on 2008-03-01
> **tropcky said:**
> i tryed but still :
tropcky@tropcky-Linux:~$ cd /home/tropcky/vdrift-2007-03-23-src
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$ ./configure
bash: ./configure: No such file or directory
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$

Well, is there a file called configure in the directory you just extracted?

---

### Post by tropcky on 2008-03-01
> **kaginken said:**
> If it still doesn't run, post the results of a listing of the directory containing your configure file like so:

```
ls -la configure
```

May be a permissions problem also, which can be fixed by chmod.

ls -la configure
ls: configure: No such file or directory
tropcky@tropcky-Linux:~$

---

### Post by kaginken on 2008-03-01
You must not be 'in' the directory containing the configure file.

Once you can type

ls -la configure

and get the file name and permissions returned as a result, then you can then run

./configure

Guaranteed.  If that doesn't work, the other guys helping you have agreed to eat their shorts.

Hope that helps!

---

### Post by tropcky on 2008-03-01
> **justsomedude said:**
> Well, is there a file called configure in the directory you just extracted?

no

---

### Post by tropcky on 2008-03-01
> **kaginken said:**
> You must not be 'in' the directory containing the configure file.

Once you can type

ls -la configure

and get the file name and permissions returned as a result, then you can then run

./configure

Guaranteed.  If that doesn't work, the other guys helping you have agreed to eat their shorts.

Hope that helps!

u mean that 
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$ ls -la configure
ls: configure: No such file or directory
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$

---

### Post by kaginken on 2008-03-01
try this,  run
```
updatedb
```
that may take a few minutes.  then:
```
locate configure | less 
```

This will output a couple of dozen lines you can scroll thru by hitting your space bar.

Look for the one you're trying to find, then

cd <directory>

into the directory listed.

THEN run ./configure

---

### Post by kaens on 2008-03-01
Could you post the output of ls on ~/vdrift-2007-03-23-src/ ?

---

### Post by kaens on 2008-03-02
> **kaginken said:**
> try this,  run
```
updatedb
```
that may take a few minutes.  then:
```
locate configure | less 
```

This will output a couple of dozen lines you can scroll thru by hitting your space bar.

Look for the one you're trying to find, then

cd <directory>

into the directory listed.

THEN run ./configure

This will take forever, and find ALL files with configure in their name on his system. This does not sound like a good solution.

---

### Post by tropcky on 2008-03-02
> **kaens said:**
> Could you post the output of ls on ~/vdrift-2007-03-23-src/ ?

tropcky@tropcky-Linux:~$ ls on ~/vdrift-2007-03-23-src/
ls: on: No such file or directory
/home/tropcky/vdrift-2007-03-23-src/:
data  docs  include  po  SConstruct  src  tools
tropcky@tropcky-Linux:~$

---

### Post by justsomedude on 2008-03-02
> **tropcky said:**
> no

Well, if there isn't you can

```
./configure
```

all day, it won't help. Best option: If there is a readme file, read it. Could you post a link to the file you try to compile, so I can take a look at it?

---

### Post by kaens on 2008-03-02
> **tropcky said:**
> tropcky@tropcky-Linux:~$ ls on ~/vdrift-2007-03-23-src/
ls: on: No such file or directory
/home/tropcky/vdrift-2007-03-23-src/:
data  docs  include  po  SConstruct  src  tools
tropcky@tropcky-Linux:~$

Ok, now could you post 

```

ls ~/vdrift-2007-03-23-src/src/

```

---

### Post by tropcky on 2008-03-02
> **justsomedude said:**
> Well, if there isn't you can

```
./configure
```

all day, it won't help. Best option: If there is a readme file, read it. Could you post a link to the file you try to compile, so I can take a look at it?

[http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=vdrift-2007-03-23-src.tar.bz2&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=vdrift-2007-03-23-src.tar.bz2&use_mirror=heanet)

---

### Post by tropcky on 2008-03-02
> **kaens said:**
> Ok, now could you post 

```

ls ~/vdrift-2007-03-23-src/src/

```

ai.cpp          font.cpp           messageq.cpp   replay.cpp    utility.cpp
backdrop.cpp    forcefeedback.cpp  model.cpp      SConscript    vamos
bezier.cpp      gamestate.cpp      mouse.cpp      settings.cpp  vamosworld.cc
binreloc.c      gui                multiplay.cpp  sound.cpp     weather.cpp
camera.cpp      joepack.cpp        net.cpp        textures.cpp
cardinfo.cpp    keyman.cpp         objects.cpp    timer.cpp
configfile.cpp  logo.cpp           particles.cpp  track.cpp
controls.cc     main.cpp           quat.cpp       trackmap.cpp
tropcky@tropcky-Linux:~$

---

### Post by kaens on 2008-03-02
Ahh, you need to

```

sudo aptitude install scons

```

Then, from the vdrift-2007-03-23 directory:

```

$ scons
$ sudo scons install

```

Please note that this information was in the file vdrift-2007-03-23-src/docs/INSTALL

Edit: you may also need to ```
sudo aptitude install build-essential
``` as well if you haven't already.

---

### Post by kaginken on 2008-03-02
locate the INSTALL file in Docs directory

Here's a snippet for ya:

Change directories to the vdrift directory (whatever it is called). From
there, you can either run VDrift from here or you can install it
system-wide. To run VDrift right now, use:

./vdrift

---

### Post by tropcky on 2008-03-02
> **kaens said:**
> Ahh, you need to

```

sudo aptitude install scons

```

Then, from the vdrift-2007-03-23 directory:

```

$ scons
$ sudo scons install

```

Please note that this information was in the file vdrift-2007-03-23-src/docs/INSTALL

when i did sudo scons install i got thes :

tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$ sudo scons install
[sudo] password for tropcky:
scons: Reading SConscript files ...
Checking for C library openal... no
You do not have the openal library installed. Exiting.
tropcky@tropcky-Linux:~/vdrift-2007-03-23-src$ 
 and sorry but i really didnt see it

---

### Post by kaginken on 2008-03-02
Check that INSTALL file - there's some dependencies you'll need to install first.

---

### Post by kaens on 2008-03-02
> **kaginken said:**
> locate the INSTALL file in Docs directory

Here's a snippet for ya:

Change directories to the vdrift directory (whatever it is called). From
there, you can either run VDrift from here or you can install it
system-wide. To run VDrift right now, use:

./vdrift

This would apply if he downloaded the binary build version, which he didn't.



Tropcky, you also need to ```
sudo aptitude install libopenal-dev libsdl-net1.2-dev
```

Edit: actually, there's a whole bunch of dependencies you're going to need to install.  As kaginken suggested, check the install file - these are : > libsdl ([http://www.libsdl.org/](http://www.libsdl.org/)), libsdl-image, libsdl-net,
libopenal ([http://openal.org/](http://openal.org/)) or libfmod ([http://fmod.org/](http://fmod.org/)), and the
OpenGL libraries installed to play VDrift. To compile, you must also have
the headers (usually the -dev packages,

You can use ```
aptitude search packagename | grep dev 
``` to find the dev versions that you need to install with aptitude before you can compile vdrift.

---

### Post by kaginken on 2008-03-02
It says there are binary installs for this - have you tried that?  The binary install might have everything you need...

---

### Post by kaens on 2008-03-02
> **kaginken said:**
> It says there are binary installs for this - have you tried that?  The binary install might have everything you need...

Yes, it would probably be easiest to download the binary version.

---

### Post by tropcky on 2008-03-02
and wher can i faind thes binary installs?

---

### Post by justsomedude on 2008-03-02
> **tropcky said:**
> [http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=vdrift-2007-03-23-src.tar.bz2&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=vdrift-2007-03-23-src.tar.bz2&use_mirror=heanet)

Ok, got it. ;) Do:

```
cd ~/build/vdrift-2007-03-23-src/tools/scripts
```

and then:

```
sudo ./vdrift-install.sh /usr/games /usr/share/games/vdrift
```

If you get error messages, post them.

---

### Post by kaens on 2008-03-02
> **tropcky said:**
> and wher can i faind thes binary installs?


[http://superb-west.dl.sourceforge.net/sourceforge/vdrift/VDrift-2007-03-23-minimal-2.package](http://superb-west.dl.sourceforge.net/sourceforge/vdrift/VDrift-2007-03-23-minimal-2.package)

Download that, and then in a console:```
bash VDrift-2007-03-23-minimal-2.package
```

You may need to ```
sudo bash VDrift-2007-03-23-minimal-2.package
```

---

### Post by tropcky on 2008-03-02
> **justsomedude said:**
> Ok, got it. ;) Do:

```
cd ~/build/vdrift-2007-03-23-src/tools/scripts
```

and then:

```
sudo ./vdrift-install.sh /usr/games /usr/share/games/vdrift
```

If you get error messages, post them.

Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$ sudo sudo ./vdrift-install.sh /usr/games /usr/share/games/vdrift

Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$

---

### Post by kaginken on 2008-03-02
try it again, but with only 1 sudo - you have sudo twice...

---

### Post by kaens on 2008-03-02
> **tropcky said:**
> Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$ sudo sudo ./vdrift-install.sh /usr/games /usr/share/games/vdrift

Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$

```

sudo mkdir /usr/share/games/vdrift

```

should fix that up for you.

---

### Post by tropcky on 2008-03-02
guuuuuuuuuys   thank sooooooooooo much   its works nonw after i install the VDrift-2007-03-23-minimal-2.package   thank u so much   
( dem i didnt know that i am that bad in linux ) lol   any way thank u so much guys for ur help and ur time

---

### Post by kaens on 2008-03-02
> **kaginken said:**
> try it again, but with only 1 sudo - you have sudo twice...

Nah, you can write sudo as many times as you want if I remember correctly.

---

### Post by justsomedude on 2008-03-02
> **tropcky said:**
> Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$ sudo sudo ./vdrift-install.sh /usr/games /usr/share/games/vdrift

Installing VDrift executable...
cp: cannot stat `vdrift': No such file or directory
Failed. Are you sure you're running as root?
tropcky@tropcky-Linux:~/build/vdrift-2007-03-23-src/tools/scripts$

Sorry, my bad. :( Do:

```
cd ~/build/vdrift-2007-03-23-src/tools/scripts
```

```
sudo sh vdrift-install.sh /usr/games /usr/share/games/vdrift
```

Edit: Sorry, I typed faster than I could think. If the binary package works for you, great.

The above should work to install it to a system wide location (if you have all the required dependencies installed). If you want to learn something, try it... :)

---

### Post by tropcky on 2008-03-02
thank u guys it working but i need 1 more faver   i need somthing like  a online book or some 
to learn how to use thes stuff tar.gz  and .tarb.bz2   u know all that fils how to install it and how fix any problem i got in my way like that 

and thank so much agen

---

### Post by kaens on 2008-03-02
> **tropcky said:**
> thank u guys it working but i need 1 more faver   i need somthing like  a online book or some 
to learn how to use thes stuff tar.gz  and .tarb.bz2   u know all that fils how to install it and how fix any problem i got in my way like that 

and thank so much agen

Check out [tldp guides]("http://tldp.org/guides.html"), and the Rute link in my sig. Documentation abounds.

---

### Post by tropcky on 2008-03-02
thank u bro so much i will mark thes as solved cus it is

---

### Post by justsomedude on 2008-03-02
> **tropcky said:**
> thank u guys it working but i need 1 more faver   i need somthing like  a online book or some 
to learn how to use thes stuff tar.gz  and .tarb.bz2   u know all that fils how to install it and how fix any problem i got in my way like that 

and thank so much agen

You can start here: [http://www.tuxfiles.org/linuxhelp/shell.html](http://www.tuxfiles.org/linuxhelp/shell.html)

Try to learn how to navigate inside the terminal first, then move on to the more advanced stuff...

---

