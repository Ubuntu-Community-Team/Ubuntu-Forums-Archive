---
title: "Switch Workspaces with cube automatically?"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by wscottp on 2007-08-06
I have a wall mounted LCD at the front of our IT department that I recently plugged into an Ubuntu machine. I've gotten Beryl and everything working on an ATI card, and love the cube effect for switching workspaces.

The reason I started this little project was to be able to fit more than one screens worth of monitoring onto the television. To finish this I need some help on switching workspaces with the cube automatically.

Is there any way to script an occasional workspace switch, with a little flair?

Also, I've cut off every power saving feature I can find, but it still seems to cut off video after 30 minutes or so of inactivity.

---

### Post by Chudilo on 2007-08-06
Check your BIOS settings some have the video Off that overrides the OS settings.
Also update your BIOS,

Check your monitor settings. It could be enabled on your monitor.

---

### Post by jpereira on 2007-08-06
Hi, 

How about sending a keypress event to the desktop, using the shortcut defined for rotating?
Here's a small program that should do what you want: [http://savannah.nongnu.org/projects/swinput](http://savannah.nongnu.org/projects/swinput)

Another alternative would be to write a compiz plugin, that schedules plugin actions, but although I'm sure it's doable (other plugins do a similar thing for other kind of triggers) I wouldn't know where to start.

Let us know if you reach a working solution.

---

### Post by wscottp on 2007-08-07
I can't get swinput working. I get no errors through make/make install but nothing ever shows up in /proc/misc, and I see no devices created. It looks like it would have worked great, just echo some text to a fake device to grab the cube and move the mouse.

Is the screensaver module able to do what I want? If so, how do I install it?

If all else fails, I'm hiring. The posistion only pays $0.50 per hour, but your sole responsibility will be occasionally rotating my cube.

---

### Post by jpereira on 2007-08-07
> **wscottp said:**
> If all else fails, I'm hiring. The posistion only pays $0.50 per hour, but your sole responsibility will be occasionally rotating my cube.

Rar, sign me in! :)

Anyway, this is interesting, so I went on to look for a solution.

1st, download xsendkey here: [http://pag.csail.mit.edu/~adonovan/hacks/xsendkey.html](http://pag.csail.mit.edu/~adonovan/hacks/xsendkey.html)
2nd, uncompress it and create a Makefile in the same folder:
Makefile:
```

CC=gcc
CFLAGS=-g -Wall
LDFLAGS=-L /usr/X11R6/lib -lX11

all: xsendkey

xsendkey: xsendkey.o

clean:
        rm -f xsendkey.o xsendkey

```

Followed by a simple
```
$ make
```

You'll end up with "xsendkey" binary, which I suggest you copy to /usr/local/bin
```
$ sudo cp xsendkey /usr/local/bin
```

In order for xsendkey to send the key to the propper window, you need the window ID. In this case, you want to use the desktop's root window. You can get this info with 
```
$ xwininfo -root
```

Now, wrapping everything up, you can use the following script for your cube rotating needs. 

rotatecube.sh
```

#!/bin/bash

# don't forget to set this key to be the "Rotate Flip Right" action in the Rotate Cube compiz plugin
KEY=F12

# wait between MIN and MAX seconds before rotating again
MIN=5
MAX=10

# get root window ID
WID=`xwininfo -root | grep "Window id" | cut -f4 -d' '`

# Loop to keep rotating
while [ 0 -lt 1 ]; do
let "WAIT = $MIN + $RANDOM % ($MIN - $MAX)"
sleep $WAIT
/usr/local/bin/xsendkey -window $WID $KEY
done

```

```
$ chmod a+x rotatecube.sh
```

```
$ ./rotatecube.sh
```

Notice that the script will sleep first, and only then rotate. Adjust the MIN and MAX parameters as intended. I tested this with F12 Key, but obviously feel free to put anything you like. I chose "Rotate Flip Right" (at the bottom of the action list), because you can set the rotation parameters for the Flip, which you can't for simple "Rotate Right" (which always goes at same speed).

Let me know how this works for you, I'm curious.

PS: can I still apply for the job? could do with the extra penny here and there... ;)

---

### Post by mikec13 on 2007-08-07
This worked for me:

[http://forum.compiz.org/viewtopic.php?t=188&sid=d2a259b667c2c7d6b54eb7f61e562e67](http://forum.compiz.org/viewtopic.php?t=188&sid=d2a259b667c2c7d6b54eb7f61e562e67)

---

### Post by wscottp on 2007-08-07
Thanks jpereira!

Got your script working before the other was posted.

That's working like a charm, I've got 2 fullscreen browsers with Cacti graphs, and another 2 with Zenoss. 4 screens worth of monitoring on one TV!

The "Flip" action is great, I was able to slow it down where the transition looks beautiful.

I'm going to have to pull that job posting though... reminds me of a sticker I had on the back of my monitor years ago at an ISP:

"Go away or I will replace you with a very small shell script"

Thanks Again!

---

### Post by jpereira on 2007-08-07
The dbus alternative is also worth taking note of - always learning! :)

Too bad for that job though, was looking forward to do somemindless clicking. ;)

Cheers,

---

