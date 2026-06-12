---
title: "Set an application to load at startup?"
date: 2009-08-28
forum: Desktop Environments
---

### Post by beastrace91 on 2009-08-28
How can I add an application to load at start up in KDE? For some reason knetworkmanager isn't starting by default and I would like to add it.

~Jeff

---

### Post by grappler on 2009-08-28
System Settings > Advanced > Autostart >Add Program


Then insert the path of the program.

Personally I use the gnome network manager rather than the kde one so I just type in "nm-applet".

---

### Post by beastrace91 on 2009-08-28
Good suggestion. I forgot I could load that one in KDE, much prefer the Gnome network manager myself as well :D

~Jeff

---

### Post by beastrace91 on 2009-08-28
So I added this command to be run at startup: ```
compiz --replace && gtk-window-decorator --replace
``` but for some reason it is not launching compiz or replacing the window decorator... if I open terminal and run the above command it works fine... Any ideas why?

~Jeff

---

### Post by enli on 2009-08-28
Simple commands will work but not like the one you wanting to.

Put following in new file and rename it something similar to "startup-script.sh"

```

#!/bin/bash
compiz --replace && gtk-window-decorator --replace

```

Go to properties of file and make it executable. (I have never used kde myself so you have to look for that option). or open up the terminal and cd to directory where you have kept the .sh file and do
```
chmod +x filename.sh
```

After that add this file as a startup item. The commands in this file will be executed at startup

---

### Post by beastrace91 on 2009-08-28
Yea... if simple commands work so should a small && command. To humour you though I create a .sh file with the contents of ```
#!/bin/bash
compiz --replace && gtk-window-decorator --replace
``` and then pointed my start program to it - still no dice. Might just go back to using Gnome - it's start up manager works at least :/

~Jeff

---

### Post by enli on 2009-08-28
I think it was not set to executable type. This seems to be very tiny problem, I would not jump back.

Check again if it is executable :D. 
```
ls -a
```

Properties of one of my scripts :
```

enli@enli-laptop:~/Scripts$ ls -l launch-foxit-reader.sh
-rwxr-xr-x [COLOR="Red"]**1**[/COLOR] enli enli 324 2009-08-18 02:22 launch-foxit-reader.sh

```

There should be bit 1 as highlighted which means script is executable.

---

### Post by beastrace91 on 2009-08-28
Yes I made it excutable... Sorry didn't think I needed to say that 0.0 - but again proof ```
-rwxr-xr-x 1 jeff jeff 62 2009-08-28 15:02 /home/jeff/.compizrun.sh
```

Other suggestions as to why its not running?

~Jeff

---

### Post by grappler on 2009-08-28
I assume you really want compiz? Why not use kwin which is pretty good - not quite all of the bells and whistles of compiz but has all I need.

---

### Post by DaithiF on 2009-08-28
> **enli said:**
> 
```

enli@enli-laptop:~/Scripts$ ls -l launch-foxit-reader.sh
-rwxr-xr-x [COLOR=Red]**1**[/COLOR] enli enli 324 2009-08-18 02:22 launch-foxit-reader.sh

```There should be bit 1 as highlighted which means script is executable.
Hi,
I don't mean to be pedantic, but the 1 highlighted does not indicate that the script is executable.  It in fact represents the number of hardlinks to this file.  The fact that the script is executable is indicated by the x's in the rwx...etc

---

### Post by rorschach988 on 2009-08-28
yeah great idea

---

### Post by rorschach988 on 2009-08-28
do it

---

### Post by beastrace91 on 2009-08-28
> **grappler said:**
> I assume you really want compiz? Why not use kwin which is pretty good - not quite all of the bells and whistles of compiz but has all I need.

Ehh lack of compiz is enough reason for me to end my trail of KDE and crawl back to Gnome lol

~Jeff

---

### Post by grappler on 2009-08-28
What aspect of compiz do you need that's not in kwin? Running something that's so fundamentally gnome in kde sounds like asking for trouble.

---

### Post by beastrace91 on 2009-08-29
3d cube? Wobbly Windows? Window create/exit/minimize effects? 3d windows on said 3d cube?

~Jeff

---

### Post by grappler on 2009-08-29
Cube is available, so are wobbly windows (I think), 3d windows on cube are also available. Not sure about the rest. I use the "view all desktops" "view all windows" features in kwin.

---

### Post by grappler on 2009-08-29
Just confirmed - wobbly windows available

---

