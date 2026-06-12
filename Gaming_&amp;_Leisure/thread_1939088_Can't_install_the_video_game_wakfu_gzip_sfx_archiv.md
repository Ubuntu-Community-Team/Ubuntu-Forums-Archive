---
title: "Can't install the video game wakfu: gzip: sfx_archive.tar.gz: not in gzip format"
date: 2012-03-10
forum: Gaming &amp; Leisure
---

### Post by dadoprso on 2012-03-10
> gzip: sfx_archive.tar.gz: not in gzip format

I am sorry, but the installer file seems to be corrupted.
If you downloaded that file please try it again. If you
transfer that file with ftp please make sure that you are
using binary mode.


I'm trying to install the video game wakfu.

I get the above error after running 
@AO532h:~/Downloads$ sudo ./wakfu-installer-linux-na.sh 

Any ideas?

---

### Post by raja.genupula on 2012-03-10
hi my friend , i have downloaded for knowing the issue but for me its good 
 here the way i did that 
```
raja@raja-Ubuntu:~/Downloads$ chmod +x Wakfu_unix.sh 
raja@raja-Ubuntu:~/Downloads$ ./Wakfu_unix.sh 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
raja@raja-Ubuntu:~/Downloads$ 
```

try in that way my friend 

one more thing i downloaded from [http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh](http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh)

if you got anything while doing installing , let us know . 

all the best

---

### Post by dadoprso on 2012-03-11
> **raja.genupula said:**
> hi my friend , i have downloaded for knowing the issue but for me its good 
 here the way i did that 
```
raja@raja-Ubuntu:~/Downloads$ chmod +x Wakfu_unix.sh 
raja@raja-Ubuntu:~/Downloads$ ./Wakfu_unix.sh 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
raja@raja-Ubuntu:~/Downloads$ 
```try in that way my friend 

one more thing i downloaded from [http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh](http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh)

if you got anything while doing installing , let us know . 

all the best

where is that link from?

---

### Post by dadoprso on 2012-03-11
> **raja.genupula said:**
> hi my friend , i have downloaded for knowing the issue but for me its good 
 here the way i did that 
```
raja@raja-Ubuntu:~/Downloads$ chmod +x Wakfu_unix.sh 
raja@raja-Ubuntu:~/Downloads$ ./Wakfu_unix.sh 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
raja@raja-Ubuntu:~/Downloads$ 
```try in that way my friend 

one more thing i downloaded from [http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh](http://dl.ak.ankama.com/games/wakfu/client/linux/Wakfu_unix.sh)

if you got anything while doing installing , let us know . 

all the best

I got:

eric@eric-MS-7596:~/Downloads$ chmod +x Wakfu_unix.sh 
eric@eric-MS-7596:~/Downloads$ ./Wakfu_unix.sh 
Unpacking JRE ...
Preparing JRE ...
./Wakfu_unix.sh: 197: ./Wakfu_unix.sh: bin/unpack200: not found
Error unpacking jar files. The architecture or bitness (32/64)
of the bundled JVM might not match your machine.

---

### Post by VH-BIL on 2012-03-11
What sort of computer are you running linux on?

---

### Post by dadoprso on 2012-03-12
> **VH-BIL said:**
> What sort of computer are you running linux on?

It is custom built, but I think you want the following:
64 bit ubuntu (upgraded to 12.04 beta)
120GB SSD
Quad Core AMD CPU

---

### Post by nothingspecial on 2012-03-12
*Thread moved to **Gaming & Leisure**.*

---

### Post by madjr on 2012-03-12
well mine works.

ubuntu 11.10 (32bit)
java installed (restricted extras in the repos / software center).

-right click properties and set permission to allow executing.

-then double click the file and choose run or run on terminal (if you want to see the process in more detail).

---

### Post by dadoprso on 2012-03-12
> **madjr said:**
> well mine works.

ubuntu 11.10 (32bit)
java installed (restricted extras).

-right click properties and set permission to allow executing.

-then double click the file and choose run on terminal.

I have not installed the java restricted extras. I will try when I get home. Thanks!

---

### Post by madjr on 2012-03-12
> **dadoprso said:**
> I have not installed the java restricted extras. I will try when I get home. Thanks!

may also want to check this thread:

[http://ubuntuforums.org/showthread.php?p=11759293](http://ubuntuforums.org/showthread.php?p=11759293)

---

