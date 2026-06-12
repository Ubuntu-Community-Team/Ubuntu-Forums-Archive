---
title: "How can I add an item to the Gnome 3 menu?"
date: 2020-11-18
forum: Desktop Environments
---

### Post by Paddy Landau on 2020-11-18
**EDIT: It's suddenly started to work!**

I've tried following the instructions found on the 'net, but I can't get the following to work.

I have Ubuntu 20.04, and a script that I've written.

I want the script to be available from the normal Gnome 3 menu (when you press the Super key and start typing the name, or press the Applications button) &#8212; but it must be available to all users, not just me.

Here's what I've done.

[LIST=1]
[*]Create the script (named *test*) to start a GUI application. Save this script to /usr/local/sbin/test. I've given read and execute permissions to everyone.
[*]Create a .desktop file for the item, which I've put into /usr/share/applications/test.desktop. The contents are as follows.
```
[Desktop Entry]
Name=Test
Comment=This is a foobar test
Keywords=foobar;
OnlyShowIn=GNOME;Unity;
Exec=/usr/local/sbin/test %u
Icon=/usr/share/icons/test.png
StartupNotify=true
Terminal=false
Type=Application
StartupWMClass=ApplicationName
Categories=Utility;
```
[*]I've tested that the script works:
```
/usr/local/sbin/test
```
[/LIST]
Now, even after I restart, when I press the Super key, I search for my app using the keyword "test" (from the Name) or "foobar" (from the Keywords), but neither returns the result. How can I fix this, please?

---

