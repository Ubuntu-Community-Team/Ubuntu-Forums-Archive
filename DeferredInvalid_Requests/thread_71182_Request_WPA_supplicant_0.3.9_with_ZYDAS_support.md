---
title: "Request: WPA supplicant 0.3.9 with ZYDAS support"
date: 2005-10-02
forum: Deferred/Invalid Requests
---

### Post by shof2k on 2005-10-02
Hello,
Any chance of getting wpa supplicant 0.3.9 compiled with ZYDAS zd1211 chipset support.  Hoary's version won't support this chipset so i'm stuck with wpa on windows :(.
Thanks!

---

### Post by dom on 2005-10-31
i second this. 

i have the 3CRUSB10075

managed to get it working with WEP only. 

downloaded drivers from [http://zd1211.ath.cx/zd1211](http://zd1211.ath.cx/zd1211)  - latest version at [http://zd1211.ath.cx/download](http://zd1211.ath.cx/download). This was more recent than the sourceforge drivers i had tried beforehand.

I had also to install the linux headers, and gcc also. Then make, make install worked. When I plugged it in it all was 'found' by the system.
{DID NOT WORK ON RE_BOOT WITHOUT MANUAL RE-SETUP VIA iwconfig.}

I done he build on Hoary. I have upgraded to breezy badger. I am going to try the WPA supplicant with Breezy to see if the zydas driver is usable, otherwise I'll have to get and try to build manually the wpa_supplicant made available on the zydas website (i think you -have- to use IE to get any use from that site, though the wpa supplicant download is linked from the zd1211.ath.cx site)


With the wep, when I reboot, i have to manually excute iwconfig to get it going again. I tried to set it up with the network administration GUI in gnome, but it doesn't set it up properly that it will work after a reboot.

Well, off to try the WPA supplicant, I had to re-enable WPA as I have some 'curious' neighbours and WEP doens't keep them at bay for long :)

---

### Post by dom on 2005-10-31
ok,

got the wpa working. :)

the supplied (breezy) wpa_supplicant doesn't work, no support for zydas driver.

so i got it from the zydas site (source)

make failed, i had to get openssl. So i got the sources for that and put a link to openssl/include in the zydas wpa source folder:
"ln -s /testing/openssl/include /testing/zydas_wpasupp/openssl"

then make worked until the link. Failed to find ssl (ld error with "-lssl").
So i made openssl and done make install. Didn't fix the issue. I know it was probably just me being tired and not spotting the link issue (yes i set LD_LIBRARY_PATH to point to the lib dir for the openssl lib but i'm sure there's something else to do).

I done an install of libssl ("apt-get install libssl", iirc, actually, i used the synaptic package installer thingy) 

Then the make worked :)

Then I set up /etc/wpa_supplicant.conf for my network (WPA-PSK TKIP)

Then it worked. Well actually it failed first, as i was picking up the standard wpa_supplicant, but when i made it use the one i just built with ./ then it worked :)

I've since un-installed the standard wpa_supplicant.

Now off to try to do something with teh boot-up sequence to get it to set up the nic then, automagically. 

That still does not work.

So for now I have a script :
------------------------8<------------------------
#
#	bring up the wireless nic
#
ifconfig wlan0 down
ifconfig wlan0 up

#
#	connect to the node using wpa
#
./wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D zydas

#
#	get us an ip address
#
dhclient wlan0 

------------------------>8------------------------

and my conf is :

# dom's conf
ctrl_interface=/var/run/wpa_supplicant
# if you want to use wpa_supplicant here you have to be in the 'wireless' group
ctrl_interface_group=wireless

eapol_version=1
ap_scan=1

#
# dom home network; wpa-psk(tkip)
#
network={
        ssid="DomsSsid"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
#my paraphrase, really ;)
#        psk="Would Be Nice To Have Zydas Driver In Wpa Supplicant and Device Usable After Boot"
#below psk generated using "wpa_paraphrase <mySsid> <myParaphrase>"
	psk=0102030405060708090a0b0c0d0e0ffefdfcfbfaefeeedebeceadfdedddcdbda
}


have fun


dom

---

### Post by shof2k on 2005-11-01
Dom,
Thanks for the pointers.  I've compiled wpa_supplicant and the zd1211 driver,  but running wpa_supplicant gives me the following:

ioctl[ZD_IOCTL_PARAM]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
Failed to enable WPA in the driver.
ioctl[ZD_IOCTL_WPA]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
Failed to disable WPA in the driver.
ioctl[ZD_IOCTL_PARAM]: Invalid argument
ioctl[ZD_IOCTL_PARAM]: Invalid argument
 
Any ideas on what I am missing here?

MODS:  Since this isn't a backports issue, would you be kind enough to move this to breezy/network issues?

---

### Post by dom on 2005-11-02
well, 

i won't lie to ya i haven't the foggiest :(

it seems he doesn't like parameter,

i'd start with checking the command line parms to wpa_supplicant (make sure you are using the one you just built and not the one from apt)

then check the config file

wpa_supplicant documentation for both of these.

Also, make sure the device is activated and using the zydas driver(dmesg or cat /var/log/messages should show you this), make sure to specify the zydas driver to the wpa supplicant

sorry for posting in the wrong forum guys, was just replying to the origninal post and it seemed like a good place to keep the related info all together.

i'll check the forum i'm in next time :)

---

### Post by shof2k on 2005-11-05
At last....finally got it working.  I'll write up my experinces into a HOW-TO over the next couple of days.  Thanks for your help Dom.

[EDIT]
How do done.....[http://www.ubuntuforums.org/showthread.php?t=92327](http://www.ubuntuforums.org/showthread.php?t=92327)
[/EDIT]

---

### Post by jdong on 2005-11-09
Sorry looks a bit too risky for backporting.

---

### Post by dom on 2006-03-09
some people had some fun trying to compile the modified wpasupplicant with the zd1211 modifications, so i'm attaching it.

dom

---

### Post by tutu on 2006-04-15
[QUOTE=shof2k]At last....finally got it working.  I'll write up my experinces into a HOW-TO over the next couple of days.  Thanks for your help Dom.

[EDIT]
How do done.....[http://www.ubuntuforums.org/showthread.php?t=92327](http://www.ubuntuforums.org/showthread.php?t=92327)
[/EDIT][/QUOTE]

I do have the same problem you had, but I cannot find the description of your solution. Can you or anyone else help me?

Here is my debug output:

tost2:/opt/wpa_supplicant/wpa_supplicant-0.4.7 # ./wpa_supplicant -wK -dd -Dzd12
11 -iwlan0 -c/etc/wpa_supplicant.conf
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'zd1211' c
trl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=16):
     41 72 63 6f 72 57 69 72 65 6c 65 73 73 4c 41 4e   ArcorWirelessLAN
key_mgmt: 0x2
proto: 0x1
pairwise: 0x18
group: 0x1e
PSK - hexdump(len=32): 0f 7d b5 ea e1 88 86 a3 49 ec 37 42 e2 b1 8b 72 88 fe 49
0c 7c d9 2d 4e 5b 1c fb 63 49 25 bc 68
Priority group 0
   id=0 ssid='ArcorWirelessLAN'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:13:49:37:56:43
wpa_driver_zd1211_set_wpa: enabled=1
ioctl[ZD_IOCTL_PARAM]: Operation not supported
ioctl[ZD_IOCTL_PARAM]: Operation not supported
ioctl[ZD_IOCTL_PARAM]: Operation not supported
Driver does not support WPA.
wpa_driver_zd1211_set_key: alg=NONE key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[ZD_IOCTL_WPA]: Operation not supported
Failed to set encryption.
wpa_driver_zd1211_set_key: alg=NONE key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[ZD_IOCTL_WPA]: Operation not supported
Failed to set encryption.
wpa_driver_zd1211_set_key: alg=NONE key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[ZD_IOCTL_WPA]: Operation not supported
Failed to set encryption.
wpa_driver_zd1211_set_key: alg=NONE key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[ZD_IOCTL_WPA]: Operation not supported
Failed to set encryption.
wpa_driver_zd1211_set_countermeasures: enabled=0
ioctl[ZD_IOCTL_PARAM]: Operation not supported
wpa_driver_zd1211_set_drop_unencrypted: enabled=1
ioctl[ZD_IOCTL_PARAM]: Operation not supported
Setting scan request: 0 sec 100000 usec
Added interface wlan0
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b19 len=24
Received 392 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:49:79:ed:7d ssid='ArcorWirelessLAN' wpa_ie_len=24 rsn_ie_len=0 caps=0x1
1
   selected based on WPA IE
Trying to associate with 00:13:49:79:ed:7d (SSID='ArcorWirelessLAN' freq=2437 MH
z)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
ioctl[ZD_IOCTL_PARAM]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00
00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2
02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_zd1211_set_drop_unencrypted: enabled=1
ioctl[ZD_IOCTL_PARAM]: Operation not supported
State: SCANNING -> ASSOCIATING
wpa_driver_zd1211_associate
ioctl[ZD_IOCTL_WPA]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)

---

### Post by dom on 2006-07-17
> **tutu said:**
> I do have the same problem you had, but I cannot find the description of your solution. Can you or anyone else help me?

Here is my debug output:
*<snip>*


That looks familiar, try using an older version of the zydas driver, like .38 for e.g. which worked for me, whereas 83 didn't. I think I read that they re-wrote the driver, and so the patched wpa-supplicant may not yet have caught up ?

Also, check out [http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259)

---

