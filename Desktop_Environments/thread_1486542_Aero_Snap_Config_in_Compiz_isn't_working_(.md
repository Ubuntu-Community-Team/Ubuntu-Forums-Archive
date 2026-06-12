---
title: "Aero Snap Config in Compiz isn't working :("
date: 2010-05-17
forum: Desktop Environments
---

### Post by Stillmatic on 2010-05-17
Hey guys,

The only tutorial I have found on trying to get Aero Snap type window management in linux is the ubuntu write-up here:
[http://www.omgubuntu.co.uk/2009/11/aero](http://www.omgubuntu.co.uk/2009/11/aero) ... linux.html

I have done everything it says and double checked, but still can't get it to work.

I am using Linux Mint 9 amd64.

Any ideas?

---

### Post by andrea000 on 2010-05-18
Are you using the cube desktop?Aero snap in compiz doesn't work
very well when using the cube.

---

### Post by wilee-nilee on 2010-05-18
The link doesn't work is this what you were trying to post.
[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)
Works fine for me but I don't have any other compiz effects running.

---

### Post by Stillmatic on 2010-05-18
> **andrea000 said:**
> Are you using the cube desktop?Aero snap in compiz doesn't work
very well when using the cube.

Yea, I disabled cube and all and still can't get it to work :(

It's too bad that I can't have both, after disabling dragging windows to other workspaces. 

It's be great to have a manual moving cube w/ snap capabilities

---

### Post by stinkeye on 2010-05-18
This worked for me on karmic and and lucid(64bit) with compiz and the cube.
Did you install wmctrl ?

Run this in the terminal 
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```
If the terminal snaps to the left , you've set up your compiz commands wrong.
If it doesn't snap left, does it give any errors.

P.S. There is an updated version here that snaps only on mouse release.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9190800&postcount=45[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9190800&postcount=45")

---

### Post by Stillmatic on 2010-05-18
> **stinkeye said:**
> This worked for me on karmic and and lucid(64bit) with compiz and the cube.
Did you install wmctrl ?

Run this in the terminal 
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```
If the terminal snaps to the left , you've set up your compiz commands wrong.
If it doesn't snap left, does it give any errors.

P.S. There is an updated version here that snaps only on mouse release.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9190800&postcount=45[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9190800&postcount=45")


I didn't have wmctrl. It's working now. Thank you very much!

---

### Post by rudster on 2011-03-09
mine isnt working either, I have everything setup in compiz correctly and wmctrl is installed.
Im running ubuntu 10.10 gnome desktop edition on my asus 1201 netbook
any ideas that can help? thanks

i also ran this code and it snaps to the left

> WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

---

### Post by Copper Bezel on 2011-03-09
Oh my. That's such an simple solution to the problem I just posted in the other Aero thread. I'm doing that.

Rudster, do you have anything else already assigned to the edge bindings you put in the command boxes?

Edit: I love me these Aero threads, I does. My desktop just got a hell of a lot more convenient to get around. No more right-clicking to maximize vertically! It just does it!

Edit's Edit: I'm finding that it's actually more convenient when set to clicking an edge, rather than just hovering it. It doesn't activate until you let go of the window, anyway.

---

