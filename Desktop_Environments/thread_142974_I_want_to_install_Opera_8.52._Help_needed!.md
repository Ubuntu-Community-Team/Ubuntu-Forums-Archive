---
title: "I want to install Opera 8.52. Help needed!"
date: 2006-03-11
forum: Desktop Environments
---

### Post by traveller on 2006-03-11
Hello, I installed Ubuntu 5.10 today and then downloaded the latest version of Opera for Ubuntu . Now I have the .deb package and I want to proceed but I have no previous experience at all with this kind of installation. I've searched the forum and found some advice, still things seem rather complicated to a beginner like me. Here's what I did so far: I  started by typing the following command in the terminal: 

sudo dpkg opera_8.52-20060201.6-shared-qt_en_etch_i386.deb 

Then the following message appeared:
Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I experimented  -I think by choosing 'aptitude'- I arrived at a black screen at some moment with some further instructions but being unsure about what was the right thing to do next I stopped in order to avoid making any damage by ignorance. 
Any help would be much appreciated. Thank you in advance.

---

### Post by brainformat on 2006-03-11
sudo dpkg** -i **opera_8.52-20060201.6-shared-qt_en_etch_i386.deb

---

### Post by brainformat on 2006-03-11
my point is that u have missed to type "-i"
that "-i" means "install". if u don't write that dpkg doesn't know what to do with ur opera packge...

---

### Post by traveller on 2006-03-11
[QUOTE=brainformat]my point is that u have missed to type "-i"
that "-i" means "install". if u don't write that dpkg doesn't know what to do with ur opera packge...[/QUOTE]
Thanks for your reply but I tried again and here's the new message I got:

@ubuntu:~$ sudo -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
-bash: opera_8.52-20060201.6-shared-qt_en_etch_i386.deb: No such file or directory 

I hope that the above is an exact copy of what appeared in the terminal. What do you think about this new message? Is there something I'm doing wrong? Please let me know.

---

### Post by cobralgato on 2006-03-11
what if you download the tarball from opera.com  and install it from the terminal ?  it worked for me..

---

### Post by traveller on 2006-03-11
[QUOTE=cobralgato]what if you download the tarball from opera.com  and install it from the terminal ?  it worked for me..[/QUOTE]
Do you mean "Download this package in TAR.GZ format instead of your distribution's native format"? I'm downloading it right now...

---

### Post by mustang on 2006-03-11
[QUOTE=traveller]Do you mean "Download this package in TAR.GZ format instead of your distribution's native format"? I'm downloading it right now...[/QUOTE]

Don't do that. Stick with the .deb file you originally downloaded.

```
@ubuntu:~$ sudo -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
-bash: opera_8.52-20060201.6-shared-qt_en_etch_i386.deb: No such file or directory 
```

First off, the command is incorrect. Second, you need to navigate to the directory where the .deb file is located. First go into nautilus and find where you put the file. Then use the **cd** & **dir** commands to go to that directory. Once you're there, type in

sudo dpkg -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb

Let us know if you have any questions.

---

### Post by traveller on 2006-03-11
[QUOTE=cobralgato]what if you download the tarball from opera.com  and install it from the terminal ?  it worked for me..[/QUOTE]
@ubuntu:~$ sudo dpkg -i opera-8.52-20060201.6-shared-qt.i386-en.tar.gz
dpkg: error processing opera-8.52-20060201.6-shared-qt.i386-en.tar.gz (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-8.52-20060201.6-shared-qt.i386-en.tar.gz

---

### Post by aysiu on 2006-03-11
You're still trying to install the **.tar.gz**
You want to install the **.deb**

---

### Post by traveller on 2006-03-11
[QUOTE=aysiu]You're still trying to install the **.tar.gz**
You want to install the **.deb**[/QUOTE]
That was before reading mustang's message. Just replied to the previous message I had received...

---

### Post by aysiu on 2006-03-11
[QUOTE=traveller]That was before reading mustang's message. Just replied to the previous message I had received...[/QUOTE] But if you're now using a .deb, why did you type this command? ```
@ubuntu:~$ sudo dpkg -i opera-8.52-20060201.6-shared-qt.i386-en.**tar.gz**
```

---

### Post by traveller on 2006-03-11
[QUOTE=aysiu]But if you're now using a .deb, why did you type this command? ```
@ubuntu:~$ sudo dpkg -i opera-8.52-20060201.6-shared-qt.i386-en.**tar.gz**
```[/QUOTE]
Hi, not any more. I did not try with the .tar again. Just replied to the other kind message I had received before mustang's message -as I already explained to you. I'll  try again with the .deb package and I'll let you know. Thank you for your interest.

---

### Post by aysiu on 2006-03-11
[QUOTE=traveller]Hi, not any more. I did not try with the .tar again. Just replied to the other kind message I had received before mustang's message -as I already explained to you. I'll  try again with the .deb package and I'll let you know. Thank you for your interest.[/QUOTE] Just so you know, I've had a lot better luck installing the **Other/Static DEB** than the Ubuntu .deb.

---

### Post by traveller on 2006-03-12
[QUOTE=mustang]Don't do that. Stick with the .deb file you originally downloaded.

```
@ubuntu:~$ sudo -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
-bash: opera_8.52-20060201.6-shared-qt_en_etch_i386.deb: No such file or directory 
```

First off, the command is incorrect. Second, you need to navigate to the directory where the .deb file is located. First go into nautilus and find where you put the file. Then use the **cd** & **dir** commands to go to that directory. Once you're there, type in

sudo dpkg -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb

Let us know if you have any questions.[/QUOTE]

Hi! 
Here's what I did so far:

nikolaos@ubuntu:~$ cd /home/nikolaos/Downloads
nikolaos@ubuntu:~/Downloads$ sudo dpkg -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
Password:
Selecting previously deselected package opera.
(Reading database ... 57669 files and directories currently installed.)
Unpacking opera (from opera_8.52-20060201.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
nikolaos@ubuntu:~/Downloads$

I then opened the Synaptic Package Manager (I got a warning that I have 1 broken package), I found xlibs (do I really need this?) in Libraries but I suppose I have to find where the other packages are as well. Meanwhile, the red icon (automatic updates) appeared I clicked and I received the warning "You have 1 broken package on your system! Use the "Broken" filter to locate it". 

What do you think? How am I doing? Please let me know.

---

### Post by JimJones56 on 2006-03-12
You're getting there! 

The pipe "|" part of the error message works like an "OR" so you need either "xlib6g" OR "xlibs" - since you've already found xlibs, let's use that. In Synaptic, click the box to the left of xlibs and select install. Use the search button on the toolbar to find "libqt3-mt" and also select it for installation. Then click the "Apply" button on the toolbar and click through the OKs.

Once these are installed, try running the dpkg command again.

You know that automatix will install Opera (and lots of other apps) automatically, don't you? :)

---

### Post by feathers on 2006-03-12
If opera 8.51 is enough for you , add this line to /etc/apt/sources.list: 
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
then type sudo apt-get update
and then: sudo apt-get install opera

---

### Post by JimS on 2006-03-12
...

I would like to jump in here and thank brainformat and others for their  help.
I was able to update Opera with NO problems and
using the same technique I also updated gramps,
my genealogy program.

I also learned something that some of you might find helpful.
When in terminal and using sudo dpkg -i
sometimes you get the error saying it "can't find" things.
Here is what worked for me in my very limited experiment:

I open file manager and find the package I downloaded.
I right click on it and copy.
In terminal I type sudo dpkg -i [with a space after] and paste.
--Here is the nice thingy--
When pasting I not only get the package, but also I get the directory structure pasted in also.
I assume (perhaps wrongly) that copying/pasting the pkg
after sudo gpkg -i, I will no longer get "can't find" errors.
Anyway it worked for me.  :D 

[COLOR="Red"]JimS[/COLOR]
[COLOR="Red"][COLOR="Blue"]Prostate Cancer Aware[/COLOR][/COLOR]

,,,

---

### Post by Xian on 2006-03-12
[QUOTE=JimS]I also learned something that some of you might find helpful. When in terminal and using sudo dpkg -i
sometimes you get the error saying it "can't find" things.
Here is what worked for me in my very limited experiment:[/QUOTE]

If you mean by "can't find" that dpkg is unable to locate the pkgs you want to install then your remedy would suffice nicely, but it will would still have difficulty finding dependencies to satisfy, since it will only look for those which are installed locally.

Dpkg defaults to looking in your home directory for pkgs to install, so if you will just place them there to begin with you will never have to paste in any sort of path.

---

### Post by paul cooke on 2006-03-12
add the repository for Opera to synaptic and then the official version of Opera will be in the list of available items... also, whenever they update their package, your package is updatable

the repository info you want in synaptic is here in my little screenshot:

---

### Post by traveller on 2006-03-12
[QUOTE=paul cooke]add the repository for Opera to synaptic and then the official version of Opera will be in the list of available items... also, whenever they update their package, your package is updatable

the repository info you want in synaptic is here in my little screenshot:[/QUOTE]

Thank you for your message. I think I managed to add it and now I can see Opera 8.50 static (Opera 8.52 had a red mark for removal) and the message "Welcome to the Opera Web browser." Perhaps it's ready for installation but I also read that "The binaries were built on a RedHat-6.2 (zoot) installation using gcc-2.95.3." And there's also a warning that I am about to install software that can't be authenticated. What do you think? Thanks again.

---

### Post by traveller on 2006-03-12
[QUOTE=JimJones56]You're getting there! 

The pipe "|" part of the error message works like an "OR" so you need either "xlib6g" OR "xlibs" - since you've already found xlibs, let's use that. In Synaptic, click the box to the left of xlibs and select install. Use the search button on the toolbar to find "libqt3-mt" and also select it for installation. Then click the "Apply" button on the toolbar and click through the OKs.

Once these are installed, try running the dpkg command again.

You know that automatix will install Opera (and lots of other apps) automatically, don't you? :)[/QUOTE]

Thank you for your kind and encouraging reply. I found again and installed xlibs but I searched and I did not find the other package needed.
So when I tried once more...
@ubuntu:~/Downloads$ sudo dpkg -i opera_8.52-20060201.6-shared-qt_en_etch_i386.deb
Password:
Selecting previously deselected package opera.
(Reading database ... 57674 files and directories currently installed.)
Unpacking opera (from opera_8.52-20060201.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

Please tell me more about automatix. Where can I find it?

---

### Post by JimJones56 on 2006-03-12
Strange... searching for "libqt" brings libqt3-mt up as the first option for me.

Anyway, Automatix is here: [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

Basically, all you need to do is to enter these into a Terminal window:

```
wget http://beerorkid.com/automatix/automatix_5.6-2_i386.deb
```
And
```
sudo dpkg -i automatix_5.6-2_i386.deb
```

And then run it from the Applications > System Tools menu.

---

### Post by traveller on 2006-03-13
[QUOTE=JimJones56]Strange... searching for "libqt" brings libqt3-mt up as the first option for me.

Anyway, Automatix is here: [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

Basically, all you need to do is to enter these into a Terminal window:

```
wget http://beerorkid.com/automatix/automatix_5.6-2_i386.deb
```
And
```
sudo dpkg -i automatix_5.6-2_i386.deb
```

And then run it from the Applications > System Tools menu.[/QUOTE]
Goodmorning from Greece! :D  Browsing the Web with my Opera (Version 8.51 Build	1462 	Platform Linux)... I received your second message during the night/early morning hours, I followed your instructions, downloaded Automatix and it worked! Automatix is so fast, methodical and yet simple to use even for beginners. Thank you very much! You've been so kind and helpful to me. Again, thank you very much!!!

---

### Post by traveller on 2006-03-13
Thanks to all of you for your help!

---

