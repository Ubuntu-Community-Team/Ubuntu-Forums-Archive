---
title: "I'm online with bnep0, but Network Manager doesn't know it"
date: 2009-02-06
forum: General Help
---

### Post by paulherron on 2009-02-06
Hi everyone. I'm delighted to have recently got my Ubuntu netbook using my phone's GPRS connection over Bluetooth. The phone's running Windows Mobile 5, and I'm using Blueman on the netbook to establish the connection. Everything's working pretty nicely. For the record, here's where I've got to so far:

[LIST=1]
[*]Pair the phones using Blueman.
[*]On the phone, select the Internet Sharing app from the programs menu. Choose 'bluetooth PAN', select the correct connection profile and connect. 
[*]In Blueman, go Edit > Services and turn on 'network'. Choose your host and set it as a network access point. Add this, and make sure 'DHCP' is selected in the options. In the 'start a server' section, click the 'network access point' icon to start it up. Close those options.
[*]In the main window, right click the phone and choose to connect. You should see a message that things are connecting on bnep0. Network manger might still say you're connected to your original, but you shouldn't be. A visit to [http://whatismyip.com](http://whatismyip.com) should show your IP has changed. 
[*]Add the line 'iface bnep0 inet dhcp' to /etc/network/interfaces. Without this, you might find your Bluetooth Internet connection drops if you turn off the wi-fi connection you had before connecting to the phone.
[/LIST]

Now, Network Manager thinks I'm still offline, but if I uncheck 'Work Offline' in Firefox, I can load pages. Brilliant! It works. 

My question is, **how can I make Network Manager recognise the connection**? Loading pages with Firefox is great, but Network Manager thinks I'm still offline, and I get errors when I try to use Pidgin, Thunderbird, etc. 

I was hoping I could easily add bnep0 to Network Manager, then just select it to connect to it, but no luck. I also tried setting managed=true in /etc/NetworkManager/nm-system-settings.conf, forcing NM to pick up the bnep0 interface I specified in /etc/network/interfaces. That at least presented bnep0 as an option in NM's tray menu, but connecting to it just times out. 

Andy ideas? Thanks!

---

### Post by walmis on 2009-02-08
Blueman 1.0 would solve your problem :)

---

### Post by paulherron on 2009-02-10
Ah! Fantastic. Thanks walmis - will give it a try.

---

