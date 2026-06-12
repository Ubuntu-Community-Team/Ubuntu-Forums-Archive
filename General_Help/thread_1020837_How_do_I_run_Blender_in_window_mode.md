---
title: "How do I run Blender in window mode?"
date: 2008-12-24
forum: General Help
---

### Post by KostadinDaveth on 2008-12-24
Hi.  I just reinstalled Blender 2.48a manually (through tar.gz archive) on my Ubuntu Intrepid Ibex; however, whenever I run Blender it always shows up in fullscreen mode.  I want it to run in window mode so I can easily view tutorials without switching workspaces.

I know that there's a way to resize the the executable file with "-w" or "W" (forget which one), but I would really like to be able to run both fullscreen and window mode.  I know the repository files, when installed, give two modes (window and fullscreen). Is there a way to add this mode to my Applications->Graphics menu?

---

### Post by damis648 on 2008-12-24
Run:
```
blender -p 5 225 1024 768
```
replacing 1024 and 768 with the starting size of the window. To add to the menu, right click the menu bar and click "Edit Menus". Go to Blender (windowed) and modify it with the above command.:popcorn:

---

### Post by KostadinDaveth on 2008-12-24
Hmm...do I need to be in the directory that Blender is installed to do this?  I tried the command cd but here's what I got...

```
cd /usr/local/Blender 2.48a
bash: cd: /usr/local/Blender: No such file or directory
```

I know this is the correct install directory (I checked it in Nautilus).
Am I doing something wrong?

---

### Post by damis648 on 2008-12-24
Blender's location isn't defined in $PATH? Try just plain
```
blender -p 5 225 1024 768
```
first and if that doesn't work do it like this:
```
cd '/usr/local/Blender 2.48a'
./blender -p 5 225 1024 768
```
OR
```
'/usr/local/Blender 2.48a/blender' -p 5 225 1024 768
```

---

### Post by KostadinDaveth on 2008-12-24
The last two methods work, but I'm given no borders to resize the window (Blender only takes up half of my 1024x768 screen).

You might also want to know that I'm using the AWN dock bar.  It seems to allow me to minimize and resize the Blender window, but every time I perform one of those actions the Blender window does not display properly (i.e. graphical glitches or doesn't show up again at all).

Here's the terminal code:

```
josh@linuxlap1:~$ cd '/usr/local/Blender 2.48a'
josh@linuxlap1:/usr/local/Blender 2.48a$ ./blender -p 5 225 1024 768
 height prob 
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Terminated
josh@linuxlap1:/usr/local/Blender 2.48a$ '/usr/local/Blender 2.48a/blender' -p 5 225 1024 768
 height prob 
Compiled with Python version 2.5.2.
Checking for installed Python... got it!

Blender quit
josh@linuxlap1:/usr/local/Blender 2.48a$ 


```

---

### Post by damis648 on 2008-12-24
What about:
```
cd '/usr/local/Blender 2.48a'
./blender -w -p 5 225 800 600
```

OR
```
'/usr/local/Blender 2.48a/blender' -w -p 5 225 800 600
```

EDIT: Also, don't forget to change the 1024 and 768! Try 800 and 600 maybe.

---

### Post by KostadinDaveth on 2008-12-24
> **damis648 said:**
> What about:
```
cd '/usr/local/Blender 2.48a'
./blender -w -p 5 225 800 600
```

OR
```
'/usr/local/Blender 2.48a/blender' -w -p 5 225 800 600
```

EDIT: Also, don't forget to change the 1024 and 768! Try 800 and 600 maybe.
I don't have any graphics glitches now, but I still can't resize the Blender window because there is no window menu at the top of the program.

---

### Post by damis648 on 2008-12-24
What window manager and decorator are you using? Also, have you tried blender from the repos?

---

### Post by KostadinDaveth on 2008-12-24
I was using the repos before I upgraded to the latest version via the Blender website.  I had the same problem.  I checked the BlenderArtists forums, and it appears I'm not the only one who has this problem - [http://blenderartists.org/forum/showthread.php?t=125884](http://blenderartists.org/forum/showthread.php?t=125884)

I tried turning off compiz visual effects (someone said Blender had problems with it). This didn't seem to change the window/border issue though.

I'm not sure exactly what window manager I have installed.  Is there a way to find this out?

---

### Post by damis648 on 2008-12-24
Re-try the one of the repos. I had this problem and fixed it with the commands I gave you (the first one, without CD'ing or without a full path).

BTW, You can re-enable compiz, it doesn't seem to affect blender. For future reference, compiz is a window manager. When it is disabled, you are using metacity. (Pronounced like capacity, not meta-city.)

---

### Post by KostadinDaveth on 2008-12-24
Is there a way to get the latest version from the repos or am I stuck with the old one?  I would like to be able to use the new features in this version of blender.

---

### Post by damis648 on 2008-12-24
> **KostadinDaveth said:**
> Is there a way to get the latest version from the repos or am I stuck with the old one?  I would like to be able to use the new features in this version of blender.

Not at the moment, unless you mind giving up windowed mode for new features.

---

### Post by KostadinDaveth on 2008-12-24
Okay.  I'll try the repo version.

---

### Post by KostadinDaveth on 2008-12-24
Nope, the repo 2.46 version does the same thing.  I run it in windowed mode from the Apps menu, but it appears fullscreen.

---

### Post by damis648 on 2008-12-24
See what happens with
```
blender -p 5 225 800 600
```

---

### Post by KostadinDaveth on 2008-12-24
Well on the bright side the generic blender command now works, but still no window border :(

---

### Post by damis648 on 2008-12-24
Hm, that is odd. Go ahead and revert back to the newer version. I am about to try something. Be right back...

---

### Post by KostadinDaveth on 2008-12-24
I reinstalled the new version.

---

### Post by damis648 on 2008-12-24
Sorry, I had to eat Christmas dinner and all. Anyway, that is odd. I tried it with:
Compiz+Emerald
Compiz+Gnome-Decorator
Metacity+Gnome-Decorator
and they all worked.

---

### Post by Samhain13 on 2008-12-25
For what it's worth, this is how I do it. (I'm on 8.04, using Blender 2.48a from their main site.) I extracted the .tar.gz contents in a place called "/media/Sandbox/Blender/appMain"; wrote a script and have my Blender launcher (in AWN dock) point to that script.

Script contents:
```
#!/bin/sh
cd /media/Sandbox/Blender/appMain
gnome-terminal -e "./blender -w"
```

So when I click my launcher, a terminal is opened and Blender is launched in Windowed mode by that terminal. I also have Compiz running and have Metacity as my window decorator.

---

### Post by KostadinDaveth on 2008-12-25
> **Samhain13 said:**
> For what it's worth, this is how I do it. (I'm on 8.04, using Blender 2.48a from their main site.) I extracted the .tar.gz contents in a place called "/media/Sandbox/Blender/appMain"; wrote a script and have my Blender launcher (in AWN dock) point to that script.

Script contents:
```
#!/bin/sh
cd /media/Sandbox/Blender/appMain
gnome-terminal -e "./blender -w"
```

So when I click my launcher, a terminal is opened and Blender is launched in Windowed mode by that terminal. I also have Compiz running and have Metacity as my window decorator.

Hmm...This sounds like the setup I have except I'm using Intrepid.  I'll give it a try, and I'll let you know what happens.

---

### Post by KostadinDaveth on 2008-12-25
Okay.  I found the media directory, but I don't have a folder called sandbox.  Do I need to create this directory or tell terminal to do something?  Also, I did not see an appMain folder in the .tar.gz file...  Was this created too?

---

### Post by damis648 on 2008-12-25
> **KostadinDaveth said:**
> Okay.  I found the media directory, but I don't have a folder called sandbox.  Do I need to create this directory or tell terminal to do something?  Also, I did not see an appMain folder in the .tar.gz file...  Was this created too?

The AppMain part is the main path for the app. Just modify that script to cd to where Blender is installed.

---

### Post by KostadinDaveth on 2008-12-25
One more question.  How do I save the terminal commands as a script?

---

### Post by damis648 on 2008-12-25
Open gedit (Applications>Acessories>Text Editor) and put in the file:
```
#!/bin/sh
cd '/usr/local/Blender 2.48a'
gnome-terminal -e "./blender -w"
```
and then save it in your home dir as blender.sh and then open a terminal and enter
```
chmod +x blender.sh
```
Now you can make a desktop shortcut for that file or just put it on your desktop, panel, or menu, or just double click it and then click 'run'.

---

### Post by KostadinDaveth on 2008-12-25
The blender script file works fine.  When I type in the command in terminal, however, it doesn't do anything.  I placed the script in my home folder...:confused:

---

### Post by KostadinDaveth on 2008-12-26
Bump bump...

---

