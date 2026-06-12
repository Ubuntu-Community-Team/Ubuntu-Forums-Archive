---
title: "Argh!!!! How do I remove Alacarte and all the Gnome dependencies?"
date: 2011-05-10
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-05-10
Running Xubuntu 11.04. 

I installed alacarte so that I could edit the menu. Problem is, alacarte trashed my DE by installing all kinds of Gnome crap. How do I uninstall, not just alacarte, but all the Gnome crap with it?!? I want my XFCE desktop back! ](*,)

---

### Post by neu5eeCh on 2011-05-10
OK. That was weird. After I installed Alacarte, Xubuntu asked to be rebooted. I rebooted and my DE was trashed (weird Gnome titlebars, no XFCE panel, missing desktop Icons, etc..)

I booted into another laptop with Xubuntu 11.04 and ran the same command in terminal: sudo apt-get install alacarte. I got my list of dependencies without installing. I then booted back into the first laptop and voila! - my XFCE desktop is back!?! alacarte pops up with gnome-do.

Here are the list of dependencies alacarte installed:

alacarte 
appmenu-gtk 
bamfdaemon 
capplets-data 
evolution-data-server
evolution-data-server-common 
gir1.2-dbusmenu-glib-0.4 
gir1.2-dee-0.5
gir1.2-gconf-2.0 
gir1.2-panelapplet-3.0 
gir1.2-soup-2.4 
gir1.2-unity-3.0
gnome-about 
gnome-applets 
gnome-applets-data 
gnome-control-center
gnome-media 
gnome-media-common 
gnome-panel gnome-panel-bonobo
gnome-panel-data 
gnome-power-manager 
gnome-session 
gnome-session-common
gnome-system-monitor 
gsettings-desktop-schemas 
gwibber 
gwibber-service
gwibber-service-facebook 
gwibber-service-identica 
gwibber-service-twitter
indicator-applet indicator-applet-appmenu 
indicator-applet-complete
indicator-applet-session 
indicator-appmenu 
indicator-me indicator-session
libatkmm-1.6-1 
libbamf0 libcairomm-1.0-1 
libcamel1.2-19 
libdee-1.0-1
libebackend1.2-0 
libebook1.2-10 
libecal1.2-8 
libedata-book1.2-8
libedata-cal1.2-10 
libedataserver1.2-14 
libedataserverui1.2-11
libegroupwise1.2-13 
libexempi3 
libgdata-common 
libgdata11 libgladeui-1-11
libglib2.0-data 
libgnome-media0 
libgnome-window-settings1 
libgtkmm-2.4-1c2a
libgweather-common 
libgweather1 libgwibber1 
libmetacity-private0
libpanel-applet-3-0 
libpanel-applet2-0 
libpangomm-1.4-1 
libprotoc6 
libunity4
metacity 
metacity-common 
mousetweaks 
nautilus 
nautilus-data
protobuf-compiler 
python-configglue 
python-egenix-mxdatetime
python-egenix-mxtools 
python-gtkspell 
python-indicate 
python-libproxy
python-mako python-markupsafe 
python-protobuf python-pyinotify
python-twisted-names 
python-ubuntuone-client 
python-ubuntuone-control-panel
python-ubuntuone-storageprotocol 
python-wnck ubuntu-system-service
ubuntuone-client ubuntuone-control-panel 
ubuntuone-control-panel-gtk

Really? Really!?! Did I really need to install all that? Can I remove any of this?

---

### Post by Toz on 2011-05-10
In theory, you should be able to```
sudo apt-get remove alacarte
``` and follow it up with a```
sudo apt-get autoremove
``` to remove all the dependencies.

Make sure you double-check what autoremove is going to uninstall with the list that you have.

---

### Post by Toz on 2011-05-10
And oh, the obligatory reference link:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by neu5eeCh on 2011-05-10
Thanks. That's a cool tip. Now that my Xubu desktop is back I'm not quite so panicked. I can also 'sudo apt-get remove 
[list of apps]. 

But do I really need all the other "dependencies" to run alacarte? I'm going to experiment. I'm going to remove all the dependencies and keep alacarte.

**Edit:** Removed everything but alacarte. Alacarte popped up. The only functionality missing was the ability to edit the app entries (significant but still...). I find it hard to believe that I needed to install the Gnome Desktop in order to run alacarte!?!

---

### Post by Toz on 2011-05-10
You could try the --no-install-recommends option to apt-get to install only the package but no recommends. Use at your own risk. Makes it easier than installing then removing the extra stuff.```
sudo apt-get install --no-install-recommends alacarte
```
You can also test to see what is going to be installed (simulates but does not run - also notice sudo is not required) by adding the -s parameter:```
apt-get -s install --no-install-recommends alacarte
```

---

### Post by neu5eeCh on 2011-05-10
Thanks. Those are all great tips. I essentially did the --no-install-recommends route by uninstalling everything **except** allacarte. I noticed at the XFCE site, however, that they tested menu editing with alacarte. I guess this is the app they want. I'm just baffled by why it's necessary to practically install the Gnome desktop.

---

### Post by ManualSparrow on 2011-05-10
Oh thanks - I wondered why all those gnome dependencies were popping up. Just removed alacarte - xml editing's not so bad really...

---

### Post by mike555 on 2011-07-26
Another menu editor is a java editor, not really made for xfce, but works without a bunch of extra stuff   ... [http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/)   ... just uncompress to your home folder, make the .jar file executable and open in jre .........

---

### Post by jlacroix on 2011-11-02
I just got bit by this in Xubuntu 11.10. I wasn't paying attention, and then it gave me a bunch of crap I never asked for. I put a lot of work into setting up this laptop, is there any way to remove this garbage?

I tried to remove alacarte and then do an autoremove, but that doesn't remove anything extra but maybe one package. I tried to remove all the packages one by one but in 11.10 I guess the names of the packages are different so I don't know what I'm removing :(

PS. Did anyone file a bug against this? I can't imagine that behavior such as this would be on purpose!

---

### Post by gsmanners on 2011-11-02
Did you try:

```
sudo apt-get remove gnome-panel
sudo apt-get autoremove
```

The only thing alacarte recommends is gnome-panel, so you remove that (and all the crap it drags in) and you should be good to go.

---

### Post by dniMretsaM on 2011-11-02
*****Be careful! This could kill your system.** If anything else depends  on any of these packages, they will also be removed/broken. I would  suggest posting the output of the first command and let someone with  a lot experience look at it BEFORE you run the second.***

You could try this:
```
sudo apt-get --force-yes --simulate purge alacarte appmenu-gtk bamfdaemon capplets-data evolution-data-server evolution-data-server-common gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-gconf-2.0 gir1.2-panelapplet-3.0 gir1.2-soup-2.4 gir1.2-unity-3.0 gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-media gnome-media-common gnome-panel gnome-panel-bonobo gnome-panel-data gnome-power-manager gnome-session gnome-session-common gnome-system-monitor gsettings-desktop-schemas gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter indicator-applet indicator-applet-appmenu indicator-applet-complete indicator-applet-session indicator-appmenu indicator-me indicator-session libatkmm-1.6-1 libbamf0 libcairomm-1.0-1 libcamel1.2-19 libdee-1.0-1 libebackend1.2-0 libebook1.2-10 libecal1.2-8 libedata-book1.2-8 libedata-cal1.2-10 libedataserver1.2-14 libedataserverui1.2-11 libegroupwise1.2-13 libexempi3 libgdata-common libgdata11 libgladeui-1-11 libglib2.0-data libgnome-media0 libgnome-window-settings1 libgtkmm-2.4-1c2a libgweather-common libgweather1 libgwibber1 libmetacity-private0 libpanel-applet-3-0 libpanel-applet2-0 libpangomm-1.4-1 libprotoc6 libunity4 metacity metacity-common mousetweaks nautilus nautilus-data protobuf-compiler python-configglue python-egenix-mxdatetime python-egenix-mxtools python-gtkspell python-indicate python-libproxy python-mako python-markupsafe python-protobuf python-pyinotify python-twisted-names python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-wnck ubuntu-system-service ubuntuone-client ubuntuone-control-panel ubuntuone-control-panel-gtk
```If everything looks good, then run this:

```
sudo apt-get --force-yes purge alacarte appmenu-gtk  bamfdaemon capplets-data evolution-data-server  evolution-data-server-common gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5  gir1.2-gconf-2.0 gir1.2-panelapplet-3.0 gir1.2-soup-2.4 gir1.2-unity-3.0  gnome-about gnome-applets gnome-applets-data gnome-control-center  gnome-media gnome-media-common gnome-panel gnome-panel-bonobo  gnome-panel-data gnome-power-manager gnome-session gnome-session-common  gnome-system-monitor gsettings-desktop-schemas gwibber gwibber-service  gwibber-service-facebook gwibber-service-identica  gwibber-service-twitter indicator-applet indicator-applet-appmenu  indicator-applet-complete indicator-applet-session indicator-appmenu  indicator-me indicator-session libatkmm-1.6-1 libbamf0 libcairomm-1.0-1  libcamel1.2-19 libdee-1.0-1 libebackend1.2-0 libebook1.2-10 libecal1.2-8  libedata-book1.2-8 libedata-cal1.2-10 libedataserver1.2-14  libedataserverui1.2-11 libegroupwise1.2-13 libexempi3 libgdata-common  libgdata11 libgladeui-1-11 libglib2.0-data libgnome-media0  libgnome-window-settings1 libgtkmm-2.4-1c2a libgweather-common  libgweather1 libgwibber1 libmetacity-private0 libpanel-applet-3-0  libpanel-applet2-0 libpangomm-1.4-1 libprotoc6 libunity4 metacity  metacity-common mousetweaks nautilus nautilus-data protobuf-compiler  python-configglue python-egenix-mxdatetime python-egenix-mxtools  python-gtkspell python-indicate python-libproxy python-mako  python-markupsafe python-protobuf python-pyinotify python-twisted-names  python-ubuntuone-client python-ubuntuone-control-panel  python-ubuntuone-storageprotocol python-wnck ubuntu-system-service  ubuntuone-client ubuntuone-control-panel  ubuntuone-control-panel-gtk
```

---

### Post by jlacroix on 2011-11-02
Thank you all, I got this sorted out now. :)

---

### Post by dFlyer on 2011-11-02
Great to hear that, can you post how it was done and then mark the thread as solved.

---

### Post by jlacroix on 2011-11-02
> **dFlyer said:**
> Great to hear that, can you post how it was done and then mark the thread as solved.
I can't mark this thread as solved because it's not my thread.

I fixed it before you guys posted, by booting my computer from a Xubuntu Live CD, entering the command that installs Alacarte, and exporting a text file of the changes it wanted to make. Then, in my actual install, I did a "sudo apt-get remove --purge" followed by the names of all the packages, one by one. It was tedious but it worked, and it was slightly easier than starting the computer over.

---

