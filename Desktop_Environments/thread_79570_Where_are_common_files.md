---
title: "Where are common files?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by tmattoneill on 2005-10-20
I just tried to make ndiswrapper and my ubuntu doesn't understand the command "make" it also doesn't have gcc or cc or a lot of other totally standard linux/unix commands.  How does one perform a simple "make" in this OS? How does one compile C++ code?

I'm very very confused.  I looked all over the install disk and saw nothing.  How can it be missing make and gcc?


Please someone HELP

---

### Post by GrumpyBob on 2005-10-20
[QUOTE=tmattoneill]I just tried to make ndiswrapper and my ubuntu doesn't understand the command "make" it also doesn't have gcc or cc or a lot of other totally standard linux/unix commands.  How does one perform a simple "make" in this OS? How does one compile C++ code?

I'm very very confused.  I looked all over the install disk and saw nothing.  How can it be missing make and gcc?


Please someone HELP[/QUOTE]

I think you need to install a package called build-essential.  
A quick search of the forum should reveal more information.

Robert

---

### Post by tmattoneill on 2005-10-21
So I was trying to add on these essential packages and I was prompted for the Hoary CD.  I've got the full Breezy one, do I now need to download the Hoary dsitrib as well just to get minimal functioanality?

M

---

### Post by GrumpyBob on 2005-10-21
I installed build-essential myself last week.  I cannot remember if I was prompted for a CD (I don't think so, though I have been for other installs) - certainly not a Hoary CD.    Did you upgrade or do a fresh install of Breezy?

Robert

---

### Post by Stormy Eyes on 2005-10-21
[QUOTE=tmattoneill]So I was trying to add on these essential packages and I was prompted for the Hoary CD.  I've got the full Breezy one, do I now need to download the Hoary dsitrib as well just to get minimal functioanality?[/QUOTE]

No. You need to open a terminal and enter the following command:
```
sudo gedit /etc/apt/sources.list
```
Remove any references to CDROM. Save the file, close the editor, and run
```
sudo apt-get update
```
and then
```
sudo apt-get install build-essential
```

---

### Post by tmattoneill on 2005-10-21
That did the trick...not sure why they didnt get installed when I installed Breezy (full, not updated).  But we're looking good now!

Thanks,
Matt

---

