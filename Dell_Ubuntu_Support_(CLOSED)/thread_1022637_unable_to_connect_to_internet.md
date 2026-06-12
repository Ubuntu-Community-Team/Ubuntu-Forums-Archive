---
title: "unable to connect to internet"
date: 2008-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrsozzy on 2008-12-27
:)[SIZE="3"][/SIZE] help!! I just got the DELL mini 9 for Xmas and unsure as to how to get it online. I have a Linksys router but it still doesn't help. Do I need something else? What does everyone else use?? THANKS!!

---

### Post by suxenexus on 2008-12-27
Have you tried installing using ndiswrapper?

OR you could check the hardware menu and check if your wifi is detected

---

### Post by Bucky Ball on 2008-12-27
Go to:

System->Administration->Network->Unlock

Click on your wireless connection then properties. Fill in the appropriate details, ESSID (your network name or access point - router), security type and the security key/password. Uncheck 'Enable Roaming' and set to 'Automatic DHCP Configuration'.

See how that goes. Of course, this is all for nothing if your wireless card is not actually up yet. Is the blue light on (or whatever light indicates wireless activity/on/off)? If not, solve that issue first.

If your card is not up, then perhaps open a terminal and paste this command:
```

lspci
```In there somewhere you will find the make and model of your wireless card (probably near the bottom of the list). Post or let us know what it is (can't find any details on it). *Don't* begin installing ndiswrapper etc until you have that information. It may well not be required (and in fact may be documented as not suitable for your card). I would save that as a last resort, if it is the case that it will work with your card. Also try:

System->Hardware Drivers

Are there any restricted drivers for wireless that aren't switched on?

---

### Post by armandh on 2008-12-27
when you say router we all have assumed it is a wireless router.
we also assume that you have other wireless computers running ok.
[if not you may need to set up the wireless router]

also you may need to plug in a wired connection for updates.

if you eventually decide to go to 8.10 the wireless workes even running live from a usb mem stick.[pen drive]

we also assume that the wireless router is blocked from channels 11,12 as is all new equipment [such as the mini9] I read this elsewhere in this forum. the fcc is re using these two channels eventually.

---

### Post by mrsozzy on 2008-12-27
> **armandh said:**
> when you say router we all have assumed it is a wireless router.
we also assume that you have other wireless computers running ok.
[if not you may need to set up the wireless router]

also you may need to plug in a wired connection for updates.

if you eventually decide to go to 8.10 the wireless workes even running live from a usb mem stick.[pen drive]

we also assume that the wireless router is blocked from channels 11,12 as is all new equipment [such as the mini9] I read this elsewhere in this forum. the fcc is re using these two channels eventually.
thanks for your reply! Yes, it is a wireless router which I just bought yesterday specifically for the mini 9 I just received. My desktop runs on a cable modem. I tried for 4 hrs to get it to connect but to no avail. I contacted Linksys support and was informed that their routers will not work on Ubuntu (only on windows) yet Dell.com assured me it would. Where is that towel to throw in??

---

### Post by mrsozzy on 2008-12-27
> **armandh said:**
> when you say router we all have assumed it is a wireless router.
we also assume that you have other wireless computers running ok.
[if not you may need to set up the wireless router]

also you may need to plug in a wired connection for updates.

if you eventually decide to go to 8.10 the wireless workes even running live from a usb mem stick.[pen drive]

we also assume that the wireless router is blocked from channels 11,12 as is all new equipment [such as the mini9] I read this elsewhere in this forum. the fcc is re using these two channels eventually.

thanks for your reply! Yes, it is a wireless router which I just bought yesterday specifically for the mini 9 I just received. My desktop runs on a cable modem. I tried for 4 hrs to get it to connect but to no avail. I contacted Linksys support and was informed that their routers will not work on Ubuntu (only on windows) yet Dell.com assured me it would. Where is that towel to throw in??:(

---

### Post by armandh on 2008-12-27
most usa mc donalds have wirless. 
a test drive is in order to see if it works there or some where with known working wireless. 
back at home.
the router setup needs to be done [pass word etc]

I use a wireless hub [netgear] and a wired router [linksys] 

the won't work with linux is a blowoff.

---

### Post by Bucky Ball on 2008-12-27
> **armandh said:**
> 

I use a wireless hub [netgear] and a wired router [linksys] 

the won't work with linux is a blowoff.

Absolutely! That is almost cause for legal action as they are denying you support which you have probably paid for by giving you misinformation due to their lack of knowledge about their own products!  :( And you could argue for discrimination against an Operating System ! :)

+1 for setting up the router. You can usually open a web browser and type in the IP address of your router to configure. IP should be in the manual but usually something starting with 192.168.x.x

192.168.0.1

is common.

---

### Post by sirebral on 2008-12-28
[http://ubuntuforums.org/showthread.php?t=999794](http://ubuntuforums.org/showthread.php?t=999794)

Read this, it might help.

Linksys provides Linux drivers.  I have a Linksys wireless adapter and I think I found the driver on their site.

EDIT:

Sorry, my bad.  Linksys did not provide the driver, but they use a driver that is available from the programmers for linux.  Here is the link that explains which driver is being used by my wireless adapter and where to get the linux drivers.
[http://forums.driverguide.com/showthread.php?t=23488](http://forums.driverguide.com/showthread.php?t=23488)

Best Advice before resorting to a wrapper: ** Find which driver you card uses and who produces it.  You MIGHT be able to download it from the driver coder in a linux format.**

---

