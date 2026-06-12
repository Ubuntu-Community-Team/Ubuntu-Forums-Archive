---
title: "Starting Emerald with Beryl"
date: 2007-02-12
forum: Desktop Environments
---

### Post by russbuss on 2007-02-12
I have successfully gotten Beryl and Emerald to work under Edgy.

What follows might be splitting hairs, but the only way I can seem to get Emerald to start is, after starting Beryl, to launch Emerald from a terminal window.  This has the unwanted side effect of requiring that said terminal window stay open indefinitely  if I want window borders (yes, I know I can minimize it, but I'm splitting hairs here....).  Is there any way to set Emerald to launch automatically with Beryl or, at the very least, launch Emerald without using a terminal window?

I have read about some people setting Emerald as the default window manager under System -> Preferences -> Beryl Settings Manager.  However, I haven't found any place in the settings manager to do this.

Thanks in advance if anyone can help me out.



-Ben.

---

### Post by john.nicholls on 2007-02-12
To launch a program without opening (and leaving open) a terminal window, you could press alt-F2 to get into the run program window.

---

### Post by barney_1 on 2007-02-12
I had been having trouble like yours in the past and ended up using a script to start beryl and emerald when I logged in.  This method was developed from the following guide:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Create a startup script:
```
sudo nano /usr/bin/startberyl.sh
```

Paste this code into the editor and press CTRL-X to save:
```
#!/bin/sh
beryl-manager &
killall emerald
emerald &
sleep 4
exec gnome-session

```

Make the script executable:
```
sudo chmod a+x /usr/bin/startberyl.sh
```

Create a beryl session option at login:
```
/usr/share/xsessions/Beryl.desktop
```

Paste this code to the editor then save it by pressing CTRL-X
```
[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application
```

Reboot.  When you get to the login screen click the icon on the bottom left and choose the session called "Beryl"

---

### Post by kevinlyfellow on 2007-02-19
one way to issue a command with a terminal window and be able to close it after is like this

```

command &
disown -a
exit

```

---

