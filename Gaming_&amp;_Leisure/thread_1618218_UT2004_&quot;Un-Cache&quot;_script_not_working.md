---
title: "UT2004 &quot;Un-Cache&quot; script not working"
date: 2010-11-10
forum: Gaming &amp; Leisure
---

### Post by Protocol84 on 2010-11-10
I found a nice "un-cache" script that worked splendidly (the only one thus far that has) the first time through. I tried to run it again later and it now spits out an error:

tail: cannot open `+5' for reading: No such file or directory

****EDIT****
I figured out what happened, I had the script set to dump to /usr/local/games/ut2004 so I thought it would need root privileges so I used sudo when executing the script. So root took over ownership of the cache.ini file in my ~/.ut2004 so the cache.ini could not be written to. 

So UT2004 kept re-downloading all the maps I was playing and in about an hour accumulated over a gig of files in the cache, and the script was returning the error because the cache.ini had no file list in it to move.

I fixed this by simply deleting the contents of ~/ut2004/cache and running ut2004 and it rebuilt the cache in the proper fashion, then using this command in the terminal to create the needed folders in ~/.ut2004:

cd ~/.ut2004 && mkdir -p Animations/ Maps/ Music/ Sounds/ StaticMeshes/ Textures/

then changing this line in the script:
target=/usr/local/games/ut2004

to:
target=~/.ut2004

Done.
***EDIT***

here is the script:


#!/bin/sh

#include <disclaimer.h>
#v 0.7

# Edit the following target=.. line to change the targetdir, the
# cachefiles will be moved into its subdirs
# usually /usr/local/games/ut2004 or ~/.ut2004 - for the former read below!

target=/usr/local/games/ut2004


# Script to move the *.uxx cache files from ~/.ut2004/Cache under
# their real name to the corresponding ut2004 subdirs which are
#         Animations/ Maps/ Music/ Sounds/ StaticMeshes/ Textures/

# - This can be either the global installdir (/usr/local/games/ut2004 usually)
# since it is usually owned by root you have to change the permissions a bit:
#  You can either do it the simple way, but then anyone will be able
#   to place files in the subdirs but not delete files added by others due to
#   the "sticky" bit (+t):  # cd $target; chmod o+wt <subdirs>
#  Or add yourself to the group "games" (or similar) and then change the group
#   ownership of these subdirs to "games" and give the group write permissions,
#   setting the sticky bit will prevent overwriting files added by possible other
#   members of the games group or of the installation itself (since these are owned by
#   root):  # cd $target; chgrp games <subdirs>; chmod g+ws <subdirs>; chmod +t <subdirs>

# - Or just use the personal ~/.ut2004 dir for which most likely the <subdirs> first have to be
# generated $ cd ~/.ut2004 && mkdir -p Animations/ Maps/ Music/ Sounds/ StaticMeshes/ Textures/
# and target= has to be changed above, these files will then only be available to you.

# Note that modfiles (*.u) which would go to the System/ subdir
# should better be installed manually, this script leaves them in the Cache.

# GPL'ed :) - by hethrep at linux-gamers dot net

# Dont edit below unless you know what you are doing

cachedir=~/.ut2004/Cache

#cmd="echo mv" # test, also comment out last line if testing!
cmd="mv -v" # action, DON'T add '-i' since piping into sh
            # is strictly noninteractive

cd $cachedir || { echo "Error: Couldn't cd into $cachedir"; exit 1; }
echo '[Cache]' > cache.ini.new
# keep a few backups, delete older ones
rm -f `ls -t cache.ini.bak.* | tail +5`
cp cache.ini cache.ini.bak.$$
grep '=' cache.ini  | awk --field-separator '=' \
--assign cmd="$cmd" --assign=target="$target" \
'{
        #print $1" "$2; # ya test here
        if(match($2,".ukx$")) { printf cmd" \""$1".uxx\" \""target"/Animations/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else if(match($2,".ut2$")) { printf cmd" \""$1".uxx\" \""target"/Maps/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else if(match($2,".ogg")) { printf cmd" \""$1".uxx\" \""target"/Music/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else if(match($2,".uax$")) { printf cmd" \""$1".uxx\" \""target"/Sounds/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else if(match($2,".usx$")) { printf cmd" \""$1".uxx\" \""target"/StaticMeshes/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
# preferably not... - better install mods youself
        else if(match($2,".u$")) { printf cmd" \""$1".uxx\" \""target"/System/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else if(match($2,".utx$")) { printf cmd" \""$1".uxx\" \""target"/Textures/"$2"\" || echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";  }
        else printf "echo \""$1"="$2"\" >> cache.ini.new\n" | "sh";
}
END { close("sh") }'

#comment out if testing:
mv cache.ini.new cache.ini

---

### Post by Brebs on 2010-11-10
> **Protocol84 said:**
> tail: cannot open `+5' for reading: No such file or directory
See [FAQ](http://icculus.org/lgfaq/#chasingmyowntail):

export _POSIX2_VERSION=199209

---

### Post by Protocol84 on 2010-11-11
I found out what it was, the file it was referencing for a file list was empty so there really was no such file, I explain further in my edit above.

Thank you for your help!

---

