---
title: "Can Audo and Wifi be connected before user login"
date: 2011-05-08
forum: Desktop Environments
---

### Post by couling on 2011-05-08
Hi All

I've got an Ubuntu 11.04 install which is primarily a desktop, but is increasingly being used for home server type stuff (Media Player, NAS, SVN).

I'm trying to get it to play music remotely from another machine.  Currently just using mpg321 on ssh.
This all works fine while I've got a user logged into the desktop front end.
But if I log out the desktop then the audio stops playback even though I'm still logged in through ssh and mpg321 is still running fine.

Does anyone know how I can get the auido to function before logging a user into the front end?

Thanks for your time

---

### Post by steinerd on 2011-05-08
NetManager is probably your culprit.  It is not present in server installs and is in desktop installs.  If you are familiar with setting up ifup/ifdown you can set up your network without netmanager and it will be present at boot time.  There are some configs that have to be done and if someone does not post them up soon I will get them for you when i get back in today.

For some more tips see my [help site]("http://deep-sea.realservers.info/")..  [http://deep-sea.realservers.info/](http://deep-sea.realservers.info/)

It's a personal site with a little info.  Most likely I will post this topic also now since I myself have to look it up everytime I want to do it also lol.

---

### Post by couling on 2011-05-08
I just managed to fix the WIFI in an unexpectedly easy way:

Went to the network manager
Wireless (tab)
Chose the wireless connection
Edit (button)
Available to all users (tick the check box)

Just got to figure out the audo now

---

### Post by couling on 2011-05-08
Turns out that this can be fixed by adding my user to the "audio" user group (in /etc/group)

By default the only user in the audio group us "pulse" allowing user switching to control which user has access to the audio for user switching.  At the login screen the user us gdm.

 By adding myself to the audio group my user bypasses the user switching and is allowed to play audio whichever user is currently active.

Found this out from [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

