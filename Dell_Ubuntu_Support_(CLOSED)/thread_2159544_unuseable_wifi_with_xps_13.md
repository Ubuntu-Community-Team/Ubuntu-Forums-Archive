---
title: "unuseable wifi with xps 13"
date: 2013-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by octetcloud on 2013-07-03
yesterday was first day spent trying to work all day with xps-13, wifi is unstable, it won't stay up. I'm running 12.04, 3.2.0-48-generic, not sure what other info is required.


kern.log showed lots of errors, mostly this one:
[FONT=arial]
[/FONT]Jul  2 11:59:59 samtu kernel: [ 1753.775608] iwlwifi 0000:01:00.0: Request scan called when driver not ready.[FONT=arial]
[/FONT]
Lots of that in the morning, I disabled the n wifi:

sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

Wasn't a noticeable improvement. Also, appears to be specific to some APs, it happens in one of my offices, but (so far) seems more stable in other offices.

Lack of wifi makes the xps unuseable for me, what can I provide to help troubleshoot this? I'm not sure how much of my log files I should paste.

Sam



Jul  2 12:50:08 samtu kernel: [ 1560.171428] cfg80211: All devices are disconnected, going to restore regulatory settings
Jul  2 12:50:08 samtu kernel: [ 1560.171457] cfg80211: Restoring regulatory settings
Jul  2 12:50:08 samtu kernel: [ 1560.171472] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 12:50:08 samtu kernel: [ 1560.179454] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jul  2 12:50:08 samtu kernel: [ 1560.179457] cfg80211: World regulatory domain updated:
Jul  2 12:50:08 samtu kernel: [ 1560.179458] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 12:50:08 samtu kernel: [ 1560.179460] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 12:50:08 samtu kernel: [ 1560.179462] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 12:50:08 samtu kernel: [ 1560.179463] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 12:50:08 samtu kernel: [ 1560.179464] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 12:50:08 samtu kernel: [ 1560.179466] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 12:50:11 samtu kernel: [ 1563.403133] wlan0: authenticate with 20:76:00:13:83:9c (try 1)
Jul  2 12:50:11 samtu kernel: [ 1563.410631] wlan0: authenticated
Jul  2 12:50:11 samtu kernel: [ 1563.411315] wlan0: associate with 20:76:00:13:83:9c (try 1)
Jul  2 12:50:11 samtu kernel: [ 1563.610480] wlan0: associate with 20:76:00:13:83:9c (try 2)
Jul  2 12:50:11 samtu kernel: [ 1563.810190] wlan0: associate with 20:76:00:13:83:9c (try 3)
Jul  2 12:50:12 samtu kernel: [ 1564.009946] wlan0: association with 20:76:00:13:83:9c timed out
Jul  2 12:50:20 samtu kernel: [ 1572.226595] wlan0: authenticate with 20:76:00:13:83:9c (try 1)
Jul  2 12:50:20 samtu kernel: [ 1572.422783] wlan0: authenticate with 20:76:00:13:83:9c (try 2)
Jul  2 12:50:20 samtu kernel: [ 1572.622558] wlan0: authenticate with 20:76:00:13:83:9c (try 3)
Jul  2 12:50:20 samtu kernel: [ 1572.822292] wlan0: authentication with 20:76:00:13:83:9c timed out
Jul  2 12:50:23 samtu kernel: [ 1575.441214] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  2 12:50:29 samtu kernel: [ 1581.050891] wlan0: authenticate with 20:76:00:13:83:9c (try 1)
Jul  2 12:50:29 samtu kernel: [ 1581.053915] wlan0: authenticated
Jul  2 12:50:29 samtu kernel: [ 1581.055557] wlan0: waiting for beacon from 20:76:00:13:83:9c
Jul  2 12:50:29 samtu kernel: [ 1581.080300] wlan0: beacon received
Jul  2 12:50:29 samtu kernel: [ 1581.123277] wlan0: associate with 20:76:00:13:83:9c (try 1)
Jul  2 12:50:29 samtu kernel: [ 1581.135835] wlan0: RX ReassocResp from 20:76:00:13:83:9c (capab=0x411 status=0 aid=2)
Jul  2 12:50:29 samtu kernel: [ 1581.135846] wlan0: associated

---

### Post by varunendra on 2013-07-03
Welcome to the forums octetcloud !

It seems you are having too many problems with 12.04 (as per your other thread : [http://ubuntuforums.org/showthread.php?t=2159549](http://ubuntuforums.org/showthread.php?t=2159549))

Although I don't recommend it often, you may try 13.04 to see if the latest drivers can perform any better on your laptop. Since its model is relatively new, the latest kernel may work better with it.

You may also try acpi=off and other parameters on the existing installation to see if it can fix the freezing issue : [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Once that is fixed (or if the the system is sufficiently stable to try this), follow the "Wireless Script" link in my signature, follow the instructions there to generate a detailed diagnostics report, and post back its pastebin link here.

---

### Post by octetcloud on 2013-07-04
> **varunendra said:**
> Welcome to the forums octetcloud !

It seems you are having too many problems with 12.04 (as per your other thread : [http://ubuntuforums.org/showthread.php?t=2159549](http://ubuntuforums.org/showthread.php?t=2159549))

Although I don't recommend it often, you may try 13.04 to see if the latest drivers can perform any better on your laptop. Since its model is relatively new, the latest kernel may work better with it.

You may also try acpi=off and other parameters on the existing installation to see if it can fix the freezing issue : [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Once that is fixed (or if the the system is sufficiently stable to try this), follow the "Wireless Script" link in my signature, follow the instructions there to generate a detailed diagnostics report, and post back its pastebin link here.

[http://pastebin.ubuntu.com/5844356/](http://pastebin.ubuntu.com/5844356/)

I have intermittent connectivity, but even when connected, the performance is terrible (took almost 2 minutes to load the page for this thread).

You suggest updating to 13.04, is that an 'official' suggestion? I'm about to see if I can get Dell support for this. I'd rather run the last ubuntu release, at all times, but I dont want to void my warranty or support.

---

### Post by varunendra on 2013-07-04
> **octetcloud said:**
> You suggest updating to 13.04, is that an 'official' suggestion? I'm about to see if I can get Dell support for this. I'd rather run the last ubuntu release, at all times, but I dont want to void my warranty or support.

I am not officially associated in any way with Ubuntu or canonical - the company that develops Ubuntu, if that's a confusion for you. I'm just a user like you. :)

However, the 13.04 is the latest "official release" of Ubuntu. The reason why I prefer 12.04 over 13.04 is that 12.04 is and LTS and hence will be supported for 5 years, while 13.04 only for 9 months. But did your laptop come pre-installed with 12.04? If not and you installed it by yourself, Dell has the same excuse to void its warranty as with 13.04.

That being said, your wireless card doesn't seem so new. It seems old enough to be properly supported in 12.04 too. Let's try a few things -

First, make sure to use encryption type in the router(s) pure WPA2-PSK (AES) only, and absolutely not WPA/WPA2 mixed mode, not TKIP. This is highly recommended.

Second, try channels 1 or 11 if you using some other channel(s). This sometimes makes a significant difference.

Of course you can not do anything about these on routers that you don't have admin access to, but if you have, try them.

With (or without) these changes in the router, try this in your Ubuntu -
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi swcrypto=1
```

If that alone doesn't help, also try disabling the N-channel again, in combination with above -
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi swcrypto=1 11n_disable=1
```
Both these parameters (swcrypto=1, 11n_disable=1) would be temporary changes and will be reset to default on reboot. If these seem to help, we can make them permanent.

You may also try changing the channel combinations in the router if that is an available option (b/g/n, b/g only, etc.), I don't remember correctly, but some of them work better than others.

---

### Post by octetcloud on 2013-07-04
I tried the 11n_disable on monday, did not help. I will try the swcrypto, see if it helps, then try both.

Thank you for the suggestions.

I don't have easy access to the AP, and I will return the laptop if it requires me to modify my APs, because I need a laptop specifically so I can roam, and work from any AP I find.

Btw, 12.04 LTS is what came with the laptop (its this one [http://www.ubuntu.com/partners/dell/dellxps](http://www.ubuntu.com/partners/dell/dellxps)). I've never understood LTS for a desktop, the chance I am going to be using 2 year old versions of my dev tools, much less 4-5 years, is .... zero. I've already rebuilt tmux from source.

Supposed to get a call from Dell tomorrow, we'll see if they can help.

---

### Post by octetcloud on 2013-07-04
I think the swcrypto=1 may be the trick. I didn't do a lot of wifi today, was just coding, but I never noticed it down when I hit the browser. Tomorrow I will do more google hangouts, and see how it works under load.

How do I make it permanent? /etc/... config file?

Interestingly, no machine lockups, either, perhaps because they are so sporadic, perhaps because no video conferencing, perhaps it was related to wifi?

---

### Post by varunendra on 2013-07-04
> **octetcloud said:**
> How do I make it permanent? /etc/... config file?
Yep, a config file in modprobe.d directory -
```
echo "options iwlwifi swcrypto=1 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
You may omit the 11n_disable=1 part if it doesn't seem to make any positive difference.

> Interestingly, no machine lockups, either, perhaps because they are so sporadic, perhaps because no video conferencing, perhaps it was related to wifi?
Any of them is possible. I'm sure we all (on this thread, as well as the other one) would love to hear YOUR opinion on this, after giving it enough time to be sure if it keeps working nicely. :)

---

### Post by octetcloud on 2013-07-09
So, I tried setting swcrypto and 11n_disable, together and seperate, neither work. Triggering drops is easy, I just use google hangout. So, any other suggestions?

Dell rep suggested disabling crypto on the AP, because the only thing he can see in the logs is loss of authorization, and reauth, but a laptop that requires AP reconfig to get wifi working is pretty much the same as laptop that doesn't work :-(. I will try when I get back to that office, just to confirm the src of problem.

I upgraded to 13.04, too, because I decided an xps-13 that I'm afraid to keep updated with ubuntu releases is also a non-working laptop... haven't had a chance to see if that makes a difference, there is a chance.

---

### Post by dhumphris on 2013-07-15
Hi,
I bought the XPS 13 on Saturday and ran a clean install of 13.04 onto it. I'm a total Linux novice so this is a learning curve for me.
I am losing my wifi connection randomly and regularly. I'm in the exact same situation as octetcloud. Any advice?

---

### Post by varunendra on 2013-07-15
Welcome to the forums dhumphris!
> **dhumphris said:**
> I am losing my wifi connection randomly and regularly. I'm in the exact same situation as octetcloud. Any advice?
It would be better if you show us the details of your network setup first.

Please follow the "Wireless Script" link in my signature and post back the report generated by the script in the linked post.

---

