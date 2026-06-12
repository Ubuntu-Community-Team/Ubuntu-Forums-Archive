---
title: "Gnome panel in script"
date: 2008-12-13
forum: Desktop Environments
---

### Post by Thingymebob on 2008-12-13
I have written a short script which is named withmetacity that switches between metacity & compiz when I launch and close particular programs:
```

#!/bin/bash

# check if compiz is running
appname=$1

if $( ps ax | grep -v "grep" | grep -q "compiz.real")
then
  if [ "$2" != "-q" ]
  then
    zenity --question --title "Stop Compiz" --text "\"$appname\" may perform better if desktop effects are disabled.\n\nTo disable desktop effects click OK otherwise click cancel to continue with the current settings.\n\nDesktop effects will be re-started when you close $appname"
  
    if [ $? = 0 ]
    then
      replacewm=1
    else
      replacewm=0
    fi

  else
    replacewm=1
  fi

  if [ "$replacewm" = 1 ]
  then
    metacity --replace 2&>1 &
    gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
  fi
fi
$1 $2

count=0
for ps in $(ps ax | grep -v "grep" | grep "withmetacity" | awk '{ print $1 }')
do
  let count++
done

if [ $count -le 2 ]
then 
  if $( ps ax | grep -v "grep" | grep -q "compiz.real" )
  then
    exit 0
  else
 gconftool-2 --type bool --set /apps/metacity/general/compositing_manager false
 compiz --replace
    exit 0
  fi
fi

```
This script is in /usr/sbin and is set executable with chmod+x. I have changed all relevant launchers to use this script when launching so for example 'blender -w' would now read 'withmetacity "blender -w"'

On the whole this script works well and switches to metacity when I launch the apps that play up with compiz and then back to compiz when I'm finished.

However there are a couple that are playing up with the metacity compositing manager so I need to turn this off (easy enough), but this will break AWN and I'll loose my window list.

I can stop and restart AWN easy enough, but am struggling for a way to add a panel with window list in it from within the script.

Any help appreciated.

I don't need suggestions like use compiz-fusion icon, I have it, my aim is to remove that step and not have to remember which apps play up with compiz + my 10yr old neice is getting my old desktop Ubuntu PC for xmas with ATI video again (She really wants the eyecandy) and would like it to just switch when needed

---

