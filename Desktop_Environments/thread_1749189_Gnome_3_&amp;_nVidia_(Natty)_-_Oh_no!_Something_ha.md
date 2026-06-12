---
title: "Gnome 3 &amp; nVidia (Natty) - Oh no! Something has gone wrong."
date: 2011-05-04
forum: Desktop Environments
---

### Post by kevpatts on 2011-05-04
I've upgraded to Gnome 3 on my Natty install on my MacBook Pro 5,1. I installed gnome-session and got around the .ICEauthority problem.

Now if I log into "Ubuntu Gnome Shell Desktop" it waits a bit and then it shows a nice graphical screen (with a picture of a sad monitor) saying:
```
Oh no! Something has gone wrong.
A problem has occurred and the system can't recover.
Please log out and try again.
Log out
```

Anyone know the cause of this?

---

### Post by Grozzy on 2011-05-04
I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```

Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```

Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!

---

### Post by kevpatts on 2011-05-04
Hey,

I found the issue by accident and it wasn't something I would have guessed! When changing settings to fix the .ICEauthority problem I had to change my "Auto eth0" NIC to DHCP (it was set in the old NetworkManager to a static IP address). To do this I had to modify the "/etc/NetworkManager/system-connections/Auto eth0" file and set "method=auto" in the "ipv4" section and remove the other lines from that section.

This is what actually fixed the issue for me. It's repeatable also; if I restore the backup file I took it fails every time. I'll check to see if this bug has been reported and report it if it hasn't.

Thanks,
Kevin

---

### Post by ontwowheels on 2011-06-06
> **Grozzy said:**
> I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```

Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```

Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!

This worked for me, thanks!!

---

### Post by Ratmatix on 2011-06-16
> **Grozzy said:**
> I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```

Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```

Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!

Had the same problem as OP, Grozzy's solution solved it for me! :)

Thanks!

(Quote spam to bump because it works =D)

---

### Post by doniking on 2011-06-24
I have this problem on my opensuse 11.4.
I found that gnome-shell-extension-xrandr-indicator was the culprit.
Uninstalling it the problem was gone.

---

### Post by legends2k on 2011-07-08
> **Grozzy said:**
> I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!

This helped me :), thanks a lot!

---

### Post by jbicha on 2011-08-19
At least in Fedora when I get the error, sometimes the error was lying and I could just Alt+F2 to access my Gnome Shell which was working just fine behind the error window.

---

### Post by MARP1961 on 2011-08-19
Strangely enough I used to have this problem, but it seems to have gone away (updates?). A second login attempt always worked.

Gnome shell is excellent and 'knocks spots' off Unity in my opinion!

---

### Post by karthikeya.vecham on 2011-09-20
yes it happened same for me pls help me out

its showing me a message describing:"No such file or directry" when i enter the cmd :"~/.config/autostart"
pls suggest me another way

---

### Post by karthikeya.vecham on 2011-09-20
> **Grozzy said:**
> I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```

Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```

Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!
when i enter the command:"~/.config/autostart"
its showing me no such file or directry
pls help me out

---

### Post by Fishnuts on 2012-02-15
> **Grozzy said:**
> I got exactly the same.
It turned you that the only thing you have to do is to add the command "gnome-shell --replace" to autostart at login.
To do so press CTRL+Alt+F1 to get to your first console, log in using you name and password, then type these commands:

```
cd ~/.config/autostart
nano gnome-shell.desktop
```

Then, in the editor, type this:

```
[Desktop Entry]
Type=Application
Exec=gnome-shell --replace
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Gnome Shell
Name=Gnome Shell
Comment[en_US]=
Comment=

```

Press CTRL+O and then ENTER (to save), after that press CTRL+X (to quit nano).

This will make so that the command "gnome-shell --replace" will run at login, because of some reason it doesn't.

Hope this will solve your problem!
Worked for me on LMDE!

---

