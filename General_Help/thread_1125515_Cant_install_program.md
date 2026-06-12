---
title: "Cant install program"
date: 2009-04-14
forum: General Help
---

### Post by chipmunkproof on 2009-04-14
i am trying to install mobloquer via terminal. I have all the dependencies as far as i can tell. when i put in qmake-qt4 nothing happens.

heres the text:
adam@adam-laptop ~/Desktop $ tar -xvf mobloquer-xx.tar.gz
tar: mobloquer-xx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
adam@adam-laptop ~/Desktop $ cd mobloquer
adam@adam-laptop ~/Desktop/mobloquer $ tar -xvf mobloquer-xx.tar.gz
tar: mobloquer-xx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
adam@adam-laptop ~/Desktop/mobloquer $ qmake-qt4
adam@adam-laptop ~/Desktop/mobloquer $ make
make: Nothing to be done for `first'.
adam@adam-laptop ~/Desktop/mobloquer $ sudo make install
[sudo] password for adam: 
install -m 755 -p /home/adam/Desktop/mobloquer/images/mobloquer.png /usr/share/pixmaps/
strip /usr/share/pixmaps/mobloquer.png
strip:/usr/share/pixmaps/mobloquer.png: File format not recognized
make: [install_icon] Error 1 (ignored)
install -m 644 -p /home/adam/Desktop/mobloquer/other/Mobloquer.desktop /usr/share/applications/
install -m 755 -p "mobloquer" "/usr/bin/mobloquer"
strip "/usr/bin/mobloquer"

I have no idea whats going on please help.
Thank you

---

### Post by cariboo on 2009-04-14
From the looks of it you have to extract the file first before you can do anything. the easiest way to extract the file is just double click on it and extract it to the directory of your choice. then open a terminal cd into the directory and follow the installation instructions.

Jim

---

### Post by Alekz_ on 2009-04-14
Hmm first of all, the file is "gzipped", so you MUST use tar -zxvf (the Z is used for compressed files)

Cmd:
tar -zxvf mobloquer-xx.tar.gz

PS: Make sure that you're running this command on the same directory that the file mobloquer-xx.tar.gz is!

Now, you should see the directory mobloquer-xx (without extension)

cd into the dir and look for a configure file

You should run ./configure before you run make && make install

Try it and tell us if there was any results!

[]'s

Alekz_

---

### Post by chipmunkproof on 2009-04-14
adam@adam-laptop ~/Desktop $ tar -zxvf mobloquer-xx.tar.gz
tar: mobloquer-xx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



it didnt work. its on my desktop

---

### Post by LowSky on 2009-04-14
cd to the correct file then it may work

for example (this may be it)
cd /home/adam/Desktop/mobloquer

then run the command

---

### Post by Alekz_ on 2009-04-14
chipmunkproof!

This err msg used appear when you're trying to use tar in a file that doesn't exist, or, maybe, you have a wrong type of the file name!

Check this out!
mobloquer-xx.tar.gz
Make sure that the file mobloquer-xx.tar.gz is in your Desktop (~/Desktop/mobloquer-xx.tar.gz). You can do this:

ls -l ~/Desktop/mobloquer-xx.tar.gz

and you must be able to see file information!

[]'s

Alekz_

---

### Post by chipmunkproof on 2009-04-14
I have both the tar.gz and the extracted file on my desktop so i tried them both, as long as the tar without the extension prefix:



adam@adam-laptop ~ $ cd home/adam/Desktop/mobloquer-0.5.tar.gz
bash: cd: home/adam/Desktop/mobloquer-0.5.tar.gz: No such file or directory
adam@adam-laptop ~ $ cd home/adam/Desktop/mobloquer
bash: cd: home/adam/Desktop/mobloquer: No such file or directory
adam@adam-laptop ~ $ cd home/adam/Desktop/mobloquer-0.5.
bash: cd: home/adam/Desktop/mobloquer-0.5.: No such file or directory


Is this a dependency issue or something?

---

### Post by Alekz_ on 2009-04-14
chipmunkproof!

Help us! Type this:

ls -l ~/Desktop

and past the output here! :)

[]'s

Alekz_

---

### Post by chipmunkproof on 2009-04-14
adam@adam-laptop ~ $ ls -l ~/Desktop/mobloquer-xx.tar.gz
ls: cannot access /home/adam/Desktop/mobloquer-xx.tar.gz: No such file or directory
 heres a screenshot

---

### Post by Alekz_ on 2009-04-14
> **chipmunkproof said:**
> adam@adam-laptop ~ $ ls -l ~/Desktop/mobloquer-xx.tar.gz
ls: cannot access /home/adam/Desktop/mobloquer-xx.tar.gz: No such file or directory
 heres a screenshot

Nice! Lets take one more shot... :)

Follow these steps:

```
cd /home/adam/Desktop/
tar -zxvf mobloquer-0.5.tar.gz
```

then, do this:

```
cd /home/adam/Desktop/mobloquer-0.5
```

if everything works fine, you should be able to find a configure file (if there is one)

type this for verify:

```
ls -l configure
```

IF the file exists, then run thi:

```
./configure && make && make install
```

else, just this should be enought:

```
make && make install
```

Hope it works now!

[]'s

Alekz_

---

### Post by chipmunkproof on 2009-04-14
adam@adam-laptop ~/Desktop $ cd /home/adam/Desktop/mobloquer-0.5
bash: cd: /home/adam/Desktop/mobloquer-0.5: No such file or directory


the first code worked.

O well its fine.
Thanks guys for all the help especially you alexz.

---

### Post by Alekz_ on 2009-04-14
No problem! If you want, I think it could be easier for you:

[http://mobloquer.foutrelis.com/download](http://mobloquer.foutrelis.com/download)

Take a look! There is a source foi ubuntu for this app!

[]'s

Alekz_

---

### Post by jre on 2009-04-15
You really should use the packages from [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net). There's also a wiki on [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

You are trying to install mobloquer 0.5. This depends on moblock-control (from [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net)) and moblock ([http://moblock.berlios.de](http://moblock.berlios.de)).

I suggest to use the current release 0.6. This depends on blockcontrol (direct successor of moblock-control) and moblock.
For moblock I strongly recommend to install the current cvs version (0.9rc2) and not the two year old, buggy release 0.8.

So you are currently trying to install outdated software and you will most probably have more trouble installing the two other applications. So take the packages: moblock-deb.sourceforge.net

---

