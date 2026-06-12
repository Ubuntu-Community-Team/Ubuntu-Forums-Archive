---
title: "Is there a RAR gui for KDE?"
date: 2005-03-21
forum: Desktop Environments
---

### Post by dermotti on 2005-03-21
I work with alot of rar files, and doing them all from command line sucks. Anyone know of a GUI for rar under KDE?

---

### Post by TravisNewman on 2005-03-21
Ark works with rar doesn't it? I know file-roller does in Gnome.

---

### Post by bored2k on 2005-03-21
[QUOTE=panickedthumb]Ark works with rar doesn't it? I know file-roller does in Gnome.[/QUOTE]
 After installing rar, unrar/unrar-nonfree I was under the impression Ark would work on them just like F-roller. They did on Xandros 2/3 at least.

---

### Post by dermotti on 2005-03-21
I tried ark , it says "an error occured while trying to open the archive". But if i run unrar from command line it decompresses fine......hmmmmm. It happens on all the rar files i try to open

---

### Post by bored2k on 2005-03-21
[QUOTE=dermotti]I tried ark , it says "an error occured while trying to open the archive". But if i run unrar from command line it decompresses fine......hmmmmm. It happens on all the rar files i try to open[/QUOTE]
 You could use winrar through wine - it's still better than any other application on any Operating System :roll: .

---

### Post by dermotti on 2005-03-21
Man...i wish there was a winrar for linux with the gui...i hate thowing in the towel and using wine

---

### Post by rwabel on 2005-03-22
file roller works fine with rar!

---

### Post by dermotti on 2005-03-22
It says i have file roller installed, yet i do not know how to get it started from command line and i cant find an icon

---

### Post by rwabel on 2005-03-23
in console just type file-roller and it starts-up
but you will find it also under Applications->Accessoires->Archive Manager

---

### Post by fdoving on 2005-03-27
[QUOTE=dermotti]I tried ark , it says "an error occured while trying to open the archive". But if i run unrar from command line it decompresses fine......hmmmmm. It happens on all the rar files i try to open[/QUOTE]
 try to make a symlink named rar pointing to your unrar file. maybe ark needs the binary to be named  rar, not unrar..

---

### Post by Randabis on 2005-03-27
Ark works just fine for rar files on this end. Don't know why you're having problems.

---

### Post by dermotti on 2005-03-27
Only thing i can think of is there are differnt kinds of rar files, maybe ones made under windows wont work, etc etc

---

### Post by nahumet on 2005-04-23
[QUOTE=fdoving]try to make a symlink named rar pointing to your unrar file. maybe ark needs the binary to be named  rar, not unrar..[/QUOTE]
 This error you have when you are trying to open a .RAR file is very common in hoary. You need to have installed the package RAR. Installing only unrar or unrar-nonfree it's not enough. So you have to do

$ sudo apt-get install rar

and I hope this will fix the problem.

---

### Post by Punktyras on 2005-04-24
[QUOTE=dermotti]I work with alot of rar files, and doing them all from command line sucks. Anyone know of a GUI for rar under KDE?[/QUOTE]
 I use Mandrake distro and Ark. I just put unrar file in path and that's it.
You can find path folders by typing in command line this:
echo $PATH
and Linux will name you all folders separated by ":"
Usually it is bin folders. The simplest way is to put unrar in bin folder /home/<username>/bin

---

### Post by raid517 on 2005-04-24
If rar's won't open in ark, then there is something wrong with your ark install, or your rar install or both. Here's a tip though. look for a debian repository distributing the "non-free" version of rar. It works so much better than the free open source version.

You should pretty much be able to open any type of file with ark. If it doesn't work, as you say, don't throw in the towel. Try to find out what's wrong.

GJ

---

### Post by Urusai on 2005-04-25
Remember, wine is "free" software, so using stuff under it is guilt-free.  I guess.

---

