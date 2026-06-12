---
title: "Add Shutdown button to Applications Menu?"
date: 2012-06-01
forum: Desktop Environments
---

### Post by bug67 on 2012-06-01
In the Xubuntu top pannel, under my user name menu, is a drop down that has Logout, Restart and Shutdown buttons.  However, I constantly find myself drifting over to the Applications Menu on the left to shut the machine down.  Probably a left over habbit from my Mac days.

Is there a way to add the Restart and Shutdown buttons (Logout is already there) to the Applications Menu?  Thanks.

---

### Post by lightning slinger on 2012-06-02
You can add Shutdown and/or Restart buttons direct to the top panel!

Right click panel>Panel>Add New Items>Action Buttons, then by right clicking on the button you have added Properties will let you edit what that button does. You can add more than one button to do a different function!

---

### Post by bug67 on 2012-06-02
I don't want them on the panel, I want them in the Applications Menu.

---

### Post by Luckiboy on 2012-06-02
Alacarte -> New item -> Command = shutdown
Choose a nice icon and you're done ;)

---

### Post by bug67 on 2012-06-02
> **Luckiboy said:**
> Alacarte -> New item -> Command = shutdown
Choose a nice icon and you're done ;)

I don't know what "Alacarte" is but I right clicked on the application menu, chose properties > edit menu > add new item, put "shutdown" in the space labeled "command", chose a pretty icon and...my new "shutdown" button in the application menu does nothing!

:popcorn:

---

### Post by Luckiboy on 2012-06-02
Hmm, try ```
sudo shutdown -h now
```?

---

### Post by bug67 on 2012-06-02
> **Luckiboy said:**
> Hmm, try ```
sudo shutdown -h now
```?

Nothing...

---

### Post by brainwash on 2012-06-02
> **Luckiboy said:**
> Hmm, try ```
sudo shutdown -h now
```?

This will only work, if you have edited the sudoers file to allow exection of the shutdown command without being asked for your password. You should use **gksudo** instead to get a grafical password promt.

On a default Ubuntu installation you can also use dbus to shutdown/restart/suspend/... your system. No password needed.

[https://wiki.archlinux.org/index.php/ConsoleKit#Use_dbus_for_power_operations](https://wiki.archlinux.org/index.php/ConsoleKit#Use_dbus_for_power_operations)

---

### Post by bug67 on 2012-06-02
So, no one knows?  :confused:

---

### Post by Toz on 2012-06-02
If you right-click the Applications Menu and choose Properties and then click on the "Edit Menu" button, you will startup the menu editor.

Click on "New Item" then add in the following info:

_For Shutdown:_
Name = Shutdown
Command = xfce4-session-logout --halt
Icon = (select an icon)

_For Restart_
Name = Restart
Command = xfce4-session-logout --reboot
Icon = (select an Icon)

Click on "Create" to create the entry, then click-drag to move it to the proper location in the menu.

---

### Post by bug67 on 2012-06-20
> **Toz said:**
> If you right-click the Applications Menu and choose Properties and then click on the "Edit Menu" button, you will startup the menu editor.

Click on "New Item" then add in the following info:

_For Shutdown:_
Name = Shutdown
Command = xfce4-session-logout --halt
Icon = (select an icon)

_For Restart_
Name = Restart
Command = xfce4-session-logout --reboot
Icon = (select an Icon)

Click on "Create" to create the entry, then click-drag to move it to the proper location in the menu.

Thanks.  That did it.  :)

---

### Post by anaconda on 2012-06-20
I just removed the "name" from the panel...
Then the "logout" menu item is automatically added to the menu....

Just like in gnome

---

