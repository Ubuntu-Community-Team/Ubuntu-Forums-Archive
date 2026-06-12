---
title: "Wireless networking with jaunty"
date: 2009-04-23
forum: General Help
---

### Post by sefs on 2009-04-23
Hi all

I usually control my networking thru /etc/network/interfaces

With jaunty it seems to now ignore this file and it uses network-manager.  

the serialmonkey rt73 driver is no longer under active development so I am using the driver that comes with jaunty which now works, at least with network-manager. The jaunty driver is rt73usb.

I used these lines in intrepid

```

    	pre-up iwpriv wlan0 set SSID=myssid
    	pre-up iwpriv wlan0 set Channel=11
    	pre-up iwpriv wlan0 set NetworkType=Infra
    	pre-up iwpriv wlan0 set AuthMode=WPA2PSK
    	pre-up iwpriv wlan0 set EncrypType=AES
    	pre-up iwpriv wlan0 set WPAPSK=mypassphrase

```

They no longer work with rt73usb

I tried these
```

	wpa-driver wext
	wpa-ssid myssid
	wpa-ap-scan 1
	wpa-proto RSN
	wpa-pairwise CCMP
	wpa-group CCMP
	wpa-key-mgmt WPA-PSK
	wpa-psk mypassphrase

```

They work but the connection keeps droping out every other second.

What commands can I use in the interfaces file for rt73usb.

Thanks.

---

