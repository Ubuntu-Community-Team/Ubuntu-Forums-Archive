---
title: "HJSplit"
date: 2006-04-14
forum: Desktop Environments
---

### Post by zorlab on 2006-04-14
Hmmmm    .........      command is simple enough,eH? ~~> ./HJSplitLX (as per install instructions)
no workie;;  after I installed kylix, (prerequisite)
*[COLOR="Purple"]Any help on this would be appreciated....[/COLOR]*

For those who know another package to install for splitting and joining files  (type .001, .002  etc. )  PLEASE let me know,   because  this is really starting to
**Bug me**](*,)   - ( I prefer GUI )

.......................................................................................................

[COLOR="Blue"]   barry@SCSI:~$ ls
automatix_5.7-3_i386.deb  automatix.log  Desktop  HJSplitLX
barry@SCSI:~$ ./HJSplitLX
./HJSplitLX: symbol lookup error: ./HJSplitLX: undefined symbol: initPAnsiStrings
[/COLOR]
.......................................................................................................

---

### Post by Spano on 2006-04-15
I got the graphical version of hjsplit working by compiling and installing LX Split and GTKlxsplit from this page:
[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)
You want [http://www.freebyte.com/download/lxsplit.tar.gz](http://www.freebyte.com/download/lxsplit.tar.gz)
and from this page:[http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/GTKlxsplit.html](http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/GTKlxsplit.html)
get [http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/packages/gtklxsplit-0.1.1.tar.gz](http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/packages/gtklxsplit-0.1.1.tar.gz)
Didn't need kylix installed, but you will need these packages from synaptic or apt-get: libgtk1.2 libgtk1.2-common libgtk1.2dev
Compile lxsplit first and then gtklxsplit (the graphical frontend).
The run command is ```
gtklxsplit
```

---

### Post by croak77 on 2006-04-15
Just use lxsplit unless you really want a gui. It's really simple. 
lxsplit -s file 100M  (split file into 100M chunks, or any size you want)
lxsplit -j file1.001 file2.002 ( join files)

---

### Post by zorlab on 2006-04-16
**croak77, ** thanks,that is where I ended up anyway, finnally  :D 

You are right, very easy!
Cheers~~~~!

---

### Post by travelbug on 2006-07-12
This thread is a little old, but I'd like to add to it anyway... 

HJSplit has the distinct advantage of being able to join file names with spaces, whereas others can't. 

To get HJSplit working:
export LD_LIBRARY_PATH=/usr/lib/kylix3

Now you can set this environmental variable in ~/.bashrc, or in /etc/bash.bashrc to have it available system-wide. It will not work in ~/.profile or /etc/profile as in other distros. Nor will it work if you try to run the command in ALT+F2. To launch HJSplit, you'll have to run it in a konsole, due to the nonstandard way to set LD_LIBRARY_PATH in ubuntu.

---

