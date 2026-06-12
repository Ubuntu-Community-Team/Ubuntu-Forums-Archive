---
title: "How-To set up internet connection sharing and how to network your xbox"
date: 2005-12-14
forum: Desktop Environments
---

### Post by mckryptyk on 2005-12-14
Hello everyone this is my first post here and I decided to join after seeing how helpful the people on this forum are.

I though that I should also contibute so I have a How-To included in this post.

<Begin How-To>

How to set up internet connection sharing in Ubuntu breezy made easy! This also works for setting up an Xbox.

First off all you need to get your internet connection up, I did this by going to [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/") because I have the Alcatel Speedtouch USB.

Back to the howto: Next you need to install firestarter so
type ```
sudo apt-get install firestarter
``` in the Terminal (Applications->Accessories->Terminal)

Now under go under System->Administration->Networking and enter your password then click on your ethernet connection
(Eth0,Eth1,you get the idea) then click properties.

Now you need to check the box for "**enable this connection**"    
and set your "Configuration" box to "**Static IP**".
Under "IP Address" type "**192.168.0.1**" (Again without the quotes).
Now "Subnet Mask" should be "**255.255.255.0**".
Make sure to leave "Gateway Address" **blank** (in this guide you won't need it).

Now on the other computer these are the settings to use:
(Just type the numbers)
StaticIP	= Yes

Ip		= **192.168.0.2**

Subnetmask	= **255.255.255.0**

Defaultgateway	= **192.168.0.1**

DNS1		= Under System->Administration->Networking

DNS2		= click on the "DNS" tab and write them down
                         copy them into "DNS1" and "DNS2".
                         

Now connect the computers (I use a crossover cable for this) 

now go into Applications->System Tools->Firestarter or type in Terminal again: ```
sudo firestarter
```

Now in firestarter click on Firewall->Run Wizard
and follow the penguin :)

Select your internet device (mine is ppp0)
Select "**start the firewall on dial-out**"
I'm on DSL so I also selected "IP address is assigned via DHCP"

Now this is where it all pays off in the next menu select
"**Enable internet connection sharing**"
Now select Eth0,Eth1,or Eth-whatever from earlier on.
Select "**Start Firewall Now**"
and click on **save**

Now click on "Firestarter" in the bottom gnome panel  
when the menu pops up (click again if it did not pop up)
click on the big "**Preferences**" button.

Under the "Policy" section enable "**Apply policy changes immeadiately**". 

Reboot if you have to but go to [http://www.fs-security.com/]("http://www.fs-security.com/") and search Ubuntu Forums for more on how to configure your shiny new connection sharing firewall. 

<End How-To>

That's all for now I have some other ideas for howto's that I'd like to do. Let me know what you thought of this
such as writing tips for the future howto's, where this needs polish,etc.

---

### Post by gb5757870 on 2007-03-10
Hi,

I realise you posted this over a year ago but I just want to say thank you, thank you, thank you! I had been scouring the forums and web trying to figure out how to get my Xbox net access with the exact scenario you wrote and now works flawlessly.

Thanks heaps !

G

---

### Post by HeruLuingul on 2008-02-29
Hey, sorry for resurrecting an old thread, but it seemed the best one to reply in.
I went through with the whole process in the tutorial, and it seemed to work great, but xbox Live is telling me the NAT is Moderate, and it should be Open. Anyone know how to fix this? When I'm playing on Live, it works for the first ~10 minutes, then lags horribly to the point of being unplayable.

PS, I used to run the Live through my win XP laptop, and it would work fine, open NAT and everything, so it's not my router, it's definitely firestarter.

---

