---
title: "How to install Cube 1? (Or how to really install tarballs?)"
date: 2013-01-22
forum: Gaming &amp; Leisure
---

### Post by linux.convert on 2013-01-22
Ok so I am running Crunchbang (Debian 6 + Openbox) and I am attempting to install Cube 1 (not Cube 2 Saurbraten or Assault Cube) from source, .tar.gz...

I know that you have to first uncompress to a folder then run in terminal:

./configure
make
make install

At the ./configure stage I get this:

```


ldc@crunchbang:~/games/cube$ ./configure
bash: ./configure: No such file or directory


```

I have gotten this error many times before, so it seems high time  to figure this crap out already.

Any help at all will be appreciated.

---

### Post by BcRich on 2013-01-23
Hi,
the error is indicating that the configure script can't be found in the current directory.
Are you certain there is a file called "configure" in the directory "~/games/cube/"?
You might also want to install the build-essential package, if you haven't already done so.
There should also be a file with installation instructions usually in the root (or one level below) of the installation folder, called something like "readme" or "install", etc. You'll need to read that file because it will likely list the dependencies that will be required for a successful installation.
good luck :)

---

### Post by linux.convert on 2013-01-23
1. I have build-essential (I wasnt sure so I ran the code and I already had it installed)

2. There is a readme file that I have gone through and I appears to be written for the windows version (even though it has linux stuff for making custom keybindings), because it refers to a cube.bat file that isnt in this folder. It doesnt say anything about ./configure make make install or anything at all about installation.

3. There is autoexec.cfg source code, and cube_unix shell script which doesnt do anything when I tell it to execute (at least not in the file manager, I have no idea how to run it from terminal).

---

### Post by AM Ramakrishnan on 2013-01-23
By > Cube 1 do you mean AssaultCube? I installed it from the Ubuntu Software Center and it works well.

---

### Post by linux.convert on 2013-01-23
No, Assault Cube is a mod of Cube 1. Cube 1 has like a single player and stuff. And its more like Quake 2, where Assault Cube is more like Counter Strike in realism.

Although I do have Assault Cube as well.

---

### Post by BcRich on 2013-01-24
> **linux.convert said:**
> 1. I have build-essential (I wasnt sure so I ran the code and I already had it installed)

2. There is a readme file that I have gone through and I appears to be written for the windows version (even though it has linux stuff for making custom keybindings), because it refers to a cube.bat file that isnt in this folder. It doesnt say anything about ./configure make make install or anything at all about installation.

3. There is autoexec.cfg source code, and cube_unix shell script which doesnt do anything when I tell it to execute (at least not in the file manager, I have no idea how to run it from terminal).
Hi,
May I ask if the tarball you downloaded is one of these [http://sourceforge.net/projects/cube/files/cube/2005_08_29/](http://sourceforge.net/projects/cube/files/cube/2005_08_29/) (perhaps the unix release). It might also be worth noting that on this page [http://cubeengine.com/cube.php4](http://cubeengine.com/cube.php4) only suppot for x86 Linux is noted. Can you confirm that your architecture matches this?
If there are no make instructions or a configure file within the main directory of the uncompressed tarball, then the game might already be precompiled.
What happens when you try to run the cube_unix from terminal?

---

### Post by Bölvaður on 2013-01-24
> **linux.convert said:**
> 3. There is autoexec.cfg source code, and cube_unix shell script which doesnt do anything when I tell it to execute (at least not in the file manager, I have no idea how to run it from terminal).

You should always use the terminal when doing "serious business".
autoexec.cfg is a config file, not a source code. The source code is kept within the src directory, which is the place were you will want to find your way to with the terminal (use the cd command such as "cd /home/linux.convert/cube/" and then "cd src"). Then (inside of cube's src/ directory) execute the following:
```

make clean all install
```
Taken from: [http://cube.wikispaces.com/Install+Guide](http://cube.wikispaces.com/Install+Guide)

If this does not work, please tell us where you got your files from so we can take a peek.

---

### Post by linux.convert on 2013-01-24
First, I got cube from 

[http://sourceforge.net/projects/cube/files/cube/2005_08_29/](http://sourceforge.net/projects/cube/files/cube/2005_08_29/)

I navigated to this page for all the versions of cube, I don't know what the src version is, I have downloaded that now.

Second (I'm not sure I did this right)
```

ldc@crunchbang:~/games/cube$ ./cube_unix
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Third, the cube_2005_08_29_src.zip that I just downloaded has a src folder in it, other than that there one in /usr and /usr/local but none in my home directory.

```

ldc@crunchbang:~/games/cube$ ls
autoexec.cfg  cube_unix  demos  packages     savegames
bin_unix      data       docs   readme.html  screenshots

```

---

