---
title: "Installing app doesnt add icon to applications drop menu."
date: 2005-10-29
forum: Desktop Environments
---

### Post by Darrin on 2005-10-29
I installed bluefish and I looked everywhere in the applications menu list. I assumed it would be under internet. Its in my applications folder though. Shouldnt this install a shortcut in the applications menu? How do I get it there?

---

### Post by aysiu on 2005-10-29
You can try typing this in a terminal ```
killall gnome-panel
``` If not, you may have to add it manually.

---

### Post by Wolki on 2005-10-29
According to [http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=bluefish&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=bluefish&version=breezy&arch=i386)  the bluefish package contains a .desktop file, so it should also create a menu entry. As aysiu suggested, try restarting the panel; if you don't find it take a look at the .desktop file ("cat /usr/share/applications/bluefish.desktop"), it contains a line specifiying where in the menu it is.

---

### Post by Darrin on 2005-10-29
[QUOTE=aysiu]You can try typing this in a terminal ```
killall gnome-panel
``` If not, you may have to add it manually.[/QUOTE]
I guess I do have to add it manually. Resarting or doing as you say did not do anything. I did a search and found some information. 
I went to the terminal and entered in ```
smeg
```Added the application. Found the icon was stored in /usr/share/pixmaps. Used that. I thought the command was a link to the file location for big fish so I put that in. Didnt work. Looked at the properties for the other applications there and noticed that the command was well....a command. So I checked out the command for bigfish and noticed it was bluefish %F. So I put that in and it worked. Waddya know. :). I know Im slow on this linux stuff. Ill catch on.

Is there an easier way to do this? is this pretty much the step. Or was my way of doing it really lame.

A couple questions though. Is there a GUI option to get to smeg? Why do some applications add themselves to the applications menu and others must be done manually? Is this a problem with ubuntu OS or with the application itself?

---

### Post by Darrin on 2005-10-29
Ok, it looks like it originally did place it in the applications menu. But it put it under programing. Didnt expect to see it there. Nvu is there also. Oh well. I have it in two spots now. ;)

---

### Post by Wolki on 2005-10-29
[QUOTE=Darrin]A couple questions though. Is there a GUI option to get to smeg? [/quote]

Right-click the Applications Menu. You should also find it under accessoires, i think.

> Why do some applications add themselves to the applications menu and others must be done manually? Is this a problem with ubuntu OS or with the application itself?

Both. Applications that are to be put into the menu need ".desktop" files, which contain information regarding the command, icon, description and similar stuff. Without such a file, the gnome menu doesn't even know the program is there. Now, not every application provides such a file by itself, so ubuntu does it for those who don't. Some are forgotten though, if you've installed a program and don't get a menu entry, tell the developers by filing a bug on [www.launchpad.net](www.launchpad.net).

This only applies to graphical programs, there is usually little reason to run command line apps from the menu, and there are by far too many of them to include them anyway. :) If you really want one of them in the menu, add it yourself.

---

### Post by glantucan on 2005-11-07
But,...

Sorry, hello all, first of all, this is my first message in this forum. And I have to say that being so happy for discovering this beautiful distro, still a bit upset because of this thing. 

It was some time ago, but I remember a small app in KDE (I think it was *kappfinder *or something like that) which used to find all those aplications not added automatically to kde menu. Is there something like that for gnome.

I like to check new software to find the programms that fit better to my needs, and so I use to install several of the same kind after looking for them in the repository. That's the reason I miss so much **gappfinder** ;)  so much

Thanks

---

