---
title: "several small E17 problems"
date: 2008-03-14
forum: Desktop Environments
---

### Post by gobbles414 on 2008-03-14
I'm trying to configure E17 well enough so that I can make it my default user interface in Ubuntu 7.10. I've installed the E17 user interface by following the directions from [here]("http://wiki.enlightenment.org/index.php/E17_User_Guide/Installing_using_Linux_distribution_packages#Ubuntu_Linux"). Neither the *Net* nor *Wlan* modules seem to provide a way for me to manage my wireless internet settings. So, I've installed [Wicd]("http://wicd.sourceforge.net/"). I've gotten the tray applet for Wicd working in GNOME. But, there doesn't seem to be a Wicd module that I can add to my iBar in E17. Here's what I need help doing:

* Finding a Wicd module to load into my iBar
* Changing the clock module from an analog clock to a digital clock.
* Creating a trash on my desktop (like in gOS Rocket)
* Automatically be informed of new system updates
* Gain access to Synaptic (software installations) and the Restricted Drivers Manager (3D acceleration)
* Change my DPI
* Can I control the Banshee music manager from the iBar?
* Launching Banshee says "Your environment is not properly setup to use DBus..."

Thanks in advance for the help!

---

### Post by smartboyathome on 2008-03-14
Use the Network module and set the double click action to open WICD (run alacarte to get the command for it, I currently don't have it installed on this machine).

The trash icon on the desktop won't work, since Nautilus isn't the default file manager and neither is thunar (assuming you use either of those)

Enable and use the TClock module to have a digital clock

Automatically being informed needs a system tray, which e17 has refused to make.

Use alacarte to create a "System Tools" folder with your most often used GNOME sysetm tools (ie, synaptic, software sources, appearance, etc).

I think this has to be done with Xorg, not sure how though.

iBar isn't a system tray, so technically no.

To launch banshee, enable the dbus module and then try again.

---

### Post by gobbles414 on 2008-03-15
> **smartboyathome said:**
> Use the Network module and set the double click action to open WICD (run alacarte to get the command for it, I currently don't have it installed on this machine).

The trash icon on the desktop won't work, since Nautilus isn't the default file manager and neither is thunar (assuming you use either of those)

Enable and use the TClock module to have a digital clock

Automatically being informed needs a system tray, which e17 has refused to make.

Use alacarte to create a "System Tools" folder with your most often used GNOME sysetm tools (ie, synaptic, software sources, appearance, etc).

I think this has to be done with Xorg, not sure how though.

iBar isn't a system tray, so technically no.

To launch banshee, enable the dbus module and then try again.

Thanks for your reply. I'll give your suggestions a try, and report back soon on my progress.

---

### Post by kellemes on 2008-03-15
Can't answer your questions I'm afraid..
Just want to let you know about [OpenGEU]("http://opengeu.intilinux.com/Home.html").
This **is** Ubuntu with Gnome/Enlightenment, looks very cool, and works great for me in a vm.

---

### Post by gobbles414 on 2008-03-15
> **kellemes said:**
> Can't answer your questions I'm afraid..
Just want to let you know about [OpenGEU]("http://opengeu.intilinux.com/Home.html").
This **is** Ubuntu with Gnome/Enlightenment, looks very cool, and works great for me in a vm.

Thanks for the info. OpenGEU came up in my research. Can one do automatic system updates in OpenGEU? If so, I'll try it when version 8.04 is released.

---

### Post by kellemes on 2008-03-15
> **gobbles414 said:**
> Thanks for the info. OpenGEU came up in my research. Can one do automatic system updates in OpenGEU? If so, I'll try it when version 8.04 is released.

It **is** Ubuntu, and so it has all Ubuntu has, only with the beautiful combination of Gnome/E17.

---

### Post by gobbles414 on 2008-03-15
> **kellemes said:**
> It **is** Ubuntu, and so it has all Ubuntu has, only with the beautiful combination of Gnome/E17.

Thanks... I only asked because the E17 interface that I'm using doesn't seem to allow for automatic updates. It definitely sounds like OpenGEU is worth trying. Like I said, I'll probably wait for version 8.04 -- but I may try OpenGEU earlier.

---

### Post by smartboyathome on 2008-03-16
> **gobbles414 said:**
> Thanks... I only asked because the E17 interface that I'm using doesn't seem to allow for automatic updates. It definitely sounds like OpenGEU is worth trying. Like I said, I'll probably wait for version 8.04 -- but I may try OpenGEU earlier.

Automatic updates doesn't happen without a tray. Try installing one like trayer and seeing if that helps. :)

---

### Post by sashko on 2008-03-17
for example 
sudo apt-get stalonetray

---

