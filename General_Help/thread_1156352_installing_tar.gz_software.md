---
title: "installing tar.gz software"
date: 2009-05-11
forum: General Help
---

### Post by MadMax2 on 2009-05-11
· Runs on Linux, Un*x, Windows (DOS); allows dual-boot systems to share the same data; and has no dependencies on other programs
[http://linux.softpedia.com/get/Science-and-Engineering/Medical-Science-Apps-/nut-8544.shtml](http://linux.softpedia.com/get/Science-and-Engineering/Medical-Science-Apps-/nut-8544.shtml)

 [ATTACH]113370[/ATTACH]
From Readme
Prepare the raw data as follows:

1)  "make" the utilities dbjw and dbabbrev in this directory.

2)  Make symbolic links to USDA data files FOOD_DESC.txt, NUT_DATA.txt,
    NUTR_DEF.txt, FD_GROUP.txt, and WEIGHT.txt in the main nut directory.

3)  Issue command "preprocess/dbfoodname 1>/dev/null" in the main nut
    directory, and correct any long lines with additional editing of
    preprocess/foodedits and/or changes to abbreviations in "abbrev.h",
    and if the latter, "touch dbabbrev.c" and "make" again.

4)  Issue command "preprocess/dbjoin" in the main nut directory.

 :confused:

---

### Post by zolistir87 on 2009-05-11
Seems that you need to do the following:

> 1)  "make" the utilities dbjw and dbabbrev in this directory.
1) simply type make in terminal while being in the main nut directory

> 2)  Make symbolic links to USDA data files FOOD_DESC.txt, NUT_DATA.txt,
    NUTR_DEF.txt, FD_GROUP.txt, and WEIGHT.txt in the main nut directory.2) ln -s FOOD_DESC.txt (repeat command for each file specified)

> 3)  Issue command "preprocess/dbfoodname 1>/dev/null" in the main nut
    directory, and correct any long lines with additional editing of
    preprocess/foodedits and/or changes to abbreviations in "abbrev.h",
    and if the latter, "touch dbabbrev.c" and "make" again.3) Try doing the command preprocess/dbfoodname 1>/dev/null and see what happens

> 4)  Issue command "preprocess/dbjoin" in the main nut directory.4) Pretty self-explanatory.

---

### Post by mikewhatever on 2009-05-11
Not sure if it matters, but the software is available through the repositories. Search for nut-nutrition in Synaptic.

---

### Post by zolistir87 on 2009-05-11
> **mikewhatever said:**
> Not sure if it matters, but the software is available through the repositories. Search for nut-nutrition in Synaptic.

Just checked. Forget what I said in the other post. Just fire up Synaptic and install it from there.

---

### Post by MadMax2 on 2009-05-11
I checked in synaptic and it is an older version . I followed the steps and got to here:

john@LoungePC:~/nut-14.4$ preprocess/dbfoodname 1>/dev/null
cat: FOOD_DES.txt: No such file or directory
john@LoungePC:~/nut-14.4$ preprocess/dbjoin
cat: WEIGHT.txt: Too many levels of symbolic links
join: FOOD_DES.txt: No such file or directory
preprocess/dbjoinweight: 5: preprocess/dbjw: not found
preprocess/dbjoinweight: 5: preprocess/dbjw: not found
preprocess/dbjoinweight: 5: preprocess/dbjw: not found
sort: open failed: +0: No such file or directory
cat: FOOD_DES.txt: No such file or directory

At some stage the USDA (US Dept Agriculture food) database has to be downloaded.

---

### Post by albinootje on 2009-05-11
> **MadMax2 said:**
> 
[http://linux.softpedia.com/get/Science-and-Engineering/Medical-Science-Apps-/nut-8544.shtml](http://linux.softpedia.com/get/Science-and-Engineering/Medical-Science-Apps-/nut-8544.shtml)


Do you really need the latest version ?
Ubuntu Jaunty has version 14.1 as a package :
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nut-nutrition](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nut-nutrition)
See here for the changes between the versions :
[http://freshmeat.net/projects/nut](http://freshmeat.net/projects/nut)

---

### Post by MadMax2 on 2009-05-11
The version in  is 13.9-1 in Intrepid. 

It doesnt show in add/remove programs. How do i run it in Terminal?
 and/or how do i get synaptic package manager to update to the latest version?

---

### Post by albinootje on 2009-05-11
> **MadMax2 said:**
> The version in  is 13.9-1 in Intrepid. 

It doesnt show in add/remove programs. How do i run it in Terminal?
 and/or how do i get synaptic package manager to update to the latest version?

```

sudo apt-get install nut-nutrition

```
I'll see whether I can set up an Intrepid installation, to perform a backport from the software from Jaunty. No promises though. ;-)

---

### Post by MadMax2 on 2009-05-11
```
sudo apt-get install nut-nutrition
```

Thanks then:
```
nut-nutrition
```

It will take a bit of getting used to as it runs in terminal.

How long would it take to give it a GUI? :o

Here's why I'm interested in nutrition software ( a general goal to aim at):

[http://en.wikipedia.org/wiki/CRON-diet](http://en.wikipedia.org/wiki/CRON-diet)

---

### Post by albinootje on 2009-05-11
> **MadMax2 said:**
> 
It will take a bit of getting used to as it runs in terminal.

I already thought so when I saw the screenshot on the freshmeat.net project page.
> 
How long would it take to give it a GUI? :o

Since the source code is open, one programmer for a GUI might be enough ;-)
> 
Here's why I'm interested in nutrition software ( a general goal to aim at):

[http://en.wikipedia.org/wiki/CRON-diet](http://en.wikipedia.org/wiki/CRON-diet)

Young of heart is a joy forever :)

I just finished backporting 14.1 on Intrepid, it goes as following :
1) add the "deb-src" lines for Jaunty in /etc/apt/sources.list
2) run "sudo apt-get update"
3) run "sudo apt-get build-dep nut-nutrition"
4) run "sudo apt-get -b source nut-nutrition" and wait till the compilation finishes.
5) run "sudo dpkg -i nut-nutrition*deb"
That's all.

---

### Post by JK3mp on 2009-05-11
Yeah its definately already in repositories, and i don't see any ups of it.

---

### Post by MadMax2 on 2009-05-11
to write script for linux do you need to learn C or C++?

---

### Post by sgosnell on 2009-05-12
No, scripts don't use a programming language, they're not compiled.  They're the equivalent of DOS batch files.

---

### Post by MadMax2 on 2009-05-12
I must have meant code.
To write code (a program) do you need to learn C or C++. I saw C++ books at the bookstore.

---

### Post by albinootje on 2009-05-12
> **MadMax2 said:**
> to write script for linux do you need to learn C or C++?

No, C or C++ are "real" programming languages, and require compilation of the source code.

There's bash scripts in Linux, but there are also scripting languages like Tk/Tcl and python available.

---

### Post by sgosnell on 2009-05-12
You can program in any of several languages, including C/C++, Pascal, python, and others.  C++ is certainly one of the more commonly used languages, but not necessarily the easiest.

---

### Post by MadMax2 on 2009-05-12
I see Nut is written in C. If I learned "C" I could perhaps work on improving Nut to give it more features such as GUI. Does a compiler (software program?) work automatically (assuming a program is relatively bug free?
I'm just curious.

---

### Post by sgosnell on 2009-05-12
Automatically?  Not sure what you mean.  You have to make and compile the source code, and it's not quite automatic, but it's not that hard.  Making a gui for a program is not a trivial programming task, especially if you've never done any programming.

---

### Post by MadMax2 on 2009-05-12
I think I understand : you write the source could and then run build essential (or something) and load it using commands. I thought (perhaps) there was a fancy compiler program (wizard) that led you through it.

---

### Post by albinootje on 2009-05-13
> **MadMax2 said:**
> I think I understand : you write the source could and then run build essential (or something) and load it using commands. I thought (perhaps) there was a fancy compiler program (wizard) that led you through it.

The package "build-essential" is a meta-package which install the GNU C compiler amongst others.
Then when the "make" command is started, the compiler starts compiling, to transform the human readable code into computer readable code.

---

