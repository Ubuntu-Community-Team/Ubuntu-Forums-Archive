---
title: "Dell E520 Wireless Not Working :("
date: 2010-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bikekid450 on 2010-09-18
Hi guys, I'm new to Ubuntu and this Forum, so bare with me.
I will explain my problem to you, it may be long but please read it as this is my last resort I have been trying for 4 days to solve this problem now lol (Haven't been able to sign onto here)

Anyways I have 3 OS, XP, Win7 and Ubuntu, I use a Wireless Adapter (NetGear) and I have to install this for it to work with windows as I have no wireless hardware built in. Now I had to install the Chipset when I installed Win7, I got this from Dell and it says it supports Ubuntu, So I tried to install this by Dubble clicking on it and it says Error, so I tried to install my NetGear software, but it says cannot open CD Cannot find Autorun file. But it worked fine with Win7 just 30mins before... So Basically I must be doing something wrong, how do I install these in Ubuntu? Do I need to install them even? I have a screenshot of what it says when I click on Network manager in Ubuntu. So if any of you can help me I'd be very grateful, if you need anymore info about my pc Etc.. Just ask please. Thanks Guys!

[IMG]http://i294.photobucket.com/albums/mm95/Bikekid450/Theme%20Photos/Screenshot.png[/IMG]

---

### Post by Joe of loath on 2010-09-18
Ubuntu won't work with the Windows drivers and software, it's a different approach in Linux.

Is the adaptor usb or PCI?

---

### Post by Bikekid450 on 2010-09-18
Usb =/

---

### Post by Joe of loath on 2010-09-18
Open a terminal (applications, accessories, terminal), type in lsusb, and post the output here.

---

### Post by Bikekid450 on 2010-09-18
This is what I got =/ 

[IMG]http://i294.photobucket.com/albums/mm95/Bikekid450/Theme%20Photos/Screenshot-1.png[/IMG]

---

### Post by Joe of loath on 2010-09-18
There are some steps for getting it working using the Windows drivers here: [http://www.associatedcontent.com/article/2665279/how_to_install_and_use_a_wg111t_wireless.html](http://www.associatedcontent.com/article/2665279/how_to_install_and_use_a_wg111t_wireless.html)

Joe

---

### Post by Bikekid450 on 2010-09-18
Thanks, but I tried this and ndisgtk isn't there =/ even if I search for it.

Dose it have to be connected to the internet? I have no connection on Ubuntu what so ever right now I am using my laptop to talk to you lol.

---

### Post by ptptaylor on 2010-09-18
If the adapter says it is compatible with Linux then it might have the necessary bits and pieces in the CD somewhere. 
Put the disk in, and browse through the files. Look for something like a driver folder, or IMG or something. If you find a linux folder within that have a delve deeper.

A quick search on the net brought me to this site:

[http://www.linux-wireless.org/Drivers/](http://www.linux-wireless.org/Drivers/)

Which seems to have the steps to follow to install a number of different products.

---

### Post by Bikekid450 on 2010-09-18
Thanks, I have looked on that site but if I click on the link I think I need it says Forbidden. Man... Why is this so awkward for me and simple for others lol

I don't think this is gona work I can't see any of the files you said about. I connected it to the internet by the cable so I can update it, then tried to install Kaspersky but it won't install. I must be doing something wrong, do you not click on AutoRun to install?

[IMG]http://i294.photobucket.com/albums/mm95/Bikekid450/Theme%20Photos/Screenshot-2.png[/IMG]

---

### Post by ptptaylor on 2010-09-18
Ok a slightly longer search in google took me to here:
[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)
Looks like the site you're wanting!

You won't want to be installing Kaspersky on ubuntu since there isn't any point. Anti-virus programs are virtually obsolete on linux since they're not needed.

---

### Post by Bikekid450 on 2010-09-19
Thank you very much I'll give that site a try now!

Edit: Okay I found "ndisgtk" but I've come across another problem. How to install it? Lol if I click Apply it doesn't install it I've look on here and google but I don't seem to have any of the buttons that I should have?

I'm learning but slowly lol.

Okay I followed the steps in that guide, I am stuck on step 6:

**Step 6**

 Plug back in USB Drive. The Network Manager should do the rest. 
WEP and WPA encryption should work out of the box. 

When I plug it in nothing happens so I tried step 7... It says command not found.

---

