---
title: "Quake II Problem"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by enim on 2006-07-19
Yes, its old news, but, i want to run quake2.  I *hopefully* have it installed correctly and everything, but, i have two questions.

One, when making a symlink, i get an error message claiming the files that are being linked both exist.  Can i just ignore that?


And also, i get this while trying to run Quake:

```
jon@jon-desktop:~/Desktop/Torrents/quake2$ ./quake2
Added packfile ./baseq2/pak0.pak (3386 files)
Added packfile ./baseq2/pak2.pak (2 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------- Loading ref_soft.so -------
LoadLibrary("ref_soft.so") failed: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
```

So, im guessing something got really screwed up.  Any help would be very appreciated.

---

### Post by scxtt on 2006-07-19
what was this symlink?, cause it looks like "ref_soft.so" isn't present ... and it seems like your sound device is locked up ...

---

### Post by enim on 2006-07-19
The soundcard is locked becuase XMMS was running, and i forgot to close it.

The symlink was 
```
jon@jon-desktop:~/Desktop/Torrents/quake2$ ln -s /usr/lib32/libGL.so.1 libGL.so
ln: creating symbolic link `libGL.so' to `/usr/lib32/libGL.so.1': File exists

```

Now, i think the problem with the missing .so was something to do with software rendering.

And im still lost here:  Following [this]("https://help.ubuntu.com/community/Games/Native/Quake2"), it tells me i can go ./quake2_ (etcetcetc), and have the game run.

but this happens:

```
jon@jon-desktop:~/Desktop/Torrents/quake2$ ./quake2_ +set vid_ref glx
bash: ./quake2_: Permission denied

```

Help?

---

### Post by goobers on 2006-07-19
try running it as root:

```

sudo ./quake2_ +set vid_ref glx

```

---

### Post by enim on 2006-07-19
It says "Command not found"

---

### Post by scxtt on 2006-07-19
well it's quite possible it does exist ... looks like you're in '~/Desktop/Torrents/quake2' -- do an **ls -l** and see if you have a **libGL.so --> /usr/lib32/libGL.so.1** entry ... also do an **ls -l** on this quake2_ file to make sure it's executable ...

---

### Post by enim on 2006-07-19
> **scxtt said:**
> well it's quite possible it does exist ... looks like you're in '~/Desktop/Torrents/quake2' -- do an **ls -l** and see if you have a **libGL.so --> /usr/lib32/libGL.so.1** entry ... also do an **ls -l** on this quake2_ file to make sure it's executable ...

Its there, and i know that the quake2 file is an executable

---

### Post by goobers on 2006-07-19
Perhaps you could do an **ls** of the quake folder and post the contents here?

---

### Post by enim on 2006-07-19
```
jon@jon-desktop:~/Desktop/Torrents/quake2$ ls
3.20_Changes.txt  opengl32                                        readme.txt
baseq2            quake2                                          ref_gl.so
lib3dfxgl.so      quake2_                                         ref_glx.so
libGL.so          quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz  ref_soft.so
libMesaGL.so      quake2.conf                                     ref_softx.so
libMesaGL.so.2    quake2.conf~                                    rogue
libMesaGL.so.2.6  README                                          xatrix
```

and ls -l if you want that too:
```
jon@jon-desktop:~/Desktop/Torrents/quake2$ ls -l
total 8388
-rwxr-xr-x 1 jon jon    4327 1998-11-30 13:11 3.20_Changes.txt
drwxr-xr-x 3 jon jon    4096 1998-11-30 13:11 baseq2
-rwxr-xr-x 1 jon jon  120460 1998-11-30 13:11 lib3dfxgl.so
lrwxrwxrwx 1 jon jon      21 2006-07-19 13:22 libGL.so -> /usr/lib32/libGL.so.1
lrwxrwxrwx 1 jon jon      14 2006-07-19 13:11 libMesaGL.so -> libMesaGL.so.2
lrwxrwxrwx 1 jon jon      16 2006-07-19 13:11 libMesaGL.so.2 -> libMesaGL.so.2.6-rwxr-xr-x 1 jon jon  897135 1998-11-30 13:11 libMesaGL.so.2.6
lrwxrwxrwx 1 jon jon       8 2006-07-19 13:13 opengl32 -> libGL.so
-rwxr-xr-x 1 jon jon  342972 1998-11-30 13:11 quake2
-rw-r--r-- 1 jon jon      60 2006-07-19 14:02 quake2_
-rw-r--r-- 1 jon jon 6004460 2006-07-19 13:11 quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz
-rw-r--r-- 1 jon jon      26 2006-07-19 14:07 quake2.conf
-rw-r--r-- 1 jon jon      24 1998-11-30 13:11 quake2.conf~
-rw-r--r-- 1 jon jon    8580 1998-11-30 13:11 README
-rwxr-xr-x 1 jon jon   61630 1998-11-30 13:11 readme.txt
-rwxr-xr-x 1 jon jon  285753 1998-11-30 13:11 ref_gl.so
-rwxr-xr-x 1 jon jon  286984 1998-11-30 13:11 ref_glx.so
-rwxr-xr-x 1 jon jon  235055 1998-11-30 13:11 ref_soft.so
-rwxr-xr-x 1 jon jon  242990 1998-11-30 13:11 ref_softx.so
drwxr-xr-x 2 jon jon    4096 1998-11-30 13:11 rogue
drwxr-xr-x 2 jon jon    4096 1998-11-30 13:11 xatrix
jon@jon-desktop:~/Desktop/Torrents/quake2$ ls
3.20_Changes.txt  opengl32                                        readme.txt
baseq2            quake2                                          ref_gl.so
lib3dfxgl.so      quake2_                                         ref_glx.so
libGL.so          quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz  ref_soft.so
libMesaGL.so      quake2.conf                                     ref_softx.so
libMesaGL.so.2    quake2.conf~                                    rogue
libMesaGL.so.2.6  README                                          xatrix
jon@jon-desktop:~/Desktop/Torrents/quake2$ ls -l
total 8388
-rwxr-xr-x 1 jon jon    4327 1998-11-30 13:11 3.20_Changes.txt
drwxr-xr-x 3 jon jon    4096 1998-11-30 13:11 baseq2
-rwxr-xr-x 1 jon jon  120460 1998-11-30 13:11 lib3dfxgl.so
lrwxrwxrwx 1 jon jon      21 2006-07-19 13:22 libGL.so -> /usr/lib32/libGL.so.1
lrwxrwxrwx 1 jon jon      14 2006-07-19 13:11 libMesaGL.so -> libMesaGL.so.2
lrwxrwxrwx 1 jon jon      16 2006-07-19 13:11 libMesaGL.so.2 -> libMesaGL.so.2.6-rwxr-xr-x 1 jon jon  897135 1998-11-30 13:11 libMesaGL.so.2.6
lrwxrwxrwx 1 jon jon       8 2006-07-19 13:13 opengl32 -> libGL.so
-rwxr-xr-x 1 jon jon  342972 1998-11-30 13:11 quake2
-rw-r--r-- 1 jon jon      60 2006-07-19 14:02 quake2_
-rw-r--r-- 1 jon jon 6004460 2006-07-19 13:11 quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz
-rw-r--r-- 1 jon jon      26 2006-07-19 14:07 quake2.conf
-rw-r--r-- 1 jon jon      24 1998-11-30 13:11 quake2.conf~
-rw-r--r-- 1 jon jon    8580 1998-11-30 13:11 README
-rwxr-xr-x 1 jon jon   61630 1998-11-30 13:11 readme.txt
-rwxr-xr-x 1 jon jon  285753 1998-11-30 13:11 ref_gl.so
-rwxr-xr-x 1 jon jon  286984 1998-11-30 13:11 ref_glx.so
-rwxr-xr-x 1 jon jon  235055 1998-11-30 13:11 ref_soft.so
-rwxr-xr-x 1 jon jon  242990 1998-11-30 13:11 ref_softx.so
drwxr-xr-x 2 jon jon    4096 1998-11-30 13:11 rogue
drwxr-xr-x 2 jon jon    4096 1998-11-30 13:11 xatrix

```

If we seem to be getting nowhere with this, is there another way to install this, keeping in mind im a semi-newb?

---

### Post by goobers on 2006-07-19
I have a random suggestion...

```

sudo sh ./quake2_ +set vid_ref glx

```

---

