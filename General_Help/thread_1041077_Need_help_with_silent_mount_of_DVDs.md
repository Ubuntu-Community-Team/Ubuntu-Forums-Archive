---
title: "Need help with silent mount of DVDs"
date: 2009-01-16
forum: General Help
---

### Post by tehchad on 2009-01-16
Well, I thought this would be pretty simple, but here I am :(. I really hope it's something simple that I'm missing. I'm running Kubuntu 8.04 pretty much out of the box. 

**GOAL:** When I insert a disk, I just want the contents mounted to /media/cdrom0. No prompts, no pop-ups, just automount whatever I put in the tray to /media/cdrom0. I would think this would be pretty common since why would I put in a disk that I don't want mounted, but again here I am :(

**HOW IT CURRENTLY WORKS:** When I insert a data DVD into the disk, the dvd icon shows up on the desktop and then a window pops up and asks me what I want to do with media type "unmounted DVD", and my choices are "open in new window" and "do nothing". Do nothing does exactly what it says, DVD is still unmounted. "Open in new window" mounts the disk, but I don't want the new window opened up (I don't even really want to be prompted). There is no option for "just mount the thing and be quiet about it"

**WHAT I'VE TRIED:** I figured if there is no option for it, I'd make one, hoping that if I make it the default action for "unmounted DVD" that I wouldn't be prompted and the disk would just be mounted. Opened up kcontrol and found the area to make new actions for a media type, created my mount command, assigned it to "unmounted dvd" and it *ALMOST* works (command I'm currently using is **"/bin/mount /media/cdrom0 -o unhide**", I've tried many other ways, but if you have suggestions here that will get this to work, I'm open)

After I insert the disk, I get an error saying "**/media/cdrom0 is a folder, file expected**", once I click through it everything is ok, disk is mounted, but I can't get rid of that error pop-up when it does my mount command. After some searching I found something about adding "%u" to the end of the command. I tried that and then I didn't get the error msg, but the mount just didn't work at all :(.

**WHY THAT PROMPT/ERROR IS A BIG DEAL:** I'm trying to make an xmbc box, so it runs without a keyboard/mouse, just lirc remote for input when xbmc is running. When I drop a DVD with a bunch of avi files on it into the drive, the window manager breaks into xbmc with the prompt (or that error with my current setup) and then I have to fire up synergy on my laptop, mouse to that server and click OK before it goes away. Very annoying, and that is why I just want whatever I drop in to be auto-mounted to /media/cdrom0 silently. Once it's mounted xbmc will pick it up and I can browse/play conent.

Sorry for the book, but this is really the last thing that's holding me up. Of all the things I've had to solve to get to this point, I never thought this would be the stumper. Hope you guys can help. Thanks for your time.

---

### Post by tehchad on 2009-01-16
Forget it. I'm tired of fooling around trying to get KDE to do what I want. Grabbed [ivman]("http://ivman.sourceforge.net/") from the repositories and just turned off kde prompting altogether. Gave me exactly what I'm looking for. Disks mounted sliently, no fuss, no muss. Works great for a media box.

---

