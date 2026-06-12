---
title: "Wireless Configuration?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by wwwebster on 2005-10-19
I need some advice on the best way to use /etc/network/if-pre-up.d/wireless-tools to get the wireless connection configured.

 I can bring the thing up by running a script (see below) after I login, but I haven't been able to figure out how to get the configuration file to do this for me automagically @ boot time.

**_Questions_**:

[LIST=1]
[*] Where should the $IF_WIRELESS_* shell variables be set? [i.e., Should the mods be made in ./wireless-tools, or is there another recommended location for this?]
[*] How can these settings be integrated w/ the Locations in the System --> Administration --> Networking configuration utility?
[*] Do the "iface ... wireless-xyz" clauses in /etc/network/interfaces support more than one value (as in "iface ... wireless-key open s:1234567890")?
[/LIST]

**_Configuration details_**:

_version_:  Ubuntu 5.10RC
_hardware_:  Dell Inspiron 600m w/ Intel PRO/Wireless 2200BG
_access point_:  2Wire HomePoral 1000HG

[U]
Relevant excerpt of /etc/network/interfaces[/U]:

mapping hotplug
        script grep
        map eth0
        map eth1

iface eth0 inet dhcp

auto eth06163812244

iface eth1 inet dhcp
        wireless-essid XYX123
        wireless-channel 1
        wireless-mode Managed
        wireless-key open

auto eth1

[U]
Contents of script I can run from a command line to enable the wireless connection[/U]:

sudo iwconfig eth1 essid ABC123
sudo iwconfig eth1 channel 2
sudo iwconfig eth1 key 0123456789
sudo ifup eth1

---

### Post by wwwebster on 2005-10-19
Checking Bugzilla, I find these:

   [http://bugzilla.ubuntu.com/show_bug.cgi?id=13173](http://bugzilla.ubuntu.com/show_bug.cgi?id=13173)

   [http://bugzilla.gnome.org/show_bug.cgi?id=313567](http://bugzilla.gnome.org/show_bug.cgi?id=313567)

So I guess we'll have to make do for a while.

Any hints on wiring-up an automated workaround would be appreciated.

---

