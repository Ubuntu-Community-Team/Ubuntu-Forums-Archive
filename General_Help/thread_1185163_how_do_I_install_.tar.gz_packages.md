---
title: "how do I install .tar.gz packages"
date: 2009-06-12
forum: General Help
---

### Post by charonred on 2009-06-12
How do I install packages with the .tar.gz extension ?

I know that I need to extract the files to a folder, but what do I do then?

there are 48 .deb packages inside (all for openoffice.org 3.1 which is the upgrade for my current install of OO.org 3.0)

---

### Post by Bigtime_Scrub on 2009-06-12
The way I do it is by making a special directory just for tarballs.
Mine is called "src" but you can make it whatever you like. So we begin:

```
mkdir /home/username/src/ 
```
You should move the tarball into it. In terminal you need to change to that directory. 

```
cd /home/username/src/ 
```

After changing directory in terminal check to make sure the tarball is there. 

```
 ls 
```

When you see the file there run this command to extract.

```
tar -zxvf <filename> 
```

You will have a new directory with source files and you need to get the name. So, run ```
 ls 
``` again. You should see the tarball and the extracted source files. 

You will have to change to the directory with the extracted source files. 

```
 cd <directory> 
```

This is where things get tricky sometimes. Some files have install instructions or read me texts. Check to see if one is there. 

```
 more INSTALL 
```

If nothing is there don't worry and move on.

In general, it goes as the following. 

```
 ./configure
```
```
 make 
```
```
 sudo make install 
```
```
 make clean 
```

Sometimes you don't need the configure command it just depends. 

That's it!

---

### Post by Ptero-4 on 2009-06-12
In the case of the OP. The tarball contains a group of .deb files. He needs to type:
```

sudo dpkg -i *.deb

```
to install all those deb files simultaneously.

---

### Post by colau on 2009-06-12
Or simply clicking the .deb packages will do.

---

### Post by dk_learning_linux on 2009-06-12
Ya click .deb file or try GDebi Package installer ;)

---

### Post by charonred on 2009-06-12
thanks, took a bit of trial and error but it installed.


following instructions from previous reply post;

```
mkdir /home/username/tarsrc/
``` 
('[COLOR="Blue"]tarsrc[/COLOR]' was what I named my folder for tarballs)


I moved the tarball into it, then in terminal I changed to that directory.
```
cd /home/username/tarsrc/
```



After changing directory in terminal, I checked that the tarball was there.
```
 ls
```
(listed the tarball as [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



Then I ran this command to extract it.
```
tar -zxvf <filename>
```
( where <filename> = [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



This created a new directory with source files, and to get the name I ran this
 ```
ls
```
which listed the tarball and the extracted source files.
[COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR]
[COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR]



next I changed to the directory with the extracted source files.
 ```
cd <directory>
``` 
(where my <directory> = [COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR])



after that the other commands didn't work, so I changed directory to the [COLOR="Blue"]DEBS[/COLOR] folder inside 

```
cd <directory>
``` 
(where the <directory> = [COLOR="Blue"]DEBS[/COLOR])



finally I ran the following which completed the install

```
 sudo dpkg -i *.deb
```

after that I fired up OpenOffice.org 3.0 and checked the version number in the 'About' menu which was 3.10

all done - thanks for help :D

.

---

### Post by alphacrucis2 on 2009-06-12
> **charonred said:**
> thanks, took a bit of trial and error but it installed.


following instructions from previous reply post;

```
mkdir /home/username/tarsrc/
``` 
('[COLOR="Blue"]tarsrc[/COLOR]' was what I named my folder for tarballs)


I moved the tarball into it, then in terminal I changed to that directory.
```
cd /home/username/tarsrc/
```



After changing directory in terminal, I checked that the tarball was there.
```
 ls
```
(listed the tarball as [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



Then I ran this command to extract it.
```
tar -zxvf <filename>
```
( where <filename> = [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



This created a new directory with source files, and to get the name I ran this
 ```
ls
```
which listed the tarball and the extracted source files.
[COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR]
[COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR]



next I changed to the directory with the extracted source files.
 ```
cd <directory>
``` 
(where my <directory> = [COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR])



after that the other commands didn't work, so I changed directory to the [COLOR="Blue"]DEBS[/COLOR] folder inside 

```
cd <directory>
``` 
(where the <directory> = [COLOR="Blue"]DEBS[/COLOR])



finally I ran the following which completed the install

```
 sudo dpkg -i *.deb
```

after that I fired up OpenOffice.org 3.0 and checked the version number in the 'About' menu which was 3.10

all done - thanks for help :D

.

Note that there is a PPA for OO3.1 here:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by charonred on 2009-06-12
I ended up doing it the above method because I tried several times this morning to get the PPA to install the update/install files, but it just doesn't work in my system, despite adding the key and the repositories .. don't know why, and that's why I had to resort to using the .tar.gz method.

---

