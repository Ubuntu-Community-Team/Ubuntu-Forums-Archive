---
title: "Configuring Network Interfaces on boot : Very slow always"
date: 2006-02-23
forum: Desktop Environments
---

### Post by veraction on 2006-02-23
On both my Desktop and laptop (wired and wireless), any time I boot up, it takes at least 60 seconds to "Configure network interfaces". Is there any way to speed this up, or something? If I Ctrl-C it, it doesn't give me connectivity to wifi. Don't know why it takes so long - I always have a network connection - so it it is not like it is searching for a nonexistant connection

Saw other threads about this, but mostly they talk about slow load times with no connection.

---

### Post by m.musashi on 2006-02-23
I've had this problem too. I noticed that it is basically timing out. It was more a problem with wireless when I had my essid hidden. In that case it couldn't find it (I don't know why it can't when I've configured it) and just timed out. When connected via wired and my wired connection was active on the previous boot it would not take as long and sometimes no time at all.

I have yet to find a good answer but some experimenting with just one connection at a time might help narrow it down. If your results are similar to mine it may be more of a bug than just a config issue.

On a side note, boot time is much faster in Dapper. Of course they recommend you don't use it unless you can deal with it breaking.

---

### Post by Tichondrius on 2006-02-23
[QUOTE=veraction]On both my Desktop and laptop (wired and wireless), any time I boot up, it takes at least 60 seconds to "Configure network interfaces". Is there any way to speed this up, or something? If I Ctrl-C it, it doesn't give me connectivity to wifi. Don't know why it takes so long - I always have a network connection - so it it is not like it is searching for a nonexistant connection

Saw other threads about this, but mostly they talk about slow load times with no connection.[/QUOTE]

During boot, Ubuntu is trying to configure all your network interfaces, which means it's trying to assign them addresses using DHCP protocol, which tries to contact a DHCP server. If any of your network interfaces is not connected, it will take up to 60 seconds for this process to time out. So if you have more than one ethernet port (which is very common on new motherboards) but only one is connected, the connected one will acuire an address quickly but the other one will time-out. The same goes for wireless network interfaces, as Ubuntu will also try to configure them, and if it fails it will still take 60 seconds to time-out.

To fix this you can edit /etc/network/interfaces and remove any interfaces you don't want to be configured at boot, or set them to a static IP, which means that they won't try to connect to a DHCP server to acquire an address at boot. You can do the same thing from the gnome network settings applet (System->Adminstration->Networking) - just set the unused interface to static configuration instead of DHCP.

problem solved

---

### Post by m.musashi on 2006-02-23
I think that is essentially what I did as I experimented. I disabled all but the network I was going to use (wired or wireless, eth0 or eth1). In that case it worked fine. However, if you want both wired and wireless active so that you can boot up in a coffee shop or connected at home what do you do?

I don't mean to hijack, but I think that is the issue the OP is describing.

---

### Post by zoroko on 2006-02-23
Im having that exact same issue, with a twist. When I have my wlan0 set to load on boot, gnome will not load. When I turn off wlan0 and eth0 boot is quick and gnome is fine, then I can turn everything on in the networking settings. 

Is there anyway to have a script turn on eth0 and wlan0 as soon as gnome loads the desktop? That would solve the boot problem and gnome not loading because of it. 

any ideas?

---

### Post by veraction on 2006-02-24
Well, yesterday night I was messing around with my filesystem and was attempting to try out reiser on a partition, but managed to f' up my ubuntu so it wouldn't boot. (could've probably fixed it with a lot of work- but I had everything backed up anyways).
[side note: tried freeBSD cause I heard good things, and eventually got gnome and such, but couldn't configure other things]

so after a fresh install of breezy, I 'fixed' my configuring network interfaces problem.

After installing, I went to network config screen and saw Wireless & wired ethernet - both unconfigured. Since I don't use wired ethernet at all lately, I didn't bother to configure that -- only wireless. And now it takes less than 1.5 sec to "Configure network interfaces"

Not a good solution, but it works for me

---

### Post by NiceGuy on 2006-03-06
[QUOTE=zoroko]Im having that exact same issue, with a twist. When I have my wlan0 set to load on boot, gnome will not load. When I turn off wlan0 and eth0 boot is quick and gnome is fine, then I can turn everything on in the networking settings. 

Is there anyway to have a script turn on eth0 and wlan0 as soon as gnome loads the desktop? That would solve the boot problem and gnome not loading because of it. 

any ideas?[/QUOTE]

Well the way I've got my laptop set up (which works very well) is to allow network mangager to sort out all of my networking stuff and because I my laptop has wireless I use the nm-applet to switch between wireless networks.

To clarify: Go to synaptic and install the nm-applet (which will also install network manager) - or if you have dapper a wireless adapter which uses the IPW2200  driver and would like WPA support go to this thread : [http://www.ubuntuforums.org/showthread.php?t=125150]("http://www.ubuntuforums.org/showthread.php?t=125150")

then go to System > administration > networking,  select your ethernet adapter and click the 'properties' button. Make a note of your settings (incase it all goes wrong) and then if you untick the 'enable this connection' check box and click 'OK'. The device should now say its not configured

Repeat for your wireless adapter if you have one and then reboot.

HOPEFULLY when you reboot it will zoom past the 'configuring network adapters' bit and when you log in the network manager will automatically connect you to your network and the nm-applet will show this.

---

