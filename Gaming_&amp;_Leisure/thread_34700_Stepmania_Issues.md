---
title: "Stepmania Issues"
date: 2005-05-16
forum: Gaming &amp; Leisure
---

### Post by Xeppo on 2005-05-16
Just to let you all know from the start, I can be classified as an extreme novice as far as linux goes.

I've downloaded Stepmania 3.9-rc3 from sourceforge. [http://sourceforge.net/project/showfiles.php?group_id=37892](http://sourceforge.net/project/showfiles.php?group_id=37892)

I've unzipped it.

After attempting to run it, I get this error:
```
error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

``` 

I'm running Hoary on an AMD64 3000+ with an ATI 9600xt running the latest proprietary drivers.  I'm also absolutely positive that I have oggvorbis installed.  Any help would be appreciated.

---

### Post by gerbman on 2005-08-28
[QUOTE=Xeppo]Just to let you all know from the start, I can be classified as an extreme novice as far as linux goes.

I've downloaded Stepmania 3.9-rc3 from sourceforge. [http://sourceforge.net/project/showfiles.php?group_id=37892](http://sourceforge.net/project/showfiles.php?group_id=37892)

I've unzipped it.

After attempting to run it, I get this error:
```
error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

``` 

I'm running Hoary on an AMD64 3000+ with an ATI 9600xt running the latest proprietary drivers.  I'm also absolutely positive that I have oggvorbis installed.  Any help would be appreciated.[/QUOTE]

What does ```
ls -l /usr/lib | grep libvorbisfile
``` output?  I have a feeling you just need to create some symlinks to the files Stepmania looks for.

---

### Post by slinga on 2006-01-15
I'm having  the same problem. I'm also on AMD64. I already have libvorbisfile3 installed: 

> apt-get install libvorbisfile3
Reading package lists... Done
Building dependency tree... Done
libvorbisfile3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


> 
ls -l /usr/lib | grep libvorbisfile
-rw-r--r--   1 root root    32348 2005-07-21 20:16 libvorbisfile.a
-rw-r--r--   1 root root      896 2005-07-21 20:16 libvorbisfile.la
lrwxrwxrwx   1 root root       22 2006-01-12 22:21 libvorbisfile.so -> libvorbisfile.so.3.1.0
lrwxrwxrwx   1 root root       22 2006-01-12 17:46 libvorbisfile.so.3 -> libvorbisfile.so.3.1.0
-rw-r--r--   1 root root    28320 2005-07-21 20:16 libvorbisfile.so.3.1.0


---

### Post by Pridkett on 2006-01-31
The problems you're encountering are due to the fact that the binary you've downloaded is for the 32 bit version of StepMania -- and thus StepMania is looking for the 32 bit version of libvorbis (and every other library it uses).  You've got two choices at this point, either install a chroot style environment for running 32 bit apps (under which I've never had much luck with getting a joystick to report more than two buttons) or compile it for 64 bit systems.  Unfortunately, the StepMania 3.9 source code is not AMD64 safe right out of the box.  I've attached a patch that allows it to compile and run just fine on AMD 64 systems.  Hope this helps.

---

### Post by Tyrance on 2006-09-05
Thanks of the patch. 

But how do i use it? :confused: 
Before or after ./configure ? 

I'm kinda new to linux so i dunno of these kind of things. 

Cheers. 

-J

---

### Post by kylebaked on 2006-09-13
*bump*
I'm having the same problem. How do I install this patch?

---

### Post by Echo35 on 2006-09-28
Super bump. Ditto.

---

### Post by sciboy on 2007-02-14
Well if you just want to use the official Stepmania linux binary i put this together pretty quickly.
[http://www.sciboy.org/stepmania/StepMania-AMD64.tar.gz](http://www.sciboy.org/stepmania/StepMania-AMD64.tar.gz)

I couldn't get that patch working so i just chucked together the libraries it needed with some other dudes wrapper script.
It'll work with both the 3.9 and 4.0 binaries, just extract it into the StepMania directory and run the script.

---

### Post by razor2518 on 2007-03-17
I tried to run the script, but appeared this:

Error: directory not safe? Check /tmp/wrap32-root (check=root-700-diretório)

---

### Post by txapelgorri on 2007-05-09
Hi there:

1- Open amd64-wrapper.sh with gedit, vim or whatever you use to edit text files.
2- In a terminal execute this command (used in the script): ```
/usr/bin/stat -c "%U-%a-%F" /tmp/wrap32-$USER/
```
3- If you are not an English user the answer to the previous command will be something like: ```
ibon-700-directorio
``` In my case the answer to that command is in Spanish. Get your eyes on **directorio** word.
4- The rest you must to do is to find in file you have already opened something like:```
 if [ $? -ne 0 -o "$check" != "$USER-700-directory" ]; then,
``` and change **directory** by the word obtained in the answer of the previous command (remember **directorio** word?).
5- Save, run and enjoy! ;)

Cheers, txapelgorri.

---

### Post by micke090 on 2007-05-22
Neither of the fixes submited works for me, i have ubuntu 7.04 and stepmania cvs. When i run the script i get this from the terminal

 ```
 mco@Michael03:~$ '/home/mco/StepMania-CVS-20070325-linux/amd64-wrapper.sh' 
StepMania CVS 4.0 CVS
Log starting 2007-05-22 16:37:53
Couldn't load driver gtk: dlopen(): libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
Error: Couldn't open any loading windows. 
```

---

