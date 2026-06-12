---
title: "Rotate the display? Possible?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by benbroad on 2005-10-17
Does anyone know how I might be able to get Ubuntu to rotate the screen by 180 degrees so the top becomes the bottom and vice versa? I cant just physically turn the screen as I need the ability to flip it back and forth.

Any ideas?

---

### Post by Goober on 2005-10-17
Well, you can move the top and the bottom taskbars to their opposite positions, but I am not sure if that is what you are asking.  To move them, just click and drag them, like in Windows.

---

### Post by benbroad on 2005-10-18
No I need to rotate the whole screen. Imagine if the screen was lying flat on a table, if I am sat in front of it it is the right way up but for someone sat opposite me it will be the wrong way up. I need a software solution so that I can flip it so my friend sat across from me can see the screen in it's correct orientation.

---

### Post by Murgle on 2005-10-18
Idealy typing 'xrandr -o inverted' or 'xrandr -x' will flip the screen and presumily go back as well, the only thing is that I get errors when ever I try to use  those features of xrandr, funny though I can use other features.  If it works for you great, otherwise maybe someone can say why it doesn't work

Edit: well after further experimentation it seems that only xrandr -o 0 works, this just returns you to your default resolution which can be nice for poorly exiting games, but is not what you are looking for

---

### Post by benbroad on 2005-10-18
Champion! I will give it a bash.

---

### Post by Murgle on 2005-10-18
so did it work for you?

---

### Post by benbroad on 2005-10-18
The development box we are working on is at another location. I will be able to try it this evening and I will give you a yell on the morrow.

Ta!

---

### Post by benbroad on 2005-10-18
It looks like xrandr might well be the way to go. Getting errors at the moment though:

```

root@candy:~# xrandr -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by Murgle on 2005-10-18
Those are the same errors that I was getting... I haven't the faintest clue why.  We propbably nee to install a package or something...

---

### Post by fif on 2006-02-05
Have a look at the outcome of xrandr -q. For me, it is the following:

```

 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 406mm x 302mm )  *85   75   60
 1   1280 x 960    ( 406mm x 302mm )   85   60
 2   1280 x 800    ( 406mm x 302mm )   60
 3   1280 x 768    ( 406mm x 302mm )   60
 4   1152 x 864    ( 406mm x 302mm )   85   75
 5   1152 x 768    ( 406mm x 302mm )   55
 6   1024 x 768    ( 406mm x 302mm )   85   75   70   60   87
 7    800 x 600    ( 406mm x 302mm )   85   75   72   60   56
 8    640 x 480    ( 406mm x 302mm )   85   75   73   60
 9    832 x 624    ( 406mm x 302mm )   75
 10   720 x 400    ( 406mm x 302mm )   85
 11   640 x 400    ( 406mm x 302mm )   85
 12   640 x 350    ( 406mm x 302mm )   85
 13   512 x 384    ( 406mm x 302mm )   87
 14   416 x 312    ( 406mm x 302mm )   75
 15   400 x 300    ( 406mm x 302mm )   85   75   72   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

```

Launching xrandr -o left gives a similar error as the one you get. Apparently due to a non supported option. I just tried out and did not discover how to enable rotations and reflections in xrandr (don't even know if it is possible for my config). I had a look in xorg.conf and did not find out anything - I am no specialist though -

Still investigating.

---

### Post by henriquemaia on 2006-04-22
Anyone has any idea on how to get this working (xrandr)? I'm also looking forward to test a rotated desktop.

---

### Post by henriquemaia on 2006-04-22
[QUOTE=henriquemaia]Anyone has any idea on how to get this working (xrandr)? I'm also looking forward to test a rotated desktop.[/QUOTE]

Ok, found it:

[http://ubuntuforums.org/showthread.php?t=108064&highlight=randr](http://ubuntuforums.org/showthread.php?t=108064&highlight=randr)

Works nicely. Lovely feature.


Note: If you're trying to get this working using xrandr and you get an error with, for instance, **xrandr -o inverted**, read the thread above.

---

