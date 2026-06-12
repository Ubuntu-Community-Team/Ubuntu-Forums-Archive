---
title: "task panel went missing"
date: 2009-02-27
forum: General Help
---

### Post by numbness05 on 2009-02-27
High people This morning I noticed my top task Panel was missing from my desktop...I have found how you replace this but now when I go to open things such as VLC or Pidgin it fails to show the little icons for them any idea how i can get them to re-appear on the new Panel have managed to get my power off button and the time etc

Any ideas please...?

Many thanks in advance!

:P

---

### Post by numbness05 on 2009-02-27
High people This morning I noticed my top task Panel was missing from my desktop...I have found how you replace this but now when I go to open things such as VLC or Pidgin it fails to show the little icons for them any idea how i can get them to re-appear on the new Panel have managed to get my power off button and the time etc

Any ideas please...?

Many thanks in advance!

---

### Post by Therion on 2009-02-27
Right-click any open space within the panel.
Select "Add to Panel".
From the what you're saying, I think what you want is either "Notification Area" and/or "Windows List (Buttons)".
The first is the list of running applications (icons will show in the "system tray" next to the clock and such), the second is buttons on your panel of open windows that you can choose from by clicking on them.  I think you want the Notification Area applet, but I'm not sure.
Just drag drop whatever you want onto the panel and move it about as you need.

Does that help?

---

### Post by internalkernel on 2009-02-27
Right click on the panel, select Add to Panel - your looking for the Notification Area.

---

### Post by geirha on 2009-02-27
If you type the following in a terminal, the panels will be reset to the way they are for a newly created user.
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by UbuntuNerd on 2009-02-27
type this in a terminal to restore your panels to their default settings like they were bofore:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by silent contender on 2009-02-27
Also, you can add the system tray applet (I take you're using gnome) to the taskbar.

---

### Post by JECHO on 2009-02-27
> **numbness05 said:**
> High people This morning I noticed my top task Panel was missing from my desktop...I have found how you replace this but now when I go to open things such as VLC or Pidgin it fails to show the little icons for them any idea how i can get them to re-appear on the new Panel have managed to get my power off button and the time etc

Any ideas please...?

Many thanks in advance!

:P


right click the panel and add the window list applet to it. boom youre done :)

---

### Post by zeealpal on 2009-02-27
If ur talking about the notification panel right click on the panel and add notification area to it.

---

### Post by bapoumba on 2009-02-28
Threads merged.

---

### Post by golroch on 2009-03-05
Great help.

The following commands made sense, THANK YOU

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

I searched everywhere and I located the panels under ~/.gconf/apps/panel
but it did not show me how to enable the default top bar. As in make gnome-panel load the xml file for the previous top bar, since I could see the xml location under top_panel1 

Is there a file which shows you how it loads the different xml configurations under ~/.gconf/apps/panel ?
This will help me understand how the different panels are loaded.

---

### Post by geirha on 2009-03-05
Run gconf-editor and browse to /apps/panel/. The keys are explained in the description field when you select them.

---

### Post by golroch on 2009-03-05
Thanks for the information the tool is very good. Do you also know which file tells gnome to load the panels xml configuration file on logging in?

Is this somewhere in .session?

Very new to ubuntu, but I'm never going back to windows hell.

---

