---
title: "XFCE - newbie questions"
date: 2011-06-20
forum: Desktop Environments
---

### Post by hashcode on 2011-06-20
Hello I am new to XFCE and I'd like to ask few question about usage:

1. How can I disable dragging windows through workspaces? I like them to stay at one.
2. How do you configure startup applications?
3. Why XFCE menu doesn't show some of my custom icons? (png, tried more than one, for custom launcher - eclipse)

EDIT:
4. How do I add custom keyboard? (ALT+SHIFT switching)
5. I restarted laptop and all my applications re-opened after restart. I do not want that. How to disable this?

Thank you!

---

### Post by Toz on 2011-06-20
> **hashcode said:**
> Hello I am new to XFCE and I'd like to ask few question about usage:
Welcome to XFCE.

> 1. How can I disable dragging windows through workspaces? I like them to stay at one.
Goto the Settings Manager->Window Manager->Advanced Tab and uncheck the 2 wrap checkboxes in the Wrap Workspaces section. 
> 2. How do you configure startup applications?
Settings Manager->Session and Startup->Application Autostart
> 3. Why XFCE menu doesn't show some of my custom icons? (png, tried more than one, for custom launcher - eclipse)If you're referring to changing the panel launcher icon, then right-click the launcher and select "Properties". Click the lowest right button ("Edit the currently selected item"), left-click the icon button, and change the "Select icon from" dropdown from "Application icons" to "Image files", then search for it. 

If you are referring to a menu entry, then you need to make the change to the appropriate .desktop file in /usr/share/applications

---

### Post by hashcode on 2011-06-20
1. thanks, works
2. thanks, works
3. I do not have eclipse.desktop in /usr/share/applications

Should I create it?

// thanks for comments so far, I made little edit

---

### Post by Toz on 2011-06-20
How did you install eclipse?

---

### Post by hashcode on 2011-06-21
> **Toz said:**
> How did you install eclipse?

I just downloaded, extracted it and made link in /usr/bin, so shell knows "eclipse"

---

### Post by nzjethro on 2011-06-21
> **hashcode said:**
> 
4. How do I add custom keyboard? (ALT+SHIFT switching)

Open Settings > Keyboard > Layout tab. Uncheck "Use system defaults". Click "Add", then find your keyboard layout (I use USA Dvorak). Not sure how to change between layouts with ALT + Shift, maybe look around for a command to change layouts, then bind that to a key combination.

> **hashcode said:**
> 
5. I restarted laptop and all my applications re-opened after restart. I do not want that. How to disable this?


When you log out, uncheck the box that says "Save session for future logins".

---

### Post by hashcode on 2011-06-21
4. I added layout but still don't know how to change it :(
5. nice, thanks

---

### Post by nzjethro on 2011-06-21
> **hashcode said:**
> 4. I added layout but still don't know how to change it :(


Ok, I had a look, and I think what you want is a plugin called xfce-xkb-plugin, found [here]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin#xfce-4.2"). Try installing that, then adding it to a panel, to easily allow you to switch between layouts. :)

---

### Post by hashcode on 2011-06-21
OK it works now thank you :)

---

### Post by Toz on 2011-06-21
> **hashcode said:**
> I just downloaded, extracted it and made link in /usr/bin, so shell knows "eclipse"

Ok. Eclipse also exists in the repositories. If you had installed it through the software centre, it would have created the menu entry for you. Anyways, here is the eclipse desktop file:```
[Desktop Entry]
Name=Eclipse
Comment=Integrated Development Environment
Exec=/usr/bin/eclipse
Icon=eclipse48.png
Terminal=false
MultipleArgs=false
Type=Application
Categories=Application;Development;
StartupNotify=true

```

Save it as **/usr/share/applications/eclipse.desktop**

---

### Post by mlnease on 2011-10-25
Hello,
> Settings Manager->Session and Startup->Application AutostartI don't seem to have 'Settings Manager' in my applications menu.  Is it something I need to install, or...?

Thanks (anyone) in advance.

---

### Post by scania_gti on 2011-10-25
If you don't see "settings manager" jus go to "session and startup".

---

### Post by Toz on 2011-10-25
On the main menu, select the Settings submenu and you should see it there.

---

### Post by mlnease on 2011-10-25
Of course--thanks (both)!

---

