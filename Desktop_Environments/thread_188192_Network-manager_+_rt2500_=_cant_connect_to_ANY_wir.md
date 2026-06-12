---
title: "Network-manager + rt2500 = cant connect to ANY wireless :\"
date: 2006-06-03
forum: Desktop Environments
---

### Post by LaMaH on 2006-06-03
hi..

i just installed Ubuntu 6.06 on my laptop, and got ATi drivers working in the first try :D

anyway, now im trying with the wireless network, but it wont work for #¤"" :(
i installed network-manager and it also find 3 networks (as my laptop did with windows) only thing is i cant connect to any of them :\

the one is without any encryption, the two others and with WPA (64bit and 128bit)

but it tries to connect, but after around a minute it just stops and tells me there isnt any connection

anyone got an idea what to do?

---

### Post by Dudesmen on 2006-06-03
Bump! :KS :) :( :p :mad: :confused: ;) :D

---

### Post by Dudesmen on 2006-06-03
Lets bump it Lamah!

---

### Post by LaMaH on 2006-06-03
you got the same problem?

---

### Post by Dudesmen on 2006-06-03
Yeah it is pretty annoying.
I have tried for a couple of days now, and I have just went through the whole Internet to find a solution, but I can't

Please help me man 

](*,)

---

### Post by LaMaH on 2006-06-03
little update..

i just reinstalled ubuntu in the hopes that that might help, but noooo..

reinstalled ubuntu and installed network manager - it finds the network perfectly, i choose 64/128bit HEX (its 64bit encryption with a hex key) - write the code and pick Open System like its set in the router..

it tries and tries to logon to it, but with no success..
i tried my neighbours non encrypted network - with the same outcome..

its a Ralink RT2500 chip, and according to Ubuntu it should be working flawlessly - but i aint due to some freak accident..

someone - please help, its totaly anoying! :(

---

### Post by ariel on 2006-06-03
I had a similar problem back in the Breezy days. My solution at that time was: NDISWrapper, and the windows driver (mine is a linksys pci card).

With dapper I haven't had problems so long, but for a couple of connection cuts during the last 3 days. I guess if the connection cuts reappear i will go back to the ndiswrapper solution.

good luck!

---

### Post by LaMaH on 2006-06-03
c

---

### Post by LaMaH on 2006-06-03
could you perhaps tell how the ndiswrapper solution is working? :)

because this arent working for s#"% :evil:

---

### Post by Dudesmen on 2006-06-03
Lamah

U gotta relax man, it is only a computer!
We won't tolerate #%" as you're using. ](*,) 

Please respect it :-k

---

### Post by Zotova on 2006-06-04
Ok I have a rt2500 based card so I may be of some help.

In Ubuntu (Gnome) I simply went to Networking under the system settings. My card was shown as ra0. You then just enter your settings - if you use a static ip make sure you enter your gateway.

Also for wep hexadecimal is the only setting which allows me to connect - this may be down to what type of router you are trying to connect too and how it is setup.

Also worth noting - in Breezy I had issues with connecting when my Ethernet was still turned on. If you don't need it simply click properties on eth0 (or whatever it is called on your system) and untick the 'Enable this connection' box and then ok the window. Now try and activate your wireless connection.

Failing that install the rt2500 package via synaptics (the proper one not the add/remove thing). Then use the rt2500 configuration tool - I have always had limited success with it, however it may work for you.

Last last resort: install kwirelessmonitor - yes it is a KDE app, however in KDE this was the only program which would connect my ra0 card to my network and allow me to access the internet - so if you've had no luck then it may be worth trying.

Finally don't bother with ndiswrapper, from my experience it is buggy and often stops working when it wants - use the native rt2500 linux drivers if you can.

Hope some of that is of help.

---

### Post by Dudesmen on 2006-06-04
That didn't help at all.

Can you please be more specific and tell us how we do those things?

Go for it dude!

---

### Post by Nasso on 2006-06-04
i have the exact same problem. has anyone managed to get it working yet?

---

### Post by ariel on 2006-06-04
Just check the NDISWrapper documentation: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)


Note that you don't need to download sources and recompile, just install the ndiswrapper package from synaptics, so you can start from here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

You will need the windows driver for the card and extract a few files from it, it's not difficult.

Now I had to use this with Breezy, with Dapper the supplied ralink driver seems to  bo working fine (I touch wood here :-). In Breezy, my problem was that after a few hours of use, the IP connection turned sluggish, instead of typically getting 2/3Mbps downloads I started to get 50Kbps, and web browsing was a pain. NDISwrapper solved my problem and I used if for 7 months or so with zero problems.

---

### Post by Zotova on 2006-06-04
There is no point using ndiswrapper as there is a perfectly good Linux driver.

More detailed guide:

Firstly open the Network settings. Depending on how you have ubuntu setup this may be different - on my system it is system > administration > networking

You should have this screen (excluding my different theme):

[img]http://www.shanghai.me.uk/ubuntu/1.jpg[/img]

Of course you may have a few different icons and names depending on your systems hardware. However you should have the ra0 option (top on the screenshot). Left click on that and then click properties:

[img]http://www.shanghai.me.uk/ubuntu/2.jpg[/img]

Change the essid to whatever your routers name is and enter your own wep key in - btw if your using wpa I cannot help as I do not use wpa myself. I personally found only hexadecimal works with my router. Use trial and error if asci doesn't work then try hexadecimal or viceversa.

I use a static ip address - if you don't then just select dhcp and that should be it. Otherwise your window should look somewhat like the screenshot above. Once done click ok.

If you have any other network devices e.g. a ethernet card like myself I suggest you disable them at least until we get wireless working. To do that click on the relevant section (in the first screenshot it would be the second listing, of course this depends on your laptop). Once you've highlighted the card click properties and untick 'Enable this connection' and then ok the window.

All things being good you should now be able to highlight the ra0 entry and click activate. Your card should connect.

If it does but you have no internet connection do the following:

[img]http://www.shanghai.me.uk/ubuntu/3.jpg[/img]

^ This should be the same as whatever your routers gateway is - I think this bit is only if you use a static ip address, if you use dhcp I think this is all taken care for you but I'm not 100% sure. 

---
If you have no joy with the above then I'll type up the other things I said in my previous post in more detail. Also if you have aim or msn I'm happy to guide you through it via that or give you a helping hand via vnc.

---

### Post by einKI on 2006-06-04
Hi

i have the same problem here.
Connecting with "System->Administration->Networking" works perfect.
Wifi-radar ([http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)) also works.

But when I use the gnome-network-manager No signal strength informations
are displayed in the drop down list and when I try to connect to my home
network it doesnt work.

I tried all tricks I know but have to go back to wifi-radar for now.

by
Lukas

---

### Post by LaMaH on 2006-06-06
hi again - just installed ubuntu once again, and installed wifi-radar.. and noticed something very very strange.

when i connect to my network it says *Found IP* and then its done and should work, but the ip it finds is 127.0.0.1 wich is the loopback..

perhaps it is the same thing happening to others? that the RT2500 card somehow screws up and instead of getting the IP the router designates to it, it get the loopback's ip..

hmm, could anyone have a look at that? :)

---

### Post by eeclark on 2006-06-06
I was able to install network-manager for gnome but never ever got it to work.
Using 2915 Intel. It always says no connections.
I have done all the tweaks to the conf files and the network config files, but no luck.
Always keep going back to the regular network monitor which does not provide that "Just Works" feeling.

---

### Post by twotonz on 2006-06-07
Hi,
Same problems here, but only since today. 
What's changed since yesterday? Well, ermm, I had noticed that the kernel was giving out a message along the tunes of "using somesort of makedo wireless - driver in proc....please see to it" (a very vague translation, I might add), sooooo, I had noticed that there was now an official driver as paket to download for the rt2500 chip based cards, and guess what, I downloaded it, and promptly installed it. 
Since exactly this point, I can see networks without problems, get the whole info's on the different ap's that are available, and thats it, I just cannot seem to get an IP assigned. I have also tried a manual connection, to no avail. 
My question is, if I just remove the packet, will the network revert to its former state? I think I can guess the answer allready.....
I know it's not a lot of help, to tell the truth I'm watching this thread in the hope that some genius out there can give us poor souls here a push in the right direction......anybody.......pleeeeeese.

love & peace to all
anthony

---

### Post by LaMaH on 2006-06-07
dunno if this is allowed, but -


BUMP

(someone out there must know SOMETHING about this problem :\ - cus everything ive tried and goten told to do (on this board and on IRC plus by some friends) havent worked. and it just sucks.. the whole idea of wifi kinda falls to the ground if it dont work :()

---

### Post by Zotova on 2006-06-08
Can you post your /etc/network/interfaces please?

Its a config file - you should be able to open it with gedit and then post it on here.

---

### Post by twotonz on 2006-06-08
Hallo,
I'm not sure who's interfaces you want, but anyway here's mine, along with iwconfig  & ifconfig outputs.......

~$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"gate5"
          Mode:Managed  Frequency=2.447 GHz  Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-94 dBm  Noise level:-220 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

ifconfig
lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:1068 (1.0 KiB)  TX bytes:1068 (1.0 KiB)

ra0       Protokoll:Ethernet  Hardware Adresse 00:11:50:8F:46:00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44348 errors:107 dropped:107 overruns:0 carrier:0
          Kollisionen:20 Sendewarteschlangenlänge:1000
          RX bytes:7280 (7.1 KiB)  TX bytes:1998880 (1.9 MiB)
          Interrupt:177


# interfaces:

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto ra0
iface ra0 inet dhcp
wireless-essid gate5

auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1



I have compared everything with this rechner (very simular, both dells, except this one has a TI acx wlan card), & everything looks honky-dory. I also tried replacing the rt2500 driver (I think), still no luck. One thing I have noticed though, the rt2500 tries to connect using the netzwerkmaske (sorry forgot what it is called in english) 255.255.255.255 - shouldn't this be 255.255.255.0?

Anyway thanks for your time, it's much appreciated.

Love & Peace
anthony

---

### Post by eeclark on 2006-06-08
Here is my interface file (the one I use when trying Network Manager):
```

auto lo
iface lo inet loopback


```

---

### Post by twotonz on 2006-06-08
Hallo, me again,
Very strange, I am now getting an IP addresse from my neighbours router. What have I changed? Well not a lot. As I was pasting & checking my earlier post I had noticed that in the Network-settings (dapper-kde) that I had an entry under "known named computer" (I think this is the english translation, in german it reads "Namentlich bekannte Rechner") called 127.0.1.1 - ubuntu, as this entry is not present on my other computer (the one that works with wlan), so I removed it. I then spent a while browsing the forums, went back to the Computer with the rt2500 card in, had a look at the settings again........and low & behold I have an IP, it's just now that the web-browser hangs on "resolving host www.google.de"  instead of the default page "no connection with the network -please try again". Soo, I guess now my problem is with dns. Can someone give me a few pointers to how I can check to see if dns is working? This is something I have never had to deal with before, so I do not even know where I start.

Love & Peace
anthony

****edit*****
It gets stanger, I started up Firestarter, to see if any traffic was passing through the wlan. I then put in the address of the router under "allow connections from.." BASTA, I now have internet, using the rt2500 card. (strange because I never made this rule before, and still got a connection)

---

### Post by twotonz on 2006-06-08
Hope this is ok, but I forgot something...........
#eedark
Look at my interfaces, and then look at yours.......do you notice something?
Ok, eth0 you can ignore, unless you also have a nic as well as your wlan. You only have loopback listed (localhost etc), but no other interface.
Try running
```
lspci
```
and then see if you have a entry along the lines of
```
"0000:00:**:* Network controller:RaLink RT2500 802.11 Cardbus reference
```

If you do, then your problems can proberly be solved, if not, you proberly do not have any drivers installed, in which case you are proberly going to have to download the missing packages from a computer connected to the internet, the packet is called simply rt2500, you could check with apt whether you have it allready. 
So now I shall be busy setting up wine on the other box, but I shall keep an eye on this thread, in case you need more help (I would like to mention though, that I am defantly not a profi - so please check all suggestions beforehand)

Love & Peace
anthony

---

### Post by eeclark on 2006-06-08
[QUOTE=twotonz]Hope this is ok, but I forgot something...........
#eeclark
Look at my interfaces, and then look at yours.......do you notice something?
Ok, eth0 you can ignore, unless you also have a nic as well as your wlan. You only have loopback listed (localhost etc), but no other interface.
Try running
```
lspci
```
and then see if you have a entry along the lines of
```
"0000:00:**:* Network controller:RaLink RT2500 802.11 Cardbus reference
```

If you do, then your problems can proberly be solved, if not, you proberly do not have any drivers installed, in which case you are proberly going to have to download the missing packages from a computer connected to the internet, the packet is called simply rt2500, you could check with apt whether you have it allready. 
So now I shall be busy setting up wine on the other box, but I shall keep an eye on this thread, in case you need more help (I would like to mention though, that I am defantly not a profi - so please check all suggestions beforehand)

Love & Peace
anthony[/QUOTE]

I configured my interfaces as per the instructions from Network Manager. It states that only loopback should be in the interfaces file.

My network card works fine if I do not use Network Manager. The problem is since it is a laptop and I am mobile, I always have to use the gnome-network-preferences to config the new ssid.  It is not very effective since I need to know the SSID.  I was hoping Network Manager would allow me to view available networks.

Again, the reason only lo is in that file is because I read that NetworkManager needs to be the only app configuring the device.

Thanks for the feedback though.

---

### Post by twotonz on 2006-06-08
Hallo,
If you are not having any luck with the desktop tools, go back to the console and type....
```
iwlist ra0 scanning
```

you should have a list of all AP's, you can then use these details to configure the network settings tool, or you can type in by hand still using the console, type in 
```
man iwconfig
```
to give all the options, for example, to set the essid
```
iwconfig ra0 essid "the essid you want to connect to"
```

This is of course assuming the name of your card is ra0, and I am sorry, but I am still not convinced that the card shouldn't show up in interfaces, but I could be wrong.

By the way, the wlan using the rt2500 has given up again, still hanging on resolving host...... how boring!

Love & Peace
anthony

---

### Post by twotonz on 2006-06-10
# Zotova,
I guess the interfaces, didn't bring any idea's??

---

### Post by ariel on 2006-06-11
Hi, just to report that in Dapper I ran into problems with the native rt2500 driver, loosing the wireless connection every two days  or so. 

I had to replace it with ndiswrapper + vendor windows drivers. I had to do this long ago with Breezy as well and back then I wrote a procedure, here's the updated procedure for Dapper:


[LIST]
[*]install the graphical frontend (will also install the base package) sudo apt-get install ndisgtk[/LIST][LIST]
[*]copy the Rt2500.INF, rt2500.cat, rt2500.sys files to a local folder (e.g., /opt/Ralink2500-driver); in my case I found these files inside the Linksys official driver package[/LIST][LIST]
[*]blacklist the old native driver that comes with Ubuntu: sudo gedit /etc/modprobe.d/blacklist; add an "rt2500" line[/LIST][LIST]
[*]stop the native driver (deactivate interface ra0) and remove the module from memory: sudo modprobe -r rt2500[/LIST][LIST]
[*]run System -> Administration -> Windows Wireless Drivers and install the driver (it will prompt you for the .inf file)[/LIST][LIST]
[*]reboot; an interface with name ra0 should still show up in ifconfig[/LIST][LIST]
[*]Optional: with lshw -C network : verify that the wireless interface is using the "ndiswrapper" driver[/LIST][LIST]
[*]Use System > Administration > Networking and configure your WEP parameters. Or alternatively, go directly to /etc/network/interfaces and set them up manuall (will require an extra reboot)[/LIST]        For a static IP and 128 bits WEP:

        iface ra0 inet static 
        address 192.168.1.111
        netmask 255.255.255.0 
        gateway 192.168.1.1 
        wireless-essid YOURNET 
        wireless-key 11111111111111111111111111 
        wireless-channel  6 
        auto ra0


        For WPA, your /etc/network/interfaces should look like the following (I did not test this with dapper, this is back from the breezy days):

        iface ra0 inet static 
            pre-up iwconfig ra0 essid YOURNET 
            pre-up iwconfig ra0 mode managed 
            pre-up iwpriv ra0 set Channel=6 
            pre-up iwpriv ra0 set AuthMode=WPAPSK 
            pre-up iwpriv ra0 set EncrypType=AES 
            pre-up iwpriv ra0 set WPAPSK="yourPasswordHerePlease" 
            pre-up iwpriv ra0 set TxRate=0 
            address 192.168.1.111 
            netmask 255.255.255.0 
            gateway 192.168.1.1

My hardware is: PCI card Wireless LAN Linksys WMP54G

Hope this helps

---

### Post by twotonz on 2006-06-12
#Ariel,
Thanks for your tip. I was trying to avoid the ndiswrapper, and get this thing going using linux drivers. I am now at the point of giving up, and shall try your suggestion when I get back from work.
Your post has also cleared up a few other things that were confusing me a bit, thanks again. Just to be sure, as I cannot use apt-get, I have to download on another computer and then install "by hand" the missing packets. So I need, ndiswrapper, ndisgtk, and ndiswrapper-modules, right? Or can I leave the last one out? (hope there are not too many dependancies!).
Thanks again for your time

Love & Peace
anthony

EDIT********
OK, Ariel, I'm now writing this using the rt2500 :-). Thanks for the instructions, just had to do a "sudo modprobe ndiswrapper" to get the thing going properly. What about the rest of you lot having problems, anyone else having success with Ariels small "Howto"?

---

### Post by ihavenoname on 2006-06-12
NetworkManager does not support the rtx00 drivers or the rt2500 drivers, at least not yet, your better off using Ndiswrapper, it's what I do, yet for some reason on Dapper using ndiswrapper I get disconnected randomly and it takes the longest time to get back, usually it forces me to restart (w/ and w/o NetworkManager)

[http://www.redhat.com/magazine/003jan05/features/networkmanager/#cards](http://www.redhat.com/magazine/003jan05/features/networkmanager/#cards)

---

### Post by bionnaki on 2006-06-13
please read this thread: [http://ubuntuforums.org/showthread.php?t=161376](http://ubuntuforums.org/showthread.php?t=161376)

the wmp54g uses the rt2500 driver and I imagine that the solution will work with any card that uses this driver. try it out.

no need for ndiswrapper
you just have to modify your /etc/network/interfaces file
+ add dns info to your network manager.

that's it, really

---

### Post by ihavenoname on 2006-06-13
hmm, intresting I will try that as I have been having problems with the internet disconnected and failing to reconnect unless I restart (wheather I am using NetworkManager or not). It's really causing me alot of problems. 

Do you think this work with the rt2570 drivers?

---

### Post by bionnaki on 2006-06-13
no idea

---

### Post by ihavenoname on 2006-06-13
nvm, my Ubuntu has become instable (everything seems to point to the wifi problem)

read more here
[http://ubuntuforums.org/showthread.php?t=196201](http://ubuntuforums.org/showthread.php?t=196201)

---

### Post by meusmetus on 2006-06-14
[QUOTE=LaMaH]little update..


it finds the network perfectly, i choose 64/128bit HEX (its 64bit encryption with a hex key) - write the code and pick Open System like its set in the router..

Hey, I have exactly same problem with a different card (Broadcom BCM4306 802.22b/g).

After about 10 times it did connect and it worked until next reboot and then it did not want to connect again. It suddenly connects for no obvious reason at all. My card could connect when WEP was turned off on the access point. When I turn WEP back on it did not want to connect for a while, but then it finally did.

---

### Post by NeoChaosX on 2006-06-18
ihavenoname is right. NetworkManager does not support the RT2x00 drivers. [This wiki page](http://live.gnome.org/NetworkManagerHardware) on gnome.org explains why.

---

### Post by SwaroopKunduru on 2006-06-18
Hi All,

I have same problem.

[http://ubuntuforums.org/showthread.php?t=199245](http://ubuntuforums.org/showthread.php?t=199245)

Regards,

Swaroop Kunduru.

---

### Post by silex on 2006-06-19
I have a card that uses the rt2500 driver (a Zonet something or other) and had these same problems.  Having found that network-manager doesn't support the rt2500, I ended up using ndiswrapper with only the problem of not having any signal strength ability (e.g. networks either had 0% or 100% strength) in network-manager.  I have not tried wifi-radar yet.

Once I have a bit of spare time I might try compiling the newest version of the rt2500 driver from source and see what happens with that and wifi-radar.

---

