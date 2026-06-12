---
title: "Partly refresh gnome-panel"
date: 2006-02-10
forum: Desktop Environments
---

### Post by dee.dw on 2006-02-10
Hello,

I have written a little script to activate and deactivate my internet connection.
```
#!/bin/bash

if [ -a /home/dee/.dsl_on ] ; then  # dsl is on
  rm -f /home/dee/.dsl_on         # delete file
  poff -a                         # kill dsl
  cp /home/dee/.icons/dsl_stat_off.png /home/dee/.icons/dsl_stat.png  # set icon to off
  killall gnome-panel             # refresh panel
else
  touch /home/dee/.dsl_on         # create file
  pon arcor                       # start dsl
  cp /home/dee/.icons/dsl_stat_on.png /home/dee/.icons/dsl_stat.png   # set icon to on
  killall gnome-panel             # refresh panel
fi
```
I have set a link in a panel to this script and set the icon to "/home/dee/.icons/dsl_stat.png".

As you can see after changing my internet status I copy a new icon to this place. To show the icon correctly in the panel I need to refesh this part. The only solution for this was "killall gnome-panel" what's a little bit annoying when all windows resize for a short time and so on.

Is there way ro refresh the link or the icon in the panel without "killall"?

Thanks, Dee

---

### Post by dee.dw on 2006-02-10
So, the answer was easy - if you knew it already. :)
```
#!/bin/bash
while(true)
do
   zenity --notification --window-icon=/home/dee/.icons/dsl_stat_off.png
   pon arcor
   zenity --notification --window-icon=/home/dee/.icons/dsl_stat_on.png
   poff -a
done
```
This little script does exactly what I want. Thanks for listening!

Greetings, Dee

---

