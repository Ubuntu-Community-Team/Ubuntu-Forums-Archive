---
title: "Window buttons in panel"
date: 2014-08-22
forum: Desktop Environments
---

### Post by Svento on 2014-08-22
For many years I've used the panel application Window-buttons, where the titelbar buttons of maximized windows are shown in the panel - so that the titelbar can be hidden when windows are maximized.

Now after a reinstallation of 12.04 I can't make them work. Synaptic tells me they're installed, but they're not displayed as an option among the other panel applications. Is there a way to fix this?

---

### Post by Toz on 2014-08-22
What you're looking for is called the xfce4-windowck-plugin. Unfortunately, its not part of the Ubuntu respositories. There was an article recently on webupd8 on how to manually build and install this plugin. See [http://www.webupd8.org/2014/07/xubuntu-how-to-put-maximized-windows.html]("http://www.webupd8.org/2014/07/xubuntu-how-to-put-maximized-windows.html") for more information.

---

### Post by Svento on 2014-08-22
[B]hwh@jhwh:~$ cd ~/xfce4-windowck-plugin-0.3.0
jhwh@jhwh:~/xfce4-windowck-plugin-0.3.0$ ./autogen.sh --prefix=/usr
xdt-autogen: This version of xdt-autogen (4.8.0) is too old.
             Version 4.9.1 or greater is required.
jhwh@jhwh:~/xfce4-windowck-plugin-0.3.0$ 
[/B]

---

### Post by Toz on 2014-08-23
Yes, this is where it gets complicated. According to the webupd8 article, you need Xfce version 4.10 to be able to build the plugin. Unfortunately, 12.04 comes with 4.8. There is a PPA referenced in that link for installing Xfce 4.10. I guess its up to you if you want to do the extra work and upgrades for this one package.

---

### Post by Svento on 2014-08-23
Installation complete, no error messages, but still there are no window-buttons among the panel applications.

---

### Post by Toz on 2014-08-23
The panel plugin is called "Window Header - Buttons" and "Window Header - Title".

[ATTACH=CONFIG]255763[/ATTACH]

Are they listed in yout panel plugins? And if so, have you added them to the panel?

---

### Post by Svento on 2014-08-23
Yes I've always had them before, but they're not available now.

---

### Post by Toz on 2014-08-23
I'm not sure what to say. To validate the process, I just installed a fresh 12.04 Xubuntu in a VM and ran through the instructions on the webupd8 page linked above, and it they show up and work fine for me.

Is your system 32 bit or 64 bit?
Did you run "sudo make install"?
Do the libwckbuttons.so and libwindowck.so libraries exist in /usr/lib/xfce4/panel/plugins?

Have you tried logging out and back in again?

---

### Post by Svento on 2014-08-23
32.

Now it all suddenly became very irrelevant... When I log in into Gnome Classic - Unity shows up! I've set the launcher to autohide, so that I can use AWN where I can at least have a Gnome Main-menu.

Very strange. But as long as I don't need to see the launcher, I believe I can live with Unity.

---

