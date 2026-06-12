---
title: "superkaramba dependencies / version 0.36"
date: 2005-05-30
forum: Desktop Environments
---

### Post by F for Fragging on 2005-05-30
I'm wondering why superkaramba has xmms as a dependency (not every karamba theme uses xmms), and why version 0.36 isn't in the APT repository yet?

I downloaded 0.35 from the repo, but some themes like liquidweather++ need 0.36. I tried installing the 0.36 deb from breezy - [http://packages.ubuntu.com/breezy/kde/superkaramba](http://packages.ubuntu.com/breezy/kde/superkaramba) - but that one whined about some libraries not being up to date (libidn or something, which can't be upgraded with kynaptic), so I gave up on that.

---

### Post by digby on 2005-05-31
As I understand the development process, 0.36 won't be put into the regular Hoary repositories.  0.35 was realeased and won't be updated except in Breezy.  When Breezy is released, whatever is current then will be used until the next Ubuntu release is finished.

What you can do is look for a slightly older version of Liquid Weather.  I have one running fine on my Hoary install.

---

### Post by F for Fragging on 2005-05-31
Great... and there isn't a backport either. I haven't been able to find an old version, so maybe I'll try compiling from source. Thanks for your help though.

---

### Post by geearf on 2005-05-31
I've compiled, was quite easy (except for the little dependencies i did not have and could not, but past that it was cool) and now everything is smooth :)

---

### Post by F for Fragging on 2005-05-31
I also decided to compile, but of course that gives problems. First i had to d/l 50 MB's of dependency packages or so. But after ./configure said it was fine I started make, and after that I got an error. I googled and I found this: [http://www.linuxquestions.org/questions/history/324916](http://www.linuxquestions.org/questions/history/324916)

My problem is that if I try to install python2.4-dev which seems necessary to be able to compile, Kynaptic wants to remove kdelibs, kde-core and kde-devel!

So what can I do about this?

---

### Post by carney1979 on 2005-05-31
> 
My problem is that if I try to install python2.4-dev which seems necessary to be able to compile, Kynaptic wants to remove kdelibs, kde-core and kde-devel!


All I did was do an 'apt-get build-dep superkaramba' from a konsole and all the dependencies to build it were installed. Nothing was removed.

Version 36 then built perfectly. The only gripe I had was I didn't read the docs carefully enough and it installed itself to /usr/local/kde, which of course is not in my path. I just copied the file from /usr/local/kde/bin to /usr/bin and the file from /usr/local/kde/share/applnk/Utilities to /use/share/applications and all worked well. The Superkaramba menu entry was in the 'Lost and Found' menu after the last step so I simply adjusted it with KDE's menu editor.

David

---

### Post by F for Fragging on 2005-06-04
I tried apt-get build-dep superkaramba as well and now make doesn't give an error anymore :)

However, there was another problem. After I ran ./configure, make and make install succesfully, superkaramba wouldn't start with the command superkaramba.

With a few secs of googling I found this in the superkaramba FAQ:

> 1.4. After running ./configure,make, and make install, the superkaramba executable is not where I expected it to be. When I try to run superkaramba from the command line it says "command not found". 
In some distributions ./configure points to different path than you might expect. For example, in Mandrake the default ./configure prefix is /usr/local/kde and the executable is installed in /usr/local/kde/bin. There are a few things you can do to fix this. You could run ./configure --prefix=/usr to specify the prefix that you prefer and then try make and make install again. Or you could create a symbolic link in your preferred directory that links to the executable. Or you could add the install directory to your $PATH.

So I did ./configure --prefix=/usr and that made it work :)
So, in short for those who have this problem as well and want to fix it:

```
sudo apt-get build-dep superkaramba
<change dir to superkaramba dir>
sudo ./configure --prefix=/usr
sudo make
sudo make install
```

---

### Post by Xian on 2005-06-11
[QUOTE=F for Fragging]
```
<change dir to superkaramba dir>
sudo ./configure --prefix=/usr
sudo make
sudo make install
```[/QUOTE]
Thanks for the info. You don't need the "sudo" in all of those instances. 
It is only necessary in the "make install" command.

In addition, I would use checkinstall to create a deb file so it is accounted for in the package management system. 

This would be the process:

```
$ sudo apt-get install checkinstall
<change dir to superkaramba dir>
$ ./configure --prefix=/usr
$ make
$ sudo checkinstall
```

---

### Post by Xian on 2005-06-11
There is now a .36 version available for Ubuntu at KDE-Look: [SK-0.36-Ubuntu](http://www.kde-look.org/content/show.php?content=25231)

---

### Post by elsewhere on 2005-06-12
FWIW, I got some pretty strange dependency requirements with the ubuntu package of superkaramba, like dnet (?), when I tried to install...  I instead went with the version on kde-look for Debian and it installed perfectly.

Cheers,
KV

---

### Post by Xian on 2005-06-12
I know that when I was first going to install this from source I did a build-dep command and it was very lengthy (talking in excess of 20 packages).

```
$ sudo apt-get build-dep superkaramba
```

---

### Post by geearf on 2005-06-13
[QUOTE=Xian]Thanks for the info. You don't need the "sudo" in all of those instances. 
It is only necessary in the "make install" command.

In addition, I would use checkinstall to create a deb file so it is accounted for in the package management system. 

This would be the process:

```
$ sudo apt-get install checkinstall
<change dir to superkaramba dir>
$ ./configure --prefix=/usr
$ make
$ sudo checkinstall
```[/QUOTE]
you mean that if i do a checkinstall on any apps i am building instead of a make install, it will go to apt too ?
If that is true it would be so cool.

---

### Post by Xian on 2005-06-13
[QUOTE=geearf]you mean that if i do a checkinstall on any apps i am building instead of a make install, it will go to apt too ?
[/QUOTE]
Sure, just try it. It will occasionally not work on some python based applications but besides that you shouldn't have any problems.

---

### Post by geearf on 2005-06-13
Well that is cool then thanks :)

But now if i want superkaramba in apt i need to build it again, maybe i'll do it, but maybe not (same for my amule).

---

### Post by Xian on 2005-06-13
[QUOTE=geearf]But now if i want superkaramba in apt i need to build it again, maybe i'll do it, but maybe not (same for my amule).[/QUOTE]
Not at all. I assume that you still have the source files that you compiled with on your system. You certainly should since without it you will have a most difficult time ever uninstalling them by using the 'make uninstall' command. Just go back into the source directory and issue the command below to place the package into the APT management system.

```
$ sudo checkinstall
```

---

### Post by geearf on 2005-06-13
i just tested it at work, it seems to work, i am installing it to my home right now, but i needed to install checkinstall before :)

---

