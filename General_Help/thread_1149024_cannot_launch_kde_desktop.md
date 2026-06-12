---
title: "cannot launch kde desktop"
date: 2009-05-04
forum: General Help
---

### Post by dtw1247 on 2009-05-04
Help, new to linux-ubuntu.  Just got a new Asus eeepc1000.  Never used a terminal before to type in commands.   After many hours I figured out how to get Konqueror, Kcontrol, and synaptic.   Synaptic shows me that  kdedesktop and gnome are installed or at least exist somewhere on the computer  butr I cannot get the kde window.  I have tried dozens of commands like startx,  start kde,  start kdesktop etc.  I have tried every command anyone has recommended on any forum. I`m sure,  me being ignorant, there is a simple solution.  Remember I am new at this so any advice must be specific,  make no assumptions.  Thanks for any help.
                                   Dennsi

---

### Post by pastalavista on 2009-05-04
When you first log on, click the little red icon on the logon screen and select session. It should give you a choice (if you installed kubuntu-desktop) to run a KDE session.

---

### Post by dtw1247 on 2009-05-05
Thanks for reply.    I have Ubuntu,  there is a little red circle in the upper right corner which is for help,  and one in the lower right corner which is for shutting the computer down.   Kubuntu may have  an icon for KDE desktop but I don`t think I do.  What I do have is a little white home icon in the lower left hand corner and when I put the arrow on it, it says show  desktop but nothing happens.  I have a feeling this is supposed to give me the desktop but it doesn`t.  I have done a system restore and thought that might correct it , but it didn`t.  Isn`t there something to type in the terminal that can get me the KDE desktop? Or can I use the cd to get it?  
                                                            Thanks

---

### Post by pastalavista on 2009-05-05
No, I mean the screen where you enter your user name and password (the log-on screen)... sorry I wasn't clear. It says 'Options' on mine in the lower left corner. It gives the options to shut down, suspend, hibernate, etc. plus _Select Session_.. which is the one you use to select KDE if it is installed.```
sudo apt-get install kubuntu-desktop
``` or find it in Synaptic. Sorry for the confusion.

---

### Post by pastalavista on 2009-05-05
I think you can do it in terminal if you're logged on, but I haven't tried it...
the only other desktop I ever tried was 'Enlightenment' which I was just curious about.. didn't like it. 

Try:```
killall ubuntu-desktop && kubuntu-desktop
```

I don't think you need sudo...

edit: nope.. tried it doesn't work. You'll have to do it at the log-on screen

---

### Post by dtw1247 on 2009-05-05
Again thanks for all the help but nothing works,  its driving me crazy.  My login screen on bootup only has  space for my password and nothing else,  maybe kubuntu has a different startup screen then Ubuntu.  My shut down screen after I log on has shutdown, restart, standby and taskmgr,  but no sessiions.  Synaptic says kde desktop and gnome are installed.  When I use sudo kdesktop is says it is already runnig.    Get this when I type sudo apt-get install ubuntu-desktop-kde3 it says it can`t find file,  a contradiction. Just tried sudo apt-get install kubuntu-desktop annd got same message,  cannot find file.   Remember I have Ubuntu not Kubuntu,  I quess there is differnce.  I have just spent 20 hours looking(really) for my lost desktop and I am discouraged.  I do have that little home icon in the lower left hand corner that says show desktop when I left click but nothing happens.  I think thats the answer,  that icon is not responding but I do not know how to fix it.   I did mention I did a restore and loaded all updates.  Thanks agin.

---

### Post by pastalavista on 2009-05-05
That is odd. I use Ubuntu also with gnome and in all the versions, 9.04 included, there has been an icon in the lower left corner of the logon screen that says "Options". This is BEFORE you log on. I don't know what else to tell you...

maybe someone else might know what's happening so...

BUMP

---

### Post by dabl on 2009-05-05
Kubuntu (KDE Desktop) uses the K Display Manager (KDM) and Ubuntu (Gnome Desktop) uses the Gnome Display Manager (GDM).  So, when you boot your system, if it gets to the Ubuntu login GUI, it is already running GDM and you can't start KDE on GDM.

If you can Alt-F1 to a tty console, and issue ```
sudo /etc/init.d/gdm stop
``` that will stop GDM.  Then issue ```
sudo /etc/init.d/kdm start
``` and that should start KDE, if everything was correctly installed.

---

### Post by dtw1247 on 2009-05-06
Thanks for all the replies.  I tried the  stop/kdm and start/gdm commands and it said it could not find file.  I tried  two restores from F9 at start up,  but I think I do not have a good installation on the computer now.  I am going to try to install os from the disk and see if that helps,  otherwise download the new kubuntu 9.05 and install that.  By the way,  when you downlaod a new updated OS like Kubuntu 9.05 and it says to copy to a cd,  can you also use a jump drive instead of a cd?
                                          Thanks all

---

### Post by pastalavista on 2009-05-06
The easiest way to make a USB flash drive distro installer is with [Unetbootin]("http:unetbootin.sourceforge.net"). It will download and install to a thumb drive automatically.

---

### Post by lil_rich on 2009-05-08
Although I can't help with your problem of starting KDE, I can tell you that your "show desktop" button is not the solution. All that button does is minimise any windows you have open.

Good luck with the rest, though.

P.S. This isn't an ASUS specific version of Ubuntu is it? I've heard that sometimes the netbook versions of linux are restricted to stop people from breaking them.

---

