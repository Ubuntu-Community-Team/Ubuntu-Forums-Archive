---
title: "Help with Tor"
date: 2005-12-24
forum: Desktop Environments
---

### Post by scottish144 on 2005-12-24
I compile tor from source, and attempted to run it.  It spat this out:

Dec 24 11:38:57.065 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.
Dec 24 11:38:57.066 [notice] Configuration file '/usr/local/etc/tor/torrc' not present, using reasonable defaults.
Dec 24 11:38:57.066 [notice] Initialized libevent version 1.1a using method epoll
Dec 24 11:38:57.067 [warn] connection_create_listener(): Could not bind to port 9050: Address already in use
Dec 24 11:38:57.067 [err] options_act(): Failed to bind one of the listener ports.
Dec 24 11:38:57.067 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

I have no idea what is using port 9050.  Then again, I've only used Ubuntu for a few weeks (after hell with Windows 2000) and don't know much about the OSs structure.

---

### Post by AmboyGuy on 2005-12-24
You have to use privoxy (port 8018 ?) and hook tor into it. ( port 9050 ). The instructions are on the Tor web page.
Also you have to set up your proxy settings in your browser to hook into privoxy.

---

### Post by scottish144 on 2005-12-24
Can't install privoxy!  Privoxy won't let me install as root, and Ubuntu won't let me install as a user.

---

### Post by AmboyGuy on 2005-12-24
I found privoxy and downloaded privoxy_3.0.3-5_i386.deb
from [http://archive.ubuntu.com/ubuntu/pool/universe/p/privoxy/]("http://archive.ubuntu.com/ubuntu/pool/universe/p/privoxy/") 
Then #sudo dpkg -i privoxy_3.0.3-5_i386.deb
No problems.

Normally I use synaptic or apt-get.

Are you having a problem with sudo ??

---

### Post by scottish144 on 2005-12-25
I tried to compile from source.  Everything works fine up till "make install".  Ubuntu won't let me install as a non-super-user, and if I use sudo privoxy says something to the effect of: "OMG ur trying to install this program as root!  This is bad and unsafe!  U are a dumba$$!!!  Install this program as non-root @#$% it!!!".  In any case, I'll try the debian package.  I didn't at first due to rumors of debian/ubuntu incompatability.  Thanks!

---

### Post by Ufo on 2005-12-25
If you enable universe repositories in synaptic, you can find both privoxy and tor there.

---

