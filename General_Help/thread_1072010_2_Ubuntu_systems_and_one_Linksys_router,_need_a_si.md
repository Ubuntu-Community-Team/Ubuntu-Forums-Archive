---
title: "2 Ubuntu systems and one Linksys router, need a simple network guide."
date: 2009-02-17
forum: General Help
---

### Post by Dieseler on 2009-02-17
I'm currently running Intrepid 8.10 hooked up to a printer and have another pc running Hardy 8.04.

They are both connected to the internet through a RT31P2 Linksys router.
(Cat5 wired ethernet) in the same house.

I'm looking for a simple method to share files between the two Ubuntu machines and also the ability for the Hardy machine to be able to use the printer hooked up to the Intrepid machine.

Its gotta be pretty simple because I am an idiot.
Thanks

---

### Post by plucky on 2009-02-17
For the printer:- Assuming the printer is set up and working on 8.10 system

On the 8.10 system where the printer is connected

**System > Administration > Printer > Server Settings** and tick the box that says "Publish printers connected to this system".

Then on the 8.04 system

**System > Administration > Printer > Server Settings** and tick the box that says "Show printers shared by other systems".

Wait a while and the printer should appear in the window.


Good Luck


For file sharing see this [link for setting up Samba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Dieseler on 2009-02-17
> **plucky said:**
> For the printer:- Assuming the printer is set up and working on 8.10 system

On the 8.10 system where the printer is connected

**System > Administration > Printer > Server Settings** and tick the box that says "Publish printers connected to this system".

Then on the 8.04 system

**System > Administration > Printer > Server Settings** and tick the box that says "Show printers shared by other systems".

Wait a while and the printer should appear in the window.


Good Luck


For file sharing see this [link for setting up Samba](https://help.ubuntu.com/community/SettingUpSamba)

Hey thanks, the printer sharing worked great.

I just set up ssh and could not believe how easy it was for the two Ubuntus to share files.
Problem though.
I did not want to do it over the internet...
I realized when I unplugged my cable modem that I lost access to the shares.
I don't really want to make it that easy for someone to just guess my ip and username then password to have access.
Is that basically what I just did?

---

### Post by internalkernel on 2009-02-17
The computers connected to your router should be NAT'd (Network Address Translation), it's a very basic hardware firewall. Bottom line is that the internet is on the other side of that router... Your machines should be secure... 

If you want to institute more security, you could google how-to's regarding hosts.allow and hosts.deny - this is another basic kind of security that will plug a hole. If you want to get really tricky, start using IPTABLES - high level firewalling and routing in Linux.

In fact, the easiest firewall available is UFW (which should already be installed in 8.10) use Synaptic or Add/Remove to locate GUFW, which is a GUI that will allow you to easily configure UFW. Just put in the IP addresses of the computers & printer on your LAN, set that to allow... and everything else will be dropped.

---

### Post by damis648 on 2009-02-17
> **Dieseler said:**
> Hey thanks, the printer sharing worked great.

I just set up ssh and could not believe how easy it was for the two Ubuntus to share files.
Problem though.
I did not want to do it over the internet...
I realized when I unplugged my cable modem that I lost access to the shares.
I don't really want to make it that easy for someone to just guess my ip and username then password to have access.
Is that basically what I just did?

Just make sure you put the local IP (192.168.1.XXX) instead of the public one and you will be locally connected.

---

### Post by Dieseler on 2009-02-17
Yes, I used the local ip addresses.
I will check into ufw firewall as well.
Once again I was blown away by how easy it was to do this. I have tried this before with Windows and beat my brains out for days trying to make it work. With ssh open server I was done in 5 minutes on both machines.
I'm looking forward to implementing a server next for backups and email.
Thanks again guys.

---

