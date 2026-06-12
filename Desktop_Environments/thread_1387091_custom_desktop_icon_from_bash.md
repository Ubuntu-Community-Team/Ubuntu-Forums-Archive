---
title: "custom desktop icon from bash"
date: 2010-01-21
forum: Desktop Environments
---

### Post by Eagleon on 2010-01-21
Hi Guys and Gals,

I've been writing a BASH script recently, and a part of the process is to add 3 sym links on the Desktop using

```

ln -s $1 ~/Desktop

```

in one of my functions. Simple enough so far, right? Ok, what I want to do next is to replace the default icon on these links to a custom one.

I know how to do this manually... by right clicking on the sym link, selecting properties, clicking on the icon and choosing a different file. However, I don't want to do it manually... I want my bash script to handle this automatically. I have been searching everywhere for the nautilus config file that contains the path to the custom icon without luck. Can anyone tell me where this file is located, or if there is a better way to accomplish what I am trying to do? I am using ubuntu 9.10, so it's GNOME.

Thanks in advance!

P.S. Also, let's say I have KDE installed as well. Is there a way to make the changes appear there as well?

---

### Post by Brandon Williams on 2010-01-21
I'm not sure where things are stored for the method that you're currently using, but I can suggest an alternative. If you put a .desktop file in your ~/Desktop directory, it should serve the same purpose as the symlink, giving you something to click on to launch the program in question. Using a .desktop file will give you control over both the icon and the displayed name, among other things.

If we assume that the command you're running is 'ln -s /path/to/somefile ~/Desktop', then you would instead create a file called ~/Desktop/somefile.desktop with at least the following content:
```
[Desktop Entry]
Name=somefile
Type=Application
Exec=/path/to/somefile
Icon=/path/to/icon
```

Creating such a file would be easy enough to do programatically in bash.

---

### Post by Eagleon on 2010-01-21
Hi Brandon,

Thanks so much! This is an excellent solution for what I want to accomplish... so I am going use it. I did a quick google search and it seems that this can work in both Gnome and KDE, if I am not mistaken. Excellent... Thanks Again!!

This solves my problem, but I am still curious about doing it the other way as well if anyone knows. The reason being... what if I actually needed a sym link here. In this situation I don't really need one, but just for future reference. A sym link would allow me to reference the link directly as a path in BASH, whereas the *.desktop solution will not, right?

EDIT:
Actually... it seems that I can't drag and drop stuff in there! This is a problem since I need that to be possible...

---

### Post by Brandon Williams on 2010-01-21
> **Eagleon said:**
> Actually... it seems that I can't drag and drop stuff in there! This is a problem since I need that to be possible...

I'm not sure what you mean by that. Do you mean that you want to be able to drag files over to the icon and have them used as arguments to the command being run? If so, then you can add "%f" (one instance of app per file dropped) or "%F" (one instance of app for all files dropped) to the end of the Exec line:
```
Exec=/path/to/somefile "%F"
```

The specifier is required for drag-n-drop support. [Look here](http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-icon.html) for more information.

If that's not what you meant, please clarify.

---

### Post by Eagleon on 2010-01-21
Hi Brandon,

Thanks again. Actually, the %F can work for me with a little scripting. Sorry for the vagueness in my response, let me clarify:

The destination is not a script or application, it's simply a directory. The bash script that I am writing is simply a custom encryption/backup solution which runs in the background. So when I drag and drop a file into the directory, the BASH script running in the background will detect it, automatically encrypt it and then upload it to my remote backup server(s). Quite simple actually. 

To use the %F solution, I could modify my bash script a bit and have it only execute when I drop something into that .desktop file... which is also a nice way of doing it. I guess I could also write a second script to handle the input as well.

However, for the sake of learning... I am still curious to know if the %F is possible using a directory as the target of the .desktop file... as well as a solution that would work with a sym link.

Thanks again, your help is greatly appreciated! :)

---

### Post by Eagleon on 2010-01-22
*bump*

---

