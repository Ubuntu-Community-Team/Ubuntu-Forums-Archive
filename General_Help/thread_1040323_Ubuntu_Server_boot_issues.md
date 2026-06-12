---
title: "Ubuntu Server boot issues"
date: 2009-01-15
forum: General Help
---

### Post by drkoop81 on 2009-01-15
[SIZE="4"]I recently did an update to my webserver running 6.06 lts on a g5 xserve. I left and returned this morning to a blank screen and no websites. I tried to restart thinking that it could be frozen on restart and as I was getting most of the normal screens I thought ok good to go. After it selected to boot linux kernel my monitor goes blank and says no signal and just sits there. Normally I get my login screen after a second. (side note I installed desktop on server edition)

So I have a frozen server with websites stuck on it. Can't do anything. I tried to repair from live cd and it gives me all sorts of trouble with video saying xorg is not configured. I try to configure with reconfigure command and it doesn't work. 

What is weird is that after the screen goes blank I try to get to the terminal with alt-f2 and the monitor lights go on but no screen. I am stumped I guess. Any takers? [/SIZE]

---

### Post by Titan8990 on 2009-01-15
Have a look at the following from the liveCD:


/var/log/messages

/var/log/dmesg

/var/log/syslog

---

### Post by drkoop81 on 2009-01-15
I guess I could with vi. The live cd only give me terminal access because of the problems with x. I get this wierd blue screen with a bunch of characters on it asking if I want to view the x output or errors. This is very strange.

---

### Post by Titan8990 on 2009-01-15
I would just use:

cat /var/log/messages | less

OR save to a file on a thumb drive to view later:

cat /var/log/messages > /media/THUMDRIVE/messages.txt


If you really want to use a text editor, I would go with nano:


nano -w /var/log/messages


There shouldn't be a GUI anyways...

---

### Post by drkoop81 on 2009-01-15
I did install the desktop with it. It really is just an experiment server with just one site I need off it. Of course this happens the morning I am going to move everything off it. 

I went through the log messages and only found a couple things. Basically it must be some sort of video card problem I think. I saw a couple of "device not found" and unsupported this and thats. 

I am using an old video card from a g3 in the pci slot of the xserve. It was working fine yesterday. But there must be some driver error or problem during the update. Can I just update the desktop version and get the driver support from 8.04 or something?

---

### Post by Titan8990 on 2009-01-15
Drivers are modules that are typically built with the kernel.

I have no clue what driver that kind of card will use but it should be defined in:

/etc/X11/xorg.conf


Apache has no GUI, why the need for the desktop? This is exactly the reason that desktops are not installed on Servers. You open up a whole new world of problems when adding graphics.

---

### Post by drkoop81 on 2009-01-15
I just need to familarize myself with the linux file system graphically I guess. I am a visual learner. 

Plus I have a huge forehead like a drive in movie theatre. :P

---

