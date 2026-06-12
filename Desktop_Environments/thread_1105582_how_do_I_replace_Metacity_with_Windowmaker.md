---
title: "how do I replace Metacity with Windowmaker?"
date: 2009-03-24
forum: Desktop Environments
---

### Post by rick71 on 2009-03-24
Can anyone give me directions on how to replace Metacity with Windowmaker?

For now :
Change Metacity to normal in Sessions, and set Nautilus to not draw the desktop. Then I kill metacity and start windowmaker with "killall metacity && wmaker" from within the run application applet. However, I can't get this configuration to stick between logins.

When I use "wmaker --replace" I get the following:
"/usr/lib/WindowMaker/WindowMaker/invalid argument: '--replace' "

Any and all help appreciated.

---

### Post by kerry_s on 2009-03-25
i think it would be easier to use wmaker and add the gnome stuff you want. for example put>

gnome-panel &

in the wmaker startup.

---

### Post by rick71 on 2009-03-25
> **kerry_s said:**
> i think it would be easier to use wmaker and add the gnome stuff you want. for example put>

gnome-panel &

in the wmaker startup.

I can do that, but then "Gnome" wouldn't be running. For instance, I wouldn't be able to browse Samba shares from Nautilus.

If I could get fusesmb to work properly under WindowMaker, I wouldn't nee Gnome, but that's a subject for a different thread. :-)

---

### Post by kerry_s on 2009-03-25
> **rick71 said:**
> I can do that, but then "Gnome" wouldn't be running. For instance, I wouldn't be able to browse Samba shares from Nautilus.

If I could get fusesmb to work properly under WindowMaker, I wouldn't nee Gnome, but that's a subject for a different thread. :-)

that does not make since. you can use nautilus and samba in any de or wm. all you have to do is look in your gnome session startup and start the same things in your wmaker startup.

better yet make sure it's setup right:
[https://help.ubuntu.com/community/FuseSmb](https://help.ubuntu.com/community/FuseSmb)

google it> [http://ubuntuforums.org/showthread.php?t=525736&highlight=fusesmb](http://ubuntuforums.org/showthread.php?t=525736&highlight=fusesmb)

xSMBrowser sounds nice and no nautilus needed.

---

### Post by rick71 on 2009-03-25
I'll take a look at xSMBrowser. I think I have pyNeighborhood working. It is looking to me like I have to exit pyNeighorhood, restart it and change username/passwords if they are different on different machines. I will have to play with it, but so far, I have shares from 3 different machines that need 2 different passwords mounted. I haven't tried to move any files yet, but I have hope.

Also, in reading various forums, it seems like there are a lot of people that have problems with fusesmb.

Thanks for the info.

---

### Post by rick71 on 2009-03-25
pyNeighboorhood is no longer working. I get "Failed to scan" when scaning from the left/global pane. If I add machines in the right pane, I get "Failed to mount". After I had pyNeighborhood working, I removed fusesmb. I don't think that shoud have made a difference, but pyNeighborhood isn't working now.

---

### Post by rick71 on 2009-03-25
I have been able to mount shares, unmount shares, delete files over several reboots. I changed one thing. I removed sudo from the smbmount and smbumount commands. All the directions I have read have said to either add the sudo command, or to use gksu to start pyNeighborhood. Things are looking up :-)

It looks like I can try build a physical machine from Hardy Server as opposed to the VM I've been practicing on.

---

### Post by mcduck on 2009-03-26
To change the window manager in Gnome open Gconf-editor (hit Alt-F2 and run "gconf-editor). Then browse to desktop/gnome/sesssion/required_components and change the valune of "windowmanager" to wha ever you want to use.

---

### Post by rick71 on 2009-03-26
> **mcduck said:**
> To change the window manager in Gnome open Gconf-editor (hit Alt-F2 and run "gconf-editor). Then browse to desktop/gnome/sesssion/required_components and change the valune of "windowmanager" to wha ever you want to use.

I don't see session in desktop/gnome.

---

### Post by rick71 on 2009-03-26
I think I have been able to replace Metacity with WindowMaker. IN gconf-editor: desktop/gnome/applications/window_manger I have put /usr/bin/wmaker in both current and default. So far, WindowMaker starts as the default window manager.

---

