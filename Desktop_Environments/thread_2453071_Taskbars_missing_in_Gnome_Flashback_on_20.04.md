---
title: "Taskbars missing in Gnome Flashback on 20.04"
date: 2020-11-02
forum: Desktop Environments
---

### Post by deck on 2020-11-02
I like the Gnome Flashback desktop.  The problem is my taskbars have disappeared.  They disappeared after having a internal network problem while logged into my Ubuntu system via xrdp from a Windows system in my house that is about 300 feet away from the shed where my Linux system is.  This had occurred once before; I re-installed Gnome Flashback (gnome-session-flashback) and xrdp.  I used the version 1.2 install script from Griffon's IT Library for the initial install and the reinstallation.  After this the desktop came back.

I did the same this time with the difference that I added sound to the xrdp installation.  My taskbars are still missing.  I don't know what is going wrong but this occurs on all users on the Ubuntu System.

---

### Post by deck on 2020-11-02
UPDATE.  I searched the forums and found a thread where some one was having problems with the taskbars in 18.04.  The advice was to do a ">killall gnome-panel" and then restart gnome-panel.  When I tried to do the killall, I found that gnome-panel was not running.  I ran gnome-panel putting it in the background.  Lo and behold, the taskbars reappeared.  What is supposed to start up the gnome-panel application?  I can't seem to find it and it is not installing properly when I install gnome-session-flashback.

---

### Post by kansasnoob on 2020-11-03
It typically doesn't need to be added directly into startup apps so I'd first try:

```
sudo dpkg-reconfigure gnome-panel
```

Then either reboot or logout and back in. If the output of that command returns any errors it might be helpful in troubleshooting the problem.

---

### Post by deck on 2020-11-03
> **kansasnoob said:**
> It typically doesn't need to be added directly into startup apps so I'd first try:

```
sudo dpkg-reconfigure gnome-panel
```

Then either reboot or logout and back in. If the output of that command returns any errors it might be helpful in troubleshooting the problem.

That didn't work.  I got no error messages at all.    I know that xdg starts my gnome session but I can't find where gnome-panel is called which may be because it is missing.  I have another system with Ubuntu 18.04 and will set up gnome-flashback there.  Then I will go look for gnome-panel if it successfully loads and runs flashback.

---

