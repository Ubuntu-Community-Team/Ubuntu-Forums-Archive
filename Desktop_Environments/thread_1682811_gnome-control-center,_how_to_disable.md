---
title: "gnome-control-center, how to disable?"
date: 2011-02-06
forum: Desktop Environments
---

### Post by NumerataNero on 2011-02-06
I did changed the login screen the following way:

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

but now each time the gnome-control-center is shown even after reboot.

How can I get rid of it?

---

### Post by Frogs Hair on 2011-02-06
Do you mean Appearance Preferences or Control Center ? There are a number of methods to change your login screen and the instructions I have seen include a way to revert to normal after making changes . Return to where you found the instruction and check to see if you missed something.

---

### Post by NumerataNero on 2011-02-06
What I mean that the control-centre still there after the reboot.
I can get rid of it with the x button. How can I permantly remove it?

---

### Post by Frogs Hair on 2011-02-06
I used a different method that included an unlink command and did not involve the control center only the appearance preferences.

Use ```
gksudo nautilus
``` 
Look in File System > usr/share/gdm/autostart/loginwindow If the control center is listed there remove it.

---

### Post by NumerataNero on 2011-02-10
> **Frogs Hair said:**
> Do you mean Appearance Preferences or Control Center ? There are a number of methods to change your login screen and the instructions I have seen include a way to revert to normal after making changes . Return to where you found the instruction and check to see if you missed something.
Yes. I mean the Appearance Preferences window.
I exactly described what i've done to change the login screen.

---

### Post by NumerataNero on 2011-02-10
I've removed the gnome-appearance-properties.desktop. Probably i've copied it from the /usr/share/applications/ directory.
Did solved it,

---

