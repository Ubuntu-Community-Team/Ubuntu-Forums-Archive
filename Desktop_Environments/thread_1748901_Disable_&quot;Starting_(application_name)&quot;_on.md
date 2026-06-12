---
title: "Disable &quot;Starting (application name)&quot; on gnome panel?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by _T_ on 2011-05-04
I would like to disable the notification in the gnome panel that adds a new button stating "Starting *insertappnamehere*" to the gnome panel everytime I launch a program. Quite often this notification is still hanging around well after my program has fully launched, not to mention the "taskbar shuffle dance" this causes.

I'm not referring to notify-osd, I've already disabled that annoyance...

In synaptic I see the libstartup-notification0 package, but if I mark it for uninstallation synaptic informs me it will also remove various things such as nautilus, metacity, firefox and compiz and about 40 more, and install about 60 additional packages . Seriously??? Just to not be told that I clicked an icon? 

PLEASE tell me I'm missing something here...

Ubuntu 10.10
Gnome 2.32.0
Kernel 2.6.35-28-generic

---

### Post by _T_ on 2011-05-06
Bump please.

---

### Post by _T_ on 2011-05-08
Bump please.

---

### Post by Copper Bezel on 2011-05-08
I have that package installed, and I certainly don't get notifications for every application I launch. I've really never seen what you're describing here - since you brought up the comparison, is it similar to a notify-osd message?

---

### Post by _T_ on 2011-05-08
> **Copper Bezel said:**
> is it similar to a notify-osd message?
No sir, not at all. This is a button that appears in the taskbar for maybe 3 -5 seconds everytime I launch an app from the desktop icons, or from the menu. In this screenshot you can see 4 buttons, 2 on each monitor from opening gnome-terminal twice from the desktop icon.

[IMG]http://img543.imageshack.us/img543/4185/screenshotdnw.png[/IMG]

---

### Post by mc4man on 2011-05-08
This is caused by a line in Some app .desktops, to stop the behavior you'll need to edit
The line is
StartupNotify=true
You'll need to edit to
StartupNotify=false

Edit: I might as well give you a clear example - 

gksudo gedit /usr/share/applications/gnome-terminal.desktop

> [Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.32.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
[COLOR="Blue"]StartupNotify=true[/COLOR]
X-Ubuntu-Gettext-Domain=gnome-terminal


---

### Post by _T_ on 2011-05-08
I did find informtion about editing that line, but my 10.10 install has something like 2400 .desktop files total. I was expecting to find some universal setting (perhaps in gconf-editor though I've looked) to disable this for all currently installed, and any future applications I may install. Just between the applications menu and my desktop I would have to edit 77 individual files, and this doesn't include things like my image viewer, or other handler type applications that don't get launched with a shortcut, but rather by simply clicking the file to be opened, but still exhibit this behavior.

Thanks for replying though guys, I was getting a little worried no one really cared to help with such a noobish question... I have been working with gambas2 (a basic-like ide) for a while now, so if it becomes necessary that the only way to do this is by editing each file one at the time, I can probably put something together to handle this.

---

