---
title: "How can I hide desktop icons?"
date: 2019-05-19
forum: Desktop Environments
---

### Post by breaktheebeat on 2019-05-19
The title pretty much says it all, I wish to hide my desktop icons, I'm running Ubuntu 19.04. I've tried to run 'sudo gsettings set org.gnome.desktop.background show-desktop-icons false' and when I run 'sudo gsettings get org.gnome.desktop.background show-desktop-icons' it outputs 'false'. I've also tried switching it on and off both in the command line and Gnome Tweaks. Any help would be appreciated, thanks!

---

### Post by LwIh%*7 on 2019-05-19
Unfortunately I don't see how with the new extension being used however if by hiding you mean the folder and the trash can then install gnome-tweaks from the terminal then load gnome-tweaks up and under the extension menu section you'll see the Desktop Icon extension listed click on the settings on that extension and turn the slider of the personal folder and the rubbish bin to off then it should be hidden you can't however remove that extension fully otherwise it'll remove the ubuntu-desktop component which is not wise to do.

---

### Post by yetimon_64 on 2019-05-19
> **breaktheebeat said:**
> ... I'm running Ubuntu 19.04. I've tried to run 'sudo gsettings set org.gnome.desktop.background show-desktop-icons false' and when I run 'sudo gsettings get org.gnome.desktop.background show-desktop-icons' it outputs 'false'....

I've never run the gsettings command or dconf-editor with sudo to change such user settings with Ubuntu. Your attempts to set them there will most likely be affecting the setting for the root account, [s]if the setting even exists as the root account normally is locked and you don't log into a desktop for root (again, under NORMAL circumstances). This is probably why the second "get" command failed as well.[/s] **Edit:** I just noted that it seems your command did work if the result was "false" but has only affected the root acoount settings because of sudo being used. I slightly misread your opening post initially there.

Try them again without sudo eg...
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
and
```
gsettings get org.gnome.desktop.background show-desktop-icons 
```

I am actually not running the main Ubuntu flavor so can't test this fully here. I'm either on Xubuntu 18.04 or Ubuntu Mate 18.04 (dual booting the two) but over the years have used the Unity and gnome desktops extensively, I just don't run a gnome based desktop at all at the moment. 

Hope this works for you, good luck. Yeti.

---

### Post by Frogs Hair on 2019-05-20
Have you checked settings/desktop or in the gnome tweak tool ?

---

### Post by LwIh%*7 on 2019-05-22
> **yetimon_64 said:**
> I've never run the gsettings command or dconf-editor with sudo to change such user settings with Ubuntu. Your attempts to set them there will most likely be affecting the setting for the root account, [s]if the setting even exists as the root account normally is locked and you don't log into a desktop for root (again, under NORMAL circumstances). This is probably why the second "get" command failed as well.[/s] **Edit:** I just noted that it seems your command did work if the result was "false" but has only affected the root acoount settings because of sudo being used. I slightly misread your opening post initially there.

Try them again without sudo eg...
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
and
```
gsettings get org.gnome.desktop.background show-desktop-icons 
```

I am actually not running the main Ubuntu flavor so can't test this fully here. I'm either on Xubuntu 18.04 or Ubuntu Mate 18.04 (dual booting the two) but over the years have used the Unity and gnome desktops extensively, I just don't run a gnome based desktop at all at the moment. 

Hope this works for you, good luck. Yeti.

Just so you know I would have suggested this to the OP if it worked but I've already tried and tested those commands on the day of release the Desktop Icon extension overwrites it and forces the desktop icons on you.

---

