---
title: "Ubuntu 11.10 Icons and Window Panel Lost."
date: 2011-10-23
forum: Desktop Environments
---

### Post by bctis on 2011-10-23
Hi Ubuntu Forum,
Here is the screenshot of what happened to my windows in Ubuntu and it is really annoying. 

[IMG]http://img854.imageshack.us/img854/4350/screenshotat20111023170.png[/IMG]

I want the black pannel on top of the windows to be back and Icons return to normal, I really have no idea how I did this, except that one day I just lost all icons and then I installed gnome tweak tool and got this crappy icons instead plus I lost my black panel at the top. Please Help.

Thanks in advance.

---

### Post by bctis on 2011-10-25
Isn't There Anybody That can Help me with this?

---

### Post by jasonread on 2011-10-25
Hi, afraid I can't help but I can commiserate. I have the same issue. I have tried changing the default icon set from gnome-tweak and dconf-editor but, while I can change the icons in the launcher, I can't seem to change the icons in any windows. Sigh...

---

### Post by frettfreak on 2011-10-28
i had the same thing happen to me.. 

First a few questions. 

Did you try installing gnome-shell or any theme?

you should be able to go into the gnome tweak tool and just make sure all teh "defualt" themes are selected and it SHOULD get you back to normal.  If this doesnt work, you can go into terminal and use the following:

```
unity --reset
```

---

### Post by wildjiji on 2011-10-29
I had the same issue.
but I was able to fix the issue with following command in terminal.

```
gsettings set org.gnome.settings-daemon.plugins.xsettings active true
```

---

### Post by jackdale on 2011-10-29
This is a problem that has been happening for a while on virtual machine installations of ubuntu (e.g. VirtualBox and VMWare).   Is yours a virtual installation of ubuntu?  I thought they'd solved it in 11.10.

(Also, if either of the two suggestion fixed the problem, please mark the thread as [solved])

---

### Post by typhoon_tip on 2011-10-29
Actually you can try to use Advanced Settings to change individual themes for icons, window borders and controls, which is the program that comes with gnome-tweaks. Try to see if the themes are still listed or not.

---

### Post by cleanthes on 2011-11-29
> **wildjiji said:**
> I had the same issue.
but I was able to fix the issue with following command in terminal.

```
gsettings set org.gnome.settings-daemon.plugins.xsettings active true
```

Worked perfectly for me - thanks!

---

