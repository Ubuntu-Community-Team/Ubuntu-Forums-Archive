---
title: "[SOLVED] True transparency on rxvt startup"
date: 2008-04-19
forum: Desktop Environments
---

### Post by x1a4 on 2008-04-19
Hi,

Right now I'm using **transset** to set transparency for **rxvt**, but with that I need to run it, then click the window each time I run an instance of rxvt.  Is there a way to enable _true_ transparency for rxvt?  Perhaps run rxvt and transset in a script?  transset places the mouse cursor over the active window's title when run, so generating a mouse click event might do the trick.  Anyone?

I know about .Xdefaults and the various options, but those only create pseudo transparency.  I want true transparency like transset does. 

Thank you.

---

### Post by x1a4 on 2008-04-20
I managed to get it done.  Here's how.  If you have a better solution than this very dirty hack please, pleease let me know.  Thanks. 

Instead of starting rxvt normally I start it in a script, run transset, then use [xdotool]("http://www.semicomplete.com/projects/xdotool/") to send a mouse click event on the newly open window.

Here's the script: 

```

#!/bin/bash
#
# Requires: xdotool, xwininfo, transset
#
rxvt &
sleep 1s
wid=`/usr/local/bin/xdotool search --class Rxvt | tail -n 1`
/usr/local/bin/xdotool windowfocus $wid &

x=$(xwininfo -id $wid | grep "Absolute upper-left X")
x=${x:25}
y=$(xwininfo -id $wid | grep "Absolute upper-left Y")
y=${y:25}
x=`expr $x + 50`
y=`expr $y + 50`
/usr/local/bin/xdotool mousemove $x $y &
sleep 0.5s
/usr/bin/transset .7 &
/usr/local/bin/xdotool click 1

```

transset and xwininfo are both in the repositories.  xdotool you have to download from the link above.  

I saved the script in ~/bin/myrxvt

EDIT: **Warning:** when using this script, don't move the mouse until rxvt is running and transparent.

---

### Post by canistra on 2008-04-23
I modified this script to use with aterm, but it doesn't seem to work, can you please make it to use with aterm

---

### Post by x1a4 on 2008-04-23
Ensure you don't move the mouse after you run the script.  Remember, it doesn't set transparency, transset does.  Transset requires the user to click the window s/he wants to set transparency for, only here I use xdotool to simulate a mouse click.  It doesn't matter what the application is: rxvt, aterm, wterm etc.  

Also, run the script on the command line and see what errors you get, then post them here.

---

### Post by canistra on 2008-04-24
Nevermind, i have rewriten it to use with aterm, It WorkS !)

```
#!/bin/bash
#
# Requires: xdotool, xwininfo, transset
#
aterm &
wid=`/usr/bin/xdotool search --class canistra@linux ~ | tail -n 1`
/usr/bin/xdotool windowfocus $wid &

x=$(xwininfo -id $wid | grep "Absolute upper-left X")

y=$(xwininfo -id $wid | grep "Absolute upper-left Y")

/usr/bin/xdotool mousemove $x $y &
/usr/bin/transset-df .8 &
/usr/bin/xdotool click 1
/usr/bin/xdotool click 1

```

---

