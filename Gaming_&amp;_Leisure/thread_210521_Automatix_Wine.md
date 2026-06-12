---
title: "Automatix Wine"
date: 2006-07-07
forum: Gaming &amp; Leisure
---

### Post by Linkhiei on 2006-07-07
Yo. I'm trying to patch Wine so that I can fix the targeting problem with WoW. I've been told to enter the command:

patch -p0 </path/to/wine-wow-fixes-0.9.16.patch

But, I just used Automatix to install Wine, so I have no clue where the "path to wine wow fixes" would be. Could anyone tell me?

Also, it says that after I enter that command i should "compile wine as you usually do." What would that involve? 

heres a link to the article(its in the "patching wine" section:
[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft]("http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft")
Thanks for anyones help >.<

---

### Post by arnieboy on 2006-07-07
Automatix adds the wine repository to apt and installs wine (you can find the wine package in synaptic). find the package --> right click--> properties to find out where all the files are.

But before you do that, you should know this:
Packages installed by apt/synpatic/automatix are all precompiled binary packages. There is no use patching anything in that. If you want to patch a source file, you need to first remove the existing version of wine:
```
sudo apt-get remove wine
```
and install checkinstall (this allows you to create your own deb after compiling from source)```

sudo apt-get install checkinstall
```
download the [latest wine source tar file]("http://prdownloads.sourceforge.net/wine/wine-0.9.16.tar.bz2?download"), untar it, execute the patch command and then do the following one by one in the directory where you untarred all the source files:
```
./compile
make
sudo checkinstall
```
This will install wine with the correct patch as a deb which you can remove from synpatic later.
After you have done all this "sudo rm" the source folder from your home folder or wherever its located.

---

### Post by vem0m on 2006-07-07
first off wow is not runnable in Wine although it is in Cedega as i run it myself there Wine is slow and is buggy making it unplayable...

---

### Post by Linkhiei on 2006-07-07
Actually Venom, after following arnieboy's suggestion (THANKS!) with a little modifying, i got wow to work on Wine totally glitch free :) even my mods work
heres a screenshot i took:
[IMG]http://img2.freeimagehosting.net/uploads/3dd2cab4dd.png[/IMG]

---

### Post by vem0m on 2006-07-07
u are in one lucky boat then as it still don't work for 90% of ppl

---

### Post by Jengu on 2006-07-07
> **vem0m said:**
> u are in one lucky boat then as it still don't work for 90% of ppl

No, he's the norm. WoW has been working under wine (w/ minor patches) for almost a year. There's a thread in the gaming forum on gentoo.org that is usually kept up to date on how to get the latest WoW version to run under the latest version of wine.

The reason the patch needed isn't in normal wine is because as far as the wine developers can tell it should only 'fix' the crash if there's a bug in WoW. It doesn't crash under Windows with the bug because Windows has a slightly different memory layout though, by pure coincidence. Someday a better fix maybe found though.

---

### Post by Wallakoala on 2006-07-07
Personally, WoW runs better on linux than it does on windows for me.

---

### Post by vem0m on 2006-07-07
hmmmmmm well i run it on cedega and it runs the same there as it did on windows although starcraft ran like crap thu cedega so i am running it thu straight wine :)

---

### Post by Linkhiei on 2006-07-08
Yea for me it runs great on linux, 20-30fps atleast, but just a little better on windows: 30-40fps atleast

---

