---
title: "wineX not in your path"
date: 2006-11-12
forum: Gaming &amp; Leisure
---

### Post by Josey on 2006-11-12
I installed Morrowind III Elder Scrolls With a loki installer and I get this when trying to run it.
> 
Wine(X) not in your PATH


This is the script to run the game. I have wine installed but not any of the other versions like cedega.

> 
#!/bin/sh

GAME_BINARY="Morrowind.exe"
SUBDIR="."
WINE_NAMES="cedega winex3 cvswinex winex wine"

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

if [ -z "$WINE_EXEC" ]
then
	WINE_EXEC=`type -p $WINE_NAMES | head -n 1`
fi


if [ -e "$WINE_EXEC" ]
then
	cd $GAME_DIR
	cd $SUBDIR
	$WINE_EXEC $GAME_BINARY $* &
	sleep 2 &&
	renice 5 -p `pgrep wineserver`
else 
	echo "Wine(X) not in your PATH"
	exit 1
fi


I'm not sure how to get it to use the wine version I have installed I guess.

---

### Post by Josey on 2006-11-12
This is what I get when I just try to run wine morrowind.exe without using the script.

```
err:module:import_dll Library MSVCP60.dll (which is needed by L"H:\\c\\game\\morrowind\\Morrowind.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\c\\game\\morrowind\\Morrowind.exe" failed, status c0000135

```

---

### Post by perky on 2007-01-14
Sounds like you may need to install some extra libraries for your wine. Give [winetools]("http://www.von-thadden.de/Joachim/WineTools/") a go if you haven't already tried.  With this you can easily install most the required libraries.  Hope this helps!

---

### Post by Jiawen on 2007-05-10
I'm having the same problem. Winetools didn't help at all.

---

### Post by 3416 on 2008-07-24
Had the same problem.

Must be a problem with the 'type' action in the script-file which searches wine

Just complete the top of the start script with 

> WINE_EXEC='/usr/bin/wine'  #or to your exec of wineX / Cedega

for example like this:

> #!/bin/sh

GAME_BINARY="gta-vc.exe"
SUBDIR="."
WINE_NAMES="cedega winex3 cvswinex winex wine"
WINE_EXEC='/usr/bin/wine'

(with GTA Vice City does it work ;) )

---

