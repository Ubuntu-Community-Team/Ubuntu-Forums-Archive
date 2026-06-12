---
title: "Conky disappears after start up"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by navneeth on 2007-06-07
After the Ubuntu splash* appears, I get a plain  Ubuntu light-brown background(similar to the one in the picture). The wallpaper takes sometime to come on; but before it does, the bottom panel, the terminal and conky show up. But as soon as the wp comes up, conky disappears. But it still shows up under the Processes tab in the System Monitor. How do I make sure that conky doesn't disappear?

Thanks for any help.




*[img]http://www.guia-ubuntu.org/images/thumb/4/43/Ubuntu-splash.jpg/180px-Ubuntu-splash.jpg[/img]

---

### Post by happy-and-lost on 2007-06-07
Conky is launched before Nautilus, so the wallpaper is covering it. Launch Conky from a sleeping script to get around that problem. Like this:

*nano .conkylaunch*
 Into that file paste:
```

#!/bin/bash
sleep 10 &&
conky &
exit
```

Then *chmod +x .conkylaunch*

And add this script to the startup.

If the problem persists, change the sleep value unil you've given Nautilus enough time to load.

---

### Post by navneeth on 2007-06-07
Thank you. 20 works fine for me. :)

---

### Post by dannymichel on 2007-06-12
> **happy-and-lost said:**
> Conky is launched before Nautilus, so the wallpaper is covering it. Launch Conky from a sleeping script to get around that problem. Like this:

*nano .conkylaunch*
 Into that file paste:
```

#!/bin/bash
sleep 10 &&
conky &
exit
```

Then *chmod +x .conkylaunch*

And add this script to the startup.

If the problem persists, change the sleep value unil you've given Nautilus enough time to load.
Open the terminal, copy and paste ```
nano .conkylaunch
``` then enter?
then copy and paste```
#!/bin/bash
sleep 10 &&
conky &
exit
```into that weird window that appears?
That weird window doesn't allow me to save.

Ho wdo I CHMOD after I figure out what is going on

---

### Post by nickless on 2007-06-13
you don't have to use nano. Use your favorite text editor, like gedit:
```
gedit .conkylaunch
```

after pasting the script just type in your terminal:
```
chmod +x .conkylaunch
```
and hit enter. That makes the file executeable.

To start the script you will have to type:
```
sh /home/YOURUSERNAME/.conkylaunch
```
This is also the code you should add to your session dialog, to let conky start at your startup.

---

### Post by S.Peterman on 2007-07-04
Just wanted to say thanks, this is exactly what I needed to get conky working properly.

---

### Post by daniel_szollosi-nagy on 2007-12-30
This post came up as the first result in Google for "conky disappears" - fixed my problem right off the bat. Thanks for the info guys!

---

### Post by wormser on 2008-03-13
This resolved my problem.  I used 20.

---

