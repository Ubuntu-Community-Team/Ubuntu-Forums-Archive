---
title: "configuring Wlan network"
date: 2005-12-27
forum: General Help
---

### Post by pooseek on 2005-12-27
guys, pls help me with this:

when i try to set up my network, it doesn't save changes like this:

i add DNS server adress, change my wlan0 device as default(instead of that ppp0(?)) and after saving configuration with clicking on OK, nothing happens, because when i start that GUI again, there's ppp0(?) set as default again and no DNS adresses added. can someone help me?

---

### Post by KurtB on 2005-12-27
Hi,

ppp0 is only for dial-up & dsl connection.

If you want to get your Wireless up:
* which NIC are you using? And do you have the proper driver installed?
* Are you using ndiswrapper? with this program you can use the windowsdriver that comes with the CDROM of your NIC...and is by far the best way to set up your wireless...

just try "ndiswrapper" & "howto", this will give you a nice lead, and try to see which NIC you have ;)

---

### Post by pooseek on 2005-12-27
no no no...

my driver's been installed succesfully, my device has been recognized. But this damn GUI doesn't save changes. So, my driver's alright, but the other settings aren't. Just can't save those adresses and settings. when the GUI's restarted, settings are gone.

Can someone tell me, which file are these settings beeing saved to? If I knew, I'd edit it...

---

### Post by kaamos on 2005-12-27
The file is /etc/network/interfaces

---

