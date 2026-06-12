---
title: "desktop not responding"
date: 2010-06-27
forum: Desktop Environments
---

### Post by eyehatehippies on 2010-06-27
Currently running Ubuntu 10.04. Recently had problems with panels not appearing but desktop responded as normal.
NOW, it would appear my icons formerly occupying my desktop are gone, and i can no longer left or right click on the desktop or group select anything. All the panels function as they should, but now the desktop itself is not responding and as stated my desktop icons disappeared.

---

### Post by stderr on 2010-06-27
I don't know quite what messes up in this fashion, but you can resolve the problem by toggling the GConf show_desktop setting off and on again. You can do this manually through the graphical gconf editor (in a terminal type: gconf-editor) or via the command line. I personally use this script, which I add to a custom menu category in my main menu, and call it "Toggle Show Desktop".

You need to toggle the setting "/apps/nautilus/preferences/show_desktop" to "false" and back to "true".

You can simply paste this script into a text file, save, chmod +x, and execute twice to achieve the same effect.

```
#!/bin/bash

GCONFTOOL=`whereis gconftool | awk '{ print $2 }'`
PATH="/apps/nautilus/preferences/show_desktop"
ERROR_MSG="Failed to set gconf key $PATH with $GCONFTOOL; return status was     $?."
VALUE=`$GCONFTOOL --get $PATH`
NEW_VALUE=""

if [[ $VALUE != "false" ]] ; then
  NEW_VALUE="false"
else
  NEW_VALUE="true"
fi

$GCONFTOOL --type bool --set $PATH $NEW_VALUE

if [[ $? -ne 0 ]] ; then
  gdialog --title "Error" --msgbox "$ERROR_MSG"
fi

```

---

### Post by eyehatehippies on 2010-06-27
"chmod +x"? Sorry, but as you can tell i'm not quite up on Linux terminology for the most part. But copy & pasting that into a terminal and running it twice DID fix my problem. Thank you very much for your help!

---

### Post by stderr on 2010-06-27
No problem, glad it helped. 

Regarding chmod +x, if you had saved it to a file (e.g. now you have a file called script.sh with that script in), then you'd have to give it executable permissions before you could run it. You do that with chmod +x:

```
chmod +x script.sh
```

and then you could run it with:

```
./script.sh
```

However, copying and pasting the whole thing works too :)

---

### Post by stderr on 2010-06-27
No problem, glad it helped. 

Regarding chmod +x, if you had saved it to a file (e.g. now you have a file called script.sh with that script in), then you'd have to give it executable permissions before you could run it. You do that with chmod +x:

```
chmod +x script.sh
```

and then you could run it with:

```
./script.sh
```

However, copying and pasting the whole thing works too :)

---

### Post by stderr on 2010-06-27
No problem, glad it helped. 

Regarding chmod +x, if you had saved it to a file (e.g. now you have a file called script.sh with that script in), then you'd have to give it executable permissions before you could run it. You do that with chmod +x:

```
chmod +x script.sh
```

and then you could run it with:

```
./script.sh
```

However, copying and pasting the whole thing works too :)

---

### Post by stderr on 2010-06-27
No problem, glad it helped. 

Regarding chmod +x, if you had saved it to a file (e.g. now you have a file called script.sh with that script in), then you'd have to give it executable permissions before you could run it. You do that with chmod +x:

```
chmod +x script.sh
```

and then you could run it with:

```
./script.sh
```

However, copying and pasting the whole thing works too :)

**EDIT: Apologies, either the forum server messed up or I adopted newbie mode and repeatedly clicked send during some connectivity issues. The server kept returning the message "This forum requires that you wait 20 seconds between posts. Please try again in 5 seconds." when I tried to post, regardless of wait time. Then suddenly all these posts show up together! Moderator: can you delete some of these?**

---

### Post by Japsser on 2010-07-07
^ thank you, had the same issue. 

Don't run it as root though, sine it doesn't resolve anything that way

---

