---
title: "Trusty Dash not finding apps with manually created desktop file"
date: 2014-04-27
forum: Desktop Environments
---

### Post by johnaaronrose on 2014-04-27
On a clean install of Trusty 64 bit desktop, desktop configuration files created manually  e.g. by Manage Launchers (which worked in Ubuntu Precise) are not found  by the Dash even though they are in /usr/share/applications. Why is  that? For example, the contents of Magnifier.desktop:[SIZE=2]
[/SIZE]
[SIZE=2][/SIZE]#!/usr/bin/env xdg-open
#ManageLauncher_Version=2.0 beta
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Magnifier
Comment=Virtual Magnifying Glass
Exec=/usr/bin/vmg
Path=/usr/bin/
Icon=/usr/share/magnifier/icon3.png
Categories=Accessibility;

PS why is the "#!/usr/bin/env xdg-open" present when it is not  present in any of the standard desktop files (e.g. evince.desktop)?

---

### Post by ppanish on 2014-06-23
I'm having a related issue with Dash filters. I've installed an application (Codeblocks) which shows up generically in the Dash with no filters applied. Presumably this was because no Categories were specified in the provided codeblocks.desktop file. 

I want this to be displayed as an application in the Developer section under Applications->filters, and modified the file to include the Categories parameter using other files in /usr/share/applications as templates. I've had no luck in getting this to show up in the desired categories. Example codeblocks.desktop file follows:

```
[Desktop Entry]
#Encoding=UTF-8
Version=1.0
Type=Application
Name=Code::Blocks svn build global
Icon=codeblocks
Path=/home/ppanish/opt/codeblocks-svn/trunk
#Terminal added
Terminal=false
Exec=codeblocks
StartupNotify=false
StartupWMClass=Codeblocks
OnlyShowIn=Unity;
X-UnityGenerated=true
Categories=System;Utility;Developer;
```

---

### Post by mc4man on 2014-06-23
> **ppanish said:**
> I'm having a related issue with Dash filters. I've installed an application (Codeblocks) which shows up generically in the Dash with no filters applied. Presumably this was because no Categories were specified in the provided codeblocks.desktop file. 

I want this to be displayed as an application in the Developer section under Applications->filters, and modified the file to include the Categories parameter using other files in /usr/share/applications as templates. I've had no luck in getting this to show up in the desired categories. Example codeblocks.desktop file follows:

```
[Desktop Entry]
#Encoding=UTF-8
Version=1.0
Type=Application
Name=Code::Blocks svn build global
Icon=codeblocks
Path=/home/ppanish/opt/codeblocks-svn/trunk
#Terminal added
Terminal=false
Exec=codeblocks
StartupNotify=false
StartupWMClass=Codeblocks
OnlyShowIn=Unity;
X-UnityGenerated=true
Categories=System;Utility;Developer;
```
try Development instead

---

