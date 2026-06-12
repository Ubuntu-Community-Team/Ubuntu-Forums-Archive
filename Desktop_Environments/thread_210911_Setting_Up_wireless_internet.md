---
title: "Setting Up wireless internet"
date: 2006-07-07
forum: Desktop Environments
---

### Post by catflea on 2006-07-07
How can I set up wireless internet in Dapper?  

I've got a BT Voyager 1040 Card which runs a broadcom chipset ,(it recognises it in Network settings,  but I can't make it active!)

---

### Post by porchcth on 2006-07-07
What happens when you click on 'Activate'.
And (sorry about the stupid question) have you set the properties correctly?

Regards,

porch.

---

### Post by catflea on 2006-07-07
1)  Properties are definatly right

2)  I click activate and it thinks about it for about 3 minutes before "activating"   but deactivates as soon as I click OK

---

### Post by porchcth on 2006-07-07
Does iwconfig reveal anything?

---

### Post by randell6564 on 2006-07-07
Hi!

I use a Linksys Wusb11 V.2.6 Wireless antenna.  This with a Wireless G Router.

I use WEP Security along with a name that I specified for my network.

I dont know... Maybe you are not providing the right info to your router.

Can you type your IP Address into your browser and pull up your routers' security page?

If so, What are the settings for wireless?

Do they match what you entered when you installed your card?

Make sure that you DE-ACTIVATE your Ethernet connection, (eth0) if it shows up, (right underneath wireless connection)

Then highlite your wireless, click on properties and enter your network name, WEP key,(if you use one), and under 'Connection Settings' choose 'DHCP' 

Occasionally, I have to unplug my antenna, wait 10 seconds, plug it in (to reset) and that will do the trick. (with a usb connection. And only because I dual-boot with XP!  For some reason, the settings get muffed-up when I boot to another OS)

Good Luck!

---

### Post by catflea on 2006-07-07
It doesn't even detect the available network - I've had to enter everything manually!   (and yes, there is signal - wireless works fine in XP)

oh, using lspci in terminal I get:

0000:02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)

---

### Post by randell6564 on 2006-07-07
> **catflea said:**
> It doesn't even detect the available network - I've had to enter everything manually!   (and yes, there is signal - wireless works fine in XP)

oh, using lspci in terminal I get:

0000:02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)

Your card is recognized. And I dont think that ubuntu goes searching for a network without "entering" the proper settings "manually".

I install and RE-install ubuntu all the time, on test boxes, and EVERY time, I've had to "enter" my wireless settings "manually".

---

### Post by randell6564 on 2006-07-07
> **randell6564 said:**
> Your card is recognized. And I dont think that ubuntu goes searching for a network without "entering" the proper settings "manually".

I install and RE-install ubuntu all the time, on test boxes, and EVERY time, I've had to "enter" my wireless settings "manually".

Did you Disable your Eth0?  Did you try UNplugging, or Disconnecting your card (to reset)?

---

### Post by catflea on 2006-07-07
> **randell6564 said:**
> Did you Disable your Eth0?  Did you try UNplugging, or Disconnecting your card (to reset)?

I havn't unplugged the card,because trying to get into my base unit is a mission (soooooo much gaffer tape!)

however I did disable all the other connections (my wireless is eth0!) and it didn't do a sodding thing.  ](*,) ](*,)

---

### Post by catflea on 2006-07-07
another gem of useless info for you

lo        no wireless extensions.

eth2      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

obtained in iwconfig,  don't know if it helps

---

### Post by randell6564 on 2006-07-07
> **catflea said:**
> another gem of useless info for you
You
lo        no wireless extensions.

eth2      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

obtained in iwconfig,  don't know if it helps

You DONT want 'eth0'! You want 'wlan0'.  If you want to run Wireless, you want to DISable your eth0.

THEN configure your wireless.

---

### Post by catflea on 2006-07-07
Thats probably it then!!!

So how in heck do I do that?    I don't have a wlan!

Sorry,  still a noob really - getting better though!

---

### Post by Barrakketh on 2006-07-07
> **randell6564 said:**
> You DONT want 'eth0'! You want 'wlan0'.  If you want to run Wireless, you want to DISable your eth0.

THEN configure your wireless.

That's not always true.  eth0 isn't always your ethernet connection, and wlan0 isn't also your wireless connection.  For example, my wireless adapter is ra0.

EDIT: catflea, [this thread](http://www.ubuntuforums.org/showthread.php?t=185650) may be of some help.

---

### Post by llamakc on 2006-07-07
My wireless broadcom card IS eth0, so don't go editing /etc/network/interfaces yet.

You want to run:

sudo iwconfig eth0 ap any
and then try iwlist eth0 scan again, and iwconfig. Hopefully you'll see your accesspoint now. I had to add:

sudo iwconfig eth0 essid MYESSIDNAME

and 

sudo iwconfig eth0 rate 11M

which after doing that (and ensuring the module was loaded) my card worked perfectly after a reboot.

Good luck.

---

### Post by deathbyswiftwind on 2006-07-07
> **catflea said:**
> How can I set up wireless internet in Dapper?  

I've got a BT Voyager 1040 Card which runs a broadcom chipset ,(it recognises it in Network settings,  but I can't make it active!)

Try using my broadcom howto [http://www.ubuntuforums.org/showthread.php?t=189070]("http://www.ubuntuforums.org/showthread.php?t=189070")
It worked for someone else with a voyager

---

### Post by PriceChild on 2006-07-07
Maybe try using gnome network manager:

sudo apt-get install gnome-network-manager

So easy to use its silly :)

---

### Post by randell6564 on 2006-07-07
> **Barrakketh said:**
> That's not always true.  eth0 isn't always your ethernet connection, and wlan0 isn't also your wireless connection.  For example, my wireless adapter is ra0.

EDIT: catflea, [this thread](http://www.ubuntuforums.org/showthread.php?t=185650) may be of some help.

OOPS!

I never claimed to be an Ubuntu Guru!  But, in my defense,  EVERY SINGLE time that I have installed ubuntu on several different boxes,  My wireless shows up as 'Wlan0' and my ethernet shows up as 'eth0'. ( And believe ME, I've installed ubuntu so many fricken times, I REALLY should get paid for it! lol!)

---

### Post by catflea on 2006-07-08
death by swiftwind, its a different chipset.  I have a 4318 not a 4306

edit:   D'OH!   Got it wrong it is a 4306!

---

### Post by deathbyswiftwind on 2006-07-08
Well there is a broadcom howto also in the forums made by another guy and it has info for your card.

---

### Post by catflea on 2006-07-08
cheers, I will try and track it down

---

### Post by catflea on 2006-07-08
cheers, I will try and track it down

---

