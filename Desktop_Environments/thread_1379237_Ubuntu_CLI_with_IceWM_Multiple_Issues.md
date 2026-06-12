---
title: "Ubuntu CLI with IceWM: Multiple Issues"
date: 2010-01-12
forum: Desktop Environments
---

### Post by adudutz on 2010-01-12
I've been compiling a customized Ubuntu from a minimal Ubuntu installation. I've managed to set up these things:
[LIST]
[*]Started X
[*]Installed IceWM and partially configuring the taskbar
[*]Installed GTK and some of the applications that depend on it (e.g. Epiphany, PCManFM, XArchiver)
[*]Installed Synaptic
[/LIST]
However, I'm encountering multiple issues with this system:
[LIST]
[*]I tried to get PCManFM to run on startup, but the background shows no sign of it running (PCManFM is used to configure the desktop).
[*]Installed qingy, but no login manager loaded during system boot (it simply came back into bash) (there's an error message related to this; I'll post it later)
PS: I wanted to install SLiM in the first place, but it's not available in the repos (using the Indonesian repo).
[*]Everytime I installed a new program, the Programs folder is autoconfigured in a way that unecessary programs are included (mostly X ones, even bash exists in the folder "Shell"), and it lost its personal configuration (my own configuration through icemc; downloaded the deb file from Debian repo)
[*]I don't know where the PCManFM configuration files are located (to configure the filetypes, implementing GPicView, etc)
[*](Reffering to the point above) how to set GPicView as both the default image viewer? I downloaded and installed from the repo, then tried the FAQ included in the [URL="http://lxde.sourceforge.net/gpicview/"]official website[/URL, but it shows no result in PCManFM. 
[/LIST]

Help will be greatly appreciated. Thanks :)

PS: If possible, I want to replace qingy with SLiM.

---

### Post by adudutz on 2010-01-13
Bump

---

### Post by adudutz on 2010-01-13
another bump..

no replies, anyone? :(

UPDATE:

currently there is no file associations linked with the PCManFM.

---

### Post by Ibidem on 2010-01-30
I did that myself on Lucid (ALPHA software, for testing purposes only, do not use on a production machine, etc.).
Note: to access the .icewm folder in PCManFM, you need to "show hidden" files (<Ctrl>+H or select from the "view" menu) or manually enter the path
To autostart PCManFM, create a text file in ~/.icewm/ named "startup", and add the following text:
```
#!/bin/sh
pcmanfm&
```
Then, make it executable:
In PCManFM, right click the file, "Properties", select "Permissions" tab, select the execute box for yourself, and apply.
Or in the terminal,

cd ~/.icewm
nano startup    #or use your favorite editor to create it
chmod a+x ./startup

Config files are in ~/.config/pcmanfm/
They don't have much for associations...
It's just a guess, but try installing "file".


To get the desktop working right, create a "Desktop" folder:
mkdir ~/Desktop

Your own menu configuration should be saved in ~/.icewm/ as "menu" (start button) and as "programs" (right click).

Are you using Karmic, or an old version like Dapper or Fiesty?
SLiM is in every other version since Hardy, including Lucid.
Not sure where you would get it, if you are, but it has been packaged from what I hear...

Dapper was probably the best version for IceWM, but...

Set as default (might come close to working):
right click on image in PCManFM, select open with..., browse to wherever the binary for gpicview is, select.
To find gpicview, run this in a terminal:
which gpicview
 (probably /usr/bin/gpicview is the binary)

You probably installed xorg for X, which pulls in various extra packages; xinit is enough.

I installed Roxterm for the terminal.
If you're interested, I've written a short script to make few changes...

And if you need to run a program, <Win>+<space> lets you launch a program from IceWM.

Hope this helps, 
Ibidem

---

