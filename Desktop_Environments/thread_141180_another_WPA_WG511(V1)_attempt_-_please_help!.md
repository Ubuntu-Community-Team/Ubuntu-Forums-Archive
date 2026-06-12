---
title: "another WPA WG511(V1) attempt - please help!"
date: 2006-03-07
forum: Desktop Environments
---

### Post by seiser on 2006-03-07
dear folks, I've been searching the web up and down ... now I'm quite confused and decided to open a new thread. I hope somebody out there may help a ubuntu newbee! I saw a few conversations about the same topic, but not with my specific hardware and problem. 

I'm trying to set up a WPA connection to my accesspoint using a WG511 card (it's the first model aka V1 aka "made in taiwan").

Ubuntu configures it nicely with WEP encryption without any problems (i was supprised it got automatically detected!) 

First I tried several howtos using ndiswrapper (e.g [ here (german)]("http://blog.4mms.org/linux/netgear-wg511-unter-ubuntu-mit-wpa")) but figured that this is for the newer version (chineese aka V2).

so, I'm doing this with WPA Supplicant. I apt-get'd the package and followed the instructions given [here]("http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa_supplicant+repository") (this is the howto of the ubuntu Forum). 

I'm pasting the uncommented information of /etc/default/wpasupplicant
```

ENABLED=1
OPTIONS="-D hostap -i eth1 -c /etc/wpa_supplicant.conf -d"

```
eth1 is my Wireless LAN extension (tells me iwconfig)
yet I'm not sure if *hostap* is the correct driver for the WG511V1 ... I know WG511V1 uses the Prism54 chipset (and I managed to use the card with this driver in SUSE), but I think the prism54 driver is not directly supported by WPA supplicant(?)
see the wpa supplicant [ README ]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain") (section driver)

other drivers are (  hostap = Host AP driver (Intersil Prism2/2.5/3) [default], hermes, madwifi, atmel,  wext, ndiswrapper, broadcom, ipw, wired, bsd, ndis)

this is my /etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=wheel
network={
	ssid="WG" #SSID
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	psk=/$§)?=?= ... 9jgkg878
}

```

In here, I wonder if the settings for *psk* are correct. I trunctated the key, but it's definitly a ASCII code, 63 charakters wide. I learnt that if entereing an ASCII key , I need to set quotes like 
```
psk="/$§)?=?= ... 9jgkg878"
```

in that case, wpasupplicant start fails with this output:
```

root@ubuntu-seb:/etc/rcS.d# invoke-rc.d wpasupplicant start
Starting wpasupplicant: Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'hostap'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line 18: Invalid passphrase length 65 (expected: 8..63) '/$§)?=?=.....9jgkg878'.
Line 18: failed to parse psk '"/$§)?=?=....9jgkg878'.
Line 19: WPA-PSK accepted for key management, but no PSK configured.
Line 19: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.
invoke-rc.d: initscript wpasupplicant, action "start" failed.

```
without quotations marks: 

```

root@ubuntu-seb:/etc/rcS.d# invoke-rc.d wpasupplicant start
Starting wpasupplicant: Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'hostap'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line 18: Invalid PSK '/$§)?=?= .... gkg878'.
Line 18: failed to parse psk '/$§)?=?= ... jgkg878'.
Line 19: WPA-PSK accepted for key management, but no PSK configured.
Line 19: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.
invoke-rc.d: initscript wpasupplicant, action "start" failed.

```

Besides from not being certain if the driver is correct, I wonder how I could enter the correct passphrase in hexadecimal numbers. I already converted the ASCII string to hex, but the result was even longer than 65 digits.

any help is greatly appreciated! thanks in advance!

---

### Post by seiser on 2006-03-08
has anyone an idea of where to start? :-D 

Or did I do something completly wrong? 
thanks, seb

---

### Post by hysterik on 2006-03-26
First, your specific problem has to do with the quotation marks on your psk, just get rid of them and the message about invalid length will go away.

I just spent the last few days, not solid mind you, trying to get this exact same card working on my laptop, and then another netgear wg311 working on the HTPC I'm trying to setup with Myth.  As a word of advice, for sake of WPA forget trying to get anything other than ndiswrapper working.  I've tried all sorts of combinations.  Go to the following website and get the Windows XP driver for the wg511 card.

[http://kbserver.netgear.com/products/WG311v1.asp](http://kbserver.netgear.com/products/WG311v1.asp)

Now, I installed this on my dual boot Windows XP to get at the .inf file, but I'm pretty sure you could do the same thing using wine.  I tried it once and it errors out near the end, but everything is copied out of the .exe file.  After you go through a partial install in wine, the .inf file will either be in ~/.wine/drive_c/Program Files/NETGEAR/WG311/Driver or it may be in drive_c/windows/drivers.  Run the following,

$ sudo -s
# ndiswrapper -i netwg511.inf

When you run ndiswrapper -l, you should see

Installed ndis drivers:
netwg511        driver present, hardware present

If it doesn't say hardware present, then it isn't finding your card.  You could have a v2, and in that case I'd try finding those drivers.  Alternately, you can run lspci -n and one of those may be your card, you could then use the -d XXXX:XXXX netwg511 to force it.

Also, you can try enabling your ssid.  I went ahead and enabled mine to try and simplify things.  If you do hide your ssid, make sure to set scan_ssid to 0 in your /etc/wpa_supplicant.conf file.

Now, it looks like ubuntu starts the prism54 module.  I don't know if there is a problem running it and ndiswrapper at the same time, but just to be safe get rid of it.

# rmmod prism54
# cd /lib/modules/`uname -r`
# vi modules.dep (then remove the line with prism54)
# rm -rf ./kernel/drivers/net/wireless/prism54
# depmod -a

Just to test things, run wpa_supplicant by hand.  You'll know if you were successfull if you see a bunch of hex being passed around, and some messages reading AUTHENTICATING and SUCCESS.

# wpa_supplicant -i eth1 -D ndiswrapper -c /etc/wpa_supplicant.conf -dd

Good luck, and if you have further questions the following thread should fill in the other pieces.

The last thing you should do, if ndiswrapper didn't do it automatically, is register it as a module.  Run,

# ndiswrapper -m

A big problem I ran into was trying to run wpa_supplicant without this module running.  If it isn't running, you aren't going anywhere.  Run lsmod |grep ndis to see if it is loaded or not.  If not, you can run modprobe -v ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa-psk](http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa-psk)

---

