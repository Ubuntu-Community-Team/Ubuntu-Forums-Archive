---
title: "Question for you superkaramba cokers"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by Nythain on 2007-09-18
So i've been working on a modified horizontal superkaramba theme and i've encountered a snag.

Over towards the right side of the screen i have amarok controls and a Clock / Date. Its sized ok to fit most song and album names, but really long ones overflow into the time... this gets sort of annoying so my question to anyone who can answer...

Is there a way to cut off text, so it doesnt go beyond a certain point, like have it just cut off, i would rather lose a word or two on a long album than have it run over into the time... here's the theme if you want to load it and see what i mean, just load up a really long song name in amarok and you'll see
```

############################################################
#   Theme by                   : Rune D'Shyznit
#   Theme date                 : 17 - 09 - 2007
#   Theme version              : 2.0
#   Theme name                 : Unamed (Original work DebianMonitor-Vertical by Jurgen Hatterscheid)
#
# Based on themes by TuxBrothers, Centurion, Jurgen Hatterscheid (original theme I modified)
###########################################################

karamba w=1595 h=75 locked=false interval=500
defaultfont font="squigleyspooge" fontsize=11 color=0,0,0

###########################################################
# System and user info
###########################################################

text x=0  y=0   value="User:"
text x=40 y=0   sensor=program program="echo ${USER}@`hostname`"
text x=0  y=15  value="Distro:"
text x=40 y=15  sensor=program program="cat /etc/issue | awk '{print $1}' | sed 's/Kernel//'"
text x=0  y=30  value="Kernel:"
text x=40 y=30  sensor=program program="cat /proc/version | awk '{print $1, $3}'"
text x=0  y=45  sensor=program program="kde-config --version | grep KDE"
text x=80 y=45  sensor=program program="kde-config --version | grep Qt"
#########################################################
# Proccesor info
#########################################################

text  x=180 y=0  sensor=program program="cat /proc/cpuinfo | grep '^model name' | head -1 | sed -e 's/^.*: //'"
text  x=180 y=15  value="Speed:"
text  x=230 y=15  sensor=program program="echo `cat /proc/cpuinfo | grep '^cpu MHz' | head -1 | sed -e 's/^.*: //'` Mhz"
text  x=180 y=30  value="Cache:"
text  x=230 y=30  sensor=program program="echo `cat /proc/cpuinfo | grep '^cache size' | sed -e 's/^.*: //'`"
text  x=180 y=45  value="Usage:"
text  x=230 y=45  sensor="cpu" format="%v%"
bar   x=275 y=48 path="bar.png" sensor=cpu format="%v"
image x=275 y=48 path="backbar.png"

#########################################################
# Memory and disk usage
#########################################################

text  x=400 y=0 value="RAM:"
text  x=450 y=0 sensor=memory format="%umb / %tm Mb used"
bar   x=400 y=15 path="bar.png" sensor=memory format="%umb"
image x=400 y=15 path="backbar.png"
text  x=400 y=20 value="SWAP:"
text  x=450 y=20 sensor=memory format="%us / %ts Mb used"
bar   x=400 y=35 path="bar.png" sensor=memory format="%us"
image x=400 y=35 path="backbar.png"
text  x=400 y=40 value="Total:"
text  x=450 y=40 sensor=memory format="%um / %tm Mb used"
bar   x=400 y=55 path="bar.png" sensor=memory format="%um"
image x=400 y=55 path="backbar.png"

#########################################################
# Disk usage
#########################################################

text  x=570 y=0 value="Root:"
text  x=620 y=0 sensor=DISK mountpoint="/" format="%f Mb / %up %"
bar  x=570 y=15 vertical=false path="bar.png" sensor=DISK mountpoint="/"
image x=570 y=15 path="backbar.png"
text  x=570 y=20 value="Data:"
text  x=620 y=20 sensor=DISK mountpoint="/data" format="%f Mb / %up %"
bar   x=570 y=35 vertical=false path="bar.png" sensor=DISK mountpoint="/data"
image x=570 y=35 path="backbar.png"
text  x=570 y=40 value="Video:"
text  x=620 y=40 sensor=DISK mountpoint="/data/video" format="%f Mb / %up %"
bar   x=570 y=55 vertical=false path="bar.png" sensor=DISK mountpoint="/data/video"
image x=570 y=55 path="backbar.png"

#########################################################
# Network statistics
#    Replace 'eth1' by the one you are using (eth0,eth1,wlan,ra0,ra1)
#########################################################

text  x=740 y=0 value="IP:"
text  x=770 y=0 sensor=program program="echo `/sbin/ip addr show ra0 | grep 'inet ' | cut -d t -f2 | cut -d / -f1 | cut -b 2-`"
text  x=740 y=15 value="In:"
text  x=770 y=15 sensor=network device="ra0" format="%in kB/s"
text  x=820 y=15 value="Total:"
text  x=855 y=15 sensor=program program="/sbin/ifconfig ra0 | grep 'RX byte' | awk '{print $3 $4}'"
text  x=740 y=30 value="Out:"
text  x=770 y=30 sensor=network device="ra0" format="%out kB/s"
text  x=820 y=30 value="Total:"
text  x=855 y=30 sensor=program program="/sbin/ifconfig ra0 | grep 'RX byte' | awk '{print $7 $8}'"
text  x=740 y=45 value="TCP Connections:" align=left
text  x=860 y=45 sensor=program program="netstat -n | grep -c tcp" interval=2000

#########################################################
# GPU Statistics
#########################################################

text  x=930 y=0 sensor=program program="lspci |grep 'VGA' | sed -e 's/.*: //' "
text  x=930 y=15 value="OpenGL:"
text  x=985 y=15 sensor=program program="glxinfo |grep 'OpenGL renderer string:' | sed -e 's/.*: //' "
text  x=930 y=30 value="Driver:"
text  x=985 y=30 sensor=program program="nvidia-settings -g | grep 'OpenGL version string:' | awk '{print $6}'"

#########################################################
# Amarok Controls
#########################################################

text x=1240 y=0 sensor=program program="dcop amarok player artist" interval=1000
text x=1240 y=15 sensor=program program="dcop amarok player title"  interval=1000
text x=1240 y=30 sensor=program program="dcop amarok player album" interval=1000
image x=1240 y=45 path="back.png"
image x=1270 y=45 path="stop.png"
image x=1300 y=45 path="play.png"
image x=1330 y=45 path="pause.png"
image x=1360 y=45 path="next.png"
clickarea x=1240 y=45 h=25 w=23 preview=false ONCLICK="dcop amarok player prev"
clickarea x=1270 y=45 h=25 w=23 preview=false ONCLICK="dcop amarok player stop"
clickarea x=1300 y=45 h=25 w=23 preview=false ONCLICK="dcop amarok player play"
clickarea x=1330 y=45 h=25 w=23 preview=false ONCLICK="dcop amarok player pause"
clickarea x=1360 y=45 h=25 w=23 preview=false ONCLICK="dcop amarok player next"

#########################################################
# Time and Date
#########################################################

text  x=1595 y=0 sensor=time format="h:mm AP" interval=1000 fontsize=41 align=right
text  x=1595 y=45 sensor=time format="MMMM dd, yyyy" fontsize=16 align=right

```note: you will need a 1600xwhatever or higher resolution to fit it on teh entire screen

---

