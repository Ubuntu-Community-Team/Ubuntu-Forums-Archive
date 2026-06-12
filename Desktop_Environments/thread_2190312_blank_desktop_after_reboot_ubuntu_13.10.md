---
title: "blank desktop after reboot ubuntu 13.10"
date: 2013-11-26
forum: Desktop Environments
---

### Post by duronjoshua on 2013-11-26
I was trying to configure an alternative openbox environment on ubuntu 13.04. 
I can't exactly remember what I edited, I think it was just the .rc files for some panels and menus, so I'm not too sure what could have caused a problem. Anyway, after logging back into my unity environment, I had only the sidebar and top panel, the area that would normally be my desktop was just black. I ran [FONT=Ubuntu Mono]gsettings set org.gnome.settings-daemon.plugins.background active true , and it brought back my wallpaper, but that was it. My folders listed in the directory aren't showing up on on the desktop, nor can I interact with it in anyway (right click, select etc)

Tutorials I used

[/FONT][URL="http://www.maketecheasier.com/configure-andcustomize-openbox/"]http://www.maketecheasier.com/configure-andcustomize-openbox/
[/URL][FONT=Ubuntu Mono]
[/FONT][URL="http://cookieshq.co.uk/posts/openbox-a-windows-environment-for-hackers/"]http://cookieshq.co.uk/posts/openbox-a-windows-environment-for-hackers/
[/URL][FONT=Ubuntu Mono]
[/FONT][http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310](http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310)[FONT=Ubuntu Mono]
[/FONT]

Any help and/or suggestions would be greatly apreciated

---

### Post by chrissie-c-l on 2013-11-26
seems like I just got the same problem as you and just posted another forum topic as it at the same time.  Hopefully this bug gets fixed.

---

### Post by duronjoshua on 2013-11-26
heh
I'm not sure if it was a bug or an error on my part. I edited a few .rc scripts, but I can't think of one that would effect nautilus that way.

---

### Post by duronjoshua on 2013-11-26
[TABLE="width: 613"]
[TR="bgcolor: transparent !important"]
[TD="class: code, bgcolor: transparent !important"]sudo gsettings set org.gnome.desktop.background show-desktop-icons false; &

gsettings set org.gnome.desktop.background show-desktop-icons false;

I THINK IT MIGHT BE THIS



[/TD]
[/TR]
[/TABLE]

---

### Post by duronjoshua on 2013-11-26
Sure enough, that fixed it. Do you remember doing something similar? @Chrissie
I just changed the statements to true and it fixed everything

---

### Post by mc4man on 2013-11-26
When you run gsettings with 'sudo' you are setting root's gsettings not your user,  so generally that should be avoided.

---

