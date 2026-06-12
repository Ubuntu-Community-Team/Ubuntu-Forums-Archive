---
title: "Can't install perl make.pl build"
date: 2009-01-20
forum: General Help
---

### Post by dw5437 on 2009-01-20
I am trying to install Eagle Mode file manager from eaglemode.sourcefroge.net. The instructions say that Perl, GCC, libx11-dev, and libxine-dev are the dependencies required. When I download the file to my desktop I cd to /home/dw5437/Desktop and run the command
perl make.pl build 
I get Can't open perl script "make.pl": No such file or directory

I can't even get to the install script so I am kind of stuck. Does anyone have an idea what may be wrong?

Ubuntu 8.10 
Dell XPS 420 Intell quad processor 2 GB ram

---

### Post by taurus on 2009-01-20
Are you even in the right directory?  Is there another directory under ~/Desktop that you have to change to first before you run that command?

What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by sedawk on 2009-01-20
Most likely you have downloaded
  [http://downloads.sourceforge.net/eaglemode/eaglemode-0.72.1.tar.bz2](http://downloads.sourceforge.net/eaglemode/eaglemode-0.72.1.tar.bz2)
which is an archive you have to unpack first.
If you haven't changed your browser settings it is stored in
your Desktop folder.
So this should work after opening a new command line terminal:
```

mkdir ./testing
cd ./testing
tar xvfj ~/Desktop/eaglemode-0.72.1.tar.bz2
cd eagle*
perl make.pl build

```

---

### Post by dw5437 on 2009-01-21
dw5437@dw5437-desktop ~ $ mkdir ./testing
dw5437@dw5437-desktop ~ $ cd ./testing
dw5437@dw5437-desktop ~/testing $ tar xvfj ~/Desktop/eaglemode-0.72.1.tar.bz2
tar: /home/dw5437/Desktop/eaglemode-0.72.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dw5437@dw5437-desktop ~/testing $ ls -la ~/Desktop
total 20
drwxr-xr-x  3 dw5437 dw5437 4096 2009-01-20 19:44 .
drwxr-xr-x 31 dw5437 dw5437 4096 2009-01-21 19:26 ..
drwxr-xr-x  8 dw5437 dw5437 4096 2009-01-16 04:28 eaglemode-0.72.1
-rw-r--r--  1 dw5437 dw5437 2401 2008-12-18 11:27 firefox.desktop
-rw-r--r--  1 dw5437 dw5437 1137 2009-01-05 15:26 thunderbird.desktop
dw5437@dw5437-desktop ~/testing $ 

Thanks for the help. Here is the results of both answers

---

### Post by dw5437 on 2009-01-21
Ok, thanks a million. I cd'd to Desktop and done the eagle* command and it worked. I had never heard of a command with * in it. Will file that one away for future reference.

---

