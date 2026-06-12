---
title: "Wireless on 1520 with ipw3945 / iwl3945"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by trmentry on 2008-02-03
I have an interesting problem.  

I have a Dell 1520 that is running Gutsy and not having any issues except for the wireless. 

It installed the restricted driver (ipw3945) and I was able to connect right away to my AP. (WEP) without issues.  Of course I ran into the issue of it dropping from time to time which is highly annoying as I would have to reboot to get it back.

I did Dell's fix.  Found [here](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues).

However the iwl3945 driver can't connect to the AP.  I can connect to some, but not the ones I need to.  The AP that worked was my Dlink.  But I wasn't able to connect to my work ones using Cisco APs.  I switch back to the restricted driver and connects.


Any ideas?

---

### Post by faulkes on 2008-02-03
> **trmentry said:**
> I have an interesting problem.  

It installed the restricted driver (ipw3945) and I was able to connect right away to my AP. (WEP) without issues.  Of course I ran into the issue of it dropping from time to time which is highly annoying as I would have to reboot to get it back.

I did Dell's fix.  Found [here](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues).

However the iwl3945 driver can't connect to the AP.  I can connect to some, but not the ones I need to.  The AP that worked was my Dlink.  But I wasn't able to connect to my work ones using Cisco APs.  I switch back to the restricted driver and connects.

Any ideas?

Different AP's are likely to have different settings and the drivers themselves may not fully support those settings (or have bugs).  Especially those from a home environment to a work one.

For the AP's you cannot connect to, the first step would be to see if the driver can see the AP's at all

```

sudo iwlist scan <wireless interface - usually eth1>

```

I would also send back the output of:

```

iwconfig

```

and check /var/log/messages or /var/log/secure for any debug output the driver may have sent out.

Finally, any details on the AP's to which you want to connect to and can't (i.e. WEP? WPA? EAP?)

Faulkes

---

