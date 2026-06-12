---
title: "Unable to change Natty clock settings in Unity menu bar"
date: 2011-04-27
forum: Desktop Environments
---

### Post by rod40cool on 2011-04-27
Hi, I recently upgraded my clean install Ubuntu Studio 10.10 64bit to Natty 11.04 and whilst everything is working well (except for having no plymouth boot splash - but I'm looking into this) I have noticed that when I log in to the "Ubuntu" desktop (with the Unity launcher and Menu bar in the top panel) I can't seem to change how the time and date is displayed. It seems to be stuck showing 24 hour time only with no date no matter which setting I select in the 'Clock' tab of 'Time & Date Settings' menu.

The clock applet works perfectly when I log into the 'Ubuntu Classic' desktop and I am able to display the date and weather ok.

I have a laptop which I upgraded from Ubuntu 10.10 64bit to 11.04 as well and it doesn't have the same issue.

I thought it might have been a rouge Gconf setting so I dumped my entire gconf using ```
gconftool-2 --dump / > ~/Desktop/allgconf.entries
``` then restarted into recovery and removed my ~/.gconf folder entirely, rebooted again and logged back on. Apart from losing some settings like Evolution and Networking, which I reloaded, and my theme going back to the default theme, the problem still exists.

I haven't been able to find anyone else with the same problem. 

Can anyone help?

Rod

---

### Post by awatt on 2011-04-30
I can't help, but I can confirm that I have a similar problem.
I can't change the time&date settings either, but mine are stuck in 12 hour (I'd prefer 24 hour). 
When I click on "Time&Date Settings..." nothing happens. 
Really annoying.

---

### Post by rod40cool on 2011-04-30
> **awatt said:**
> I can't help, but I can confirm that I have a similar problem.
I can't change the time&date settings either, but mine are stuck in 12 hour (I'd prefer 24 hour). 
When I click on "Time&Date Settings..." nothing happens. 
Really annoying.

Well I decided to reload Ubuntu from Alternative CD as I just set up 2 disks in Raid 1 so I'm no longer the Studio version, and now I have exactly the same problem as you. Clicking on Time & Date Settings does nothing - all I've got is the time in 24 hr mode and I can't display the date. Agree - really annoying.

Is there a way to change the thread tag from [ubuntu_studio] to [ubuntu]?
What's the command to bring up Time & Date settings in Unity? Maybe that will tell us whats going wrong? It's like the program is not even loaded.

---

### Post by awatt on 2011-04-30
I don't know what happened, but it works now. I had restarted a few times to try to fix this problem, but that didn't work. I just started my laptop up again and all of the sudden it works now. I didn't do anything.

As far as the command goes, I really don't know. I'm not that strong of a terminal user.

Good luck.

---

### Post by garvinrick4 on 2011-04-30
Here you go:

unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session,
            ubuntuone-control-panel-gtk
```
rick@rick-HP:~$ aptitude show indicator-datetime
Package: indicator-datetime              
New: yes
State: installed
Automatically installed: yes
Version: 0.2.3-0ubuntu3
Priority: optional
Section: misc
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,094 k
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10),
         libcamel1.2-19 (>= 2.32), libcamel1.2-19 (< 2.33), libdbus-1-3 (>=
         1.0.2), libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib3 (>= 0.4.2),
         libdbusmenu-gtk3 (>= 0.4.2), libebook1.2-10 (>= 2.32.2), libecal1.2-8
         (>= 2.32.2), libedataserver1.2-14 (>= 2.32.2), libedataserverui1.2-11
         (>= 2.32.2), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgeoclue0
         (>= 0.11.1+git20091217), libglib2.0-0 (>= 2.26.0), libgtk2.0-0 (>=
         2.22), libical0 (>= 0.31), libido-0.1-0 (>= 0.2.2), libindicator3 (>=
         0.3.19), libjson-glib-1.0-0 (>= 0.12.0), libnspr4 (>= 4.7.0~1.9b1),
         libnss3 (>= 3.12.2~rc1), libpango1.0-0 (>= 1.18.0),
         libpolkit-gobject-1-0 (>= 0.94), libpolkit-gtk-1-0 (>= 0.94),
         libsoup2.4-1 (>= 2.4.0), libsqlite3-0 (>= 3.7.3), libunique-1.0-0 (>=
         1.0.0), libxml2 (>= 2.6.27), geoclue-ubuntu-geoip | geoclue-provider
Recommends: indicator-applet | indicator-renderer
Description: A very, very simple clock
 A simple clock appearing in the indicator bar
Homepage: https://launchpad.net/indicator-datetime

rick@rick-HP:~$ 

```

---

### Post by rod40cool on 2011-05-01
> **garvinrick4 said:**
> Here you go:

unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session,
            ubuntuone-control-panel-gtk


Thanks garvinrick4.
I found the terminal command which brings up the Date/Time settings too:
```
$ indicator-datetime-preferences
```

Well awatt, the same thing that happened to you happened to me - it's just working now - i just fired up my desktop a moment ago after leaving it for a day and Date Time settings was the first thing I tried and voila. I don't know if there was an update that was installed that needed a reboot or whatever but for now I'll say it's solved - magically.

---

### Post by mr_niceguy on 2011-05-17
> **rod40cool said:**
> I found the terminal command which brings up the Date/Time settings too:
```
$ indicator-datetime-preferences
```


Even that just hangs for me.

Unity is, quite honestly, unusable for me at the moment. I know they were excited to get it out but it is not even close to being ready for prime time. (and I am a huge Ubuntu fan)

I did, however find a fix in the mean time:

```
sudo apt-get install gnome
```

---

### Post by westie457 on 2011-06-04
Hello I too had this minor nuisance of not being able to change time and date settings. The solution I found was to kill one of the zeitgeist-data services. It is fixed for now and probably until computer is restarted. Will come back and let you know the result.

Edit:  No that was not the answer. After reboot still unable to change settings. However I did try killing the indicator-datetime-preference service. This service restarted itself and when I clicked on 'Time&Date' in System Settings I was then able to change things.

Hope this is of help to someone

---

### Post by dom134 on 2011-06-19
Thanks westie, I have been having the same issue: it seems to be a feature of Natty! It was solved with:
sudo killall indicator-datetime-preferences

---

### Post by Benedolt on 2011-06-24
Hey, I'm having the same problem, really annoying! 
Have any of you guys filed a bug? If not, I'd do it.

#EDIT
Okay, the bug is already "in progress". ^^

[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/751175](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/751175)

---

