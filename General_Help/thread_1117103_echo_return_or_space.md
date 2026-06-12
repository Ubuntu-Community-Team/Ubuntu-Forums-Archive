---
title: "echo return or space"
date: 2009-04-05
forum: General Help
---

### Post by colsandurz on 2009-04-05
Hello,

I have playing with my .baschrc file and I set it so it starts screen on default.  However, whenever screen starts it displays this splash screen and to get it to go away you have to press enter or space.  Is there a way to use echo to automate this?  I tried a few things already 

```

echo \n
echo " "
echo -e \n

```

and none worked.  

I also did look through the screen manual and it didn't seem like there was a way to suppress the splash screen.

---

### Post by Brucevdk on 2009-04-17
Add the following to your ~/.screenrc:

```

startup_message off

```

This option is also described in *man screen*.

You might also be interested in [Brad Sims's screenrc](http://www.mail-archive.com/screen-users@gnu.org/msg00103.html).

Also note that echoing a linebreak (which goes to stdout) is not the same is hitting enter (which goes to the stdin for screen). I'm not actually aware of an easy method to fake stdin apart from macro playback (xmacro) or possibly having a Python wrapper script to start and communicate with the process (see [Access mplayer (slave mode) from python](http://code.activestate.com/recipes/542195/)).

---

### Post by raptor2552 on 2009-04-17
See my reply number 10 [http://ubuntuforums.org/showthread.php?t=953779](http://ubuntuforums.org/showthread.php?t=953779) on how to echo characters in a bash script

---

