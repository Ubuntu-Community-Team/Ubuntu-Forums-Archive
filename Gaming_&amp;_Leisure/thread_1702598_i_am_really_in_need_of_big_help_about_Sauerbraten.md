---
title: "i am really in need of big help about Sauerbraten"
date: 2011-03-08
forum: Gaming &amp; Leisure
---

### Post by ame82 on 2011-03-08
this time i just install ubuntu 10.10 and i decided to only use it till i understand it and not give up like every time, 
now i am trying to run this game Sauerbraten
but no way. i dont know why, whats wrong?
the last i did i move the game to home folder( as i understood is the folder that have my username((x)) after the the home folder e.g. [/home/x]
and i run the sauerbraten_unix , i get little window with few choises , run, display, run in terminal ,.....
i did all of them no result
i even went to the trtminal and tried to run it there no thing, i get command not found while i did list and its there
i installed java 
plz some help plz
i did same with other games and i still dont get any thing loock at 

deamon@deamon-pc:~/sauerbraten$ ls
bin_unix  docs      README.html       server-init.cfg
data      packages  sauerbraten_unix  src
deamon@deamon-pc:~/sauerbraten$ sauerbraten_unix
sauerbraten_unix: command not found
deamon@deamon-pc:~/sauerbraten$

---

### Post by mastablasta on 2011-03-08
how did you install the game?
 
if you are having probelm with instalation there is a .deb file you can use to download, double click and install the game. it should then appear in the menu.
 
for example: [http://linuxappfinder.com/package/sauerbraten](http://linuxappfinder.com/package/sauerbraten)
 
i would check it in the software center first though.

---

### Post by dfreer on 2011-03-08
Also try:
./sauerbraten_unix

The ./ tells it to look in the current directory. If you specify a command without the ./, it will search your $PATH variable which may or may not contain the current directory, hence why it can't find your game. Also, ls -l to make sure it's an executable and it has the execute permissions set correctly.

---

### Post by ame82 on 2011-03-11
thanks alot
i just need to understand how things work here , its not about the game its about how to make it work and other similar programs 
i tried what u said but i got this
deamon@deamon-pc:~$ cd Desktop
deamon@deamon-pc:~/Desktop$ ls
commands           robombs
cube-2.run         robombs.zip
gcalctool.desktop  sauerbraten
minecraft.jar      sauerbraten_2010_07_28_justice_edition_linux.tar.bz2
mohaa.run          uhexen2-20110303-r3929.tgz
rhythmbox.desktop
deamon@deamon-pc:~/Desktop$ cd sauerbraten
deamon@deamon-pc:~/Desktop/sauerbraten$ ls
bin_unix  docs      README.html       server-init.cfg
data      packages  sauerbraten_unix  src
deamon@deamon-pc:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
deamon@deamon-pc:~/Desktop/sauerbraten$ 



i think i am missing to install some more liberaries
do u mean by install it, extract it , ??

---

### Post by Perfect Storm on 2011-03-11
> ./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

Try with:
```
sudo apt-get install libsdl-image1.2
```

---

### Post by ame82 on 2011-03-11
ok the point is not to run the game i wanna know how to install it, 
to learn how to install other software
i made some progress i found out some thing for all new people like me
if u r in a directory and wanna ran a file u cant just write the file name u must write ./ before it which mean look in current folder
so that what i got

deamon@deamon-pc:~/Desktop/sauerbraten$ ls
bin_unix  docs      README.html       server-init.cfg
data      packages  sauerbraten_unix  src
deamon@deamon-pc:~/Desktop/sauerbraten$ sudo ./sauerbraten
sudo: ./sauerbraten: command not found
deamon@deamon-pc:~/Desktop/sauerbraten$ sudo ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
deamon@deamon-pc:~/Desktop/sauerbraten$ 
so i will keep trying if any one has good idea let me know , thanks

---

### Post by ame82 on 2011-03-11
evantually i found this post 
hope it helps
[http://ubuntuforums.org/showthread.php?t=266058](http://ubuntuforums.org/showthread.php?t=266058)

---

### Post by ame82 on 2011-03-11
latest i got is 
Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed
i am so begining , i get lost how i get this liberaries

---

### Post by ame82 on 2011-03-11
now i get this
./cube: 89: ./linux_client: not found
i am stuck here any help

---

### Post by dfreer on 2011-03-11
Here's a helpful tip when installing programs: 

If you are getting errors about libraries missing, you can run the ldd command against the binary. Here's an example of what you would see:
```
ldd ./program_name

linux-gate.so.1 => (0xffffe000)
libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0
(0x49ae6000)
libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0x4a157000)
libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x49a52000)
libhal.so.1 => /usr/lib/libhal.so.1 (0x49781000)
libdbus-1.so.2 => /lib/libdbus-1.so.2 (0x49c56000)
libc.so.6 => /lib/libc.so.6 (0x495b8000)
libnsl.so.1 => /lib/libnsl.so.1 (0x498fa000)
/lib/ld-linux.so.2 (0x80000000)
```

The items on the left are the *names* of shared library files, and the right are locations on your system to the files themselves. If you run this against your program, and find that on the right side there is an error like "File not found" or "Missing", that means you are missing a shared library, i.e. a dependency.

You can then go straight to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the shared library name, and it will tell you exactly which package to install. From there, install it from apt-get/aptitude/synaptic.

Some more detailed explanation:
In linux, binaries (binaries = executable compiled programs) are often dynamically linked, which means some sections of code that are common place are not included in the program itself. Instead, those common sections of code are installed once on your system, and then all programs that use that can access it and it saves you hard drive space and memory.

Now, normally when you install a package the easy, debian way (through apt-get/aptitude/synaptic), all of these *dependencies* are installed automatically for you when you install the program. But in your case, you had to install the package manually, and so now must download all the dependencies yourself.

ldd basically just checks and sees what shared libraries the program is looking for.

EDIT: If none of this helps, here's a start on the packages you need:
> ./bin_unix/linux_client: error while loading shared libraries: **libSDL_image-1.2.so.0**: cannot open shared object file: No such file or directory
```
sudo apt-get install libsdl-image1.2
```

---

### Post by sakuramboo on 2011-03-11
sudo apt-get install sauerbraten

There is a package manager, use it.

---

### Post by ame82 on 2011-03-12
thanks alot DFREE that was so helpfull professional answer, i did what u told me and i got it working, 
and sakurambo ,thanks for ur try but i know about the package for the game, the point is not to play the game , the point is to understand how linux working

---

### Post by calin rusu on 2011-03-20
> **Artificial Intelligence said:**
> Try with:
```
sudo apt-get install libsdl-image1.2
```

add zlibc and sdl mixer to that

sudo apt-get install libsdl-image1.2 libsdl-mixer1.2 zlibc

---

### Post by calin rusu on 2011-03-20
> **sakuramboo said:**
> sudo apt-get install sauerbraten

There is a package manager, use it.

In ubuntu 10.10, the sauerbraten trooper edition installed via synaptic from the repos gives a lot of modified maps alerts on most of the servers. That means you will be put to spectators because server thinks you're playing with a modified map. The best way to avoid it is not to install using apt-get or synaptic but to use the package from sauerbraten home page [http://sourceforge.net/projects/sauerbraten/files/sauerbraten/2010_07_19/sauerbraten_2010_07_28_justice_edition_linux.tar.bz2/download](http://sourceforge.net/projects/sauerbraten/files/sauerbraten/2010_07_19/sauerbraten_2010_07_28_justice_edition_linux.tar.bz2/download) .
Download it, unpack it in your home directory make sure you have all libraries required (sudo apt-get install libsdl-image1.2 libsdl-mixer1.2 zlibc). You can start the game just by clicking the sauerbraten_unix file inside the sauerbraten directory.
Or, for ease of use create a desktop launcher: open an empty gedit document on Desktop and put this in it:

!#/bin/sh
cd ~/sauerbraten
sh ./sauerbraten_unix

save and close
Name the file "sauerbraten" and make it executable and start the game by clicking on it.

---

