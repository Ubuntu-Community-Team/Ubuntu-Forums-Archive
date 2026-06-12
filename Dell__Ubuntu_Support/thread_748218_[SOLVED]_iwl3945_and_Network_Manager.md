---
title: "[SOLVED] iwl3945 and Network Manager"
date: 2008-04-07
forum: Dell  Ubuntu Support
---

### Post by kmleon on 2008-04-07
Greetings everyone,
First time posting here.

I have a brand new Dell m1330 (maxed out) only about 2 weeks old now (preinstalled with ubuntu 7.10) and all the current updates as of today.

Using the Dell wiki, addressed the hibernate issues.
Then followed the directions to switch from ipw3945 to iwl3945.
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)


For some reason the first time around it locked up the mouse. Rolled it back and wrote a script to automate the switch, and went smoothly the second time.

Networking works with the wifi with the iwl3945 driver.

However, Network Manager (and related profiles) do not work properly. I had a static IP assigned (port forwarding in my firewall for some services) when using the ipw3945 (and that feature worked fine), but now can't get it to be assigned, the iwl3945 driver just keeps defaulting to dhcp.

In Network Manager it doesn't even recognize the wifi card as wireless, only "wired" now. I configure it anyway (wlan0_rename is what the system calls it now) as static, it adds it to the settings interfaces list (both gui and in /etc/network/interfaces), but then still adds a separate additional listing for wlan0_rename auto, and only uses the auto setting.

Using "Network Tools" it shows the device, but when I hit the "configure" button, it gives the following error:
"The interface does not exist.
Check that it is correctly typed and that is is correctly supported by your system."

This worked properly with the ipw3945 driver, but of course, under load it would drop it's connection, and make it impossible to shutdown the system cleanly. So far (1 day) no more lockup problems, so this is an improvement as far as stability, but causes problems in other usability.

Suggestions please?
Thanks!

---

### Post by sdennie on 2008-04-07
One thing that you might try would be to comment out the ipw3945 udev rule in the file: /etc/udev/rules.d/70-persistent-net.rules.  On reboot (or restarting some services), that should cause the wireless card to be named something more sane like wlan0.  That change fixed a number of problems for me.

---

### Post by kmleon on 2008-04-07
Thank you very much. That did help.

One thing I notice (And have seen others post this on other forums) is that it takes quite a while for the card to initialize now.
Whereas before the ubuntu/gnome desktop would come up quite quickly after logging in, it now can take upwards of a minute before it loads after logging in, it looks like it is waiting on the Network Manager loading the iwl3945 driver before it lets me access the desktop. This is less annoying than the previous lockup issues with the ipw driver, or the now fixed issue with not being able to assign an IP and have it show up in Network Manager with the iwl driver, but still definitely needs some resolution.

Hopefully driver updates will resolve that.

Thanks again for the info. The problem as posted is now resolved with that edit.

Cheers!

---

### Post by sdennie on 2008-04-08
I'm glad that helped.  

As for the slow login stuff, if I remember right, it used to be the case in older versions of Ubuntu that not letting Network Manager have complete control over your network card would cause some strange timeouts when trying to bring the card up (It's been so long that I don't remember exact details).  I don't know if that's still the case but if you've previously used System->Adminstration->Network to try to force a static IP it's possible that you are seeing something like that.  You could check to see if that's the case by looking at /etc/network/interfaces and, if it lists your wireless card in that file, that could be the problem (it should only have two lines for the loopback interface if everything is under Network Manager control).  Setting all the network interfaces to "roaming mode" in System->Administration->Network may be all you need to do to get things running quickly again.

---

