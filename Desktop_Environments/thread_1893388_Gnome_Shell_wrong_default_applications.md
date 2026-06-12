---
title: "Gnome Shell wrong default applications"
date: 2011-12-10
forum: Desktop Environments
---

### Post by BigSilly on 2011-12-10
I've been into System Settings/System Info/Default Applications, and changed the defaults to my preferred applications, but how come when I, say, put an audio CD or a DVD in the computer, the Gnome Shell notifications still lists bloody Brasero rather than Banshee, or Totem rather than VLC? Anyone fixed this and wishes to share the voodoo? Many thanks.

---

### Post by Frogs Hair on 2011-12-10
This thread may point in the right direction . The method of choosing the application from the list in system settings worked with Opera and Rhythmbox , but I still have Gedit as my default calendar and I refuse to install Evolution .

[http://ubuntuforums.org/showthread.php?t=1844227&highlight=make+vlc+default](http://ubuntuforums.org/showthread.php?t=1844227&highlight=make+vlc+default)

---

### Post by t.rei on 2011-12-10
I was just here to find a solution to this:
I am using the epiphany-webapp-mode for my google-calendar. And that's all well and works smoothly, but I cannot set it to be the default for calendar. 

The whole "default application" settings thing in gnome-shell is very... very... not done, I guess.

Hope someone finds a solution or a "this is still a WIP" note. 

*continues the search*

---

### Post by BigSilly on 2011-12-10
And suddenly it's working. I went into System Settings/Removable Media, and changed the settings to whatever my preferred program was, ie. VLC for DVD, Banshee for CD etc, but when I tried a disc it just went straight to the application rather than notifying me. So I went back and reset all the options to "ask me what to do" in Removable Media, checked my Default Applications were set properly (one or two of them had reset themselves), and now when I put a disc in I get two notification boxes. The first offers to open the disc via the file manager, and the second offers the correct default application I have set. I imagine this is the correct Shell behaviour.

It seems very much to me a case of WIP too though. I hope things like this get ironed out soon enough.

---

