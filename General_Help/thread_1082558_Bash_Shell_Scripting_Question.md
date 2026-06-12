---
title: "Bash Shell Scripting Question"
date: 2009-02-27
forum: General Help
---

### Post by dstein on 2009-02-27
I have a program that requires /dev/dsp , which I do not have. However, there is a file on my computer, /dev/dsp1. When I create a symbolic link from dsp to dsp1, my program runs fine.

I would prefer not to do this.

The program I am referring to is actually called from a shell script. Is there any code that I can add to the script that will essentially cause the program to use /dev/dsp1 every time it tries to use /dev/dsp ?

This way I can delete the symbolic link I created.

Thanks.

---

### Post by sdennie on 2009-02-28
What program are you trying to run?

If the program can't use /dev/dsp1, you could also use a udev rule to create a symlink from /dev/dsp1 to /dev/dsp automatically every time /dev/dsp1 is created.  See: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by dcstar on 2009-02-28
> **dstein said:**
> I have a program that requires /dev/dsp , which I do not have. However, there is a file on my computer, /dev/dsp1. When I create a symbolic link from dsp to dsp1, my program runs fine.

I would prefer not to do this.

The program I am referring to is actually called from a shell script. Is there any code that I can add to the script that will essentially cause the program to use /dev/dsp1 every time it tries to use /dev/dsp ?

This way I can delete the symbolic link I created.

Thanks.

Post the shell script.

---

### Post by leewebb on 2009-02-28
> **dstein said:**
> I have a program that requires /dev/dsp , which I do not have. However, there is a file on my computer, /dev/dsp1. When I create a symbolic link from dsp to dsp1, my program runs fine.

I would prefer not to do this.

The program I am referring to is actually called from a shell script. Is there any code that I can add to the script that will essentially cause the program to use /dev/dsp1 every time it tries to use /dev/dsp ?

This way I can delete the symbolic link I created.

Thanks.

Why not simply create /dev/dsp?
 [FONT=Courier New]
$ sudo mknod /dev/dsp c 14 3 
$ sudo chgrp audio /dev/dsp
$ sudo chmod 660 /dev/dsp[/FONT]

---

### Post by dstein on 2009-02-28
leewebb, the method you described did not work. There was still no sound.

dcstar, here is the script I am currently using:
```

#!/bin/sh

# Global quake2 directory
# Directory for ref_*.so files
QUAKE2_CONF=~/quake2
export QUAKE2_CONF

# Directory for game data ("baseq2")
QUAKE2_BASE=$QUAKE2_CONF/baseq2
export QUAKE2_BASE

# Check if a +map arg was handed to this script
#  if yes pass it on through to the game
#  if no pass a default +map arg
ARGSTRING=$*
MAP_INDICATED=`echo $ARGSTRING | grep "+map"`
if test -n "$MAP_INDICATED"; then
   echo "+map arg included"
fi

if test -n "$MAP_INDICATED"; then
    $QUAKE2_CONF/quake2 +set vid_ref softx +sw_mode 4 +vid_gamma .6 +set game quagent "$@"
else
    $QUAKE2_CONF/quake2 +set vid_ref softx +sw_mode 4 +vid_gamma .6 +set game quagent +map demo1 "$@"
fi

```

---

