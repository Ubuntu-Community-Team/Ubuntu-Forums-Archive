---
title: "Limewire Problem"
date: 2005-08-26
forum: Desktop Environments
---

### Post by DREMA on 2005-08-26
Hi guys, I have a problem with my Limewire, when I try to open it i get a error windows and in the details I have this;

LimeWire version 4.9.27
Java version 1.5.0_04 from Sun Microsystems Inc.
Linux v. 2.6.10-5-386 on i386
Free/total memory: 2304960/7692288

FATAL ERROR!

java.lang.UnsatisfiedLinkError: initNative
at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.initNative(Native Method)
at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.(Unknown Source)
at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
at org.jdesktop.jdic.tray.SystemTray.(Unknown Source)
at com.limegroup.gnutella.gui.notify.LinuxNotifyUser.(LinuxNotifyUser.java:24)
at com.limegroup.gnutella.gui.notify.NotifyUserProxy.(NotifyUserProxy.java:49)
at com.limegroup.gnutella.gui.notify.NotifyUserProxy.(NotifyUserProxy.java:26)
at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:254)
at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:41)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
at java.lang.reflect.Method.invoke(Unknown Source)
at com.limegroup.gnutella.gui.Main.main(Main.java:44)

-- listing session information --
Current thread: main
Active Threads: 11

-- listing threads --
Image Fetcher 3: 1
main: 1
NIODispatcher: 1
AWT-EventQueue-0: 1
AWT-Shutdown: 1
AWT-XAWT: 1
Image Fetcher 1: 1
Timer-0: 1
Image Fetcher 2: 1
Java2D Disposer: 1
TimerQueue: 1

-- listing properties --
APP_WIDTH=985
APP_HEIGHT=716
WINDOW_Y=27
WINDOW_X=39
EVER_ACCEPTED_INCOMING=true
FILTER_HASH_QUERIES=true
LAST_GWEBCACHE_FETCH_TIME=1121547363726
TOTAL_UPTIME=13278
INSTALLED=true
CONNECTION_SPEED=350
UNSET_FIREWALLED_FROM_CONNECTBACK=true
COUNTRY=
LAST_ACCEPTABLE_BUG_VERSION=4.9.5
CLIENT_ID=8D684E4A59ED44943D70D8F21BBBA800
LAST_EXPIRE_TIME=1124955607622
UI_SMALL_ICONS=true
RUN_ONCE=true

Anybody knows whats going on??? How can I fix it???
Tnks

---

### Post by DREMA on 2005-08-26
Anybody ???? :(

---

### Post by DREMA on 2005-08-27
Somebody help meee pleeeeeease, i wanna download music a other stuff, pleaaaase, or tell me another good program to download music, videos, and other things, for linux, pleeeeeeeeeease!!!!    ](*,) 

TNKS!!!

---

### Post by *nix_noob on 2005-08-27
simply convert the limewire rpm (that you get from limewire.com) to a deb useing alain 

like so

say you save it to your desktop 

```
sudo alain ~home/Desktop/linux.rpm
```

and then use the command line to run the deb

also make shure you have the lateind java installed

```
sudo apt-get update
``` 
```
apt-get install sunj2re1.5
```

---

### Post by vaskark on 2005-08-27
Shouldn't that be *alien* and not *alain*?

---

### Post by DREMA on 2005-08-28
Nope, that doesn't works, I have the same error, what's going on??  I can't make it work, please heeeelp meeeee!!!

---

### Post by DREMA on 2005-08-31
:( ](*,)

---

### Post by mcduck on 2005-09-01
I really can't help you with LimeWire, but for same use I've been using Nicotine. It uses the Soulseek network, and it's very easy to use.

For bonus, it uses Python and GTK2 instead of Java, so it'll fit your desktop perfectly. You can get it with Synaptic (or apt-get).

edit:
I think it's in Universe/networking, so if you haven't yet enabled extra repositories, go to ubuntuguide.org for instructions about that..

---

### Post by KingBahamut on 2005-09-01
ReInstall as such..............

wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh
Insert the following lines into the new file

cd /opt/LimeWire/
./runLime.sh

Save the edited file

sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop

Insert the following lines into the new file

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;

Save the edited file

run - killall gnome-panel

---

### Post by DREMA on 2005-09-01
I did all you say, but im still having the same problem, I was reading the text of the error, and I think that is something qith the java... but I really dont know, I hope yo can check the error message and tell me whats the problems.
Thanks again.

---

### Post by DREMA on 2005-09-02
I can't fix it!!!    ](*,) :( ](*,)

---

### Post by DREMA on 2005-09-02
I can't fix it!!!    ](*,)  :(  ](*,)

---

