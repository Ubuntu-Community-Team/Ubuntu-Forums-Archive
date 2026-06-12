---
title: "how to install the tar.bz"
date: 2009-04-13
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-13
**** how to install tar.bz file and the how to convert the package rpm to .deb and deb to.rpm. anyone know means reply me..

---

### Post by Aubergines on 2009-04-13
Check [Compiling Easy How To](https://help.ubuntu.com/community/CompilingEasyHowTo) and [Alien](http://taufanlubis.wordpress.com/2008/01/22/alien-%E2%80%93-convert-rpm-to-deb-or-deb-to-rpm/)

---

### Post by 3Miro on 2009-04-13
First of all, you shouldn't play with .rpm and .tgz unless there is no other option. So make sure that whatever you are installing is not in the Ubuntu repository already.

tgz is actually an archive (like .zip). Then you install stuff from it depending on what is in it. There should be instructions on how to install it either on the web-page where you downloaded it or inside the archive or both. Look for INSTALL and README and read carefully. (if it is the source-code for something for example, you will have to compile it with commands like make, make install)

to convert .rpm to .deb, you can use alien. It is a program that you can install from the repos. To see how it works, wither got to Google and search for tutorials or go to Apps -> Accessories -> Terminal and type
```
man alien
```

Again, this should be the last resort.

---

### Post by benj1 on 2009-04-13
if its a tar.bz file
```

tar -jxf file.tar.bz
```
should extract it 
is it already a .deb or .rpm? ive never come across one thats been compressed in a tar archive.
anyway after its extracted, if its a .deb file doble clicking on it will start an installer.
if its an rpm see other posters above (although you may just be better off getting the source or looking for the .deb).
if its anything else open up the file and read the README and INSTALL files they should give you full instructions for installing

---

### Post by ceylonerana on 2009-04-13
You can simply try this..

To Extract your file 

"tar xvzf your_file_name.tar.gz"

-x means extract. -v means verbose (list what it is extracting). -z means filter through gzip. gzip is what compresses the archive (tar cannot compress them remember?). -f specifies the file to use. (You could extract this package by first using the command gzip, then you would be left with a .tar file. You would then not have to specify the -z switch as it would no longer be compressed.) OK...

Then you can try this.

cd /path/to/extracted/package
./configure
make
make install

Typing ./ before a filename tells unix to try and execute the file as an application.

If build is successful, consider making an Ubuntu (Debian) package (.deb) for future use: 

I think these information is good enough to achieve your task. For converting .deb --> .rpm & .rpm --> .deb I too think alien is better. I never use it. But I read several articles about that.

If you need more info ::- [http://kubuntuguide.org/index.php?title=Feisty](http://kubuntuguide.org/index.php?title=Feisty)

Have Fun....:guitar:

---

### Post by benj1 on 2009-04-13
> **ceylonerana said:**
> You can simply try this..

To Extract your file 

"tar xvzf your_file_name.tar.gz"


it needs to be ```
tar -xjf your_file_name.tar.bz
```

the op said it was a bzip archive

---

