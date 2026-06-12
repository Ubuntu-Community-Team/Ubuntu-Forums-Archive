---
title: "Networking to MSHome on Dell Mini"
date: 2009-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lmbevard on 2009-01-30
I got a new Mini last Sunday and got most things working. I had to work to get the wireless internet working (works great) but eventhough I am on the wireless for internet I can not get connected to my existing MSHome network off of my Dell 4300 running Win XP. Right now I can see my other Dell laptop and my Son's computer and can share the printer and the extra drives across the network. I cannot see the Mini or the Mini can not see the network. I go to Places>Network and see the Icon for Windows Network, click, See MSHome and MSWork, click on MSHome and nothing. I do have my Firewall set on the desktop to accept all address of the Network. Any Ideas?

---

### Post by emnii on 2009-01-30
You'll need to map the share by IP address.

Go to Places -> Connect to Server
In the Service Type dropdown select Windows Share
For Server enter the IP address of the machine with the share
For Folder enter the share name.
Click Connect

The share should pop up. Hope this helps!

---

