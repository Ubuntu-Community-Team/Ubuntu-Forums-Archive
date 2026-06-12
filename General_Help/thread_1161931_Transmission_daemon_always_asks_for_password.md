---
title: "Transmission daemon always asks for password"
date: 2009-05-17
forum: General Help
---

### Post by Jungies on 2009-05-17
Hi,

I've got Transmission-daemon set up on my server, which is running Jaunty (uname gives "Linux 2.6.28-11-server #42-Ubuntu SMP x86_64 GNU/Linux"). I'm using the standard package from the Ubuntu repos; I haven't compiled it from source. I've run apt-get update and upgrade as of this morning, so I guess I'm using the latest package.

I'm trying to set up authentication so that only people on my LAN can get to the web GUI, and so they aren't prompted for a password. I've set    [FONT="Courier New"]"rpc-authentication-required": 0[/FONT] in /etc/transmission-daemon/settings.json, and restarted the daemon, but it's ignoring the setting and demanding a password. I've also set the username and password to "", but that didn't help either. I've tried deleting those three keys from the config, but to no avail. 

I'm sure transmission's reading the config file, as if I throw in an extra comma or two it complains about them in the log file. I've also had a look at the init script, but can't see any easy way of adding the "no auth" command line option to it. 

Is there anything else I should try?

---

### Post by mancimailman on 2009-05-17
Use ktorrent:)

---

### Post by FrankT-Qc on 2009-05-25
You have to go edit /etc/default/transmission-daemon . Remove the option "--auth" which has the [safe|paranoid] behavior of forcing authentication.

In fact, you have to 
1 - Stop the daemon
2 - Edit /etc/default/transmission-daemon
3 - Edit /etc/transmission-daemon/config.json (rpc-auth = 0)
4 - Enjoy

have fun,
Frank

---

### Post by Jungies on 2009-05-27
FrankT-Qc:
That worked perfectly! Many thanks.

---

### Post by aqui_c on 2010-03-08
Thanks!
It worked :)

P.S.: I'm actually using Debian Lenny.

---

### Post by ThomasB2k on 2011-09-04
> **FrankT-Qc said:**
> You have to go edit /etc/default/transmission-daemon . Remove the option "--auth" which has the [safe|paranoid] behavior of forcing authentication.

In fact, you have to 
1 - Stop the daemon
2 - Edit /etc/default/transmission-daemon
3 - Edit /etc/transmission-daemon/config.json (rpc-auth = 0)
4 - Enjoy

have fun,
Frank

Thank you so much for this. I've edited every other of the 5+ transmission settings.json but this one, and of course it'd be this one that I had to change <_</

---

### Post by NickD-NLUG on 2011-10-17
> **ThomasB2k said:**
> Thank you so much for this. I've edited every other of the 5+ transmission settings.json but this one, and of course it'd be this one that I had to change <_</

Me also.  I've been looking at the settings.json file for weeks trying to figure out why it wasn't implementing the options I'd chosen; thanks for this.

---

