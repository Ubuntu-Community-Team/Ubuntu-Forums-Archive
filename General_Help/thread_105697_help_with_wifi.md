---
title: "help with wifi"
date: 2005-12-19
forum: General Help
---

### Post by tunads on 2005-12-19
hello ubuntu fourm (this is my first post)!

im having problem with my wifi network and was wondering if anyone could help.

i have no internet access and the only way i can post is off a windows based computer.

im a brand new to this and have no idea how to move around in ubuntu yet so please use dumbed down language.

the network setting window says that the wireless card is active but i still have no internet access.  how do I resolve this?

thanks in advance for any help

---

### Post by BathroomNinja on 2005-12-19
OK, first off, what do you know about your wireless connection?  Do you have a wireless router at your home?  Are you using this at a coffee shop, or another free wireless 'hot spot'?  

The reason I ask is to attempt to find out the right settings for you.  Right now, under your network settings, what do you see?

---

### Post by tunads on 2005-12-19
thanks for responding!!

yea its through a router at home

i use wep security and have it set to 64 bit encryption.

the router settings say that it gets all the info dynamicly from the isp

any thing else and i'll try and find it for you. (remember im working in windows)

thanks again for responding!!!!!!!!!!

---

### Post by BathroomNinja on 2005-12-19
OK, do you have your wep key entered in under the settings for your wireless adapter in the network settings?  That sounds a bit odd.  Under your network settings, then looking at the settings for your sifi card, do you have your WEP key entered into the appropriate box?

EDIT- crud.  Your in windows.  OK, go to your network settings in Windows.  Find your wifi adapter.  Right click, go to properties.  you need to find your WEP key.  write this down, it's pretty long.  Go back into Ubuntu, go to network settings, then to the settings of your wifi card, and adjust it for WEP (not WAP) and enter in the key.  

you may also need to temporarily turn off WEP encryption to make sure the card is working.  you should be able to go to:
[http://192.168.1.1](http://192.168.1.1) or [http://192.168.2.1](http://192.168.2.1) to log into your router and adjust it's security settings.  If you can't find your WEP key, temporarily turn off wireless security, then login with ubuntu, just to see if the wifi works.  Then, you can always setup a new key.  Your router should show you what key it is using.  After you get that key and enter it into the network settings in Ubuntu, everything should work fine.  I have this same setup on my laptop and 1 wireless desktop.

---

### Post by tunads on 2005-12-19
so i have to use hex?

edit- thaaaaaaaaaaaank yoooooooooou!!!!!!!!!!!!!!!!!!!!!!!!!!!!

works like a charm

now all i have to do is learn how to use linux (lol)

---

### Post by BathroomNinja on 2005-12-19
No problem.  glad your using security and not letting your router hang out in the breeze open and free to the world.  Security = good.

---

