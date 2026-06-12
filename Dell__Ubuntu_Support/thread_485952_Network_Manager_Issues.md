---
title: "Network Manager Issues"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by slackorama on 2007-06-27
Hi --

I'm trying to connect to a wireless network with my new 1505N  at work but network manager is silently failing.  I had it working yesterday but when I went home and tried to connect to my home wifi, it wouldn't work unless I deleted the work key from the default keyring.

Now I'm back at work trying to connect and nothings going.  I'd rather not delete my home network key to get it to work.

Any and all help in getting network manager to work would be appreciated.

---

### Post by apel_2804 on 2007-06-27
maybe same ssid's at home and at work?

---

### Post by fjgaude on 2007-06-27
> **slackorama said:**
> Hi --

I'm trying to connect to a wireless network with my new 1505N  at work but network manager is silently failing.  I had it working yesterday but when I went home and tried to connect to my home wifi, it wouldn't work unless I deleted the work key from the default keyring.

Now I'm back at work trying to connect and nothings going.  I'd rather not delete my home network key to get it to work.

Any and all help in getting network manager to work would be appreciated.

In order to use two different keys you will have to store location profiles, not a simple task. Such is way over my head. Maybe others here can help.

Seems the best you can simply do is have the same SSID and keys for home and work. Or perhaps use no keys at home... depends on your neighborhood and how safe you feel.

frank

---

### Post by slackorama on 2007-06-27
The SSID and kesy for the two networks is different.

I'm new to Linux so forgive what may be an ignorant question but isn't Networkmanager able to handle connecting to two different networks?  I do see two keys now in the default keyring but it's still not connecting to the network.

Thanks for the quick replies.

---

### Post by walkerk on 2007-06-27
delete network-manager and give [wicd]("http://wicd.sourceforge.net")

---

### Post by fjgaude on 2007-06-27
> **slackorama said:**
> The SSID and kesy for the two networks is different.

I'm new to Linux so forgive what may be an ignorant question but isn't Networkmanager able to handle connecting to two different networks?  I do see two keys now in the default keyring but it's still not connecting to the network.

Thanks for the quick replies.

Sure I know it can connect to many different networks, but I've only done it roaming, from WiFi spot to another in different cities, all out in the clear.

If you have two keys showing you should be able to do it. Make sure to select the correct SSID as you go from one location to another. You have to go into the  System/Administration/Network menu to make sure you are where you wish to be. Good hunting.

frank

---

### Post by slackorama on 2007-06-27
Weird.  
The key is set in my keyring with a valid value in it.  
The work DNS shows up in my DNS network settings panel.  
Yet it's not connecting.

---

