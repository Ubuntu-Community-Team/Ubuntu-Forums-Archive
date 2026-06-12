---
title: "Need help finding these dependences for RealPlayer"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Optimal Aurora on 2005-04-22
I was trying to install realplayer and I converted the .bin file to an executable file, but when I ran it as myself and sudo it stated the following

 sudo ./RealPlayer10GOLD.bin
Some required libraries seem to be missing from your system.  Installation
can continue without them, but you will be unable to run the HelixPlayer
without them.  You will need to install them (or if they are already present
you may simply need to update your system's library paths or LD_LIBRARY_PATH
environment variable.
        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)
continue with installation? [y/n]:

When I continue on it will load successfully, but even put the icon in the Kmenu but when I go to run it... It shows the busy bouncing Realplayer icon, then it after about 30 secs it wouldn't be loaded  ](*,) and their is nothing in the taskbar or system tray that indicates its running or even a window on the screen that indicates that it started. 

Where can I find those dependency files at? 

Thanks Optimal...

---

### Post by raid517 on 2005-04-22
So you have never heard of apt-get or synpatic?

Try reading a little about them on google.

Basically - I shouldn't really do this as it rather demonstrates that you haven't bothered to read anything - but anyway at the command prompt do,

sudo apt-get update
sudo apt-get install synaptic,
synaptic

then do a search in both the name and description field for any file providing those dependancies.

Then do a search here and read as much as possible on the web about apt-get. Without apt-get, you really probably shouldn't be using Kubuntu/debian - as that is pretty much the whole point of it.

GJ

---

### Post by Optimal Aurora on 2005-04-23
No offense but I have been using linux for a long time especially fedora with apt4rpm, so I know but when I do that I get this

                                             $ sudo ./RealPlayer10GOLD.bin
Some required libraries seem to be missing from your system.  Installation
can continue without them, but you will be unable to run the HelixPlayer
without them.  You will need to install them (or if they are already present
you may simply need to update your system's library paths or LD_LIBRARY_PATH
environment variable.
        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)
continue with installation? [y/n]: n
                                        sudo apt-get install gtk+ 2.0   
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtk
                                        sudo apt-get install libgtk-x11-2.0.so
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-x11-2.0.so

So where can I find these files at...

---

### Post by raid517 on 2005-04-23
They may be listed under slightly different names. Which is why I told you to use synaptic to search.

If you had followed my instructions, including the part about synaptic you would have solved this aready. Please at least make some effort to read.

It isn't so hard.

GJ

---

### Post by Optimal Aurora on 2005-04-23
well doing it that way it says that I have libgtk1.0-0 and the same for lib----1.0.-0 etc..., but even when I install all of the libgtk or what ever the case may be, I can't get it to load still...

Later...Optimal...

---

### Post by phillygirl on 2005-04-24
Synaptic only assist in installing version 8 of RealPlayer.  I downloaded from [www.real.com](www.real.com), which now has version 10.  Read the installation instructions, which were very simple but I still couldn't get it to work.  I read in another site that if your running debian to remove the swf files in the plugins dir.  After I did this realplayer ran.   \\:D/

---

### Post by Nis on 2005-04-24
Try
```

sudo apt-get install libgtk2.0-0 libpango1.0-0 libatk1.0-0

```

---

