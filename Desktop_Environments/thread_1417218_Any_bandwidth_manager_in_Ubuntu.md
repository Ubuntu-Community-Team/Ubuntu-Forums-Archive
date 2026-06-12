---
title: "Any bandwidth manager in Ubuntu?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by vksingh on 2010-02-27
Hi,

Can some body tell me about any bandwidth manager in ubuntu?

Thanks,

Vivek

---

### Post by speedygeo on 2010-02-27
In kubuntu we have knemo. I don't know if exists somethings like this!
Do you know? GNOME simplicity = lack of functions!

---

### Post by 2hot6ft2 on 2010-02-27
> **speedygeo said:**
> In kubuntu we have knemo. I don't know if exists somethings like this!
Do you know? GNOME simplicity = lack of functions!
It can be used in gnome as well. I have both KDE and Gnome apps they both work fine.
That's a network "monitor"
Conkey can even do that
> KNemo displays for every network interface an icon in the systray.
Tooltips and an info dialog provide further information about the
interface.  Passive popups inform about interface changes.
A traffic plotter is also integrated.

knemo polls the network interface status every second using the
ifconfig, route and iwconfig tools.

I believe vksingh wants something else since **"bandwidth manager"** was what was asked for.

I've seen something about it when looking thru the "route" functionality but I'm not familiar with an app that has a GUI for bandwidth manipulation.

Perhaps one of these will fill your needs.

[HOWTO improving your internet connection using wondershaper]("http://ubuntuforums.org/showthread.php?t=25911")
or
[MasterShaper - Network traffic under control]("http://www.mastershaper.org/index.php/Main_Page")
or
[trickle]("http://monkey.org/~marius/pages/?page=trickle")

Wondershaper looks interesting the first link above and it's in the repos
> **ubuntu_demon said:**
> I just downgraded my internet connection. I just hate it when a p2p application prevents me from browsing the web fast. So let's do something about it :)

wondershaper is an easy to use traffic shaping script that provides these improvements:

 * Low latency for interactive traffic (and pings) at all times
 * Allow websurfing at reasonable speeds while uploading / downloading
 * Make sure uploads don't hurt downloads
 * Make sure downloads don't hurt uploads

official webpage :
[http://lartc.org/wondershaper](http://lartc.org/wondershaper)

about the ubuntu package :
[http://packages.ubuntu.com/hoary/net/wondershaper](http://packages.ubuntu.com/hoary/net/wondershaper)

/usr/share/doc/wondershaper contains readme files. You might want to read these also.

I'm using firestarter together with wondershaper. Nothing has to be changed to firestarter.

So here we go :
sudo apt-get install wondershaper

use ifconfig to determine which of your networkcards is the one that is connected to your modem (and thus the internet).

$ifconfig

the networkcard that has your normal ip adress is the one (not 192.168.x.x)

Go to a speedtesting website (for example a speedtesting website by your internet provider or [www.speedtest.nl](www.speedtest.nl) if you live in the netherlands) and determine your average upload and download speed. Use these speeds as a guide.

$sudo wondershaper eth1 downspeed upspeed

download a big and uncompressable file while pinging to a fast and stable server on the internet or to your modem and adjust your downspeed until you are satisfied :

$sudo wondershaper eth1 downspeed upspeed

Now do the same with uploading a big and uncompressable file.

You have to tweak these settings a while until you are satisfied. When you are ready you can make these connection settings permanent by :

$ sudo pico /etc/network/interfaces

add these lines under eth1 if eth1 is your internetconnection. Change eth1,upspeed and downspeed to your settings.

```

up /sbin/wondershaper eth1 downspeed upspeed
down /sbin/wondershaper clear eth1

```

And we are done!

edit : removed a bug from interfaces

Also may want to look into using the Quality of Servcie (QoS) function of your router if you're using one and it has it.

---

