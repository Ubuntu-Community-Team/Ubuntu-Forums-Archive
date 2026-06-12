---
title: "RPN Programmable Calculator suggestions"
date: 2009-11-09
forum: Education &amp; Science
---

### Post by magicmax0 on 2009-11-09
Im looking for a Reverse Polish Notation (RPN) calculator program for Linux. Must be programmable, im not too picky on the exact syntax of the language, as long as there is adequate instruction on its use (man page). Preferably something in the Ubuntu Repositories (or has a .deb for it). Any suggestions welcome!

---

### Post by tgalati4 on 2009-11-10
rpn apt-cache search

---

### Post by gunksta on 2009-11-10
I would recommend using this instead:

```
apt-cache search rpn
```

Or, you could also open Kpackagekit, Synaptic, etc. and search there. I'll be the first to admit that I do most of my system administration from the command-line, but I'm not convinced that opening the terminal is the best solution for every package search on the planet.

---

### Post by magicmax0 on 2009-11-10
> **gunksta said:**
> I would recommend using this instead:

```
apt-cache search rpn
```Or, you could also open Kpackagekit, Synaptic, etc. and search there. I'll be the first to admit that I do most of my system administration from the command-line, but I'm not convinced that opening the terminal is the best solution for every package search on the planet.

I have tried all results of "rpn". Most function very well as basic RPN calculators but are not programmable, i specifically would like to save variables and automate the arithmetic using a script or programing language supported by the calculator.

---

### Post by gunksta on 2009-11-10
I did a little looking and there are some options out there, but not too many that are being actively developed any more.

I remember when I was in college, I used a calculator called qalculate. Not sure if it does RPN, but it is programmable. Unfortunately, it looks like development ceased in 2007.
[http://qalculate.sourceforge.net/](http://qalculate.sourceforge.net/)

There are a few emulator programs for HP calculators. Some require you to download the system ROM from HP, others do not.
[http://www.hpcalc.org/hp48/pc/emulators/](http://www.hpcalc.org/hp48/pc/emulators/)
[http://www.linuxfocus.org/common/src/article319/hp67.html](http://www.linuxfocus.org/common/src/article319/hp67.html)

Finally, I did find vc. It's a perl script that is essentially a programmable vector calculator and it does RPN.
[http://vc-calc.sourceforge.net/](http://vc-calc.sourceforge.net/)

Being perl, the last one should be very extensible/programmable, but it's CLI only. You didn't mention whether or not you wanted something with a GUI, but it looks like Qalculate was the best programmable GUI calculator.

Finally, there is a module for Python that lets it do RPN style calculations. Again, it's CLI only, but it's running in python so it's as programmable as you want it to be.
[http://calcrpnpy.sourceforge.net/](http://calcrpnpy.sourceforge.net/)

---

### Post by magicmax0 on 2009-11-10
> **gunksta said:**
> I did a little looking and there are some options out there, but not too many that are being actively developed any more.

I remember when I was in college, I used a calculator called qalculate. Not sure if it does RPN, but it is programmable. Unfortunately, it looks like development ceased in 2007.
[http://qalculate.sourceforge.net/](http://qalculate.sourceforge.net/)

There are a few emulator programs for HP calculators. Some require you to download the system ROM from HP, others do not.
[http://www.hpcalc.org/hp48/pc/emulators/](http://www.hpcalc.org/hp48/pc/emulators/)
[http://www.linuxfocus.org/common/src/article319/hp67.html](http://www.linuxfocus.org/common/src/article319/hp67.html)

Finally, I did find vc. It's a perl script that is essentially a programmable vector calculator and it does RPN.
[http://vc-calc.sourceforge.net/](http://vc-calc.sourceforge.net/)

Being perl, the last one should be very extensible/programmable, but it's CLI only. You didn't mention whether or not you wanted something with a GUI, but it looks like Qalculate was the best programmable GUI calculator.

Finally, there is a module for Python that lets it do RPN style calculations. Again, it's CLI only, but it's running in python so it's as programmable as you want it to be.
[http://calcrpnpy.sourceforge.net/](http://calcrpnpy.sourceforge.net/)

Qalculate does support RPN but i see nothing about being programmable, are you sure it is? How do i go about figuring out how (i see no man page).

I'd like to avoid emulators, since i dont want to bother with copyrighted ROMS. vc and calcrpnpy seem promising, although im not very familiar with either Perl or Python. Thats fine though, the information on those languages is extensive so it looks like i have alot of reading to do. I downloaded the vc.pl file, and im pretty sure i have Perl already, what do i do with the pl file to "install" vc exactly? Similar with the rpncalc-2.7 file, i have Python already, how do i install it?

---

### Post by gunksta on 2009-11-11
I thought Qalculate was programmable, but that was years ago. I honestly don't remember for sure. Since it's primarily a GUI app, I doubt it has a manpage. But, there should be some help installed with it (if you have installed it).

To "install" the perl script, vc, you just need to download the file form the website and set it so that it is executable. Just right click on the file and go to properties or whatever Nautilus shows you. (I run Kubuntu and I am assuming that you are on Ubuntu and I don't know the words nautilus uses.) Or you could just use chmod. Once you've done that, open a terminal and go to where you downloaded the file and execute this:

```
./vc.pl
```

It should work. It's an ugly tool, but I suspect it's rather powerful. My perlfu is weak, so I didn't really do much beyond check that it works.

Installation of the python tool is a little more involved, but not much. Download the package and unzip it. You will need to use a terminal and browse over to this folder. Inside the folder you will need to:

```
python clnum_setup.py install --prefix=/usr/local
```

Better instructions can be found in the folder. I put the folder into ~/bin and I found the instructions at:

~/bin/rpncalc-2.7/

There are several HTML files. clnumManual.html will be useful to you. I did not actually install it but it doesn't look too complicated. The rest of the files there should show you how to get it up and running and what not.

---

### Post by magicmax0 on 2009-11-11
After i set the vc.pl file to be executable, and run the "./vc.pl" command in its directory, the terminal becomes non responsive (strange). Running it as sudo doesn't improve things. Im on Ubuntu karmic amd64.

After successfully running the install command for the python module (no errors), i tried to test it, as shown in the clnumManual.html file, with "test_clnum.py" and it returned "command not found", same thing running as sudo. I did install all listed dependencies before installing the module. I also tried installing the module again.

Maybe these don't like ubuntu karmic amd64? My filesystem is ext4 (karmic default).

---

### Post by hubie on 2009-11-16
I highly recommend [Free42]("http://thomasokken.com/free42/"), which is an HP 42S calculator simulator.  It is free and multi-OS (I run it on my 64-bit Ubuntu as well as in WinXP).  It was written from scratch, so it doesn't require you to provide a ROM.  I haven't tried the programming functionality of it, but it claims to be an accurate simulation of the real thing and the developer suggests you use the HP 42S owner's manual for instruction.

It can use a variety of skins, but the one I prefer is the one that looks just like the real 42S (my preference, largely because I own a 42S).  Interestingly, the realistic skin is not the one presented to you when you install.

---

### Post by magicmax0 on 2009-11-16
This works great, thanks. I ended up finding a good manual written by Jose Lauro Strapasson. For being more than 20 years old, this calculator is surprisingly capable. I've got alot of reading to do but i think this will work for me.

---

### Post by hubie on 2009-11-16
> **magicmax0 said:**
> For being more than 20 years old, this calculator is surprisingly capable.

Boy, way to make a guy feel old!  :)

---

### Post by magicmax0 on 2009-11-16
Heh, well technically its 21 years old, but it was made right up until 1995. So you can say its 9 years old, if that makes you feel better :P.

---

