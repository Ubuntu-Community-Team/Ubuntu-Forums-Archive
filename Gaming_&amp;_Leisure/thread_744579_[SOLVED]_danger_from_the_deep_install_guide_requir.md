---
title: "[SOLVED] danger from the deep install guide required"
date: 2008-04-03
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-04-03
Hi,
Could someone please post a step by step install guide for Danger from the Deep?
This guide would include everything from install package (.deb) links and all the command lines required. 

I installed  Danger from the Deep but I can't start it. I got it here: [http://downloads.sourceforge.net/dangerdeep/dangerdeep_0.3.0.1_i386.deb]("http://downloads.sourceforge.net/dangerdeep/dangerdeep_0.3.0.1_i386.deb")

I keep getting this:

```
Caught exception: DftD error: Can't open directory /usr/share/games/dangerdeep/objects/airplanes/
Stack trace: (5 frames)
0x8070202 in dangerdeep at ??:0
0x806d431 in dangerdeep at ??:0
0x806d4f1 in dangerdeep at ??:0
0xb7a5b050 in __libc_start_main at ??:0
0x804e6a1 in dangerdeep at ??:0
```

I have come across other threads with same problem but their solution was unclear.

Thank you.

---

### Post by spyros71 on 2008-05-09
EXactly the same thing here!! Can somone help please?

---

### Post by DoktorSeven on 2008-05-09
There's a huge file called "dangerdeep-data-0.3.0.zip" that suggests you might need to download and extract that in the location specified by the error (/usr/share/games/dangerdeep/); I'd think those are the program's data files, independent of the binary package.

Edit: Confirmed.  Download and install the .deb file as you have then download and extract the data zip file noted above to a temporary directory.  This will create a directory called "data".  From a terminal, cd into that data directory (you'll see directories like "maps" "missions", etc if you do ls), and copy that over to /usr/share/games/dangerdeep:

**sudo cp -R * /usr/share/games/dangerdeep/**

Either the game itself was buggy or I had no idea what to do, though.  Good luck.

(changed mv to cp, less destructive if you make a mistake :) )

---

### Post by Rytron on 2008-06-09
I tried danger from the deep in Windows XP, it seems very buggy and I presume the Linux version of danger from the deep would be the same. I will stay with the excellent Silent Hunter III running in Windows XP.

---

### Post by Legendário on 2010-01-08
I installed the it by the linux installer <[http://downloads.sourceforge.net/dangerdeep/dangerdeep-0.3.0-linux-installer.bin]("http://downloads.sourceforge.net/dangerdeep/dangerdeep-0.3.0-linux-installer.bin")> which is said to have the data included in it.

> GNU/Linux (x86 & x86-64):- dangerdeep-0.3.0-linux-installer.bin
The above installers include both the program and the data, these are licensed under the GPL and Creative Commons respectively (see LICENSE for full details).

I can run the game but the missions seem to be empty. Any help here?

---

### Post by frogotronic on 2010-06-20
Hello,

  Try the SVN deb files here: [http://dangerdeep.sourceforge.net/2010/01/23/latest-ubuntu-builds/](http://dangerdeep.sourceforge.net/2010/01/23/latest-ubuntu-builds/) 

and add this PPA: ppa:aegirxx-googlemail/dftd-latest

- CH

---

### Post by rosswmcgee on 2010-12-25
I have downloaded the <http://downloads.sourceforge.net/dan...-installer.bin> to my desktop but do not know how to install it or run it. I have always run SS2 in dos box

but would like to check this out,

---

### Post by Rytron on 2010-12-27
> **rosswmcgee said:**
> I have downloaded the <http://downloads.sourceforge.net/dan...-installer.bin> to my desktop but do not know how to install it or run it. I have always run SS2 in dos box

but would like to check this out,

```
chmod a+x name_of_file.bin
```

```
./name_of_file.bin
```

---

### Post by mips on 2010-12-27
> **Rytron said:**
> 
```
./name_of_file.bin
```

Installer requires root privileges so it would be
```
sudo ./name_of_file.bin
```

---

### Post by mips on 2010-12-27
Hmm, so how do I launch the game seing it does not appear in the menu?

---

### Post by Rytron on 2010-12-28
> **mips said:**
> Hmm, so how do I launch the game seing it does not appear in the menu?

Open a terminal. Type in danger and hit tab key. Else try Danger and hit tab key to show up all programs starting with word danger/Danger.

---

### Post by rosswmcgee on 2011-01-01
This worked for me:
[http://www.unixmen.com/gaming-on-linux/1151-danger-from-the-deep-an-awesome-submarine-sumilator](http://www.unixmen.com/gaming-on-linux/1151-danger-from-the-deep-an-awesome-submarine-sumilator)

Open terminal and enter the following commands:
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
 sudo apt-get update && sudo apt-get install dangerdeep-latest

To run the game type the command :
$ dangerdeep

---

### Post by Rytron on 2011-01-02
Cheers rosswmcgee.

---

### Post by realzippy on 2011-01-02
...unfortunately game crashes after minutes.?.
Anyone able to play without crash?

---

### Post by mips on 2011-06-12
> **rosswmcgee said:**
> This worked for me:
[http://www.unixmen.com/gaming-on-linux/1151-danger-from-the-deep-an-awesome-submarine-sumilator](http://www.unixmen.com/gaming-on-linux/1151-danger-from-the-deep-an-awesome-submarine-sumilator)

Open terminal and enter the following commands:
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
 sudo apt-get update && sudo apt-get install dangerdeep-latest

To run the game type the command :
$ dangerdeep

which gives me 

```
xxxx@obelix:~$ dangerdeep
Stack trace: (5 frames)
0x427639 in  at ??:0
0x41eb87 in  at ??:0
0x41ec5c in  at ??:0
0x7f4b30b32d8e in __libc_start_main at ??:0
0x40a119 in  at ??:0
```


Any ideas on how to get this running?

Ubuntu 10.10, AMD64, nVidia 9600GT

---

