---
title: "Places -&gt; Search for Files"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Tomlin on 2006-07-18
OK, what am I missing here?

Places -> Search for Files

I type in a filename I KNOW exists in 3 places and use 'File System' in the 'Look in folder:' and it finds NOTHING.

I change the 'Look in folder:' to 'lib' and it finds the 3 files in:

lib/modules
lib/modules/2.6.15-26-386/ivtv
lib/modules/2.6.15-26-386

Why isn't it finding the files in the 'File System'? 'lib' is under the 'File System'. I liked 5.10's search function better. It allowed you to type in a directory like '/' or '/home'.

Tomlin

---

### Post by not_yet on 2006-07-18
how about trying the terminal :) 

open the terminal and enter the following

sudo updatedb

press enter and give it your password

its takes a bit of time the first time, but after that its fast and easy

to find the file "myfile", enter the following

locate myfile

cheers

---

### Post by Tomlin on 2006-07-19
Thanks for the info.

I know 'locate' works. I'm trying to set up a machine to replace my brother's windoze box. If I'm to convince him that Linux is a viable alternative, he's got to be able to do simple things without resorting to the command line. He's not computer 'illiterate', but he says that's like stepping back to DOS.

I'm just wondering if it's a bug or something.

Tomlin

---

### Post by Thund3rstruck on 2006-07-19
Install Beagle... it stomps the sh@t out of everything else out there on any OS (IMHO)

```

$ sudo aptitude install beagle deskbar-applet
$ beagled

```

---

### Post by chadk on 2006-07-19
Yep, Thund3rstruck has it. Beagle is what my wife uses, I use slocate (locate)

---

