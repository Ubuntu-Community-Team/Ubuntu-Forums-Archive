---
title: "how? wider net/cpu panel plasma widgets"
date: 2010-07-19
forum: Desktop Environments
---

### Post by betlog on 2010-07-19
I would like ot make the plasma widgets for CPU and network wider, so that I can see a larger section of their history.
How?

---

### Post by betlog on 2010-07-19
I dont get it.. is the size of these things hardcoded into the widget?
They seem to force a 1:1 scaling no matter what
I guess there are various reasons for doing that.. but it's pretty damn annoying when even editing stuff directly doesnt allow minor changes to be made.

Sigh, after initial excitement about useful looking widgetry.. somehow I always end up discarding widgets because of their lack of customization and therefore lack of functionality... but now that I have tried to do it via direct edits i am even more annoyed at the whole widget concept... what a tease!

Someone please tell me I am wrong  and it is possible to make simple changes like this.
..please

gksu kate ~/.kde/share/config/plasma-desktop-appletsrc
(just the relevant bits)
```

[Containments][222]
activity=
desktop=-1
formfactor=2
geometry=0,-923,767,128
immutability=1
location=4
plugin=panel
screen=0
zvalue=150

[Containments][222][Applets][223]
geometry=6,6,256,122
immutability=1
plugin=sm_cpu
zvalue=0

[Containments][222][Applets][223][Configuration]
Share=true
cpus=cpu/system/TotalLoad
interval=2

[Containments][222][Applets][223][LayoutInformation]
Order=0

[Containments][222][Applets][224]
geometry=138,6,256,122
immutability=1
plugin=sm_net
zvalue=0

[Containments][222][Applets][224][Configuration]
Share=false
interfaces=network/interfaces/eth0/transmitter/data
interval=2

[Containments][222][Applets][224][LayoutInformation]
Order=1

[Containments][222][Configuration]
maximumSize=767,101
minimumSize=767,101

```

---

