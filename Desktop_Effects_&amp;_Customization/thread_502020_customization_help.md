---
title: "customization help"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by p3ngu1n on 2007-07-16
i am an ex-windows user gone linux and i still have a couple questions. when i look at some tutorials with images, it shows on their desktop a realy cool thing that shows the computer info and prosesses and stuff. but its ON the desktop. how do i do that?

---

### Post by andrewsomething on 2007-07-16
> **p3ngu1n said:**
> i am an ex-windows user gone linux and i still have a couple questions. when i look at some tutorials with images, it shows on their desktop a realy cool thing that shows the computer info and prosesses and stuff. but its ON the desktop. how do i do that?

It sounds like you're talking about Conky. I don't use it, but if you search the forums for it there are tons of posts about it. You could also use screenlets or gDesklets if you want to look more like the Vista side bar or Mac Dashboard. Both have system monitors.

---

### Post by derby007 on 2007-07-16
To see PC info: open a terminal and type in some of the commands in the shell script below:
ie. grep "MemFree" /proc/meminfo
or: cat /proc/meminfo
Note: u can save all the text below in a file & call it pcinfo.sh and run it in a terminal:  ./pcinfo.sh
If u want it on your desktop, then i suppose copy/paste the o/p into a .png file & save it as ure background !!

#!/bin/bash
#####
##### iphitus' screenshot script :D
#####
#####RENAME THIS FILSE EXTENSION FROM .txt to .sh
#####-edit as needed
#####-execute from a terminal or run dialog with
#####sh info.sh

# screenshot dir
ssdir="$HOME/"
# screenshot description
ssdesc="$HOME/"
# screenshot format
ss=`date +%d%m%Y`.png

# Extra hdd details?
hdddetails=0
# Use comments file?
comments=0
# Automatically grab gnome theme info
autognome=1

#echo
#date
echo
echo "Kernel: `uname -r`"
#echo "Distro: `cat /etc/*release`"
source /etc/lsb-release
echo "Distro: $DISTRIB_ID $DISTRIB_RELEASE $DISTRIB_CODENAME"
echo "Uptime: `uptime |cut --delimiter=" " -f 2`"
echo ___________________________________________________________________
echo "CPU: `grep "model name" /proc/cpuinfo|cut --delimiter=":" -f 2`" 
echo "Speed: `grep "cpu MHz" /proc/cpuinfo|cut --delimiter=":" -f 2` mhz"
echo "Bogomips: `grep "bogomips" /proc/cpuinfo|cut --delimiter=":" -f 2` bogomips"
echo ___________________________________________________________________
let memtotal=`grep "MemTotal" /proc/meminfo|cut -c 12-22|indent -i0`/1024
echo "Memory Total: $memtotal mb"
let memfree=`grep "MemFree" /proc/meminfo|cut -c 12-22|indent -i0`/1024
let memcache=`grep "Cached" /proc/meminfo|cut -c 12-22|indent -i0`
let memcache=$memcache/1024
let memfreetotal=$memfree+$memcache
echo "Memory Free: $memfreetotal mb"
echo ___________________________________________________________________
#echo "Graphics: `grep "Product" /proc/fb0/vbe_info|cut --delimiter=" " -f 5`" 
cat /proc/driver/nvidia/version
echo ___________________________________________________________________
if [ $autognome == 1 ]; then
echo "GTK2: `gconftool-2 --get /desktop/gnome/interface/gtk_theme`"
echo "Metacity: `gconftool-2 --get /apps/metacity/general/theme`"
echo "Icons: `gconftool-2 --get /desktop/gnome/interface/icon_theme`"
# echo "Titlebar Font: `gconftool-2 --get /apps/metacity/general/titlebar_font`"
echo "Application Font: `gconftool-2 --get /desktop/gnome/interface/font_name`"
echo "Terminal Font: `gconftool-2 --get /apps/gnome-terminal/profiles/Default/font`"
fi
sleep 2
import -window root $ss
echo
exit 0

---

### Post by hyperair on 2007-07-16
What exactly does that script do? Anyway I use GKrellM and I really like it. Why don't you go take a look? [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

To install it in Ubuntu, here's the command:
```
sudo apt-get install gkrellm
```

---

### Post by notwen on 2007-07-16
This is indeed conky.  Installation is as easy as opening a terminal and entering the following command
```
sudo apt-get install conky
```
then type the following command to launch conky
```
conky
```

You can view other ppl's conky configs at this [thread]("http://ubuntuforums.org/showthread.php?t=281865").

[Here is the conky homepage]("http://conky.sourceforge.net/"), it has a little bit of everything. Documentation, installation and some screenshots.  Have fun w/ conky, I have 3 conkys running on my desktop at all times.  It can be a fun thing to customize and make your desktop look nice.  Good luck. =]

---

### Post by hyperair on 2007-07-16
Someone should make a GUI for configuring conky. It sure beats configuring that conkyrc file. Anyway, what's double buffering? It seems that conky on my system refuses to support it. Any workarounds?

---

### Post by chuckyp on 2007-07-16
Yeah to get Double Buffer to work you need to load the dbe module in your xorg.conf.  Go in there and edit it.  Its near the top of the file under modules you need a line reading 
Load     "dbe"

Then restart X you should be good to go.

---

### Post by hyperair on 2007-07-16
Ok, thanks. What exactly is double buffering anyway?

---

### Post by notwen on 2007-07-16
Double buffering would prevent the flickering you're likely seeing in your conky w/ single buffering.

---

### Post by hyperair on 2007-07-16
Yeah I knew that much, I wanted to know what it does exactly, and how it stops the flickering.

---

### Post by notwen on 2007-07-16
> Name
DBE - Double Buffer Extension
Synopsis
The Double Buffer Extension (DBE) provides a standard way to utilize double-buffering within the framework of the X Window System. **Double-buffering uses two buffers, called front and back, which hold images. The front buffer is visible to the user; the back buffer is not. Successive frames of an animation are rendered into the back buffer while the previously rendered frame is displayed in the front buffer. When a new frame is ready, the back and front buffers swap roles, making the new frame visible. Ideally, this exchange appears to happen instantaneously to the user, with no visual artifacts. Thus, only completely rendered images are presented to the user, and remain visible during the entire time it takes to render a new frame. The result is a flicker-free animation.**

Obtained from [here]("http://linux.die.net/man/3/dbe").

---

### Post by hyperair on 2007-07-16
Cool. Thanks. =) Considering it came from that site, I just realized that "man dbe" would give the same explanation. After all, that site is a web based version of the man pages.

---

### Post by notwen on 2007-07-17
You're welcome.  Man pages should always be one of your first reference checks for all linux related things. =]

---

### Post by hyperair on 2007-07-17
Yeah, I still haven't gotten used to it even after one year of using Ubuntu.

---

### Post by Shakkaa on 2007-07-18
Conky gives you stats about your system....depending on which ones you want is up to you.  As to how you can take off the flickering, well you need to enable double buffering and that should solve your issue.....use the examples use the examples of other people so you can see how to do that by the thread provided to you above :)

---

