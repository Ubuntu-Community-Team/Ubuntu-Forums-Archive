---
title: "Tungsten E Hotsync problems!!"
date: 2006-07-14
forum: Desktop Environments
---

### Post by gdgardnerw on 2006-07-14
I cannot get Evolution to hotsync with my Tungsten E palm pilot. I am running Dapper. I installed Dapper Drake on my son's machine and it had no problem detecting the user information on the Tungsten. I then bought a new machine and put Dapper on it, and I have been two weeks trying to get it to hotsyc to no avail!

I read and followed Robenroute's suggestions (except for the first two steps, since I don't have groups) and it did not help at all. 
> 
1. In a terminal window:

rob@ubuntu:~$ ls -al /dev/pilot
crw-rw-rw- 1 root dialout 188, 1 2005-10-19 18:08 /dev/pilot
rob@ubuntu:~$

As you can see, root is the owner, dialout the group.

2. make sure the user wanting to sync, belongs to group dialout
System->Administration->Users and Groups
(just make sure you tick "Show all users and groups") If the sync users doesn't belong to group dialout (or whatever other group name /dev/pilot shows), make sure you add this user to this group. Also make sure everyone has read+write (666) rights.

3. System->Administration->Device Manager
Browse through the device tree and locate your Palm device (in my case "palmOne Handheld"; click on it/select it. In the righthand pane, you'll see 2 (or 3, deending on which branch/leaf in the tree you selected) tabs; select the Advanced one. There should be an "info.udi" key. In my case the key value reads:
/org/freedesktop/Hal/devices/usb_device_830_61_.....

The "830" and "61" values (they might differ in your case) are needed and should be used to configure the following file correctly; type in a terminal window:

sudo gedit /usr/share/gnome-pilot/devices.xml

Scroll down the file and locate "your" device. Well, in my case, my device wasn't present at all so I had to insert it:

<!-- Palm Tungsten T -->
<device vendor_id="0830" product_id="0060" />
<!-- palmOne Handheld -->
<device vendor_id="0830" product_id="0061" />
<!-- Palm Zire -->
<device vendor_id="0830" product_id="0070" />
<!-- Palm M100 -->
<device vendor_id="0830" produ....

Be careful! In my setup, there was a Palm Zire 31 listed with this same product_id="0061". Now, having 2 identical product IDs in this file won't work (I've tried...) So, make sure there's only one and the string between <!-- and --> reads what you've copied from the Device Manager tree.

Save and exit.

One more file to edit (i got this from [http://www.ubuntuforums.org/showpost...72&postcount=4)](http://www.ubuntuforums.org/showpost...72&postcount=4)). Again, in a terminal window:
sudo gedit /etc/udev/rules.d/10-custom.rules

and add the following line.

BUS="usb", SYSFS{product}="palmOne Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Save and close it. As you can see, I applied MY device name here, again. Check your Device Manager's tree for the correct device name of your Palm device!!!

4. Sytem->Preferences->PalmOS Devices
Follow the wizard, but make sure you select a high time-out value (I've got 30 sec.). BTW, there's no need to change the device to something along the lines of /dev/ttyUSB0, or so. /dev/pilot works like a charm, for me.

Also, no need to press the Hotsync key before proceeding with the wizard (as suggested in other threads). In fact, doing that didn't work at all, in my case. Just follow the wizard and when it tells you to press the Hotsync key, press it! On my laptop, it took about 10 sec. before the wizard told me that it had successfully retrieved my ID and username.

Stil in the wizard, press the forward button

5. Now, on the Conduits tab, set the correct behaviour for your conduits and close.

6. Start up Evolution and from the Edit menu, select Synchronization options. Follow the same procedure (somehow, in my case I was guided through the PalmOS Devices wizard again).

7. With your Palm connected, just hit the Hotsync button on the cradle (or the one on the screen).


Everything got synchronized. All appointments, addresses, to-dos, etc. Just one little hiccup: during the rest of the backup (some T5-settings were being synchronized, according to my T5), Breezy popped up a little window telling me that the gpilotd program had crashed. Bother!!! I just need to find out what happened there....

Happy syncing!

Rob

I have even manually copied off the pilot user information from my son's machine and put it in Evolution on my machine...and it still doesn't hotsync. The information for the Tungsten on both machines looks identical on System>Administration>Device Manager. I am on the verge of going insane! Help, please!](*,) 

Thanks in advance for your help.

Greg

---

