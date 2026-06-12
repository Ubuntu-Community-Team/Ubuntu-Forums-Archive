---
title: "How To Change The &quot;Show Desktop&quot; Icon"
date: 2010-06-17
forum: Desktop Environments
---

### Post by nodrog1952iii on 2010-06-17
I hate the purple "Show Desktop Icon" in Lucid and I finally figured out how to change it:

[INDENT]1) sudo apt-get install wmctrl
2) Create the following script and proceed as directed within the script's comments:

[INDENT]#!/bin/sh
# GLD's Show Desktop Button script. Here's how to do it.
# sudo apt-get install wmctrl
# Right click on the panel and select "Add To Panel".
# Choose "Custom Application Launcher".
# Use the file name of this script for the Command.
# Use whatever icon that you want.  The generic Ubuntu
# Show_Desktop_Button icon is located here:
# /usr/share/gnome/help/user-guide/C/figures/show_desktop_button.png
#

if [ -f /tmp/toggle_show_desktop_$USER ]
     [INDENT]then
          [INDENT]wmctrl -k off
          rm /tmp/toggle_show_desktop_$USER[/INDENT]
     else
          [INDENT]wmctrl -k on
          touch /tmp/toggle_show_desktop_$USER[/INDENT][/INDENT]
fi[/INDENT][/INDENT]


Enjoy,

Gordon

---

### Post by nilarimogard on 2010-06-17
There's no need for a temp file:

```
#!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
```

---

### Post by nodrog1952iii on 2010-06-17
> **nilarimogard said:**
> There's no need for a temp file:

```
#!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
```


Cool!  Thanks.

---

