---
title: "Unreal Tournament 2004 Mod Installation"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by MonkeyBoy on 2007-05-23
After successfully installing UT2004 I have downloaded and installed some mods.  They don't run when I execute their scripts though.

This is the script for Piddly's Chance:

```
#!/bin/sh

SUBDIR="."

#----------------------------------------
script=$0
count=0

while [ -L "$script" ]  
do
    script=`perl -e "print readlink(\"$script\"), \"\n\""`
    count=`expr $count + 1`

	if [ $count -gt 100 ]  
	then
	    echo "Too many symbolic links"
	    exit 1
	fi
done

GAME_DIR=`dirname $script`

cd $GAME_DIR
cd $SUBDIR

exec ut2004 "$@" -ini=Piddly2004.ini -userlogo=Piddly.bmp -userini=PiddlyUser.ini -log=Piddly.log
```

I noticed that the script expects a symbolic link to ut2004 in my home dir which for some reason the game install didn't make.  I am launching the game form inside it's dir instead.

Can anyone suggest a way of either altering the script so it launches the game from /ut2004/ dir rather than home, or of making the correct type of link into my home dir?

---

### Post by MonkeyBoy on 2007-05-23
I fixed it.   :p

</thread>

---

