---
title: "WPA wireless help..."
date: 2005-12-17
forum: General Help
---

### Post by pugs on 2005-12-17
Trying to get WPA-PSK working on my IBM Thinkpad A20m...I have a D-link DWL-G650 card.  The card worked great with the ubuntu live CD and no security.  I had some trouble getting it working when I actually installed kubuntu.  The GUI is strange, but I finally got it working through that without any wireless security.

Now I am trying to get WPA-PSK up and running.  I followed this Tutorial:
[http://ubuntuforums.org/archive/index.php/t-90450.html](http://ubuntuforums.org/archive/index.php/t-90450.html)

But it did not work.  Since I used the GUI to set it up I dont really even know what driver the card is using.  I am assuming its the madwifi driver since its an atheros based card.  I just dont know where to go next...seems like many people were able to get up and running with that tutorial.

Maybe I should start over and try to configure it all manually without the gui garbage and without WPA and then try adding it again?  Are there any good how-to's for doing that?

---

### Post by Lambert on 2005-12-17
See if any of these help.

[http://www.madwifi.org/wiki/UserDocs/802.11i](http://www.madwifi.org/wiki/UserDocs/802.11i)

You can ignore the part on compiling the source as you can just install wpasupplicant from the repos.

[http://www.madwifi.org/wiki/UserDocs/HostAP](http://www.madwifi.org/wiki/UserDocs/HostAP)

Post back you results on getting this to work. I have the same card which i plan I playing with wpa in the future at some point to see if I can get it working.

---

### Post by wabene on 2005-12-17
Hi-
Just installed Ubuntu for the first time and now I find out my D-Link DWL-122 USB wireless adaptor is not supported. Can anyone suggest a good, affordable option? My router is a D-Link DI-764 which is A & B (I think I am the only person who thought A was the way to go because it operates on a different frequency than cell phones).

Wilbur

---

### Post by pugs on 2005-12-17
[QUOTE=Lambert]See if any of these help.

[http://www.madwifi.org/wiki/UserDocs/802.11i](http://www.madwifi.org/wiki/UserDocs/802.11i)

You can ignore the part on compiling the source as you can just install wpasupplicant from the repos.

[http://www.madwifi.org/wiki/UserDocs/HostAP](http://www.madwifi.org/wiki/UserDocs/HostAP)

Post back you results on getting this to work. I have the same card which i plan I playing with wpa in the future at some point to see if I can get it working.[/QUOTE]

2 questions...does madwifi come on the kubuntu CD?  I never downloaded it and I cannot find it in the package manager or whatever.

Second, do I need HostAP to get this working?  I found another tutorial that says you do need it...while the tutorial I posted a link to doesnt make any mention of it :(

---

### Post by pugs on 2005-12-17
Well making some progress.  The reason I could not find madwifi is that I did not have the repository for it.  Apparently (k)ubuntu comes out of the box with an old version.  So I upgraded to the latest and greates according to this:

[https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29)

Then I ditched the GUI and followed along with this:

[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)

At this point I have a working network again with a WEP 128 bit key.  This is with a DWL-G650 as I said before...I think its a Revision B.  Not the 650+.  There is a special how to for that somewhere because it uses a Texas instruments chip....not atheros.

Next step try WPA-SPK again.

---

### Post by pugs on 2005-12-18
Well WPA-PSK seems to sorta work.  I think the card and the router are talking now.  BUT...I cannot get an IP address for some reason.

I just get:

No DHCPOFFERS received
No working leases in persistent database - sleeping.

But looking at the "KWiFiManager" says its connected...but obviously no Local IP address.

I found this in syslog:

ath0: no IPv6 routers present

Anyone have any ideas on where to go from here?

---

### Post by klepto on 2005-12-19
You have ipv6 turned on and unless it's configured properly you won't get a connection. If you want to turn it off: 

nano /etc/modprobe.d/aliases

add this:
#alias net-pf-10 ipv6
##################
#Enter Stuff Here#
##################
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

remember to comment out alias net-pf-10 ipv6
reboot and it should have turned ipv6 off.

Now as far as not getting an ip addess from your dhcp router. are you using dhclient or dhcpcd? I have problems getting ip's at times after I make changes to my wireless device like going from monitor mode to regular 802.11g. Any one got an easy solution for that one?

---

### Post by pugs on 2005-12-19
What does IPv6 have to do with it?  I honestly dont know....I dont like turning things off that I dont have a reason for ;)

It looks like kubuntu comes with dhclient...but I tried dhcpcd as well.

One question.  What is hostapd?  Do I need it along with the wpa_supplicant?  I see alot stuff talking about hostapd in regards to wpa, however I cant seem to find any pages that say you do or do not need one or the other...

I did find some pages about people having issues with IPv6...but no info about exactly why it causes problems.  I will give that a try though.

I did get WPA-PSK to work once or twice yesterday, but it was using old DHCP leases.  It could not get a current one and just used a stored one.  So I dunno if the IPv6 is gonna help unless it is causing my DHCP problems.

---

