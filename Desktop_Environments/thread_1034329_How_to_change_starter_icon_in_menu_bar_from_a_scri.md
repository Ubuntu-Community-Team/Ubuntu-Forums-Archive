---
title: "How to change starter icon in menu bar from a script"
date: 2009-01-08
forum: Desktop Environments
---

### Post by hgerstung on 2009-01-08
Hi!

I am looking for a way to visually indicate the status of a self-written script (bash) that runs in the background. My first idea was to set up a custom starter in the menu bar, define mystatus.png as its icon and then copy either green.png or red.png over it in order to reflect the states "enabled" and "disabled". 

Unfortunately Gnome does not seem to update the icon (at least not within a couple of seconds) in the menu bar and I wonder if there is a way to force it to reload the icons (or the whole menu bar, but that would probably be overkill...).

Any ideas anyone?

Cheers,
  Heiko

---

### Post by zhocchao on 2009-01-08
hi
look at this:

#!/bin/bash
 exec 3> >(zenity --notification --listen)
while(true)
do
  echo "icon:info" >&3
sleep 1
echo "icon:error" >&3
sleep 1
done

if you want to change the state clicking the icon, you have to use zenity --notification the normal way

g
z

---

