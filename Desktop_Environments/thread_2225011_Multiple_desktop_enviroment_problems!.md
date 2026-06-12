---
title: "Multiple desktop enviroment problems!"
date: 2014-05-19
forum: Desktop Environments
---

### Post by dannyboyinpy on 2014-05-19
I am running Ubuntu 14
I recently installed xubuntu-desktop with
```
sudo apt-get xubuntu-desktop
```
so my brother could have a more windows-like enviroment. Now, the login/switch user screen is the xubuntu one. Is there a way to change this back?

thanks in advance

---

### Post by oldrocker99 on 2014-05-19
Try this:

```
sudo dpkg-reconfigure xdm
```

This should allow you to select the display manager (the screen you log into).

---

### Post by dannyboyinpy on 2014-05-27
> **oldrocker99 said:**
> Try this:

```
sudo dpkg-reconfigure xdm
```

This should allow you to select the display manager (the screen you log into).

i did this and got

```
dpkg-query: package 'xdm' is not installed and no information is availableUse dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xdm is not installed

```

---

### Post by deadflowr on 2014-05-27
See if this works
```
sudo /usr/lib/lightdm/lightdm-set-defaults --greeter unity-greeter
```

Edit: I don't think this command works anymore.
They've seemed to have change a few things.
Perhaps a little digging is in order.
Basically though, what I've mentioned is what you need to switch.
It's the greeter that needs changing, and not the display manager.

This closed thread, should help provide some clues as to where the files are that house the greeter
[http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)

---

### Post by grumblebum2 on 2014-05-27
_[COLOR="#FF0000"]EDIT[/COLOR]_
I installed lightdm-gtk-greeter and found it adds this config... **/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf**
which overrides Ubuntu's **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** because of the numbering.

Run in terminal ...
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
```
and comment out([COLOR="#FF0000"]#[/COLOR]) the line **greeter-session=lightdm-gtk-greeter**
eg
```
[SeatDefaults]
[COLOR="#FF0000"]#[/COLOR]greeter-session=lightdm-gtk-greeter
```
----------------------------------------------------------------------------------------------------------------------


You could probably just uninstall lightdm-gtk-greeter which is not installed in ubuntu.
Simulate first...to check what else it may want to uninstall.
```
sudo apt-get **--simulate** remove lightdm-gtk-greeter
```

Check the "The following packages will be REMOVED:" section.

Omit the **--simulate** to remove...
```
sudo apt-get remove lightdm-gtk-greeter
```

---

### Post by dannyboyinpy on 2014-05-29
Thank you very much! I commented it out and am back to the default greeter. Thank you also to deadflowr and oldrocker99 for caring about my question!

---

### Post by deadflowr on 2014-05-29
> **dannyboyinpy said:**
> Thank you very much! I commented it out and am back to the default greeter. Thank you also to deadflowr and oldrocker99 for caring about my question!


If the problem has been solved, please[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"] mark this thread as solved.
[/URL]

---

