---
title: "Dell Latitude D600 Problem"
date: 2011-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goldstoned on 2011-08-05
Hi All

I am a newbie to this and last night was my Ubuntu debut. I am not familiar with the Linux code at all and find it very confusing so full instructions (dummy help) will be great.

I have Ubuntu Gnome on my Dell Latitude D600 laptop, which is a secondary machine to play with. I installed instead of Windows XP. My ethernet cable connection works fine. My WPA wireless though, doesnt work. I downloaded Network Manager from the Software centre which found the network as before I couldnt see it. I entered the security key, but still wouldnt work. My suspicions are that the Intel PRO Wireless 2200 or Intel PRO Wireless 2100 isnt WPA compatible. This didnt work in Windows either after a Service Pack 3 upgrade. Any ideas?

Is there an Ubuntu driver that will make this work, or can I flash the network card to make it WPA compatible?

Any other ideas?  Many Thanks

---

### Post by MARP1961 on 2011-08-05
Good luck and welcome!

First thing to try is connect the ethernet cable and search through the menus until you find the 'Additional Drivers' feature. Click on this and see if it invites you to install any drivers. Then unplug the ethernet cable, right click the Network Manager icon on the top panel and see if it lists any wi-fi signals (hopefully your router). 

If you do find your router listed then right click, enter passwords and WPA security key when prompted. I have also discovered there are often issues to do with the Ubuntu Keyring which can be a pain. Make sure you check the box that allows ALL USERS to use the WiFi.

Possibly more people will see your posts if you post them under 'General Help' rather than 'Dell Ubuntu Help'.

---

### Post by goldstoned on 2011-08-05
> **MARP1961 said:**
> First thing to try is connect the ethernet cable and search through the menus until you find the 'Additional Drivers' feature. Click on this and see if it invites you to install any drivers. Then unplug the ethernet cable, right click the Network Manager icon on the top panel and see if it lists any wi fi signals (hopefully your router).

Hi, i have tried this but to no avail. It found my router when I installed network manager, so i unplugged the ethernet cable, entered my password but timed out when validating encryption. My router is WPA 1/2 compliant. I dont want to switch it back to WEP. I had this trouble with the laptop wireless card when on XP and I switched my router from WEP to WPA. Therefore it would seem my wireless card isnt WPA compatible or needs a relevant driver.

---

### Post by MARP1961 on 2011-08-05
If you have checked ALL USERS option and it is still trying to connect then I think it might be worth disabling the keyring:
[http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu]("http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu")

---

### Post by goldstoned on 2011-08-05
> **MARP1961 said:**
> If you have checked ALL USERS option and it is still trying to connect then I think it might be worth disabling the keyring:
[http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu]("http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu")

Hi, thanks for your response. You have completely lost me now. What is a keyring password? :confused:

---

### Post by MARP1961 on 2011-08-05
I wish I knew what use it was. Unless you changed it, it should be the same as the password you use to login or the one you use when accessing the Software Centre. For reasons I don't understand the 'keyring password' seems to stay locked and can prevent wi-fi connection. I disabled it by following these instructions:  [http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu]("http://www.technoblob.com/archives/2010/11/how-disable-keyring-password-ubuntu") This effectively makes the keyring password completely blank. You will still have a login and authorization password.

If you can get your head around how Ubuntu passwords,keyrings,passkeys work then give yourself a big medal and start to write tutorials on them for these forums!

---

### Post by bayouoldguy on 2011-08-06
There are a bunch of us trying to get the wireless driver to work on the Dell D6XX series laptops running 11.04. Seems to be a Ubuntu 11.04 upgrade problem, I have my D620 running Ubuntu 10.04 LTS using the old "b43" driver. 
Found my wireless connection ok.....read some of this link...."G"

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

I responded on pg .44........

---

### Post by goldstoned on 2011-08-07
Hi
I tried the keying and worked sort of. However, the wireless now constantly disconnects and then reconnects. All very strange. I have also ticked the all users box. I just wonder how to keep the connection. I did a check in terminal on the hardware and its definetly an Intel 2100 card. I tried looking for an Intel firmware upgrade but couldn't install.

Any further advice?

---

### Post by MARP1961 on 2011-08-07
I had quite a few problems with my son's Dell Inspiron 6400 wireless. It worked fine with 10.04 Lucid Lynx and only gave problems with 11.04 Natty Narwhal. In Lynx, the 'Additional Drivers' invited me to install Broadcom STA or the B43 driver. The STA one never worked but the B43 did. 

When we upgraded to Natty, I noticed that Additional Drivers only offered Broadcom STA and I let it install. It would not even detect wifi signals!

In the end, I tried to install the B43 firmware (fw B43 cutter installer) from Synaptic Package Manager; but Additional Drivers did not seem to update and list it. I eventually guessed that perhaps an earlier install of the STA driver was blocking or blacklisting B43, so I completely reinstalled Natty. I then ignored Additional Drivers, indeed I actually removed it via Software Centre! I then reinstalled fw B43 cutter installer from Synaptic Package Manager, rebooted, left clicked the Network Manager and found to my delight my Thompson router waiting to be authorized. I have had no problem since.

Now I have no idea whether this will work for you; but it is worth a shot if it's only a second computer. If you get no luck with this and make no progress with your own efforts then try a fresh install of the Long Term Support (LTS) 10.04 Lucid Lynx. This is much more likely to work 'out of the box'.

---

### Post by MARP1961 on 2011-08-07
I'm sorry. I have not been concentrating. Your issue sounded so similar to mine I made the blinkered mistake of assuming you also have a Broadcom wifi!

However, in your post you state that it is definitely an Intel 2100 so my advice will probably be useless! Nevertheless you do seem to be getting closer to getting it all to work. If you post it under the 'General Help' category rather than 'Dell Ubuntu Support' it might be read by more people. Good luck!

---

### Post by bayouoldguy on 2011-08-08
Look what I found !....

[https://launchpad.net/ubuntu/maverick/i386/firmware-b43-installer/4.150.10.5-4](https://launchpad.net/ubuntu/maverick/i386/firmware-b43-installer/4.150.10.5-4)    & listed file:  

firmware-b43-installer_4.150.10.5-4_all.deb (5.1 KiB)

I downloaded the file to the "Downloads" folder, & commanded to "extract". 
It installed.....found my Wireless  & is up & running from the USB stick !!:D.
I installed the b43-fwcutter package from the Synaptic Package manager first. The wireless apt always showed me "no firmware", & the "apt-get install firmware-b43-installer" command would not execute.

Now I guess I can upgrade to the 11.04 version !......"G"

All you guys having Dell D6XX series laptops with the Broadcom BCM4311
802.11 b/g Wlan wireless card may want to try this......

---

### Post by Jaxilian on 2011-08-09
Goldstoned > Try this [http://ubuntuforums.org/showthread.php?t=1621331](http://ubuntuforums.org/showthread.php?t=1621331)

It helped me with my D600 to get wireless working

---

### Post by MARP1961 on 2011-08-09
'Goldstoned' has an Intel Pro Wireless 2100; not Broadcom as I belatedly noticed. Anyone got one of these to work with Natty Narwhal?

---

