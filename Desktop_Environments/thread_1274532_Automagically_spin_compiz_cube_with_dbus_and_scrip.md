---
title: "Automagically spin compiz cube with dbus and script?"
date: 2009-09-24
forum: Desktop Environments
---

### Post by akaione on 2009-09-24
Hello hello Ubuntuforums :-)

I have for more than a year been trying to get back a function I found quite pleasing in Ubuntu 7.04 and 7.10 - A scripted way of making the compiz cube spin by using crontab et.al.

I did this by doing code such as:

```

/usr/bin/dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/rotate/allscreens/rotate_left org.freedesktop.beryl.activate string:'root' int32:0x1a5
sleep 2
/usr/bin/dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/rotate/allscreens/rotate_left org.freedesktop.beryl.activate string:'root' int32:0x1a5 

```

..etc.

Since Hardy (8.04) I have (because of the merge of compiz,beryl, etc) not been able to track a way to do this. 

Are anyone aware of a way, even perhaps more elegant to do this?


--
All the best,
Anders "akai" Kringstad

---

### Post by Giblet5 on 2009-09-24
You're close. Beryl merged with compiz and is now compiz-fusion.

The names were changed to confuse the distracted. :)

Here's an [archived forum discussion]("http://ubuntuforums.org/archive/index.php/t-612358.html") on the topic.

Edit: their script doesn't work.

And, Avant (AWN) does it from C++ if you need a better way.

---

### Post by Giblet5 on 2009-09-24
The information provided on [this page]("http://sfyang-en.blogspot.com/2008/02/rotate-cube-in-compiz-with-wmctrl.html") works on Jaunty.

For simplicity sake:

Install wmctrl:
```
sudo apt-get install wmctrl
```

Create a script (eg, compiz-rotate) that contains:
```
#!/bin/bash
#
# compiz-rotate-wmctrl - Rotate the cube using wmctrl
#
# Author: Shang-Feng Yang
# Released under GPLv3

VER="1.0"


function rotate() {
  # The target face number (begins with 0)
  TVPN=$(( $1 % ${NF} ))

  # The X coordinate of the target viewport
  TVPX=$(( ${TVPN} * ${WW} ))

  # Change to the target viewport
  wmctrl -o ${TVPX},0
}

function usage() {
  echo -e "$(basename $0) v${VER}\n"
  echo -e "Usage:\n"
  echo -e "\t$(basename $0) {left|right|#}\n"
  echo -e "\tWhere:\n"
  echo -e "\t\tleft - rotate the cube to the left"
  echo -e "\t\tright - rotate the cube to the right"
  echo -e "\t\t# - rotate to #th face (begins with 0)\n\n"
  echo -e "Author: Shang-Feng Yang <storm dot sfyang at gmail dot com>"
  echo -e "Released under GPLv3"
}

# The action to be performed. $ACT could be 'left' or 'right' to rotate
# left or right, accordingly. $ACT could also be the number of the face
# to rotate into.
ACT=$(echo $1 |tr '[A-Z]' '[a-z]')

[ "x$ACT" == "x" ] && { usage; exit 1; } || {
  case $ACT in
    left|right|[0-9]|[0-9][0-9])
      ;;
    *)
      usage
      exit 1
      ;;
  esac
}


# The informations about the desktop
INFO=$(wmctrl -d)
# The width of the desktop
DW=$(echo "${INFO}"| awk '{sub(/x[0-9]+/, "", $4); print $4}')
# The width of the workarea
WW=$(echo "${INFO}"| awk '{sub(/x[0-9]+/, "", $9); print $9}')
# The number of faces on the cube
NF=$(($DW/$WW))
# The X coordinate of the viewport
CVPX=$(echo "${INFO}" |awk '{sub(/,[0-9]+/, "", $6); print $6}')
# Current number of the face in all faces (begins with 0)
CVPN=$(( ${CVPX} / ${WW} ))

[ "$ACT" == "right" ] && {
  ACT=$(( ${CVPN} + 1 ))
} || {
  [ "$ACT" == "left" ] && {
    ACT=$(( ${CVPN} - 1 ))
  }
}

rotate ${ACT}
```

Make it executable via ```
chmod 755 compiz-rotate
``` and execute it via:

```
./compiz-rotate right | left | face#fromzero
```

Don't thank me, thank S.F.Yang's blog...

---

### Post by akaione on 2009-09-30
> **Giblet5 said:**
> ```
./compiz-rotate right | left | face#fromzero
```

Don't thank me, thank S.F.Yang's blog...

Actually, I'll thank you for pointing me in the right direction :)
It works brilliantly for left and right moves. How to make it turn also onto the bottom and skycaps I have yet to figure out.

Any pointers on those would be very much appreciated!

Again, thanks for the pointers, and a big thanks to S.F. Yang!

---

### Post by juako on 2011-01-04
Sorry to revive if it's a too old thread, but i'm looking to expand on a script i wrote a few months back based also on wmctrl. I want to make it to use dbus instead to juice out more of compiz.

[http://www.linuxquestions.org/questions/programming-9/bash-script-for-automatic-viewport-changing-and-other-wm-stuff-works-with-compiz-838827](http://www.linuxquestions.org/questions/programming-9/bash-script-for-automatic-viewport-changing-and-other-wm-stuff-works-with-compiz-838827)

Features automatic rotation, relative/absolute viewport changing, bidirectional wrap-around, and a little read eval loop over a fifo to listen for commands.

What i need is rotate the cube (maybe set a distance too while autorotating), and being able to stop, go to a specific viewport, resume rotation, change speed/distance etc dynamically. Tought first on writing a plugin but this is quicker and maybe more easy to integrate with other stuff.

Hope you enjoy it, if someone has dbus based shell code i'd greatly appreciate it if you let me check it out. I'm collecting more info (have to work on this today).

---

