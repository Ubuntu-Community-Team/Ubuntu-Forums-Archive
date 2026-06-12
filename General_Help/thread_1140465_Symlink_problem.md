---
title: "Symlink problem"
date: 2009-04-27
forum: General Help
---

### Post by mrdarrenm on 2009-04-27
Hi. Kinda new so bear with me. Thanks in advance for any help.

So I was installing Songbird, just for learning how stuff works I'm attempting to have it in the applications menu as well as having a symlink to it so that I can just run it from anywhere including the 'run application' prompt. So I have it working in the applications menu by pointing to the full path of the app, but cannot get the symlink working.
I have Songbird extracted in /opt/ folder so /opt/Songbird/songbird is the actual application I want the symlink to point to. So I created a symlink in /usr/bin so an 'ls -la /usr/bin/S*' gives me:
lrwxrwxrwx 1 root root 22 2009-04-27 22:30 Songbird -> /opt/Songbird/songbird
... this is looking good to me (from the eyes of a beginner!) but then typing Songbird gives me: 'Songbird: Cannot execute .'
The command I used to create the symlink was:
sudo ln -s /opt/Songbird/songbird Songbird
This is straight from man pages, tutorials, etc, and I can't find anything but this as a command to create a symlink!

Cheers,
Darren

---

### Post by sefs on 2009-04-27
The command to start songbird is "songbird" with a lowercase "s" and not an uppercase "S".

Here are your two options to try



Assuming songbird is installed in /opt/Songbird then the executable script to start songbird is at /opt/Songbird/songbird

option 1
-------------
open a terminal and execute the command

```

sudo ln -s /opt/Songbird/songbird /usr/bin/songbird

```

option 2
--------

open a terminal

change to the /usr/bin dir
```
cd /usr/bin
```

execute the command below
```
sudo ln -s /opt/Songbird/songbird songbird
```

---

### Post by mrdarrenm on 2009-04-28
Thanks sefs, unfortunately though ...

These are the commands I did try yesterday, I had tried both of your options of being in the /usr/bin directory or specifying this directory while positioned in another, tried again there both ways in case I was missing something and it's nothing to do with that.

Yes the command to start Songbird starts with a lower case 's', i did specify that in creation of the symlink, but then put a capital S on the actual symlink that I created. AFAIK this should not make a difference as it is pointing to the lower case s version of the actual app which it is calling so when calling it from somwhere else by symlink I would just call 'Songbird'. I just tried creating a symlink called 'songbird' pointing to /opt/Songbird/songbird and as I thought, no difference :/

---

### Post by sefs on 2009-04-28
can you show the results of 

```
ls -la /opt/Songbird/song*
```

```
ls -la /usr/bin/song*
```

also when you type songbird at the terminal what error msg does it give.

I'm assuming you are using all lowercase "s".

---

### Post by sefs on 2009-04-28
Ah yes I see what you mean...there start up script is someone different to firefox and thunderbird.

We need a bash script specialist to look at /opt/Songbird/songbird and make it work correctly.

---

### Post by mrdarrenm on 2009-04-29
Hi again Sefs ... following are the outputs you were after ...

me@blah:~$ ls -la /opt/Songbird/song*
-rwx--x--x 1 bill bill  11890 2009-03-31 22:23 /opt/Songbird/songbird
-rwx------ 1 bill bill  27360 2009-03-31 22:23 /opt/Songbird/songbird-bin
-rw------- 1 bill bill 112568 2009-03-31 22:23 /opt/Songbird/songbird.png
me@blah:~$ ls -la /usr/bin/song*
lrwxrwxrwx 1 root root 22 2009-04-28 14:36 /usr/bin/songbird -> /opt/Songbird/songbird

ok ... hadn't thought to look if 'songbird' was a shell script ... turns out it is getting called as the output is usually "cannot execute ." when I call the link. So the problem isn't with my symlink. I had thought that it surely was since I could call the script directly without a param or anything from where I entered it in the applications menu.

So ... looking into the script we have:
if [ ! -x "$prog" ]
    then
        moz_bail "Cannot execute $prog."
    fi

... obviously $prog is not being populated with anything so ...
prog variable was previously populated by $MOZ_PROGRAM
We are told that the 'if' is there to check if the application is executable & since it's bombing out there ... it is not.
so ... still now faced with the question ... why isn't $MOZ_PROGRAM getting populated with anything?? Seems to be something to do with how it is launched, the 'launcher' from the menu seems to load it a different way or something :/ 

Maybe I need a new thread since I may not get anyone looking at this who knows about that stuff?? This is my first thread so assuming that would be how it works!!

---

### Post by mrdarrenm on 2009-04-29
Ok I fixed it ... just to let you know and to show my appreciation for helping out  (sefs) and pointing me in the right direction.

A bit of debugging of the script and I solved the problem ... was in the variables within the script ... if I run 'songbird' script it from a symlink it takes the location of the symlink as the current directory in the file ... then it tries to see if the <current dir>/<filename>-bin exists and is executable and if so, runs this. Obviously not gonna happen. So I have hard coded the current dir rather than automagically finding it and this is working well.

Suppose I learned a little from the frustration so its all good.

Cheers,
Darren

---

### Post by jfanaian on 2009-05-12
What I did was just create a script in my bin directory that runs Songbird, here it is:

```

#!/bin/sh
cd /opt/Songbird
./songbird

```

---

