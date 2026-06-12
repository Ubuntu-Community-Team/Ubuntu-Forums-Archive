---
title: "[SOLVED] zsnes problem in 7.10"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by ascent01 on 2007-10-19
when i run from terminal i get this output and the zsnes screen opens and then closes.  

> ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Creating link /root/.kde/socket-god.
can't create mcop directory


what do i need to do?

---

### Post by ascent01 on 2007-10-19
> **ascent01 said:**
> when i run from terminal i get this output and the zsnes screen opens and then closes.  



what do i need to do?

nevermind, i figured it out; if anyone else gets the "can't create mcop" error, then run the program in terminal and then just manually create the directory the program needs.

---

### Post by Draek on 2007-10-20
Create the folder where is really the question...

---

### Post by martinx73 on 2007-10-20
hi

in ubuntu 7.04 zsnes working fine to me.
i updated to version 7.10 and have the can't create mcop directory error

my solution is

open console
Try launching with 

```
zsnes -ad oss 
```

or

```
zsnes -ad alsa09
```

regards

---

### Post by Depressed Man on 2007-10-20
> **Draek said:**
> Create the folder where is really the question...

Well in the case of the topic creator..

```
Creating link /root/.kde/socket-god.
can't create mcop directory
```

He'd have to create a directory in /root/.kde/ called socket-god. Then inside there create a directory called mcop.

Just run znes in the terminal and see what message you get. And add those directories manually.

---

### Post by campaigner444 on 2007-10-24
I had the same problem with ZSNES. I needed to add the following directory to make it work...

/home/*your_folder*/.kde/socket-*computer_name*


-Sorry for the lack of a command box, but this is my first forum post and I don't know how.

---

### Post by bmartin on 2007-10-27
> **campaigner444 said:**
> mkdir /home/*your_folder*/.kde/socket-*computer_name*

-Sorry for the lack of a command box, but this is my first forum post and I don't know how.
Thanks! I just looked this up... I had the same problem and you fixed it!

Here's a cleaner command:
```
mkdir -p $HOME/.kde/socket-$HOSTNAME/mcop
```

---

### Post by mavsman4457 on 2007-11-13
Thank you so much for this thread.  I have had it up to here with this stupid problem and didn't think anything short of an ubuntu reinstall would solve it.  Thanks for the help guys.

---

### Post by Pecster on 2007-11-14
Thank you very much it worked for me!! :)

---

### Post by doorknob60 on 2007-11-22
Hey! Thanks it workwd for me too!

---

### Post by garrison on 2007-11-28
This also works:

Edit /etc/libao.conf in your favorite editor (vim) and change

```
default_driver=alsa09
```

to

```
default_driver=alsa
```

found it on [this blog]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/ogg123-mcop-error")

---

### Post by EnsignR on 2008-01-06
> **martinx73 said:**
> 

```
zsnes -ad alsa09
```



```
zsnes -ad alsa
```

The above works for me in Ubuntu 7.10 Gutsy. (with the 09 it doesn't)

---

### Post by mastahkillah666 on 2008-02-10
There is a more 'elegant' fix of the problem  8)  :

Instead of creating a directory, we will create a link of the socket to the /tmp directory and pointing it to null by typing in a terminal :

```
lnusertemp socket >/dev/null
```You can also create such "links" not only for kde resource sockets, but also for its resource cache (lnusertemp cache >/dev/null) and its tmp (lnusertemp tmp >/dev/null).

Hope it 'helps' (even if the problem is indeed resolved with mkdir)  ;)  .

---

