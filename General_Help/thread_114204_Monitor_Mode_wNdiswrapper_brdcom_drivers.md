---
title: "Monitor Mode w/Ndiswrapper brdcom drivers"
date: 2006-01-08
forum: General Help
---

### Post by xxsiriusxburnxx on 2006-01-08
Now, I have read in a few sites that it doesn't seem to be possible at this time to use monitor mode with Ndiswrapper. Seem as I am using a Broadcom wireless nic, which isnt supported by linux the only way I have come across to use these drivers is Ndiswrapper. Now as an advanced windows user for years but Finally getting into linux I am looking to try and practice WEP cracking on my router. I took many steps to get connected with ndiswrapper in the first place from trying auditor/knoppix to now using Ubuntu linux, and if at all possible would like to be able to use it as I have this setup with Ndiswrapper if possible... If anyone has any suggestions please reply ,pm me or send me an email, Thanks Greg.

---

### Post by ahave2005 on 2006-01-08
From the ndiswrapper FAQ:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ)
>  Is master mode supported?

No! NDIS doesn't support Master/Repeater/Monitor modes. The only modes supported are Ad-Hoc and Managed. Note that some drivers may support features that are not in NDIS e.g., showing signal noise and possibly Master mode, but they are proprietary and no documentation available for them, so such features won't be supported by ndiswrapper.

So I'm afraid not, tried the same yesterday.

/ahave

---

### Post by ahave2005 on 2006-01-08
Are you certain your nic isn't reconized in Linux? I thought mine wasn't, but I only just found out, that it worked, only not when I try to set it up in GUI.

Have a look at this list: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

There's a good few broadcom chipset around.

Mine does even support monitor mode in the native linux module.

/ahave

---

### Post by xxsiriusxburnxx on 2006-01-08
As far as I can tell you it isnt recognized at all when I first started even before using ndiwrapper I dont believe I had a wlan in gui or under the shell just checking with iwconfig no extensions were present until I used the ndiswrapper, I checked that list and dont seem to find it, its an internal Broadcom 43xx series and it comes in a gateway laptop. I am unsure of how you say you got it too be detected under native linux w/o the gui saying its active or even the shell. I may end up buying a prism2 or orinoco based chipset card, if anyone has any suggestions on cards and where to buy them that would be much appreciated, Thanks Greg

---

