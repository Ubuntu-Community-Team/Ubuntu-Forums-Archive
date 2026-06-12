---
title: "Automatic Detect IP Address?"
date: 2006-02-06
forum: Desktop Environments
---

### Post by Postman on 2006-02-06
I had just got my Ubuntu CD and have been using Live CD to try out things before I totally install it in my hard drive.  I was told by my local internet provider that I do not have a static IP and it is constantly released and renewed every four hours.  I was wondering if it was possible to program the Network Settings in the Ubuntu computer for it to Automatically Detect, Release and Renew my IP and other internet info like DNS, DHCP, Gateway, Mask etc.  Windows already does this but I was just curious about this.  Thanks!

Matt T.
Postman

---

### Post by RAOF on 2006-02-06
Yes, and this is the default.  You shouldn't have to do anything to get this working.

---

### Post by Postman on 2006-02-06
Could it be the Live CD affecting it?  And if not, how come it didn't work the first time around and me having to manually input the IP address and other info?   BTW, what does the other option other than Static IP address mean?  I think it's DHCP or something like that.  Does it automatically detect it or something?

---

### Post by dickohead on 2006-02-06
You just need to make sure that your computer is set-up to use DHCP (Automatic IP Address), it will also automatically pick up the required DNS information.

Is your computer plugged directly into your Modem?

---

### Post by Postman on 2006-02-06
My computer is connected from an internal Ethernet card to a Router which then connects it to the phone socket in the wall.  Is setting up the DHCP in the computer in the BIOS setup or in the Ubuntu setup?

---

### Post by dickohead on 2006-02-06
In order to connect to your ISP, your router will need either a Modem inbuilt or attached to it via bridged mode on the port designed for modems. You will then need to have the router setup with the required information to connect to your ISP, username, domain name servers, password etc.

Are you currently on the Internet at home now?

If you are already connected to the Internet at home, and can browse the web in ubuntu, there is nothing else you need to do.

For your info DHCP stands for: Dynamic Host Configuration Protocol, what it does is automatically assigns your machine an IP address upon request. So your computer will be turned on, the network service in ubuntu will start and then broadcast a message stating that it wants an IP address, a DHCP server will then respond giving it the required information, in your case the DHCP server will most likely be your Router, which will get a different IP address for itself from your ISP...

---

### Post by Postman on 2006-02-06
My apologies, I apparantly mistook my DSL modem for my router.  *duh*  So that means my internal Ethernet card (Linksys) is connected to my DSL modem which in turn is connected to my phone jack.  Sorry bout that.  I tried doing a DHCP while inputing the DNS address but I don't think I am inputing the right host address since it has similar digits to the DNS and IP address.  What is the host address hexadecimal or standard numerics?  I'm sorry I am confusing the heck out of you guys but I sure have no clue what to do other than use a static IP address to access the internet and I'd rather not pay extra for that.  I am currently using the internet on Windows and it autodetects the IP address and all and I have to use a static IP address and all to use the internet in Ubuntu Live CD.  Hope this helps.

---

### Post by dickohead on 2006-02-06
Okay.

You have an External Ethernet Modem. This helps.
You currently have an INTERNAL static IP. This helps.
IP Addresses will always be in the format of(excluding IPV6): 123.123.123.123 for example 192.168.1.1 is a common household IP address - note: #HOUSEHOLD ADDRESS.

What your ISP has informed you of is the way that the Modem connects to them. Your Modem asks your ISP for an IP Address, it does this through DHCP, very politely your ISP will say, may I please have your username and password, your modem responds with, why certainly: userx and passx, your ISP then says to your modem, don't be smart jackass, here have an IP address: 123.123.123.123, and a DNS server address: ntp1.isp.com, now goodbye.

And so that's how DHCP works.... sort of.

But that's only good for your modem when connecting to the Internet. For you and your modem to talk through the Ethernet ports on each you will need an Internal IP Address, either set by your Modem via DHCP, which could be something like 192.168.1.100, or it can be static.

To use a static IP Address you will need to give Linux these three things (sometimes only the first two are enough):
IP Address you want: 192.168.1.100 is a good choice
Gateway: Address of your modem (consult manual) but could be in the format of: 10.1.1.1 or 192.168.1.1 (most common)
&
DNS Address: your ISP can give you this, or your modem.

I assume you know how to change or find out your modem settings? If not... you will need to try the web address of your modem (consult manual) into a web browser and enter a username and password (consult manual).

Something to consider is to make sure that REMOTE ACCESS to your modem is DISABLED!

---

### Post by mbeach on 2006-02-06
Some DSL modems have the ability hold your username and password (as provided by your ISP) to make the connection to your ISP.  If that is your case, your modem may be holding your public IP address.  Your ethernet card will likely then pick up a private IP address from your modem (via DHCP).  Your eth card will hold an IP which looks like 192.168.0.1 (or something similar).  

It sounds like to me though that your dsl modem does not maintain the connection to your ISP, and does not act as your DHCP server, in which case Ubuntu will need to make the connection.  I had a heck of a time installing Edubuntu the other day at work without an active network connection ( I was out of ports under my desk and too lazy to run a cable over to the nearest port ).  I suspect your installation is doing the same as what I experienced where during the installation you are being prompted for your primary DNS server ( he's the one which translates [www.ubuntu.com](www.ubuntu.com) to 82.211.81.166 ), and a default gateway (which is your route to the world ), and your IP address.  

I figure you are in the situation where you need to connect via PPPoE in which case you likely don't know your default gateway.  You might need to search for some information on installation with a PPPoE type connection.  There is probably some step during the installation which you can indicate you connect via PPPoE which will allow you to enter your username and password as given to you by your ISP.  I'll take a look and report back anything I find.

---

### Post by mbeach on 2006-02-06
Not sure if this will work from the live CD but it's worth a shot.  You may still be able to get your modem to maintain your connection information in which case, disregard any information I've provided, and go down that route.  Otherwise, go buy a linksys router ( I'm put off Dlink [but make your own decision] for a reason described at: [http://www.dyndns.com/about/company/notify/archives/useragent_block_client10.html](http://www.dyndns.com/about/company/notify/archives/useragent_block_client10.html) ) 

about half way down on
[http://www.planetamd64.com/index.php?showtopic=11465&st=0&p=110784&#](http://www.planetamd64.com/index.php?showtopic=11465&st=0&p=110784&#)
is this little tidbit:

How to create DSL (LAN) connection via PPPoe protocol in Ubuntu - STEP BY STEP

As you might see, Ubuntu does not have a built-in PPPoe configurator visible in GNOME but you can easily create a DSL connection on LAN modem via console.

1.) Open ROOT TERMINAL an run following commands:
2.) pppoeconf (to configure and create connection)
3.) pon dsl-provider (to start a connection manually)
4.) poff (to stop connection manually)
5.) ifconfig ppp0 (last sign is number ZERO :yeah: .... this command will show you the info about traffic and IP...)

:thmbup: MISSION SUCESSFULL :thmbup:


some good writing and reading at:
[http://www.ubuntuforums.org/showthread.php?t=117357&highlight=pppoe](http://www.ubuntuforums.org/showthread.php?t=117357&highlight=pppoe)


guy here with a similar problem, no answer yet:
[http://www.nabble.com/problems-installing-Breezy-from-CD-t812547.html](http://www.nabble.com/problems-installing-Breezy-from-CD-t812547.html)

---

### Post by Postman on 2006-02-07
Well I tried using the 'pon dsl-provider' option and it just gives me abunch of random characters and stops on the middle of it and I have to restart the Terminal.  Then I tried the 'pppoeconf' and it would scan for an 'Access Concentrator' but in the end it would tell me that it could get one from the server and that the problem may lie in the cords (?) or another device using PPP.  Any more suggestions on what to do next or is this a Live CD fluke?

---

