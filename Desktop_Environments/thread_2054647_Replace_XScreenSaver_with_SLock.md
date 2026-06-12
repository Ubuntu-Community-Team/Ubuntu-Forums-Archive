---
title: "Replace XScreenSaver with SLock"
date: 2012-09-07
forum: Desktop Environments
---

### Post by pantagruel on 2012-09-07
Hi, I'm a bit tired of the basic screensaver, could anyone direct me to some information on how to replace the execution of XScreenSaver with SLock?
Where would I find the place where XScreenSaver is called?
Where can I find information on these topics?, as I'd like to change other details as well later.
Thanks

---

### Post by Toz on 2012-09-08
Hello and welcome to the forums.

To install slock:
```
sudo apt-get install suckless-tools
```
 
The easiest way to use slock instead of xscreensaver is to uninstall xscreensaver:
```
sudo apt-get remove xscreensaver
```

Other options instead of uninstalling xscreensaver is to make sure its not running (Xubuntu will use slock if it can't find xscreensaver or gnome-screensaver - have a look at the contents of /usr/bin/xflock4 to confirm) - remove it from Autostart. 

Or replace the xflock4 executable with a link to slock:
```
sudo mv /usr/bin/xflock4 /usr/bin/xflock4.orig
sudo ln -s /usr/bin/slock /usr/bin/xflock4
```
...just keep in mind that this last option if xfce4-utils ever gets updated, it will reset this and you will have to run these commands again.

As to where to find this information, you can search here on ubuntuforums, the Xfce forums, or ask in the #xfce or #xubuntu irc channels. Google is always an option as well.

---

### Post by pantagruel on 2012-09-08
Thanks for the help Toz, but I still have some questions.  

In  /usr/bin/xflock4, it looks a bit like this:

if pgrep xscreensaver > /dev/null 2>&1; then
    xscreensaver-command -lock 
elif pgrep -f gnome-screensaver 2>/dev/null; then
    gnome-screensaver-command --lock
elif test x"`which slock 2>/dev/null`" != x""; then
etc

Could someone explain what the conditionals mean? Why does each command get a different one?
Can I have some script that runs when I login that sets up my preference (like Arch's .xinit)? i.e. I would prefer a more permanent and personalizable solution, like having one user be simple and use slock, while another uses XScreensaver and has fancy stuff.

What calls xflock4? i.e. how can I modify the conditions for screen lock from a terminal?

Thank you very much

---

### Post by Toz on 2012-09-08
> **pantagruel said:**
> Thanks for the help Toz, but I still have some questions.  

In  /usr/bin/xflock4, it looks a bit like this:

if pgrep xscreensaver > /dev/null 2>&1; then
    xscreensaver-command -lock 
elif pgrep -f gnome-screensaver 2>/dev/null; then
    gnome-screensaver-command --lock
elif test x"`which slock 2>/dev/null`" != x""; then
etc

Could someone explain what the conditionals mean? Why does each command get a different one?

Basically, first command asks if there is a process called xscreensaver is running and if so, use xscreensaver-command to lock the screen...

...or if gnome-screensaver is running then use the gnome-screensaver-command to lock the screen...

...or if slock exists, use slock to lock the screen...

...otherwise use xlock

> Can I have some script that runs when I login that sets up my preference (like Arch's .xinit)? i.e. I would prefer a more permanent and personalizable solution, like having one user be simple and use slock, while another uses XScreensaver and has fancy stuff.
As per the above script, if xscreensaver or gnome-screensaver are not running, then slock will be used. So, for each user that you want slock to be used, make sure that xscreensaver or gnome-screensaver are not running. Look in Settings Manager -> Session and Startup -> Application Autostart and if xscreensaver is listed there, remove it. Otherwise, kill the screensaver process:
```
pkill xscreensaver
```
...and logout and back in again. Just keep in mind that slock doesn't have idle timer functionality, so it won't be able to lock the screen after a period of inactivity. You'll have to lock manually.

> What calls xflock4? i.e. how can I modify the conditions for screen lock from a terminal?
xflock4 is an Xfce utility that is mapped to Ctrl+Alt+Del. You can change that mapping to run slock instead. Have a look at "Settings Manager -> Keyboard -> Application Shortcuts". Sorry, what do you mean by "modify the conditions for screen lock from a terminal"? You could always just run "slock" manually or create a launcher for it.

I also just realized that if you disable xscreensaver, you will lose screen lock functionality if you want the screen to lock on lid close. To fix that, you'll need to edit the /etc/acpi/lid.sh file to add the proper code to use slock.

slock is more of a manual tool.

---

