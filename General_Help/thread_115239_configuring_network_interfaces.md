---
title: "configuring network interfaces"
date: 2006-01-10
forum: General Help
---

### Post by paracetamolo on 2006-01-10
hi,
during my boot that it lasts 1 min and 50 sec, 1 minute is taken by "configuring network interfaces", I'm running the last release of ubuntu beezy on a laptop, I didn't need any wifi driver do make my card work, my question is:

if I install a driver (i.e. ndiswrapper) it will make the boot faster or is just the normal time needed for assigning ip addresses and other network stuff?

thanks

---

### Post by nkhansen on 2006-01-10
I have had the excact same problem. Some times it took around 10 seconds, others it would be more like a minute. I solved it by making the interface static, but it seems like a bad solution. Maybe this is a bug to be reported??

---

### Post by kwaanens on 2006-01-10
I also have issues with this. I don't usually use a cable network, and when it is plugged in, it takes forever.
Recently it's also acting up with only wireless.

- Ketil

---

### Post by healychan on 2006-01-10
[QUOTE=paracetamolo] I didn't need any wifi driver do make my card work, my question is:[/QUOTE]
You do need a driver for wireless card to work. You didn't install doesn't mean you don't need. I think because your card is compatible with Ubuntu, so you don't need to do it yourself, driver maybe installed when you install Ubuntu.

[QUOTE=paracetamolo]
if I install a driver (i.e. ndiswrapper) it will make the boot faster or is just the normal time needed for assigning ip addresses and other network stuff?
[/QUOTE]

Ndiswrapper will not make boot time faster. We only install ndiswrapper when we need to use Windows driver on Linux. If you don't use wireless card, then disable it. And choose the interface you fancy as the default gateway.

If configuring network interface taking too long at start up. Press Ctrl + c to skip that part. Then do the configuration manully later.

---

### Post by fast orange on 2006-01-10
is this even necessary at startup?  i always use ctrl+c to skip this part of the boot, and i never have issues that i have to configure later on.  is there a way to completely remove this part from the boot process (and the one after it, "Waiting for network interfaces to come up").  Or is there a way to make this part of the boot go faster.  P.S. i use a wireless network and wifi-radar if this makes a difference.

---

### Post by Whatsisname on 2006-01-10
thats because the DHCP server is taking a moment to reply.

---

### Post by healychan on 2006-01-10
[QUOTE=Whatsisname]thats because the DHCP server is taking a moment to reply.[/QUOTE]
If you try to gain IP with a wrong setting of the network, it is not possible.
The system will keep trying until timeout, that's why people think the system hang.
The best solution is configure your card properly instead of pressing Ctrl + c when boot.

---

### Post by fast orange on 2006-01-11
i'm not quite sure what i need to do to configure my card correctly.  can you explain what you mean in some more detail or point me to a site that may be helpfull?  thanks.

---

### Post by healychan on 2006-01-11
[QUOTE=fast orange]i'm not quite sure what i need to do to configure my card correctly.  can you explain what you mean in some more detail or point me to a site that may be helpfull?  thanks.[/QUOTE]
What do you wanna know???

---

### Post by rbattenfeld on 2006-01-11
Hi

I experienced the same problem in Ubuntu 5.10. There is no difference if I am using Ndiswrapper or a PCMCIA-Wlancard. After the long startup time, I have always to deactivate and and activate the wlan0, without any changes in the settings. Then, the internet connection works. It seems to be a timing problem. It worked fine in Ubuntu 5.05.

Of course, I can live with this issue, but for me, I am interested to know the reasons for this behaviour.

Regards,
Ralf

---

### Post by paracetamolo on 2006-01-11
ok, thanks everybody, I wanted just to be sure there was nothing to be done:D

---

### Post by Tiede on 2006-01-17
I am also having the same problem with breezy. This step of the boot up lasts about two to two minutes and a half on my laptop. 
Now I know Ctrl+C works, I do it quite a lot actually. But sometimes, when I do it, internet apps (apt-get, firefox) acts like there is no internet connection even if network-manager says I am connected. Then I have to reboot and it works. Why? Go ask a lamma.
So yesterday I have been trying to find a way to solve this. Since I knew that it took so long because of bad ESSID or other conf, I erased my default ESSID from System->Administration->Network, thinking that network-manager (nm-applet) will find the correct one and load it. Boy, was I wrong. If I take out the default ESSID, then the wlan interface is deactivated and does not even appear in the network-admin, which means, network-manager cannot connect to anything and only shows cable connections.
So in other words, I am stuck with leaving an ESSID in the network-admin so my card gets activated, and do Ctrl+C - which makes me have to stay in front of my laptop during boot time, which I hate - to have it working because I move a lot and of course so does the wlan network along with the ESSID...
Now here are my questions.
Does anyone know of a way to disable the default ESSID and still have the wlan0 interface present?
I don't understand why a default ESSID is necessary when using a laptop, since in theory a laptop is used for mobile computing, and it is rather unlikely that all the places one goes to will have the same ESSID...Can someone point to me the obvious reason that I cannot seem to figure out on my own?
Finally - and maybe just a tad too broad, - why doesn't ubuntu move the whole ntp time mess to a shutdown procedure rather than startup so the network could be wake on call, or something along those lines?

---

### Post by tkjacobsen on 2006-01-17
if you comment out the line  "map eth0"  in /etc/networks/interfaces the network device eth0 won't configure at bootup. When logged in you just type 
```
sudo ifup eth0
```
to configure the device. I do this on my laptop cause it is now allways wired. I do the same with ra0 (my wireless lan pcmcia card).

---

### Post by Tiede on 2006-01-17
But I am always on the move with my laptop...
Do you think that commenting out mapping and write a script to
```
sudo ifup eth0
sudo ifup wlan0
```
and have it run at gnome login will make things better?

and thanks for replying so fast.

---

### Post by Fr33d0m on 2006-01-24
I have not yet set my wireless to start automatically because of the time it takes to start.

IMHO part of the time issue is the search for a channel.  I'm still looking for where to set that up.

BTW, I had nothing but trouble with Network-Manager and removed it with prejudice.

---

### Post by Tiede on 2006-01-25
May I ask what you use in its place then?
nm-applet hasn't given me any problems as of yet, but it's always better to know the alternatives in advance ;)

---

### Post by Fr33d0m on 2006-01-25
[QUOTE=Tiede]May I ask what you use in its place then?
nm-applet hasn't given me any problems as of yet, but it's always better to know the alternatives in advance ;)[/QUOTE]

I don't use any of them.  They all make my network unusable.  I just tried NM again and got the same result.  Lots of folks say they have good results with each of these apps so I have to figure I'm missing something.  Perhaps I need to uninstall something or tweak some file....  I'm still looking for answers.

---

### Post by stream303 on 2006-01-25
Have you looked at your **/etc/resolv.conf**
file to see if the nameserver is pointing to your isp's actual dns nameservers?

It might just be pointing to some local hardware providing dns services, but not doing a good job of it.

There is an easy fix by editing /etc/dhcp3/dhclient.conf but we can go from here...

---

### Post by robotgeek on 2006-01-25
Just remove the line "auto wlan0" or "auto eth0" to stop it from bringing it up at boot in the file /etc/network/interfaces

---

### Post by Madpilot on 2006-01-26
Are ifdown/ifup the Linux equivilent of Window's "Release/Renew?

If not, what is? I was having network trouble tonight - partly self-inflicted - and actually had to restart the machine to renew the IP address. I *know* there's a more elegant way than the Restart button... :P

---

### Post by Fr33d0m on 2006-01-26
[QUOTE=stream303]Have you looked at your **/etc/resolv.conf**
file to see if the nameserver is pointing to your isp's actual dns nameservers?

It might just be pointing to some local hardware providing dns services, but not doing a good job of it.

There is an easy fix by editing /etc/dhcp3/dhclient.conf but we can go from here...[/QUOTE]

Yes.  It is (or was at the time).  Today I couldn't get the network up and did sudo ifup ath0 and watched as it looked for dhcp offers, failing many times.  Thats curious.  I wonder if there is a setting somewhere to tell it to where to get the dhcp address.  Perhaps I need to change the router's channel and try again. 

Any other ideas?

---

### Post by Robor on 2006-01-26
[QUOTE=Madpilot]Are ifdown/ifup the Linux equivilent of Window's "Release/Renew?

If not, what is? I was having network trouble tonight - partly self-inflicted - and actually had to restart the machine to renew the IP address. I *know* there's a more elegant way than the Restart button... :P[/QUOTE]

I would think they would be more like 'disable/enable' than 'release/renew'.

---

### Post by Robor on 2006-01-26
[QUOTE=Fr33d0m]Yes.  It is (or was at the time).  Today I couldn't get the network up and did sudo ifup ath0 and watched as it looked for dhcp offers, failing many times.  Thats curious.  I wonder if there is a setting somewhere to tell it to where to get the dhcp address.  Perhaps I need to change the router's channel and try again. 

Any other ideas?[/QUOTE]
I'm *far* from an expert in TCP/IP and networking in general but I believe DHCP requests are broadcasts so you don't have to tell them where to go.

---

### Post by Fr33d0m on 2006-01-26
[QUOTE=Robor]I'm *far* from an expert in TCP/IP and networking in general but I believe DHCP requests are broadcasts so you don't have to tell them where to go.[/QUOTE]

Requests, offers... they are broadcasts at least.  The point is that If I could tell it to get DHCP from a particular domain/network name, perhaps it wouldn't take so long to get an address.  I did find something at /etc/dhcp3/dhcp.conf but will have to research to be sure.

---

### Post by ned.b on 2006-01-27
[COLOR="Red"]###IGNORE THIS - IT FAILED - READ ON FOR A FIX###[/COLOR]

I have cured this problem on my wireless network by specifying the connection settings for my access point in the /etc/network/interfaces file; this means the card does not spend ages searching...

The following is the relevant snippet

----------------------------------------------------------------------------
#Wireless Interface
auto wlan0
iface wlan0 		inet 		dhcp
wireless-essid 	         FRED
wireless-mode 		managed
wireless-channel	11
-----------------------------------------------------------------------------

Obviously you may need to make changes for your particular config
* replace wlan0 with whatever your wireless nic is called 
* replace FRED with whatever your essid is 
* replace 11 with whatever your channel is

hope this helps :)

---

### Post by Robor on 2006-01-27
I just checked my /etc/network/interfaces file and I already had a lot of that info there.  the trouble is, I'm not sure if I manually entered it previously or if it was saved when I configured my wireless connection.

**Note:  My file had my WEP key in there as well so if you're running WEP encrypted wireless I think you'll need to put it in there as well.**

---

### Post by Tiede on 2006-01-28
[QUOTE=ned.b]I have cured this problem on my wireless network by specifying the connection settings for my access point in the /etc/network/interfaces file; this means the card does not spend ages searching...

The following is the relevant snippet

----------------------------------------------------------------------------
#Wireless Interface
auto wlan0
iface wlan0 		inet 		dhcp
wireless-essid 	         FRED
wireless-mode 		managed
wireless-channel	11
-----------------------------------------------------------------------------

Obviously you may need to make changes for your particular config
* replace wlan0 with whatever your wireless nic is called 
* replace FRED with whatever your essid is 
* replace 11 with whatever your channel is

hope this helps :)[/QUOTE]
Your trick would work if I was not on the move with my laptop, but I change location all the time, and thus the ESSID changes. Unless it does not even try to check it if it is already specified... then Network Manager would fix it right up :)

---

### Post by Fr33d0m on 2006-01-28
[QUOTE=ned.b]I have cured this problem on my wireless network by specifying the connection settings for my access point in the /etc/network/interfaces file; this means the card does not spend ages searching...

The following is the relevant snippet
<snipped>

I have moved to a static address for now to clear my mind on the exact issue.  Now I get near instantanious interface activation.  But if I set auto on I get an activated connection and no IP address.  This is my interfaces at the moment:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

#echo connects ath0 when device is hotplugged. using echo instead of grep #allows any device to be brought up when hotplugged. Note this could cause a #problem if a device is active and another one that is mapped is plugged in.
mapping hotplug
        script Echo
        map ath0

#iface ath0 inet dhcp
iface ath0 inet static
gateway 192.168.0.1
wireless-essid myessid
address 192.168.0.2
netmask 255.255.255.0
#wireless-channel 9
auto ath0

---

### Post by ned.b on 2006-01-31
:mad: It broke again!

Have tried setting a manual IP configuration too - it worked flawlessly the first time, then nothing...  In order to get it working I have to go:

system\administration\networking\wireless connection\properties\remove and replace the tick from [enable this connection]

This *usually* gets the nic up and running again

back to square one :???:

---

### Post by ned.b on 2006-02-04
In my case the delay in booting and subsequent failure of the wireless nic to do anything useful until re-enabling the interface was intermittent, once working, it worked on subsequent reboots and then failed again.  The key factor being rebooting was fine, shutdown and restart was not fine.  After shutdown and restart the "default gateway device" in system\administration\networking was blank, selecting wlan0 cured the problem.  Specifying "auto wlan0" at the end of the stanza rather than at the beginning in /etc/network/interfaces seems to have resolved this issue (at least it currently works after repeated reboots and shutdowns).  My interfaces now looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
#      map eth0
	map wlan0
#iface eth0 inet dhcp

#Wireless Interface
iface wlan0 inet dhcp
wireless-essid #ESSID#
wireless-mode 	managed
wireless-channel 11
auto wlan0
```

keeping my fingers crossed :neutral:

---

### Post by oliwally on 2006-11-22
I have found [this post]("http://ubuntuforums.org/showthread.php?p=1794951") quite useful for my Dell D820:

[http://ubuntuforums.org/showthread.php?p=1794951](http://ubuntuforums.org/showthread.php?p=1794951)

In a nutshell:

> i assume you've confirmed that ra0 is your wireless adapter? if so, make a backup of the file:

```
sudo cp /etc/network/interfaces /etc/network/interfaces_old

```
and delete all entries except for the lo and ra0. modify ra0 so it looks like this:

```
auto ra0
iface ra0 inet dhcp
wireless-mode managed
wireless-essid default
```

and see if it still hangs.

---

