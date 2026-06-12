---
title: "[Request] Right-click app in menu to remove"
date: 2007-11-12
forum: Desktop Environments
---

### Post by daengbo on 2007-11-12
I would like to see an option added to the application context menu in Gnome/Ubuntu. Right now there are three options:
[LIST]
[*]Add this launcher to the panel
[*]Add this launcher to the Desktop
[*]Entire menu
[/LIST]
I would like to see the following added for users in the admin group
[LIST]
[*]Remove this application
[/LIST]
Clicking the option would search for the package containing the executable (for example, " dpkg -S /usr/bin/avscan" returns "avscan: /usr/bin/avscan"). A front end to "gksudo aptitude remove avscan" could then be launched.

This would make removing unwanted applications much easier and more intuitive than it is now.

---

### Post by daengbo on 2007-11-12
The command line to achieve this looks like
> i=gcalctool.desktop;j=`grep Exec= /usr/share/applications/$i|awk -F= '{print $2}'`;k=`whereis $j|awk -F\  '{print $2}'`;sudo aptitude remove $j

I don't know how to find the launcher's name (defined by "i" here) or to do the UI stuff. There's also no error checking here, which there, of course, should be.

---

