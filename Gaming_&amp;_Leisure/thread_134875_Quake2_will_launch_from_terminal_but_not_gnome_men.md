---
title: "Quake2 will launch from terminal but not gnome menu."
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by smack on 2006-02-22
This is the original launch script.

```

#!/bin/sh
###############################################################################
#
## LIFLG Startup Script
#
###############################################################################
#
# The game binary
#GAME_BINARY="quake2"
GAME_BINARY="sdlquake2"

# Subdirectory
SUBDIR="."

# Additional commandline options for mods etc.
#CMD_ARGS="+set vid_ref glx" # x86_64 startup
CMD_ARGS=""

# don't use US keyboard layout
#NOUSLAYOUT="true"


###############################################################################
## DO NOT EDIT BELOW THIS LINE
###############################################################################
readlink() {
    local path=$1 ll
    
    if [ -L "$path" ]; then
        ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
	echo "${ll/* -> }"
    else
	return 1
    fi
}

LANG=POSIX
export LANG
script=$0
count=0
while [ -L "$script" ]  
do
    script=$(readlink "$script")
    count=`expr $count + 1`
    if [ $count -gt 100 ]  
    then
        echo "Too many symbolic links"
        exit 1
    fi
done
GAME_DIR=`dirname $script`

trap "setxkbmap" EXIT

if [ ! "$NOUSLAYOUT" = "true" ]; then
    #games are better played with us keyboard layout
    setxkbmap -symbols 'us(pc101)'
fi

cd $GAME_DIR
cd $SUBDIR

xgamma -gamma 1.3
./$GAME_BINARY "$CMD_ARGS" "$@"
EXITCODE="$?"
xgamma -gamma 1

# reset kb layout
setxkbmap

exit $EXITCODE

```

That's a ton of junk so I tried simplifying to this.

```

#!/bin/sh
cd "/usr/local/games/quake2/"
./sdlquake2 $* 
exit $?

```

Those both work fine when launching them in a terminal but if I launch them from my gnome menu my screen flickers a bit like it launched and then crashed immediatly. I need to be able to launch this game normally so it can work with XQF. Does anyone have a suggestion? :cry:

*edit* oh yeah this is the latest version downloaded from liflg.

---

