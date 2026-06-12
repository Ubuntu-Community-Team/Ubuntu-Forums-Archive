---
title: "Dell Vostro 2510  issues - SOLVED"
date: 2008-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by morgan_greywolf on 2008-12-24
This thread is to keep track of issues I've had installing the Vostro 2510 with Ubuntu Studio 8.10 [Intrepid Ibex]

[LIST=1]
[*]**Wireless**
The built-in Broadcom BCM4312 worked flawlessly with the (included) restricted drivers.  If you don't get the little 'new restricted drivers available' in in the notification area, just do 'System -> Administration Hardware Drivers' and click the 'Broadcom STA wireless' driver in the list and click 'Activate'.  You don't need a working Internet connection to do this.

One thing of note is that the Ubuntu Studio developers, in their infinite wisdom, decided not to include the Network Manager applet.  Since you need a working Internet connection to do this, you'll need to either hook the Vostro up wired and install it that way, or, for the more adventurous folks, you can do this (**optional**):

Note that these instructions are for routers with WPA/WPA2 Private Shared Key (PSK) security enabled. For other configurations, YMMV. Create a file in your home directory called 'wpa-supplicant.conf'.  This is what the file should contain:

```

network={
	ssid="<your router's essid>"
	scan_ssid=1
	key_mgmt=WPA-PSK
	psk="<your router's shared key>"
}
```

See your router's instructions for finding out your ESSID and shared key if you don't know what they are.

Then, run the following in a terminal window:
```

sudo wpa_supplicant -i eth1 -c wpa_supplicant.conf
sudo iwconfig eth1 essid <your router's essid>
sudo ifconfig eth1 up
sudo dhclient3 eth1 &

```

Wait a few minutes and then type:
```

ifconfig eth1 | grep 'inet addr'

```
If you got an IP address, you're good to go!  Now you can install 'Network Manager' via 'Add/Remove Programs'.  If you have problems, click the 'Reload' button in 'Add/Remove Programs' first.

[*]**Built-in Webcam**
Works out of the box. You can check this by installing and running 'Cheese'. Just make sure you remove the film sticker over the camera lens, or your pictures will look like crap. ;-)

[*]**Built-in nVidia 8400M**
Works out of the box.  You'll want to install the newest driver from 'restricted drivers'.  Do like the above for the wireless card, but select the driver for the nVidia 8400M that's labeled '[recommended]'.

[*]**Sound**: 
The sound hardware will be detected, but will not work out of the box.  You need to merely add the following line to your /etc/modprobe.d/alsa-base file:

```

options snd-hda-intel model=dell

```

and restart the computer.  Open up the volume control and select 'HDA Intel (Alsa mixer)' under Device.  You'll see a new slider there labeled 'Speaker'.  Turn that puppy all the way up.

[*] **Built-in mic**:
Still working on this.  Will post here when I find out more.

[/LIST]

---

### Post by Whiskerburn on 2009-03-22
Thanks for the great post...  I've been bashing my head against the sound issue on my 2510 for a week and now - - Sweet success!!!  :p

Thanks again!!

---

### Post by michaelbelt on 2009-03-24
Man, I *still* cannot get the sound to work.  Morgan_Greywolf, is your 2510 using the Realtek audio?

I got this Vostro in December, so I'm guessing ours are probably pretty close.

---

### Post by -Ender on 2009-04-02
Thank you for this article! I've been trying solution after solution to try to get my audio to work on my new Vostro 2510, and this one little line did the trick!
For the record my audio chip is an ICH8 (rev3).

---

