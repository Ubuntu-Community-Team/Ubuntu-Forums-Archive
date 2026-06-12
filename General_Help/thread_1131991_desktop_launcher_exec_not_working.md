---
title: "desktop launcher exec not working"
date: 2009-04-21
forum: General Help
---

### Post by manolo_asdf on 2009-04-21
My desktop launcher (IntelliJ.desktop) does not work, the app just not starts. The Exec command seems to have problems, though when executing the same command on the terminal the app starts correctly.

Does somebody see what is going wrong?

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=IntelliJ
Comment[en_US]=
Comment=
Exec=/bin/sh -c "cd /usr/local/share/idea-9732/bin && ./idea.sh"
GenericName[en_US]=
GenericName=
Icon[en_US]=gnome-panel-launcher
Icon=/usr/local/share/idea-9732/bin/idea32.png
MimeType=;
Name[en_US]=IntelliJ
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

---

### Post by VCoolio on 2009-04-21
sh -c /usr/local/share/idea-9732/bin/idea.sh
as command should do the trick. Also there are two name lines and several twice with enUs for one of them. That seems unnecessary. Try my line first in terminal to see if it works.

---

### Post by manolo_asdf on 2009-04-21
I changed it to:
sh -c /usr/local/share/idea-9732/bin/idea.sh

But still it does not work as a launch command. Here the update.

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=test
Exec=sh -c /usr/local/share/idea-9732/bin/idea.sh
Name=test
Icon=gnome-panel-launcher

```

---

### Post by CatKiller on 2009-04-21
What's the command supposed to do? If it's supposed to be doing something in a Terminal then you won't see any output if you don't do it in a Terminal. If that's the case, setting ```
Terminal=true
``` will be necessary.

---

### Post by manolo_asdf on 2009-04-22
The app (IntelliJ Java IDE) must be started through idea.sh. 

I changed it to Terminal=true now, but still it does not start. Is there somewhere a log for launching *.desktop or a command-line tool for launching desktop files, so I can better see what goes wrong?

---

### Post by chandrakant11 on 2009-08-20
It Seems you have set environment variable in .bashrc file. Place the environment setting in .profile file for the execution of sh file that fetch values from ENVIRONMENT variable like JAVA_HOME etc. 
We were facing the same problem, launcher of TOMCAT were not working. After setting JAVA_HOME in .profile is working fine. 

You can test what variable is missing by creating a sh file
for example.
#!/bin/sh
echo "Test Missing"
/home/ubuntu/jakarta-tomcat-4.1.18/bin/startup.sh
sleep 100000

Make launcher of this sh. There u will get error if exist else if work fine.
Hope this will help you.

---

### Post by manolo_asdf on 2009-09-02
indeed, thanks this worked.

i will now move the non-bash-only envs (like JAVA_HOME) from .bashrc to .profile

---

