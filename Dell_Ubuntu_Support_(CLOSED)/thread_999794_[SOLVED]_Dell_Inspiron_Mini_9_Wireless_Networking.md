---
title: "[SOLVED] Dell Inspiron Mini 9 Wireless Networking"
date: 2008-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spelkZERO on 2008-12-02
I'm having a lot of trouble getting the wireless networking to connect to the Internet (I am a total Ubuntu novice, so please bear with me)

My connection does not show up on the wireless connection list, using the network manager icon, when I choose to connect to a different wireless network and enter the SSID and WPA password, it say it connects 100%, the 5 signal bars go blue, but theres no Internet connectivity as far as I can see it.

I opened a Terminal window and used the ifconfig command

it reports the following devices

eth0
eth1
lo


eth0 and eth1 have two different MAC Addresses, but putting both in my routers access table, doesn't make much difference.. 

If I try to set up the connection manually (eth1 seems to be the one connected to the manual wireless connection setup), connection settings to Automatic DHCP, I still get no joy with the Internet.

From the ifconfig report eth1 seems to have an ever increasing number of TX packet errors

iwconfig gives me

lo : no wireless extensions
eth0: no wireless extensions
eth1: IEEE 802.11 Nickname "", Access Point: Not-Associated

ip addr gives me

lo <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue
eth0 <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
eth1 <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000

and on odd occasions I seem to get

eth1:avahi showing up, but I have no idea what this is.

Can anyone point me in the right direction when it comes to troubleshooting setting up a wireless connection on an Inspiron Mini 9, I have no idea what version of Ubuntu is on it, but some of the tools don't seem to work properly..

The nm-editor version 0.6.6 won't let me set up Wireless connections, I can type in the connection name, but it won't let me edit the BBSID field or any other field.

The Manual Connection Manager, doesn't seem to have an option to enable or disable roaming - which some forum posts have said to try..

Anyway, any help anyone can give would be most appreciated.

P.S. I'm not sure whether its Gnome or not.. apologies if I've catagorised the problem wrongly.

---

### Post by yakker.yak on 2008-12-02
I guess the 1st question/problem to resolve is why you can't see your own wireless router via network manager when you pull down the list of available wireless routers.

Is your wireless router enabled to broadcast its SSID?

Are you currently using access security for your wireless router? Is it WEP, WPA, WPA2? Do you have a MAC filter enabled?

---

### Post by spelkZERO on 2008-12-02
> Is your wireless router enabled to broadcast its SSID?

I did have it not broadcasting the SSID, but I have changed that. It is now set to Allow Broadcast of SSID. Still not showing up though, and the worst of it is, there are a number of similar broadband connections around this area that are showing up. Same ISP. When I do enter the info to connect direct, it shows up in the list, but has an empty signal strength, whereas these other connections all have orange bars in their signal strength boxes.

> Are you currently using access security for your wireless router? Is it WEP, WPA, WPA2? Do you have a MAC filter enabled? 

Using WPA. I did have a MAC filtered Access List, yes, and I've tried it with the MAC addresses on both eth0 and eth1, as well as turning the Access list off.. without much success.

---

### Post by Forecast on 2008-12-02
Same problem here. I got my Mini today, you too spelkZERO?

Usually a hidden SSID is no problem when I'm using Ubuntu on notebooks with a wireless connection. But here, after entering the hidden SSID and WPA2-key, it looks as if it were connected. It says in the bubble help that signal strength were 100% but the signal strength bar in menu is empty nonetheless.  Network is unreachable. Also, the applet forgets the access credentials every time.

I can't seem to activate the manual configuration via gui either.

---

### Post by spelkZERO on 2008-12-02
> **Forecast said:**
> Same problem here. I got my Mini today, you too spelkZERO?

Yeah just delivered today.

> **Forecast said:**
> I can't seem to activate the manual configuration via gui either.

I found you have to unlock the Manual Configuration, using your user password. Its an authentication thing, to stop casual users from messing about with your system settings, I think.

---

### Post by Forecast on 2008-12-02
> **spelkZERO said:**
> Yeah just delivered today.
I found you have to unlock the Manual Configuration, using your user password. Its an authentication thing, to stop casual users from messing about with your system settings, I think.

I unlock it alright, and enter my credentials, but it doesn't get me connected.

Well and sometimes the applet even crashes...
```

Dec  2 19:12:11 NetworkManager: <info>  eth1: Device is fully-supported using driver 'wl'. 
Dec  2 19:12:11 NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Dec  2 19:12:11 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Dec  2 19:12:11 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Dec  2 19:12:11 NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Dec  2 19:12:11 NetworkManager: <info>  Deactivating device eth1. 
Dec  2 19:12:11 NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Dec  2 19:13:11 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec  2 19:13:11 NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / <MYSSID> 
Dec  2 19:13:11 NetworkManager: <info>  Deactivating device eth1. 
Dec  2 19:13:11 NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Dec  2 19:13:11 NetworkManager: <info>  Device eth1 activation scheduled... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) started... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  2 19:13:11 NetworkManager: <info>  Activation (eth1/wireless): access point '<MYSSID>' is encrypted, and a key exists.  No new key needed. 
Dec  2 19:13:12 NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Dec  2 19:13:12 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Dec  2 19:13:12 kernel: [  109.618984] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec  2 19:13:12 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  kernel_driver for non broadcast check: wl (has_scan_capa_ssid=0) 
Dec  2 19:13:13 NetworkManager: <info>  Using plain AP_SCAN 2 for wl 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was '0' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid <LONG NUMBER>' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  2 19:13:13 NetworkManager: <info>  SUP: response was 'OK' 
Dec  2 19:13:13 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Dec  2 19:13:14 avahi-daemon[3979]: Registering new address record for <GENERATED IPv6 address> on eth1.*.
Dec  2 19:14:13 NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Dec  2 19:14:13 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Dec  2 19:14:13 NetworkManager: <info>  Activation (eth1) failed for access point (<MYSSID>) 
Dec  2 19:14:13 NetworkManager: <info>  Activation (eth1) failed. 
Dec  2 19:14:13 NetworkManager: <info>  Deactivating device eth1. 
Dec  2 19:14:13 avahi-daemon[3979]: Withdrawing address record for <GENERATED IPv6 ADDRESS> on eth1.
Dec  2 19:14:13 NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Dec  2 19:14:23 NetworkManager: <WARN>  request_and_convert_scan_results(): unknown error, or the card returned too much scan info: Invalid argument 
Dec  2 19:14:26 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec  2 19:14:26 NetworkManager: <WARN>  nm_device_802_11_wireless_get_activation_ap(): nm_device_802_11_wireless_get_activation_ap: tried to manually connect to network '<MYSSID>' without providing security information! 
Dec  2 19:14:26 NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / <MYSSID> 
Dec  2 19:14:26 NetworkManager: <info>  Deactivating device eth1. 
Dec  2 19:14:27 NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Dec  2 19:14:27 NetworkManager: <info>  Device eth1 activation scheduled... 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) started... 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Dec  2 19:14:27 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Dec  2 19:14:27 NetworkManager: <WARN>  nm_signal_handler(): Caught signal 6.  Generating backtrace... 
Dec  2 19:14:27 NetworkManager: ******************* START **********************************
Dec  2 19:14:27 NetworkManager: (no debugging symbols found)
Dec  2 19:14:27 last message repeated 11 times
Dec  2 19:14:27 NetworkManager: [Thread debugging using libthread_db enabled]
Dec  2 19:14:27 NetworkManager: [New Thread 0xb7b14720 (LWP 4659)]
Dec  2 19:14:27 NetworkManager: [New Thread 0xb6b11b90 (LWP 4963)]
Dec  2 19:14:27 NetworkManager: [New Thread 0xb7312b90 (LWP 4812)]
Dec  2 19:14:27 NetworkManager: [New Thread 0xb7b13b90 (LWP 4685)]
Dec  2 19:14:27 NetworkManager: (no debugging symbols found)
Dec  2 19:14:27 last message repeated 9 times
Dec  2 19:14:27 NetworkManager: 0xb7efd410 in __kernel_vsyscall ()
Dec  2 19:14:27 NetworkManager: ******************* END **********************************
```

Could it be that it tries to use IPv6 and my access point does not answer?

---

### Post by spelkZERO on 2008-12-02
I'm getting the same error in the daemon.log, where during activation the association took too long. Everything leading up to is was reporting ok.

Is there a way to disable the use of IPv6?

I've also tried a wired connection to my router, which worked fine, when allowed to automatically configure itself. I updated the Ubuntu system, it was 80 days out of date. But am still seeing this lack of connectivity to my wireless router.

The System Monitor reports

Ubuntu release 8.04 (hardy)
Kernel Linux 2.6.24-19-lpia
GNOME 2.22.2

---

### Post by yakker.yak on 2008-12-02
I would try a few things:

- Disable encryption altogether and see if you can connect then.
- Enable encryption, and try to connect with WEP enabled.
- Turn off WEP, and try to connect with WPA (TKIP) enabled.
- Turn off WPA(TKIP) and try to connect with WPA(AES) enabled.

For my router, I would get an occasional system lock-up via WPA(TKIP), but then switched to WPA(AES) and haven't had any problems since.

BTW, I'm referring to WPA above, not WPA2.

Also, is your SSID unique in your area (i.e. you're not trying to connect to someone else's router)? Obvious perhaps, but thought I'd ask just in case ...

---

### Post by Forecast on 2008-12-02
> **spelkZERO said:**
> 
Is there a way to disable the use of IPv6?


I tried that but I figure that is not the problem.

I've googled and read about quite some bugs. It could either be a problem with the bcm driver or with the network-manager.

I also managed to boot Ubuntu Intrepid from an USB Stick, getting slightly different syslog messages but basically the same result.

---

### Post by Forecast on 2008-12-02
Can't believe I found it!!!:lolflag:
 I did a scan with iwlist to see the networks and I wondered why there I couldn't see all the channels (all my neighbors use wlan too, using all the frequencies :-)). Then I remembered something I read weeks ago. It was about some wlan frequences that aren't no longer avaliable in the drivers or the hardware since they are not allowed in the USA. Just looked it up: in Europe, we use channels 1-13, but in the US they only use only 1-11. And in fact I did use channel 12 until today.
 So the solution is really simple: change your router to use any channel from 1 to 11. Wifi on my Mini works now, I'm happy. Hoping that will help you too.

Cheers,
 Wolfram from Berlin, Germany

---

### Post by spelkZERO on 2008-12-03
Well done spotting that one Wolfram! I was on Channel 13 (here in the UK)- so I've changed my Channel to 11 and voila! It connects up fine..

Thank you very much..

---

### Post by armandh on 2008-12-03
don't forget to mark thread solved

---

### Post by danellisuk on 2009-04-30
This problem has not been solved, but has a workaround.  The solution would be to get the wireless to work with channels 12 and 13.

I have added a bug to launchpad regarding setting the regulatory domain on the mini9.

[https://bugs.launchpad.net/ubuntu/+source/iw/+bug/370046](https://bugs.launchpad.net/ubuntu/+source/iw/+bug/370046)

The reason this is important is for the scenario where you cannot change the wireless channel, such as at a hotel/coffee shop/school etc.  Or the scenario where you prefer the router to auto select the least congested channel.

---

### Post by krige on 2009-05-01
I have the same problem here with an Asus EEE PC 1000HE.

> **danellisuk said:**
> This problem has not been solved, but has a workaround.  The solution would be to get the wireless to work with channels 12 and 13.

I agree with that, in fact I am in a situation where I cannot change the wireless channel of the router I want to connect to.

I have tried to use the command "iw reg set EU" (I live in EU) but with no luck: after running the command "iwlist wlan0 channel" still only 11 channels are displayed.

---

