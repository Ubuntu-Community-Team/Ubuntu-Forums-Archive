---
title: "I am tired of Konqueror not starting in file management mode!"
date: 2013-04-21
forum: Desktop Environments
---

### Post by fixitdude on 2013-04-21
File Magement mode has two sections, one to the left showing folders and the right shows the files inside folders etc...

This isn't happening anymore as it did on previous versions of kubuntu.

Doesn't work:

konqueror --profile filemanagement

kfmclient openProfile filemanagement

kdesudo -c "konqueror --profile filemanagement"

kdesudo -u myuser -c "konqueror --profile filemanagement"

I always have to go to the menu and select it every time I want to use it.

12.04 LTS updated to latest stuff made sure konqueror is up to date.

Worked fine in previous versions WHY DO THEY HAVE TO SCREW UP EVERYTHING ? Leave it alone!

I am not saying Konqueror doesn't start, it's just not in File Management mode.

And what happened to the clipboard you could paste by clicking right and left mouse buttons at the same time?

And what's with the desktop icons for this new KDE? Mouse over and some lame menu pops up and screws with you, then it will move the icon around if you aren't careful instead of just starting the program, talk about annoying. WHY? Leave it alone!

---

### Post by fixitdude on 2013-04-24
In case someone finds this from google search, the way to get around all the frustration with this new "plasma" silly desktop concept is to install a desktop called "Trinity Desktop". It's KDE done by a bunch of developers that are like me and hate what they did to KDE with this stupid stuff. I think Redmond sent infiltrators over to work on the new KDE plasma to try to mess it up so bad that no one will want to run Ubuntu anymore! It's AWFUL !! (but that's my opinion, I am sure Mac people think it's great, little do they know what life with a great desktop is REALLY like).

So if you are tired of lame things happening on your desktop, try this. (look around the sites)

[http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)
[http://www.trinitydesktop.org/wiki/bin/view/Documentation/UbuntuBinaryInstallation](http://www.trinitydesktop.org/wiki/bin/view/Documentation/UbuntuBinaryInstallation)

I followed the instructions For "Precise [Ubuntu 12.04] LTS (v3.5.13.1)" and it just works!

When you are all done, log out and on the log in screen where it asks for a password you need to choose the "TDE" instead of KDE meaning ""Trinity Desktop Environment". It's a little icon to the left on my computer, look for something that lets you choose what desktop to start with, from then on when you log in you have the TDE !

Everything works like it did in the old desktop and Konqueror is working great in file management mode.

I still can't get my middle click as a PASTE function like before but I ran out of time trying to figure that out, it's got to be some setting I hope because I use that all the time.

So...... - KARMA - if this helped you, please go help someone else with something you know!

EDIT:

To fix the middle mouse button click for PASTE, just install:

sudo apt-get install gpointing-device-settings

Run it from a terminal and select "Middle Button Emulation".

THAT WORKS! I don't know what it does exactly but it works perfectly now and I didn't even have to log in again.

Some developers said "There's not a lot of two-button mice around anymore" and took it out, NOT GOOD GUYS !!! STOP SCREWING WITH WHAT WORKS!

---

