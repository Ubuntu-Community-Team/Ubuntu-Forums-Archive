---
title: "Swapping a drive from an Inspiron 1525 into a 1545"
date: 2010-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rthorpe on 2010-08-21
About a year ago I bought a Dell Inspiron 1525 with Ubuntu Hardy Heron preinstalled.  It worked great.

I broke that computer recently by accident. I replaced it by buying an Inspiron 15 (aka Inspiron 1545) with Windows 7. I live in Ireland and Dell no longer sell Linux machines there.

Both of these machines have removable hard drives. So, when I got the 1545 I took out the HDD from the 1525 and put it in the 1545. To my surprise this worked, it gave a few errors but fairly much booted correctly. Everything works except the WiFi card.

Should I continue using the HDD from the 1525? I don't think that HDD is physically damaged, but the software on it is configured for a different machine. I could fix this by installing the right drivers.

Or, should I reinstall Linux?

Is it easy to fix the WiFi and other incompatabilities between the two machines? Or should I not bother trying? I have quite a bit of experience of Linux in general.

Thanks for your help

---

### Post by chaorace on 2010-08-22
being a rookie ubuntu/1525 user myself I suggest that:
1) connect via ethernet cable (should work) then do a check for updates, if you are lucky that may then tell your system about some restricted driver that are available and then activate those.

2) IF 1 doesn't work, it always helps to run computer janitor.

3) If 1 doesn't work, do #2 first then, connect via ethernet cable, then (WARNING THIS NEXT PART IS AN EXCCERT FROM UBUNTU DOCUMENTATION, USE AT YOUR OWN RISK, I DIDN'T EVEN BOTHER TO READ IT ALL, I JUST SKIMMED)
*First thing you'll need to do is get the [wireless-tools]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html") package (see [SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")). [I]Since  this document is about how to get (wireless) networking working, we  need an explaination here on how to install packages without a network  connection!*[/I] 
*sudo apt-get install wireless-tools**You  will then have to find what chipset your card is (this is the chips the  manufacturer uses, the make/model is of limited use as some  manufactures use the same chipset and they also change the chipset  without changing the model number).  To do this in a shell type: *
*lspci | grep Network**One  of the lines will tell you what chipset you have. It will be listed as a  Network Controller. If it says something like unknown device, then  Google for it. *
*Some  Wi-Fi Cards work out of the box, specifically the ones with the  Orinoko, Prism2 or Atheros chipsets (some Prism cards may not work out  of the box).   *

[LIST]
[*]*For cards based on **Ralink's RT2500** chipset, see [WifiDocs/Driver/RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500").   *
[*]*For cards based on **Rakink's RT61** chipset see [[Rt61WirelessCardsHowTo]("https://help.ubuntu.com/community/Rt61WirelessCardsHowTo")], these show up as 'Network controller: Ralink Unknown device 0301' if you do lspci. *
[*]*If you have a **Centrino based laptop**, it likely has an Intel ipw2200 based card.  It works out of the box but uses an ancient driver.  See [Luca_Linux's post]("http://ubuntuforums.org/showthread.php?t=26623")  for a really good guide on getting the ipw2200 card setup (you may want  to stop before he takes you into the WPA portion of the setup).  [I]Some  users have experienced problems with their wireless connections after  upgrading to Hoary from Warty with the Intel ipw2200 (prior to upgrade  in Warty everything worked fine).  The following message on the mailing  list is relevant: [http://lists.ubuntu.com/archives/ubuntu-users/2005-April/029837.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-April/029837.html)   One user reported having to remove the module and re-insert the driver  once or twice before it can associate with the access point (on kernel  linux-image-2.6.10-5-686).*[/I]
[*]*For cards that do not work out of the box you can try [WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). *
[/LIST]
*To  begin with you'll need to set your Wireless Router up as an 'open'  network.  This means you'll need to turn off all security such as WAP,  WEP and Mac Address restrictions.  You'll be able to turn these back on  later, we just want to make sure that they aren't causing any problems  in the beginning.   *
*You'll  also need to give your network an ESSID.  Most wireless routers have  one set by default.  Often it is "default", "linksys" "netgear" or some  other generic name. *
 
***iwconfig Before You Start***

 *(optional, but not a bad idea) Ubuntu ships with a fantastic GUI network tool called [network-admin]("https://help.ubuntu.com/community/network-admin").   It can be run from a terminal but it is also readily available under  the system menu. (System)->(Administration)->(Networking).  You  can jump right in and start poking around with network-admin, but its  best to run iwconfig from a terminal first. Since linux names your wifi  card based on the driver it uses (can somebody back that up?) we first  need to figure out what your card is called.  Bring up a terminal  (Applications)->(System Tools)->(Terminal) and issue the following  command: *
*iwconfig**Your output should look like: *
[I]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]*If  all devices listed say "no wireless extensions." then your wireless  card is not configured.  You need to go back and get it setup.  Please  see the top of this document and also [WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for more information. Alternativly, the device may be disabled - you could try *
*sudo ifconfig wlan0 up*
*you may also try to wake-up the interface using the keyboard command (Dell)**Then try iwconfig again to see if the device is now recognised. *
*Based on the iwconfig output from above, we know that "wlan0" is our [WiFi]("https://help.ubuntu.com/community/WiFi")  card's linux device name.  Knowing this you'll be able to use the  Networking GUI tool to connect to your wireless router. (You may also  see ath0 or even eth1 come up as your device name.  Don't worry, that's  totally fine, it just depends on the type of card you have and the  drivers that are accessing it.) *
*Sometimes  there are two devices that appear: wlan0 and wifi0, even if there is  one card. This causes errors sometimes, like a tendency to not detect  wireless access points. In certain configurations, this is caused by  hostap_cs and hostap kernel modules. Check your dmesg output for errors around "wlan0". Place the appropriate excludes into /etc/modprobe.d/blacklist and reboot. An example workaround the wlan0 for the "orinoco" wifi driver: *
[I]ubuntu-7.10# gksu echo "blacklist hostap" >> /etc/modprobe.d/blacklist-orinoco
ubuntu-7.10# gksu echo "blacklist hostap_ap" >> /etc/modprobe.d/blacklist-orinoco[/I]*Click  on (System)->(Administration)->(Networking) and see if your  wireless network card is listed.  If it isn't you've got a problem.   (Somebody needs to describe what to do next) <!--  Is it possible for wireless interface to be in kernel and not be  recognized by the GUI tool? If the tool is reliable we can reference  user to troubleshooting a driver. --> ***AND REMEMBER YOU INEX****PERIENCED USERS: CONSULT A PROPER LOCAL UBUNTU EXPERT ( CAN BE FOUND AT LOCAL FARMERS MARKETS AND BASEMENTS**) **AND YOUR LOCAL DOCTOR** **DUE TO RISK OF HEART ATTACK FROM COMPLICATIONS OF IDIOTISM ( A SEVERE MENTAL IMPAIRMENT DUE TO LACK OF KNOWLEDGE OF UBUNTU)** 
4) check your bios just to be sure!

_*NO OFFENCE INTENDED TO INEXPERIENCED UBUNTU USERS, JUST TRYING TO KNOCK THE THOUGHT THAT I HAVE ANY RESPONSIBILITY FOR YOUR ACTIONS OUT OF YOUR REALM OF EXISTANCE*_

---

### Post by rthorpe on 2010-08-22
Thanks for the extensive reply.

I can install the proprietary driver for the Broadcom WLAN card, the Broadcom STA driver. That's not a big problem.

But, will I find other problems in the future? Is swapping around drives a generally robust thing to do?

---

### Post by ExK444 on 2010-08-22
Generally you won't cause much harm, though it will ultimately cause Windows to explode. Ubuntu (and just about any other Linux distro for that matter) should be fine. I'd just recommend removing the old drivers to avoid creating conflicts later on.

---

### Post by rthorpe on 2010-08-23
That's what I needed to know, thanks for the help.

---

