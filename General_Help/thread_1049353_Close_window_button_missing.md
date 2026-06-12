---
title: "Close window button missing?"
date: 2009-01-24
forum: General Help
---

### Post by Odd_sam on 2009-01-24
I installed compizfusion and when I start it up my title bar at the top of all my windows disappeared. Using the latest version and ubuntu 8.10.

---

### Post by Wartender on 2009-01-24
use metacity --replace, i don't know what your problem is but this'll revert you back to metacity
edit: type metacity --replace in the terminal that is

---

### Post by TheViLliN on 2009-01-28
I'm having the same issue.  
My Visual Effects are disabled every time I reboot presumably causing the same issue.  Cant close or move any windows.

I'm still looking into it....
When I find out I'll pass it on.

[http://ubuntuforums.org/showthread.php?t=1050666]("http://ubuntuforums.org/showthread.php?t=1050666")

---

### Post by N4zgu1 on 2009-01-28
have you tried to installl compiz from the shame repositorie???


Here is a how-to

 

First remove the originally installed Compiz packages. You can do this by opening Synaptic, search (*Name* only) for Compiz and mark all packages for complete removal (see attachment). Apply the indicated changes.
When you now click *Status* the libdecoration0 package is marked as Auto removable. Also remove this package.
Now close Synaptic and open a terminal.

In the terminal you now open the */etc/apt/sources.list* file with your favorite editor.
I personally use *nano*
```
sudo nano /etc/apt/sources.list
```
If you are not comfortable with a "terminal editor" you can use in XFCE
```
gksu mousepad /etc/apt/sources.list
```
or in Gnome
```
gksu gedit /etc/apt/sources.list
```

At the bottom add the following lines to your file
```
#SHAME'S COMPIZ REPOSITORY
deb http://download.tuxfamily.org/shames/debian-lenny/desktopfx/unstable/ ./
```
Save the file and close the editor.

Now get the GPG repo key
```
wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | sudo apt-key add -
```

Now open Synaptic again and click "Reload"
Perform the same search as indicated when removing the orginal packages (compiz and only Name).
I am running an XFCE installation, so I marked everything _starting with_ compiz EXCEPT the packages _ending with_ *-all*,*-kconfig* or *-kde* (see attachment).
Mark the packages for installation and also except the additionally to be installed packages.

NOTE: Make sure you do NOT mark the original Debian packages (like for example compiz-gtk).
You can recognize the Shame packages since they have *git* in the version number.

Apply the changes.
When the changes are applied close Synaptic.




NOTE: I didnt make the how-to I took it from here

[http://dreamlinuxforums.org/index.php/topic,2871.msg23715.html#msg23715]("http://dreamlinuxforums.org/index.php/topic,2871.msg23715.html#msg23715")

---

### Post by vinthund on 2010-02-14
Hello,

I just installed Ubuntu NBR. I did not install any window decorator, but right from the beginning there is no "close" button on any window, as far I could see. Any help with this?

---

### Post by Yogotiss on 2010-02-14
> **vinthund said:**
> Hello,

I just installed Ubuntu NBR. I did not install any window decorator, but right from the beginning there is no "close" button on any window, as far I could see. Any help with this?

When using the NBR your interface is pretty much like the Google Chrome web browser, nothing but tabs. You should see [x] symbol to the right of that tab...

---

### Post by vinthund on 2010-02-14
I do not use Chrome, so I might get it wrong, but I do not see any buttons on the top bar. Now I realized, that I do not see the top bar at all (the one with app name and with maximize/minimize/close buttons. But why?

---

### Post by flippo on 2010-02-14
You should have really started a new thread for this, the decription of the problem in the first post is different than your problem.  You may not have a window manager running, try opening a terminal and typing ```
metacity --replace &
```I'm not sure if NBR has metacity though, this may be better asked in the netbook remix section of the forums.

---

### Post by vinthund on 2010-02-14
> **flippo said:**
> You should have really started a new thread for this, the decription of the problem in the first post is different than your problem.
Yes, but I did not realize it at first.

Reply to your command is as follows:
```
marek@marek-eee:~$ metacity --replace &
[1] 4377
marek@marek-eee:~$ 

```

---

### Post by flippo on 2010-02-14
Does it make the window borders reappear?

---

### Post by vinthund on 2010-02-14
No :(

---

### Post by farfellas on 2010-10-08
hi guys,
ive been having the same problem but its intermittent, im really not quite sure what could be triggering this to happen (its quite annoying)
metacity --replace &seemed to restore the bar  , but if anyone knows the cause of this it would be a great help.
btw im running Ubuntu 10.04 LTS - the Lucid Lynx if that helps
thanks

---

