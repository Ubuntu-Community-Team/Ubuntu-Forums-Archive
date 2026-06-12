---
title: "Internet connection drops to 0 kbps"
date: 2010-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by venkyms on 2010-02-26
Hi guys,
I am facing problem with my wifi internet,
i am connected to internet, but my connection speed drops to 0 kbps for 10 to 15 secs and regains the speed. this happens in regular interval.

my system is DELL Studio XPS 1340 and karmic koala

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express)

please suggest any solutions

Cheers
Venkat

---

### Post by coffeeaddict22 on 2010-02-27
Hi,
Need a bit more info.
Standard network?  ie PC -> Wifi ->router ->modem -> phone line?
If using Gnome, what's the output of ```
nm-tool
``` when you're connected?  Delete the MAC address lines if you like.
How often are you dropping?  Are you using other hardware?

---

### Post by venkyms on 2010-02-28
Hey
Thankyou for the reply, here is the result for nm-tool
the internet connection drops to 0.0Kbps every 2 to 3 minutes and regains, but it doesnt dis connect the connection, only the speed drops.
due to this the websites wont respond during tat time.

I am connected to WIFI modem

NetworkManager Tool

State: connected


** (process:9051): WARNING **: Tried to set deprecated property gsm/band
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:22:19:DF:88:36

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Sapient] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:22:5F:62:2C:EF

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    sommer:          Infra, 00:22:B0:F1:89:49, Freq 2417 MHz, Rate 54 Mb/s, Strength 38 WPA2
    EasyBox-9DC352:  Infra, 00:23:08:9D:C3:B6, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    Hank Moody:      Infra, 00:24:01:B8:76:7D, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA
    NETGEAR:         Infra, 00:22:3F:BF:4A:6A, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    lmmh:            Infra, 00:1F:3F:A0:AE:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    WLAN-434098:     Infra, 00:1A:2A:43:40:0C, Freq 2432 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    HeimNetzwerk:    Infra, 00:15:E9:E1:56:07, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA
    GoMoNet:         Infra, 00:19:5B:B4:2D:11, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
    *Sapient:        Infra, 00:1E:40:DA:80:51, Freq 2452 MHz, Rate 54 Mb/s, Strength 92 WPA
    WLAN-0FB304:     Infra, 00:1A:2A:0F:B3:DE, Freq 2427 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    IPV-GMBH:        Infra, 00:17:9A:6F:E1:CB, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    WLAN-8FD807:     Infra, 00:1D:19:8F:D8:3E, Freq 2442 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.50
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8

Thankyou
Venkat

---

### Post by coffeeaddict22 on 2010-02-28
Hi,
You may have trouble.  If you look at the wireless access points, you're on one that shares a frequency with another separate network.  Consider it like listening to schoolkids talking; if there's two with open mouths in the same group at the same time, chances are nobody can hear either of them.
The solution is to change the channel you're on;  there's 11 possible, and about 7 are being used in your locale.  that assume you can get access to the router, of course; if you can't, you're going to have to talk nicely to someone.

Good luck!

---

### Post by venkyms on 2010-03-01
Hi,

Thankyou for the interesting information :)
i didnt know this and was confussed of the problem,
will change to different channel and monitor my connection

Cheeers
venkat

---

### Post by jtpoole99 on 2010-03-09
I have a similar issue, but I'm only connecting to one access point.  When I'm connected, the connection stays on for a bit and then the speed starts to drop and drop until it says 0B and then I have to disconnect and then connect to the location again.

Does anyone know why this happens?

---

### Post by coffeeaddict22 on 2010-03-10
Hi jtp,
The problem is not what _you're_ connecting to.  It's the crosstalk.  If you look at the output (copied): 
Wireless Access Points (* = current AP)
EasyBox-9DC352: Infra, 00:23:08:9D:C3:B6, **Freq 2412 MHz**, Rate 54 Mb/s, Strength 42 WPA
NETGEAR: Infra, 00:22:3F:BF:4A:6A, **Freq 2412 MHz**, Rate 54 Mb/s, Strength 54
lmmh: Infra, 00:1F:3F:A0:AE:EF, **Freq 2412 MHz**, Rate 54 Mb/s, Strength 51 WPA WPA2

 and so on.  I've deleted a whole lot from the list, but on most channels there are at least 2 separate networks operating, which = trouble.  

If you use either ```
nmtool
``` or ```
sudo iwlist scan
``` you'll see the access points in range, and the channel they are on; if you're on the same channel as another network, problems are more likely.

---

### Post by lz1dsb on 2010-03-12
Thank you [coffeeaddict22]("http://ubuntuforums.org/member.php?u=636580"). So far I was checking this information from my AP, and this is how I'm staying out of trouble. I didn't know about the console tools. They look quite convenient...

Cheers,
Boyan

---

### Post by venkyms on 2010-03-12
Hi Coffeeaddict
i was traveling and was busy couldnt monitor my connection. Now i am India and i have only 1 wifi network arround me and i am connected to it

Even then i am facing the same problem but this time the interval is bit more. Any idea for further diagnoizing the problem?

Thanks & Regards
Venkat

---

### Post by coffeeaddict22 on 2010-03-13
Hi venkyms,
Your DNS might be the problem.  When I ping it(yeah, I know it's google, but not even google is perfect :)  ), there's a heap of packet loss, so I'd be suspicious that's where your problem lies.  Try using your ISP's DNS.

Try having a look at the output of ```
ifconfig
```; it might help as it'll show you if there's packet loss as part of the problem.  Post it back if you need a hand.

Also, I've had router trouble in the past because it heated up- ended up buying a laptop fan pad to sit it on, which has stopped random disconnects (this was at ambient temp of ~25 deg C, which I would have thought was within design capability, but there you go).  It's possible you've got a similiar problem with your card.  Have you checked how hot your LT is running?  There's a downloadable program (yeah, I realise how useful that might be, but you are managing to connect, and it's easier than writing your own) in the Ubuntu software centre called "X sensors" that might help check.

The signal strength is a bit miserable.  Have you tried moving closer to the router to see if that helps?

---

