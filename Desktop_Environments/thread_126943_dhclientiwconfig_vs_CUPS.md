---
title: "dhclient/iwconfig vs CUPS"
date: 2006-02-07
forum: Desktop Environments
---

### Post by ambrosewheatcroft on 2006-02-07
I have a problem with CUPS that seems to be something to do with iwconfig or dhclient which I use to connect to my wireless network.

I'm new to everything so I'll try and be as precise as possible, but please bear in mind I don't know what I'm talking about.

So, what happens is this:

1) I load up my system from cold.  It doesn't attempt to connect any network interfaces -- I always do this "manually".

2) I get into Gnome, and can happily run gnome-cups-manager and things like lpinfo -v and lpadmin, and the little panel cups icon works (in actual fact, my printer isn't yet working properly but I'll cross that bridge when I come to it.)

3) I run my "connect to internet" script which goes like this:

sudo iwconfig wlan0 key open xxxxxxxxxxx;
sudo iwconfig wlan0 essid xxxxxxx;
sudo dhclient;

4) My internet works fine but CUPS has gone crazy.  Specifically: gnome-cups-manager fails -- after a long pause, it says "cannot connect to cups server" or something similar, and lpadmin and lpinfo don't work either.  The cupsd entry in the System Monitor stays for some time but disappears in the end.

So my questions are:

1  Is it possible that dhclient is crashing CUPs?

2  How do I find out?

3  How do I fix this?

Thanks a million,

Ambrose

Some more details:

All the software I talk about above was installed from ubuntu packages thorugh synaptic etc.

Here's my /var/logs/cups/errors_log (it's from a session where I basically booted up, started CUPs, went online, then tried to restart it a couple of times)

I [08/Feb/2006:00:37:02 +0000] Listening to 7f000001:631
I [08/Feb/2006:00:37:02 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [08/Feb/2006:00:37:02 +0000] Configured for up to 100 clients.
I [08/Feb/2006:00:37:02 +0000] Allowing up to 100 client connections per host.
I [08/Feb/2006:00:37:02 +0000] Full reload is required.
E [08/Feb/2006:00:37:02 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [08/Feb/2006:00:37:02 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4105 PPDs...
I [08/Feb/2006:00:37:02 +0000] LoadPPDs: No new or changed PPDs...
I [08/Feb/2006:00:37:02 +0000] Full reload complete.
I [08/Feb/2006:00:53:32 +0000] Scheduler shutting down normally.
I [08/Feb/2006:00:53:32 +0000] Listening to 7f000001:631
I [08/Feb/2006:00:53:32 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [08/Feb/2006:00:53:33 +0000] Configured for up to 100 clients.
I [08/Feb/2006:00:53:33 +0000] Allowing up to 100 client connections per host.
I [08/Feb/2006:00:53:33 +0000] Full reload is required.
E [08/Feb/2006:00:53:33 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
W [08/Feb/2006:00:54:03 +0000] LoadDevices: Backend did not respond within 30 seconds!
I [08/Feb/2006:00:56:43 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4105 PPDs...
I [08/Feb/2006:00:56:45 +0000] LoadPPDs: No new or changed PPDs...
I [08/Feb/2006:00:56:45 +0000] Full reload complete.
E [08/Feb/2006:00:56:45 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.
I [08/Feb/2006:01:06:26 +0000] Listening to 7f000001:631
I [08/Feb/2006:01:06:26 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [08/Feb/2006:01:06:26 +0000] Configured for up to 100 clients.
I [08/Feb/2006:01:06:26 +0000] Allowing up to 100 client connections per host.
I [08/Feb/2006:01:06:26 +0000] Full reload is required.
E [08/Feb/2006:01:06:26 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
W [08/Feb/2006:01:06:56 +0000] LoadDevices: Backend did not respond within 30 seconds!
I [08/Feb/2006:01:09:36 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4105 PPDs...
I [08/Feb/2006:01:09:37 +0000] LoadPPDs: No new or changed PPDs...
I [08/Feb/2006:01:09:37 +0000] Full reload complete.
E [08/Feb/2006:01:09:37 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.

---

### Post by ambrosewheatcroft on 2006-02-07
My problem has been solved -- sorry to have wasted anyone's time.

Thanks,

Ambrose

---

