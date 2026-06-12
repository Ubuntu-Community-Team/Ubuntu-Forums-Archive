---
title: "can't get connected when i enable WEP"
date: 2006-01-08
forum: Desktop Environments
---

### Post by MikieEars on 2006-01-08
So I have a wireless connection and i used ndiswrapper and got it all configured. But I obviously don't want an open AP. So I enabled WEP but when I got to my wireless utility options, I put in the key, and i know its in HEX. But I can't get connected to the internet. I'm not sure what other information you would need to help me with this. But any help would be much appriciated.

P.S. I have only been using Ubuntu with Gnome for 2 days now. I absolutly love it. But  just letting everyone know I'm a beginner with this OS

---

### Post by az on 2006-01-08
[QUOTE=MikieEars] i know its in HEX. [/QUOTE]

In the networking tool, by default, the WEP key is input in ascii.  You have to select Hex.  Did you do that?

---

### Post by MikieEars on 2006-01-08
yes i did. I select all the right options, and put in the correct wep key. This just does not make sense

---

### Post by harisund on 2006-01-08
if you have configured your wireless router correctly (as in correct essid, the wep and dhcp) try doing this in the command line 

iwconfig wlan0 mode Managed essid <name of your network> key restricted <enter your wep key here> 
dhclient wlan0 

I am assuming wlan0 is your wireless device, and you need to enter sudo appropriately. 

If you need further help, post the output of ifconfig and iwconfig here

---

### Post by Dr. Nick on 2006-01-08
Not sure if what suggested above will work, never done it. If it doesnt work post the ouptuts mentioned above aswell as the cotents of the interfaces file, That can be obtained by running
**sudo cat /etc/network/interfaces **from a terminal, This file contains your WEP key aswell as other wireless and wired network information and can be very helpful for troubleshooting network problems.

Just to confirm you can connect if you disable wep in your router and dont enter a wep into the network dialog?

---

### Post by xxsiriusxburnxx on 2006-01-11
Maybe you should stop using linux all together god... lol, ya i cant figure it out either, as for the "key restricted" I dont think that will work there is no fuction like that however typing iwconfig --help , shows a command ENC (nnnn-nnnn) , imaging that is the wep key restricted type command, however Mikieears and I have tried that as well with and w/o a - after every 4 characters, and have also tried using dhclient wlan0 with no success, oddly and if someone could PLEASE shed some light on this, it tries to send a dhcp request to an ip of 255.255.255.0, which obviously makes no sense and as well doesnt result in connection, any help appreciated, Thanks Greg

oh and yes for Dr. Nick, we can connect when the wep key is disabled...

---

### Post by Dr. Nick on 2006-01-11
if you can connect without wep then post you /etc/interfaces file like i mentioned abouve. You can just type the hex directly into that file. I am not at home now though so i cant check the exact syntax. I think it is wireless_key xx:xx:xx... though

---

### Post by EnderTheThird on 2006-01-11
Knowing which wireless adapter you have might help as well.  I know I've been able to get wireless with WEP working on a D-Link DWL-520 (with ndiswrapper) and DWL-G520 (without ndiswrapper)  at home and at work, even though I think I remember the Wiki saying WEP didn't work with at least one of those.

---

### Post by erioll on 2007-12-29
hello
i'm having the same probelm, i tried *iwconfig wlan0 mode Managed essid <name of your network> key restricted <enter your wep key here>* and seem to work without any problems but when i tried to *dhclient wlan0* the output said: "No DHCPOFFERS recived" :? how can i fix this?
thanks for ur help

---

