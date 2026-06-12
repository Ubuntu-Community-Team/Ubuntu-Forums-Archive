---
title: "Clean install of 11.10, removable media does not show on desktop."
date: 2011-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bobsageek on 2011-10-16
Greets, did a clean install of 11.10 on Thursday and all went well but no removable media of any sort (thumb drives, USB hard drives, DVD/CD) show up in Nautilus and the side bar, but no the desktop. I still have options to eject and safely remove, but was expecting the mounted item to show on desktop? Did this change in 11.10 or do I need to adjust something? I took a quick look through gconf-edit but didn't see anything obvious. 

Thanks in advance for any assistance.

Sorry, thought I was in the general help section, although the machine in question is a Dell N7110. Mods feel free to move.

---

### Post by mikewhatever on 2011-10-16
In 11.10, install dconf-tools, run dconf-editor and navigate to /org/gnome/nautilus/desktop. Check the 'volumes-visible' box, and if it's already checked, uncheck and then recheck it. Volume icons should be the desktop now.

---

### Post by bobsageek on 2011-10-16
I actually don't mind it, I've long been a proponent of a clean desktop and usually have windows open that cover them up anyway, it's just new-ish behavior. Also, when running the System Testing app the section on mounting a USB hard drive returns a failed result because the icon does not appear on the desktop. 

If someone can validate I'll gladly file a bug report. Thanks.

---

### Post by az_s_za on 2011-10-18
I would also like to put my devices back onto the desktop.  Unfortunately the desktop option no longer appears in gconf-editor/apps/nautilus.

Does anyone know how to do this now?

---

### Post by jahst on 2011-10-30
I've also wanted to do this.. so finally got around to figuring it out.

Following this thread:
[http://askubuntu.com/questions/62756/where-do-i-set-use-time-for-policy]("http://askubuntu.com/questions/62756/where-do-i-set-use-time-for-policy")

following rinzwind steps for time for policy you can do the following:

In terminal:


```
gsettings list-recursively | grep nautilus|more
```


one entry should look like this:
**org.gnome.nautilus.desktop volumes-visible false**


then type this to set it to true

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

logout or restart nautilus.

---

### Post by az_s_za on 2011-10-31
awesome.  thanks.

suggest you mark this "solved" Bob.

---

