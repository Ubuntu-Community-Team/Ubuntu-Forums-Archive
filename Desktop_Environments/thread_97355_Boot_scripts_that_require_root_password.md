---
title: "Boot scripts that require root password"
date: 2005-11-30
forum: Desktop Environments
---

### Post by shaggydoo on 2005-11-30
I set up a bridge between two of my network cards (eth1 connects to another computer, eth0 connects to my dsl modem). It works perfectly fine, but the problem is that every time I reboot, all my network settings are gone.

ifconfig after a reboot reports that all my network interfaces are down and the bridge is gone. So, I wrote a bash script to create a bridge and bring up my network interfaces, then connect via pppoe. It works if I call it manually, but asks for the root password to do anything. I've tried putting it in init.d, chmod +x and using the thing to add symlinks to the startup directories (rc*.d), even tried in rcS.d (I think that's what it was called, you know what I mean) and in Sys > Prefs > Sessions.

ONLY the one I added to the Sys > Prefs > Sessions area seems to work, but that one comes after I'm logged in to Ubuntu and STILL asks for my password. Basically, all I want to do is run this script without requiring to input the password (and if possible, before logging into Ubuntu so everything's ready to go before the login is complete, but I'll settle for anything at this point - as long as I don't have to type the password).

Here's the script in case anyone needs to know what I'm trying to do. And in case you couldn't tell, I'm new to all this:
```
#!/bin/bash

echo 'BN: Shutting down ethernet'
gksudo 'ifconfig eth0 up'
gksudo 'ifconfig eth1 up'
echo 'BN: Creating bridge'
gksudo 'brctl addbr br0'
gksudo 'brctl addif br0 eth0'
gksudo 'brctl addif br0 eth1'
echo 'BN: Registering ethernet addresses'
gksudo 'ifconfig eth0 192.168.2.2'
gksudo 'ifconfig eth1 192.168.2.3'
echo 'BN: Initializing bridged network'
gksudo 'ifconfig br0 up'
echo 'BN: Connecting PPPOE'
exec pppd call dsl-provider
```

I await fellow Ubuntu user awesomeness to rock my world.

---

### Post by RAOF on 2005-11-30
I'd try the same script, but without the "gksudo" bits.  If you add it to your init.d it should get run as root, so you don't need to sudo at all.  Plus, gksudo is a graphical sudo thingy - I'm not sure what it'll do if you try and run it without an X server up.  Since when you run it in your init scripts there won't be an X server running yet, I think it'll probably fail.

EDIT: A simple check shows that gksudo will fail without an X server.  So that script is bound to fail.

---

### Post by shaggydoo on 2005-11-30
Oh, so that's what the gk in gksudo is! Thanks! I'm going to give this a try.

**Update:** Awesome, it worked. Thanks a ton RAOF! I love Ubuntu, the community just never ceases to amaze me.

---

