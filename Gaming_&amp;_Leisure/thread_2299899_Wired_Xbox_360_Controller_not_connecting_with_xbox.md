---
title: "Wired Xbox 360 Controller not connecting with xboxdrv"
date: 2015-10-22
forum: Gaming &amp; Leisure
---

### Post by Christopher_Childs on 2015-10-22
Hi, 
So I am trying to connect my wired 360 controller with xboxdrv with steam so I can use it. I have been trying for a few days and can't seem to get it to work. I have blacklisted xpad with my text editor, and here is what happens when I run xboxdrv 

xboxdrv
xboxdrv 0.8.5 - [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 


Controller:        Joytech Neo-Se Take2
Vendor/Product:    162e:beef
USB Path:          002:003
Controller Type:   Xbox360
Segmentation fault (core dumped)

It keeps saying segmentation fault core dumped, and the xbox 360 controller just keeps trying to connect, and can't. Any help with this would be greatly appreciated. 
Thanks

---

### Post by Chris on 2015-10-22
The first thing I would do is try the [latest version]("https://github.com/xboxdrv/xboxdrv") from git (this is the 0.8.6 WIP). There have been quite a number of patches over the last 2+ years. I have no idea why he hasn't released the newer version.

You will have to compile it from source. Alternatively, there is at least one fork that has a ppa but I don't know its status compared to the main version. [https://github.com/raelgc/ubuntu_xboxdrv](https://github.com/raelgc/ubuntu_xboxdrv)

---

