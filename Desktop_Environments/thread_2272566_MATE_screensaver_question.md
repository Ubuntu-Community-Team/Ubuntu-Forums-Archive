---
title: "MATE screensaver question"
date: 2015-04-07
forum: Desktop Environments
---

### Post by Joe_Johnston on 2015-04-07
Hello All,

I absolutely love the MATE screensaver but I am curious if there is a way to get the screensaver for another distro such as Ubuntu Unity or Ubuntu GNOME. I am not sure which files are needed and what to install to make it operate like it does in the MATE desktop. Is this even possible and does anyone have any input as to how to make it happen? I love the Ubuntu Unity desktop but want the MATE screensaver as I love the screen blanking when locking the computer and hope to get this installed in Ubuntu Unity or any other Ubuntu based distro. Xscreensaver by itself does not work like the screensaver in MATE so I am not sure if they are using a specifically designed screensaver for MATE or using a mix of screensavers to make this effect happen.

Thank you.

---

### Post by kerry_s on 2015-04-07
sudo apt-get install mate-screensaver

---

### Post by Joe_Johnston on 2015-04-07
When I do that it tells me it cannot find it. 

E: Unable to locate package mate-screensaver

Is there a special PPA needed for that?

---

### Post by Dennis N on 2015-04-07
> I absolutely love the MATE screensaver but I am curious if there is a way to get the screensaver for another distro such as Ubuntu Unity or Ubuntu GNOME

You could, but not without installing a lot of stuff you probably wouldn't want, because it depends on a number of MATE packages. 

For example, here are the additional packages that would be installed on Xubuntu 15.04 when installing mate-screensaver:

```
dmn@Sydney:~$ apt-get install -s mate-screensaver
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
...
The following extra packages will be installed:
  caja caja-common cryptsetup-bin libcaja-extension1 libcanberra-gtk-module
  libcanberra-gtk0 libdevmapper-event1.02.1 libexempi3 libgail18 liblvm2app2.2
  libmarco-private0 libmate-desktop-2-17 libmate-menu2
  libmate-panel-applet-4-1 libmatekbd-common libmatekbd4 libmateweather-common
  libmateweather1 libsgutils2-2 marco marco-common mate-desktop
  mate-desktop-common mate-menus mate-panel mate-panel-common mate-polkit
  mate-polkit-common mate-power-manager mate-power-manager-common
  mate-screensaver-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-settings-daemon-pulse menu menu-xdg udisks
```

---

### Post by Joe_Johnston on 2015-04-07
Well as long as it did not change the desktop environment then I would gladly install extra stuff to get that ability. Would the desktop still look like Unity after installing these packages? How would I go about doing this, is it a PPA added?

---

### Post by Dennis N on 2015-04-07
> **Joe_Johnston said:**
> Well as long as it did not change the desktop environment then I would gladly install extra stuff to get that ability. Would the desktop still look like Unity after installing these packages? How would I go about doing this, is it a PPA added?

If you are using Trusty, you do need a PPA to add MATE desktop environment:

Study this article - pay attention to the caveats and caution:
[http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts](http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts)

This is the PPA the article refers to. Check it out to see the packages it offers.
[https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate](https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate)

---

### Post by Joe_Johnston on 2015-04-07
Thank you very much! I really appreciate the assistance as this may be a good option for me.

---

### Post by Joe_Johnston on 2015-04-08
I'm going to hold off on this project for a while as it is more trouble than it is worth. Thank you all for the feedback and assistance.

---

### Post by Dennis N on 2015-04-08
> **Joe_Johnston said:**
> I'm going to hold off on this project for a while as it is more trouble than it is worth....

If the reason you like MATE screensaver is it's animated screensavers, you should consider using xscreensaver which offers a lot more of them and will work with any of the Ubuntu family of distros. It's settings dialog is very similar. It is also no problem to install:

To have all the screensavers, you need to install these packages:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

xscreensaver-data comes with xscreensaver, but the others are installed separately and will provide the missing screensavers. rss-glx requires some extra steps, and contains some of the most beautiful screensavers. Read the file /usr/share/doc/rss-glx/README.xscreensaver.

note: best to turn off existing screensavers (gnome-screensaver, light-locker, mate-screensaver) if you want to use this.

---

### Post by Joe_Johnston on 2015-04-12
Thank you for the tips! I am actually using Ubuntu MATE now and getting the best of everything with compiz and MATE. Very much enjoying this distro!

---

