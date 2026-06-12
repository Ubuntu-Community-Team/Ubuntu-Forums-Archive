---
title: "Logitech Webcam STX does not work in Jaunty 9.04"
date: 2009-04-23
forum: General Help
---

### Post by revelationman on 2009-04-23
Well I though the new kernel would help but it has not the big question will this webcam ever work in Ubuntu 

Here is Lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by yahs on 2009-04-23
I have the same webcam

lsusb output

Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX

Just installed Jaunty for testing and the Webcam works in camorama and cheese but in skype I get a green screen.

This is a quick fix which works for me

open a terminal and type 

LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so skype

I'm still running 8.04 as skype uses v4l1 whereas intrepid and jaunty use v4l2.

You can test your webcam under v4l1 and v4l2 by running gstreamer-properties from a terminal

---

### Post by rayde on 2009-04-23
how do you guys with the Communicate STX modify the settings for it?  I am able to get the camera to load up in Skype, however it is REALLY zoomed in.  skype gives practically no options when it comes to video.

---

### Post by Merk42 on 2009-04-25
My Logitech Communicate STX Webcam isn't working either.  It shows up as a device but won't work in Skype, though it worked in 8.10.

I did a fresh install
also /dev/video0 does not exist on mine.

---

### Post by nomediakings on 2009-04-26
Thanks for this fix yars! I've added 
skype LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so
to my startup programs and everything's working.

---

### Post by spegru on 2009-08-04
The workaround works ok for me from the command line, but I'd like to understand how to make it work automagically for other family members etc.

Strange thing is adding to startup programs like nomediakings said seems to work ok on one PC, but on another with the same OS installed, it doesnt.

On the problem PC I can get it to work OK with the command:
LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so skype
(as yahs said)

But that is different from the preload command:
skype LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so
(as nomediakings said)

[the skype part is at the opposite end of the text string]

On the problem PC, if I execute the nomediakings version with the Skype command at the end, either at command line or startup, I still get a green scratchy camera pic. If I execute the yahs version with the Skype command at the beginning, it's ok. 
However if I try to put yahs version with Skype command at the end into a launcher I get
*There was an error launching the application. Details: Failed to execute child process "LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so" (No such file or directory)*

Why should it behave differently??

On the other non problem PC the nomediakings version with the skype command at the beginning, the camera works fine either as a launcher or at startup

Odd...........:confused:

---

### Post by spegru on 2009-08-04
Answering my own question......

I'm guessing that the problem with the launcher is that the required file is not in the path from the Desktop.

However all of this is avoided if the preload is launched system wide at startup

I found this link [http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/](http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/) which explains. 
Basically, tha answer is to install preload-manager from the repositories
full name: ld.so.preload-manager
Then get it to preload the V4l compatibility layer using the command
sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so

After that everything works fine, from launcher, applications, cli - whatever and it's OK for the family 
:popcorn:

---

### Post by spegru on 2010-02-04
In 9.10 Preload Manager seems to be missing.
I think you can get the system to use the v4l compatibility with export command but I havnt found a way to make that automatic
Any ideas?

---

### Post by spegru on 2010-02-06
Well answering my own question a bit again

First you can still get preload-manager, but it doesnt fix the webcam problem now

You can start skype with a working webcam in two ways I found so far

LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so skype

or (on two lines)

export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so 
skype

However if I install preloed manager from here
[http://packages.ubuntu.com/dapper/admin/ld.so.preload-manager](http://packages.ubuntu.com/dapper/admin/ld.so.preload-manager)
and install the v4l1compat like this
sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so
it adds v4l1compat.so to the startup - but then when you start skype the camera is completely missing!

Help. I am just trying to add compatibility layer automatically

---

### Post by spegru on 2010-02-09
Well I think this will be my last post on this thread as no-one else seems to be here.
So I fixed it again. Preload manager does not seem to do the job any more in 9.10/mint8 even though you can get it (not from the repo)

Note that I tried lots of other ways of achieving the same thing but this is the only one I found that works from the menu.

I created a script by simply creating a new plain text document (using gedit or whatever) simply called 'skyper' in my home directory.
Inside this text file I put the simple command  
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I changed the properties of skyper so that it is executable.

I then edited the skype entry in the menu (by a right click on menu and choose edit menu - for Mint8 - I cant quite remember what that is in ordinary Ubuntu 9.10 but it's probably very similar) so that instead of running skype, it now runs /home/stephen/skyper
(Of course you would have to change stephen to be your own user name)

So when you press the button, it runs skyper, which in turn runs skype with the preload command. It works and the cam is fine.

Note that I had to reboot before the modded menu would take effect. 

bye now...........

---

