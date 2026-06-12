---
title: "Xubuntu 7.10 WPA not working (I searched)"
date: 2008-01-09
forum: Desktop Environments
---

### Post by ilovebsod on 2008-01-09
I found several posts regarding these 2 problems, but they were all for previous versions of Ubuntu and none of the solutions worked for me (also many steps were different or not available because of version differences).

the most important is that WPA will not work.  If I try to connect to a WiFi network detected using the Roaming method I don't even get an option for WPA (just WEP64/128).  If I manually try to connect I am able to select WPA/TKP and it attempts to connect but eventually fails.  If I go into the manual network settings and turn off Roaming and enter in the SSID/passphrase/DHCP the same occurs.

wpasupplicant is already installed, not sure what else I'm missing.

Thanks in advance!

---

### Post by gilf on 2008-01-09
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by ilovebsod on 2008-01-09
hmmm...I can't boot from the CD, I have no CD drive lol.  I had to install Xub via PXE

---

### Post by gilf on 2008-01-10
Okay, but try the connection method described in the post.

Does xubuntu use network manager?

if so you won't get a WPA dialog unless you click on the network essid line of a WPA network detected.

You can't enter WPA passwords in a setting in NM. It asks for them when needed.

---

### Post by ilovebsod on 2008-01-10
when I try the connection method in your post (i.e. selecting the essid from the drop down after clicking on Network-Manager) I get prompted to enter the security info for my wifi network.  the only encryption options I'm allowed to select from are
WEP64/128 (passphrase, hex or ASCII)
LEAP

no WPA

I turned WEP128 on on my router and was able to connect, also turned off encryption and could connect

if I go back to the network-manager drop down where it lists the wifi networks I can select 'Connect to other wireless network....', If I select this I can manually input an essid and select WPA as the encryption type and input my passphrase, but it won't connect to the network.

I also tried replacing the contents of /etc/network/interfaces with those listed in your thread, but that rendered the wireless features in network-manager inoperative (i.e. they didn't even show up any more).

I thought maybe I had screwd something up with all the fixes I had tried so I reinstalled Xubuntu today and the same behavior occurs.

---

### Post by gilf on 2008-01-11
Sorry not as familiar with xubuntu -- and I'm surprised that you can't get the WPA dialog from clicking on the icon on top right.

It must be a difference in that distro, because it works in Ubuntu, Kubuntu 7.04, and 7.10 -- I have all of those.

However If you can input WPA, through the method you mention here:

> f I go back to the network-manager drop down where it lists the wifi networks I can select 'Connect to other wireless network....', If I select this I can manually input an essid and select WPA as the encryption type and input my passphrase, but it won't connect to the network.

I know you're sure of this, but can you just check one more time that your WPA password is the same on router and computer?

Try maybe a one letter password? (be sure both are **wpa-psk**, by the way)

Other than that I have no ideas --  other than the obvious -- WPA is not working with your distro, in your install method,  using your card. Maybe someone else using Xubuntu can help.

It definitely is NOT acting like Ubuntu or Kubuntu in this case. Under both K, and U, If your card lists Essids after clicking on the NM Icon, you WILL be asked for a WPA password, if attempting to connect to a WPA enabled router.

---

