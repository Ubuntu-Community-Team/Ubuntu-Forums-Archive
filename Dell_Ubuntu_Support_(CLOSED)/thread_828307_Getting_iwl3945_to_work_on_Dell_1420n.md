---
title: "Getting iwl3945 to work on Dell 1420n"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mlsquad on 2008-06-13
I have a Dell 1420n that came with Ubuntu preinstalled. I tested the 8.04 waters, but the wireless didn't work and neither did the work-arounds. So I went back to 7.10 using the .iso from ubuntu.com, not from Dell. The Dell image seems to load a little slower.
Anyhow, I have witnessed the problem listed at [http://linux.dell.com/wiki/index.php/Ub···e_Issues](http://linux.dell.com/wiki/index.php/Ub···e_Issues) where after a while the wireless dies and the computer needs to be rebooted. I followed the instruction and the iwl3945 loads fine, but the wireless doesn't work at all.

Here are the obligatory outputs. Let me know what other information is needed.

> lsmod | egrep 'Module|iwl|ipw'
Module Size Used by
iwl3945 88168 0
iwlwifi_mac80211 175112 1 iwl3945
cfg80211 7304 1 iwlwifi_mac80211


> iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Interface doesn't support scanning.

wlan0_rename No scan results

---

### Post by fragos on 2008-06-13
I also have a 1420n which came with 7.04, replaced by Dell 7.10 and finally replaced by 8.04. I did look at [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04), add a Dell software source and install the backport to get my WiFi led to work. Wifi with the IWL driver works well even coming back in roam moad after suspend and hibernate with a change of physical location and available access points. There are ocassional signal drops when connected to public access points with lower signal levels that have multiple users. I have no drop off with strong signals at home. From my perspective, each new release of Ubuntu has has improved WiFi operation. Perhaps your issue relates to the applications you're running. I quit Firefox and only use Epiphany as I find it both faster and more stable. They both use the Gecko rendering engine. My 1420n has the Intel video so if you have the Nvidia video that might be acontributing factor. I've Nvidia on my desktop and never had any trubles with it but it has a wired connection to my access point eliminating WiFi as a factor.

---

### Post by mlsquad on 2008-06-13
Thanks for the response.  My issues with wireless on 8.04 where out of the box.  Some Googling showed the issue to be widespread, but the fixes that worked for some did not work for me.  This was on a vanilla install with nothing changed except the latest updates downloaded.
This problem I am having with 7.10 is also on a fresh install.  Well, the install isn't fresh anymore, but when I did install it fresh, I was having this exact same problem with using the iwl drivers.

---

### Post by treeclimber on 2008-06-15
My 1505n came with 7.04 and connected wonderfully with the driver that came with that.  It was a proprietary driver for the 3945 card.  I updated to 7.10 and it still worked, but did what you are talking about, dropping my connection after operating for awhile.  So when 8.04 cam out, I updated, hoping this little problem would be fixed.  Nope!  Mine did what yours did, no connection.  It sees the connection, it just won't connect.  And, as you say, it is a widespread problem with this particular card.  I hope they get it fixed.  i have read so many "fixes", but none of them work on every computer with this problem.  I really don't feel like fiddling around with it anymore.  I went back to 7.04 and am currently updating to 7.10 again.  Let's hope they make a big announcement when it is fixed.

---

### Post by mlsquad on 2008-06-15
I am a little disappointed in Dell.  The reason I went with Dell + Ubuntu was because I assumed Dell would be proactive about making sure these machines worked great with Linux.

---

### Post by fragos on 2008-06-15
I think this WiFi card is getting an undeserved bad rap. There are steps in making a connection with timeouts and delays before retry. 1st there is an interval at which the access point annouces it's presence. How often and if sent is a function of the access point. If a connection isn't found there will be a delay before retry. No connection can be made if the access point doesn't respond when a connection is requested. My home access point has a stronger signal and only one user -- it responds quickly to connect requests and connections are never lost. When at my favorite coffee house there are many access points with multiple users and lower signal strength. It takes longer to establish a connection or recognize all the available access points. Connections on sometimes dropped but that may be an indication that the access point is heavily loaded or even that a moving truck has interferred with the poor signal. I have niticed that even when an access point hasn't announced itself you can still manualy initiate a request to connect by right clicking the network manager icon and selecting "Connect to other wireless network..." If there was a problem with the card you wouldn't be able to connect manually. This isn't to say that the WiFi card, it's driver and the network manager don't play an important role.

---

### Post by mlsquad on 2008-06-15
> **fragos said:**
> I think this WiFi card is getting an undeserved bad rap. There are steps in making a connection with timeouts and delays before retry. 1st there is an interval at which the access point annouces it's presence. How often and if sent is a function of the access point. If a connection isn't found there will be a delay before retry. No connection can be made if the access point doesn't respond when a connection is requested. My home access point has a stronger signal and only one user -- it responds quickly to connect requests and connections are never lost. When at my favorite coffee house there are many access points with multiple users and lower signal strength. It takes longer to establish a connection or recognize all the available access points. Connections on sometimes dropped but that may be an indication that the access point is heavily loaded or even that a moving truck has interferred with the poor signal. I have niticed that even when an access point hasn't announced itself you can still manualy initiate a request to connect by right clicking the network manager icon and selecting "Connect to other wireless network..." If there was a problem with the card you wouldn't be able to connect manually. This isn't to say that the WiFi card, it's driver and the network manager don't play an important role.
The problem with this wifi card and the ipl driver is a known issue.  My problem is that I cannot get it working with the iwl driver either.  I have two other computers that use the wireless, and they don't have any problems.

---

### Post by fragos on 2008-06-15
For some reason I haven't experienced the problems you're having. That doesn't mean what I said is wrong. I didn't say I'd identified the problem. I'm curious about what the root of the problem is so that I can avoid exposing myself to it.

---

### Post by sdennie on 2008-06-16
If you are seeing wlan_rename while using iwl it means that you have a stale udev rule for the ipw driver.  Try:

```

gksudo gedit /etc/udev/rules.d/70-persistent-net.rules

```

Comment out the line below where it describes the "ipw" driver by putting a "#" in front of the rule.  You may have to reboot to see this take effect.

---

### Post by mlsquad on 2008-06-16
> **vor said:**
> If you are seeing wlan_rename while using iwl it means that you have a stale udev rule for the ipw driver.  Try:

```

gksudo gedit /etc/udev/rules.d/70-persistent-net.rules

```

Comment out the line below where it describes the "ipw" driver by putting a "#" in front of the rule.  You may have to reboot to see this take effect.

Thanks for the feedback.  I shall make this change when I get home and see how it goes.

---

### Post by mlsquad on 2008-06-18
I made that change and this is what I get now.

```
~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```This is after a reboot of course.  I'm thinking I'm just going to reinstall with Dell's ISO.

---

