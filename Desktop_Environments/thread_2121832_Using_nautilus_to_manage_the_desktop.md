---
title: "Using nautilus to manage the desktop"
date: 2013-03-03
forum: Desktop Environments
---

### Post by Seddy on 2013-03-03
I'm currently trying to use nautilus for desktop managment, but I can't get it to work.

My OS: Xubuntu 12.10 (Quantal Quetzal)

What I did:
- uninstalled thunar
- installed nautilus
- mv /usr/bin/xfdesktop /usr/bin/xfdesktop-bin
- ln -s /usr/bin/nautilus /usr/bin/xfdesktop

In other tutorials, regarding this replacement of thunar with nautilus, this works perfectly, but for me I end up with a black and empty desktop.
I figure that the problem is that nautilus is behaving as if it was started with the "--no-desktop" flag, but I have no idea why it behaves like this.

Does anyone have an idea on how to fix this?

---

### Post by Frogs Hair on 2013-03-03
I would check preferred applications > utilities and see if nautilus is the selected as the file manager.  To restart Nautilus use the following which is often in the instructions when installing a different file manager  . ```
nautilus -q  
```
The context menu actions may change when you remove Thunar.

---

### Post by Seddy on 2013-03-03
> **Frogs Hair said:**
> [...] selected as the file manager [..] It allready is set to nautilus.

> **Frogs Hair said:**
> ```
nautilus -q  
``` This changes nothing, but this is no surprise as I did a reboot in the process of setting up what I currently have.

---

### Post by Frogs Hair on 2013-03-03
I found this regarding exo-utils . [http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu](http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu)

---

### Post by Seddy on 2013-03-03
> **Frogs Hair said:**
> I found this regarding exo-utils . [http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu](http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu)
"exo-preferred-applications" is the application that you already mentioned, so this changes nothing.
The link also mentions two variable in the gnome-config, but both are already set to true on my system.

---

### Post by Frogs Hair on 2013-03-03
I thought as much . Because I am using a newer version of Thunar via PPA I have a different version exo-utils so  couldn't verify what was installed previously.  I don''t know what to suggest if the entire configuration is pointing to Nautilus. 

I have the  XFCE session  on  Ubuntu and not Xubuntu and in the Gnome Tweak Tool there is a setting to have the file manager handle the desk top and that corresponds to what ever is set as default. I have had Pantheon, Nautilus and Thunar set as default at one time or another and don't understand the difficulty.    


If you want to give the latest version Thunar a try see the link.  

[http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html](http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html)

---

### Post by Seddy on 2013-03-05
Problem solved.

The solution:
- Install gnome-tweak-tool
- In gnome-tweak-tool: File Manager->Have file manager handle the desktop.

---

### Post by Peripheral Visionary on 2013-03-05
Be sure to use the Thread Tools to mark it [SOLVED]

---

