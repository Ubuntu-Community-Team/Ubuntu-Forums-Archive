---
title: "Reversi/Othello on Linux"
date: 2005-12-24
forum: Gaming &amp; Leisure
---

### Post by htinn on 2005-12-24
After getting bored with Iagno (which plays okay for a beginner on level 3, but is no real challenge for any player with experience), I decided to install WZebra. It runs pretty slow under Wine and the graphics are messed up, so I looked on the author's web site for a Linux version. Sure enough, there is one (LZebra).

[http://www.radagast.se/othello/](http://www.radagast.se/othello/)

LZebra is nice and fast but there are some minor problems with the UI. It took a few minutes to get it to install (some dependencies on old libs that you have to work around). Anyhow, I'm back to getting slaughtered by the computer again. :D

---

### Post by mmariomm on 2007-07-14
I was trying to install Lzebra but I didn't manage it. It seems it is not a easy programs to install for not-experts. Could you tell me how to begin? because I'm really lost. :confused:

Thank you.

---

### Post by mmariomm on 2007-07-21
After I realized I was not going to get too much help I decided to keep trying all the week until i got it. Maybe the problem was one week ago I didn't have any idea of how it worked anything :P.

It seems the problem was it missed lots of libraries. I will write a small summary in case someone is interested on it. Because if you are a noob like me it will be a nightmare.

In my case I just used Ubuntu Feisty Fawn, for that reason I guess the libraries must be different in other linux distributions.

When you download the file just begin entering in the terminal

**sudo ./bookinst **

to install the book. Although you can use your old Wzebra book from windows.

Later when I tried to launch the program began the problems because lot of libraries missing, and even didn't know what was that XD.
in my case,

*libstdc++-libc6.2-2.so.3*

This file missing can be found if you search online. For installing those .rpm was a problem, but checking a bit online you will learn several ways to install them.
The following file is the package that include the missing library.

*86-compat-libs-9.0-2mdk.ia64.rpm*

The next missing library is

l*ibstdc++2.10-glibc2*

Which you could find in the file

*libpng10-1.0.18-2.i386.rpm*

If you have problems to install .rpm, download "Alien" from the synaptic, that is a program to convert .rpm files into .deb, and then later you can install them with a click. Online there is also a lot of information.

Finally I couldn't launch Lzebra because one of the library version was newer than the requirements. Although it was enough doing with the terminal in the directory /usr/lib/

**sudo ln -s libtiff.so.4 libtiff.so.3**

And after that enough with

**./lzebra**



I'm not sure this is the right way to do it, but at least I achieved, and if someone who doesn't have too much idea won't lose so many hours as me xDDD.

Mario.

---

### Post by SanskritFritz on 2007-12-15
Hey, Mario, here is another convert to Ubuntu, me :-)

I use Gutsy, and I also tried to install LZebra. Thanks for your explanations, I dared to go my own way, and found most libraries in deb format, except the libpng one, which I converted using alien. However, when I start LZebra, it looks good, until I click on the board, then it crashes with segmentation fault, core dumped.
LZebra version 4.01

Any ideas, anyone?

---

### Post by Vadi on 2007-12-15
Isn't this game the same as lagno?

Anyway, what I did to get it working was get the following:

sudo apt-get install libstdc++2.10-glibc2.2

I couldn't find the libpng and libtiff anywhere, but I looked in /usr/lib, and libpng.so.3 was there, so I made a link to it, and called it libpng.so.2. Same for libtiff - libtiff.so.4 was there, I made a link to it and called it libtiff.so.3.

So that fooled the game, and it's working too. Doesn't crash when I click on the board either :)

Try that - if you'll need any help, let me know.

---

### Post by mmariomm on 2007-12-15
Yes Vladi, LZebra is the same game than Lagno, although the original name is Reversi/Othello.
 LZebra is the strongest Othello program you can find for Linux, and it is used for professional players for training purposes.

Hey Frank, nice to see you around here. I am sorry I can't not help you because I don't have any idea about it, although maybe you can find for similar errors in other programs. Hope you can make it! :KS

---

### Post by SanskritFritz on 2007-12-16
Hey there, thanks for your help! Hey Mario, nice to see you here also!

I started again installing LZebra from scratch, and did what you suggested. So now I have this message: 

[FONT="Fixedsys"]./lzebra: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/FONT]

Can you help me, what package this belongs to?
I found this and used that at my previous install:
[http://ubuntuforums.org/showthread.php?t=599032](http://ubuntuforums.org/showthread.php?t=599032)
But that install went wrong. Maybe I shoud try installing the rpm packages, like Mario did?

---

### Post by Vadi on 2007-12-16
Stay away from the rpms, if possible. You use debs in Ubuntu.

Synaptic is your friend. Search for "libgtk 1.2" in synaptic - and install the libgtk1.2 and the libgtk1.2-common packages.

---

### Post by SanskritFritz on 2007-12-16
Thanks, that is what I already found. So now I did all you suggested, but the result is the same, segmentation fault, core dumped :-(
Any more ideas? Can I somehow read the dump file to know what is wrong?

---

### Post by Vadi on 2007-12-16
I'm not sure. Try posting it here, maybe we'll figure out something... try mailing the author too.

---

### Post by mmariomm on 2007-12-16
Frank I didn't try to install LZebra on Gutsy but I don't know how to help you because I'm quite noob :). However I would recommend you to install the .rpm packages as this program hadn't been updated during long time and I think it was original programed for Redhat. In fact I don't know if that is true, but you don't lose anything for triying it. Keep us informed.

---

### Post by SanskritFritz on 2007-12-16
I have found the problem. I installed LZebra as root, but tried to execute it as a normal user, of course. I guess, there are some problems writing the log and ini files, as soon I figure out more, I will keep you posted (i tried to set the write permissions for the files). For the time being, I can use it installed in my home folder.
Thanks for all the help here!

---

### Post by SanskritFritz on 2009-11-23
Old and dusty tread, but I again tried to run lzebra, this time on Arch.
I did all the things covered in the thread:
```
ln -s libstdc++.so.5 libstdc++.so.3
ln -s libjpeg.so libjpeg.so.62
ln -s libpng.so libpng.so.2
ln -s libstdc++.so libstdc++-libc6.2-2.so.3
```but now I'm confronted with this message that I cannot make use of:
```
./lzebra: symbol lookup error: ./lzebra: undefined symbol: cerr
```
Any ideas please?

---

### Post by SanskritFritz on 2010-01-22
I must BUMP this thread, I still couldnt figure out why I am receiving that error. I need help please.

---

### Post by DonHaeberle on 2010-12-29
I also tried to run LZebra on Ubuntu 10.10 and for me it works this way:


[LIST=1]
[*]After downloading from the [homepage]("http://radagast.se/othello/") and extracting follow the instructions from the INSTALL file and run **./bookinst** first.
[*]Now **libstdc++-libc6.2-2.so.3** is missing.
To fix this download and install **libstdc++2.10-glibc2.2_2.95.4-24_i386.deb**:
[http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/dapper/libstdc++2.10-glibc2.2)
[*]Now **libgtk-1.2.so.0** is missing.
To fix this follow the instructions of this posting:
[http://ubuntuforums.org/showpost.php?p=10185003&postcount=8]("http://georgia.ubuntuforums.org/showpost.php?p=10185003&postcount=8")
[*]Now **libpng.so.2** and **libtiff.so.3** are missing.
First install **libpng12-dev**:
```
sudo apt-get install libpng12-dev
```Then create the links to these files like in this posting:
[http://ubuntuforums.org/showpost.php?p=2848224&postcount=2](http://ubuntuforums.org/showpost.php?p=2848224&postcount=2)
```
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```
[*]Now **libcanberra-gtk-module.so** is missing (LZebra also seems to run without this but with an error message).
To fix this you've to unset the GTK_MODULES variable (each time before starting LZebra!):
```
unset GTK_MODULES
```(default: GTK_MODULES=canberra-gtk-module)
[*]LZebra should now run without any errors on Ubuntu 10.10. Have fun:
```
unset GTK_MODULES && ./lzebra
```
[/LIST]

---

### Post by elianto on 2011-11-05
I wonder why nobody has wrote about gRhino I found it to be pretty strong (level >=4) and is currently in the repositories. 
what you think?

---

