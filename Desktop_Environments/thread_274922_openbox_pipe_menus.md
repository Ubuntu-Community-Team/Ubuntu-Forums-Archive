---
title: "openbox pipe menus"
date: 2006-10-10
forum: Desktop Environments
---

### Post by JRaz on 2006-10-10
i recently switched from gnome to openbox but found the lack of time in the bottom right hand corner annoying. Rather than install a taskbar (sensible option?), I decided to write a pipe menu to show the time in the main menu.

I wrote the following python code to display the time in pipe menu format:

import time
now=time.localtime(time.time())
year, month, day, hour, minute, second, weekday, yearday, daylight=now
print "<openbox_pipe_menu>"
print "<item label=\"%02d:%02d\"/>" % (hour, minute)
print "</openbox_pipe_menu>"

and the following xml was used to embed the menu

<menu id="time" label="time" execute="python ~/tme.py"/>
<menu id="time"/>

This works fine except like the name suggests its a menu, but I would rather it be a label, is there a way to achieve this?

---

### Post by kerry_s on 2006-10-10
You can alway's use> xclock <it's installed already. I just used conky to display the time. Are you running a mixed system(gnome/openbox) or just openbox? If it's mixed you can use the gnome-panel in openbox(in terminal> gnome-panel & ). I'm not using openbox anymore so i can't really with your pipe menu, it's been to long since i last used it, and i've got a bad memory.LOL Sorry

---

### Post by JRaz on 2006-10-10
I tried xclock but as far as i can tell its a standalone app, which is not quite what im after, but thanks for the fast reply.

Im currently running just openbox, i love its simplicity - which is also the reason I dont want to run a panel.

---

### Post by JRaz on 2006-10-11
I cleaned the code up a bit, so if anyone wants to add a clock to their openbox menu it is as follows.

> Make a file called tme.py and save it in ur home folder

> Copy the following into tme.py and save

import time
a,a,a,h,m,a,a,a,a=time.localtime()
print"<openbox_pipe_menu><item label='%02d:%02d'/></openbox_pipe_menu>"%(h,m)

> Open your menu.xml file (home/.config/openbox/menu.xml) and insert the following line between the opening and closing root-menu tags

<menu id="time" label="time" execute="python tme.py"/>

> Save the file and you should now have a new menu called time in your main menu which wen hovered over shows the current time (24 hours)

---

### Post by fuscia on 2007-09-01
better than what i was looking for. thanks, jraz.

---

### Post by moore.bryan on 2007-09-01
[I]i was interested in this too, but couldn't get it to run.  so, i checked it in cli and got this:
```
Traceback (most recent call last):
  File "tme.py", line 1, in <module>
    import time
  File "/home/moore/time.py", line 2, in <module>
AttributeError: 'module' object has no attribute 'localtime'
```
huh?[/I]

---

