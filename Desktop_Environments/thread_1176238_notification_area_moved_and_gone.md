---
title: "notification area moved and gone"
date: 2009-06-02
forum: Desktop Environments
---

### Post by Chrisynde on 2009-06-02
Hi, 

I'm a relative new ubuntu user and have used these forums allot for help with great success. 
However I've encountered something quite strange with my Xubuntu Jaunty distro.

Here goes:
Today I booted my laptop and noticed the notification area (with network applet etc) was missing.
But a notification came up my screen right below the applications menu saying my connection was established. 
So I figured the notification area is still running but not in the place I want it to be. I've tried 'killall' for both the nm-applet and the entire xfce4 panel to no avail. I've tried reinserting the notification area with "add panel" but was unable. It said "There is already a notification area running on this screen" followed by "Could not load systray module". 

So I figure i'll have to kill the notification area and have to add it again, just don't know how if i can't find it..

Any help?

PS: Based on earlier research on these forums i have a feeling it has something to do with installing and removing the Compiz settings manager..

---

### Post by Chrisynde on 2009-06-02
Anyone? I'm really out of ideas except for the obvious reinstall..

---

### Post by mister_p_1998 on 2009-06-02
Easy!
Right Button over the task bar, select "Add to Panel" and select "Notification Area". Sometimes the items on the taskbar move about (dont know why) and sometimes vanish (Like yours).

Steve

---

### Post by Chrisynde on 2009-06-02
> **mister_p_1998 said:**
> Easy!
Right Button over the task bar, select "Add to Panel" and select "Notification Area". Sometimes the items on the taskbar move about (dont know why) and sometimes vanish (Like yours).

Steve

Thx Steve, but I already tried that to no avail. I always get an error saying there is already a notification area running on my screen (see above). I still can't seem to find it though...

---

### Post by kerry_s on 2009-06-02
look in ~/.config/xfce4/panel
delete "systray-*"

in panels.xml, delete the line for systray

logout and back in, put the notification back on.

---

### Post by Chrisynde on 2009-06-02
> **kerry_s said:**
> look in ~/.config/xfce4/panel
delete "systray-*"

in panels.xml, delete the line for systray

logout and back in, put the notification back on.

Thx! Problem solved!

---

### Post by Theobalt on 2010-06-28
It worked for me too, although there was nothing in panels.xml about systray.

Thanks!

---

### Post by michaelmouf on 2010-08-03
I'm running an Ubuntu minimal install with xfce 4.6. I have the same problem and tried deleting the file and line in panels.xml, but the files keep getting created again everytime i login. Help anyone?

---

### Post by affert on 2010-11-08
I bet you have a session saved.  Try going to  ~/.cache/sessions/ and deleting the files there.

---

### Post by Mappenz on 2011-07-14
I have the same Problem. But those hints don't apply to me. I am using 11.04.

my  ~/.config/xfce4/panel looks like:

```

michael@michi:~/.config/xfce4/panel$ ls
launcher-13  launcher-15  launcher-17  launcher-19  launcher-21
launcher-14  launcher-16  launcher-18  launcher-20

```

---

### Post by azertyh on 2011-07-14
right-click on a panel, panel, panel preferences, items tab, and move the notification area to the place where you want.

---

