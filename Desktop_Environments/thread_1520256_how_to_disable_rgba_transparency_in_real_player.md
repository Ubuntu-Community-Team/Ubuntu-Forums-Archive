---
title: "how to disable rgba transparency in real player"
date: 2010-06-29
forum: Desktop Environments
---

### Post by Yoge on 2010-06-29
Hi friends,
            I'm new to linux and i really like it. Recently i tried rgba transparency in my karmic 9.10 and it works fine.:razz:... My problem is i want to disable transparency in real player.  I tried by adding 'realplay' in the file '/etc/profile.d/gtkrgba.sh' but nothing works. :confused:... Please give me a solution.

Regards
Yoge

---

### Post by moongia on 2010-06-29
I had a similar prob. with kdenlive. what i did was right click on the applications then go to edit menu.for me i went to kdenlive and hit properties,under command i put 

env XLIB_SKIP_ARGB_VISUALS=1 kdenlive

this might help.

---

### Post by stinkeye on 2010-06-29
Open **~/.profile** (hidden file in your home folder) with gedit
```
gedit ~/.profile &
```



and at the very bottom of the file add
```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:openoffice
```

To add more apps to the "GTK_RGBA_APPS=allbut" line put a **:** followed by the application.
They will be blacklisted and RGBA support won't be used for them.
Use system monitor to get the correct name.

---

### Post by Yoge on 2010-06-30
Thank you friends, both solutions work fine...[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

