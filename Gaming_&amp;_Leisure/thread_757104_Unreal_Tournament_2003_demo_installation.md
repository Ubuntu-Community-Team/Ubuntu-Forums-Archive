---
title: "Unreal Tournament 2003 demo installation"
date: 2008-04-16
forum: Gaming &amp; Leisure
---

### Post by itix on 2008-04-16
This is waht I get:

```
itix@itix-laptop:~/Downloads$ chmod u+x ut2003demo-lnx-2206.sh.binitix@itix-laptop:~/Downloads$ ./ut2003demo-lnx-2206.sh.bin
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 1386214276 is different from 764522044

```

My computer is an Acer Aspire 3610:
Intel Pentium Celeron 1.5 ghz
1 gb DDR2
Intel 910/915 chipset graphics
Lotsa other stuff.

---

### Post by schmatzler on 2008-04-28
Open the file with an Hex-Editor (for example GHex) and replace every "tail +266" with "tail -n +266". :)

---

### Post by drink on 2008-06-26
I have a better solution for this install
Just create your own 'tail' script
it looks like this:

#!/bin/sh
/usr/bin/tail -n $*

Put it in your path before /usr/bin someplace (I used $HOME/bin)
Make it executable
Delete it after the install.

Problem solved!

P.S. run the installer with "bash ./linux-installer.sh"

---

### Post by Saatii on 2008-08-06
To make it ultra clear:

Create the script and name it whatever you want. I used "ut_script".
Create a folder in your home directory called bin - /home/<username>/bin - and put your script in it.
Open a console and enter: PATH=$PATH:/home/<username>/bin/ut_script
Run the ut_installer.sh with bash,so that's not './' or 'sh', because those are dash-thingies.

EDIT;
whoopsiedaisy, Drink allready said the bash thingy

greets,
prakka

---

### Post by Brebs on 2008-08-07
There is an [easier fix](http://icculus.org/lgfaq/):
```
export _POSIX2_VERSION=199209
```

---

