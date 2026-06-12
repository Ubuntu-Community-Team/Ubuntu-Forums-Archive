---
title: "create icons in icewm/rox and enlarge bottom panel"
date: 2007-03-18
forum: Desktop Environments
---

### Post by seshomaru samma on 2007-03-18
I was running icewm for a while but just couldn't over my attachment for desktop icons. I finally installed rox ,which gave me one desktop icon (home) , but i just can't figure out how to create other icons , except loging into gnome , creating them and dragging them into the desktop. For example , how do i create a skype icon ?
Another icewm question is how do i make the lower panel thicker ? I went thru all the config files but couldn't find that option.
last question - in icewm there is no default application to deal with png files. it offers me to set one by either dragging an application or writing the command. i want gthumb to do it , what should  i drag or what is the gthumb command?

---

### Post by Peter76 on 2007-03-18
With Rox, you just drag wath you want to the desktop and it will create the shortcut for you; to do this with skype: in rox goto /usr/bin ( or where ever the skype binary is ) and drag the skype binary to the desktop. To set an icon for it, right click on it and select 'set icon' or something. Now you need to drag an icon to it; with rox, goto /usr/share/pixmaps ( most of the time ) and drag the skype icon to the window. The procedure for gthumb is the same, just drag gthumb from /usr/bin to the set application window.

Good Luck

---

### Post by seshomaru samma on 2007-03-19
Thanks 
/usr/bin is what I needed...

But what about the bottom panel?
anybody knows ?

---

### Post by Peter76 on 2007-03-20
I recall there is an option in ~/.icewm/preferences somewhere about 'double height taskbar' or something alike... Good luck

---

### Post by kerry_s on 2007-03-20
You might want to look in synaptic, theres a gui app for preferences( iceconf ) there's also a menu one (icemc ).

---

### Post by seshomaru samma on 2007-03-21
> **Peter76 said:**
> I recall there is an option in ~/.icewm/preferences somewhere about 'double height taskbar' or something alike... Good luck

thanks but this only gives me two thin taskbars on top of each other instead of a big thick one.

---

