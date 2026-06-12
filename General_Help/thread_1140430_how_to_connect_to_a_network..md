---
title: "how to connect to a network."
date: 2009-04-27
forum: General Help
---

### Post by dragonbeast25 on 2009-04-27
1 - my router does not pick up ubuntu but it picks up on XP

2 - It dosn't connect with the manager, ive done everything. Edit.

Information.

- Im running a speed touch home modem > D-link router ( WB-1310 ) to PC>

Highspeed.

Thanks and please reply.

---

### Post by 3Miro on 2009-04-27
How do you connect, wireless/wired, static IP or DHCP?

---

### Post by RedSingularity on 2009-04-27
When you get a chance type "lspci" in the terminal and post the output.

---

### Post by dragonbeast25 on 2009-04-27
> **Shadow121 said:**
> When you get a chance type "lspci" in the terminal and post the output.
Bump. Will have the results in one minute.

---

### Post by dragonbeast25 on 2009-04-27
> **Shadow121 said:**
> When you get a chance type "lspci" in the terminal and post the output.
Results"
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



And well in XP my router remebers my password username PPPoP so i think its DCHP, Thanks. Reply soon.

---

### Post by dragonbeast25 on 2009-04-27
> **Shadow121 said:**
> When you get a chance type "lspci" in the terminal and post the output.

Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump !!!

---

### Post by dragonbeast25 on 2009-04-28
Bump !

---

### Post by halovivek on 2009-04-28
are you using wireless or wired router?
if wireless double click the lan icon and select the new wireless router and get connected. if wired check the ip address and lan settings and give it.

---

### Post by dragonbeast25 on 2009-04-28
> **halovivek said:**
> are you using wireless or wired router?
if wireless double click the lan icon and select the new wireless router and get connected. if wired check the ip address and lan settings and give it.
The thing is i my router ip is 192.168.0.1 i no all the ips but when i drop down manual i fill all info in and it wont let me apply, also i use my itouch to get BBSID mac adress and i change it then the whole thing changes, and i cant see my new network under wired connection?

---

### Post by dragonbeast25 on 2009-04-28
Bump plz reply

---

### Post by RedSingularity on 2009-04-28
Ok so your wired connection is not working correct?  Let me see if i can find some drivers.

---

### Post by RedSingularity on 2009-04-28
Oh and post "ifconfiig" from terminal.

---

### Post by dragonbeast25 on 2009-04-28
ok 1 sec

---

### Post by dragonbeast25 on 2009-04-28
REsults for : IfConfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:1a:e5:cc  
          inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by freonchill on 2009-04-28
> **dragonbeast25 said:**
> Results"
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



And well in XP my router remebers my password username PPPoP so i think its DCHP, Thanks. Reply soon.

i dont see a wireless device
typically if you are using a router (the d-link) you should have it configured to do the pppoe connection and then any wired device behind it will just be NAT dhcp.

---

### Post by dragonbeast25 on 2009-04-28
BuMP !!

---

### Post by dragonbeast25 on 2009-04-28
For the Last Time:

ITS WIRED NOT WIRELESS JUST ITS CONNECTED TO A ROUTER

---

### Post by freonchill on 2009-04-28
i told you what your setup and whats should be going on

[SIZE="7"]QUIT BUMPING[/SIZE]

without asking a further question/clarification

do you have your router configured appropriately?
e.g.

modem in bridge mode
router with pppoe configured WAN
standard NAT dhcp for wired client machines (e.g. yours)

---

### Post by dragonbeast25 on 2009-04-28
WEll when im on windows its already connected i no my password and username ive put them in also no help. And yeah my router remembers everything

---

### Post by dragonbeast25 on 2009-04-28
If anything its not configured in ubuntu i have no idea, but in xp it works fine. And its configured in xp.

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump i posted my info u asked they"re yeah go ty !

---

### Post by dragonbeast25 on 2009-04-28
Bump !

---

### Post by freonchill on 2009-04-28
you never said whether you have your pppoe configured on your router.

whats this password you are talking about that windows knows but if you put it in ubuntu it doesnt change it?

if you have it done properly, (as i addressed before, and you ignored)

modem should be in bridge mode
router should be configured pppoe
then windows and ubuntu can both use dhcp with no configuration, password, etc.

---

### Post by dragonbeast25 on 2009-04-28
Can you tell me how to do that stuff on ubuntu? Bridge it and everything??

---

### Post by dragonbeast25 on 2009-04-28
Bump !

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by dragonbeast25 on 2009-04-28
Bump bump and bump !

---

### Post by dragonbeast25 on 2009-04-28
Bump

---

### Post by max_power on 2009-04-28
im almost tempted to NOT help you because of all the "bumps"

if you want help you need to explain what hardware you are using, wired or wireless connection, are you using a router?

What Ubuntu release are you using?

---

### Post by halovivek on 2009-04-29
check this [link]("https://help.ubuntu.com/8.04/installation-guide/powerpc/pppoe.html")
and stop bumping

---

### Post by dragonbeast25 on 2009-04-29
i dont no where to enter those promts, and im using a ethernet modem high speed to router DLINK witch connects auto on windows, and im running ubuntu 9.04

---

### Post by OzOle on 2009-04-29
Hi Dragon,

You certainly have a bit of a problem, but the problem is no doubt one of communication. I'm no networking expert, but it is clear to me that the guys want to help you and therefore ask some questions which I don't think you understand. Also, you keep referring to the fact that your XP installation works. That's great because that proves that your equipment is working both your modem/router and your computer with its ethernet connection.

So, to get it working in Ubuntu 9.04 I suggest you ask the network gurus one question at the time, get an answer and try that out. If that doesn't work, come back with a comment about what happened and see what the next suggestion is. Remember, if they ask you to do something and you don't understand what they are asking, simply come back and say so, we are not all experts. Sometimes the gurus ask us ordinary guys a question and think we understand the question but if we don't then there is no shame in admitting that.

Just my suggestions, good luck with your network, I'm sure you will get it to work.

Cheers,

OzOle

---

### Post by muhannadfa on 2009-04-29
hey Guys, memebers & moderators
u're asking him stop bumping
till now u asked the same question with no further help
[SIZE="6"][COLOR="Red"]Wired or Wireless > WIRED[/COLOR][/SIZE]
[COLOR="Red"][SIZE="6"]OS> ubuntu 9.04 (buggy) (for most of users)[/SIZE][/COLOR]
[COLOR="Red"][SIZE="6"]any further help > Nothing[/SIZE][/COLOR]
[SIZE="6"][COLOR="Red"]all you've done > Stop bumping
my help to u dragonbeast25 > keep Bumping
------------------------------------------
when u release such a buggy ubuntu > u have to be ready not sit htere and say stop, don't[/COLOR][/SIZE]

---

### Post by muhannadfa on 2009-04-29
> Hi Dragon,

You certainly have a bit of a problem, but the problem is no doubt one of communication. I'm no networking expert, but it is clear to me that the guys want to help you and therefore ask some questions which I don't think you understand. Also, you keep referring to the fact that your XP installation works. That's great because that proves that your equipment is working both your modem/router and your computer with its ethernet connection.

So, to get it working in Ubuntu 9.04 I suggest you ask the network gurus one question at the time, get an answer and try that out. If that doesn't work, come back with a comment about what happened and see what the next suggestion is. Remember, if they ask you to do something and you don't understand what they are asking, simply come back and say so, we are not all experts. Sometimes the gurus ask us ordinary guys a question and think we understand the question but if we don't then there is no shame in admitting that.

Just my suggestions, good luck with your network, I'm sure you will get it to work.

Cheers,

OzOle
1st > thanks
2nd > this is of no help
3rd > Bump

---

### Post by OzOle on 2009-04-29
Hey muhannadfa,

You sound a bit angry. It sounds like you too are having networking problems with Ubuntu 9.04, that's not encouraging. I myself have a very puzzling problem with wireless networking. Before I upgraded from version 8.10 I had no problems with wireless networking, and I should mention that I have no problems at all with wired networking through the ethernet port. But it is strange that something which was working in the previous version now has problems.

I suppose we have to be a little patient because we need to remember that most of the people who work on bringing us this FREE operating system, work in their own time and receive no pay for their work.

I hope you get your working. As a matter of interest, how were you able to post your message if you could not get on the Internet?

All the best,

OzOle

---

### Post by muhannadfa on 2009-04-29
mmmmmmm
good question actually
do u think that there is no other OS out there 
i'm connected using XPSp3
wired connection
:)

---

### Post by brunogirin on 2009-04-29
OK, so dragonbeast25, to summarise your problem, here is what I have understood of it. Please correct me if I'm wrong.

You have a D-Link router that provides broadband: can you confirm the exact model of that router so that I can have a look at its details please?

You connect to the router using a wired Ethernet connection. This works fine in XP but not with Ubuntu 9.04.

The output you provided for ifconfig shows that you have an IPv6 address but no IPv4 address. That may or may not be related but just to confirm, can you start XP, open a command prompt and post the result of the following command please?

```
ipconfig /all
```

---

### Post by OzOle on 2009-04-29
Hi muhannadfa,

Is your name dragonbeast25? That's who I was writing to.

Actually, if you don't understand the nature of FREE software and FREE community support, then I would certainly suggest you go back to using your XP installation and if you have a problem with that, then you can always rely on Microsoft for excellent support.

---

### Post by dragonbeast25 on 2009-04-29
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Desktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : TRENDnet, TE100-PCIWN  32-bit 10/100
Mbps PCI ADAPTER
        Physical Address. . . . . . . . . : 00-11-09-1A-E5-CC
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Wednesday, April 29, 2009 6:12:28 AM

        Lease Expires . . . . . . . . . . : Wednesday, May 06, 2009 6:12:28 AM

---

### Post by muhannadfa on 2009-04-29
> **OzOle said:**
> Hi muhannadfa,

Is your name dragonbeast25? That's who I was writing to.

Actually, if you don't understand the nature of FREE software and FREE community support, then I would certainly suggest you go back to using your XP installation and if you have a problem with that, then you can always rely on Microsoft for excellent support.
seems like u figure it out lately dear
look at this :confused:
> 
Hey [SIZE="6"]muhannadfa[/SIZE],

You sound a bit angry. It sounds like you too are having networking problems with Ubuntu 9.04, that's not encouraging. I myself have a very puzzling problem with wireless networking. Before I upgraded from version 8.10 I had no problems with wireless networking, and I should mention that I have no problems at all with wired networking through the ethernet port. But it is strange that something which was working in the previous version now has problems.

I suppose we have to be a little patient because we need to remember that most of the people who work on bringing us this FREE operating system, work in their own time and receive no pay for their work.

[SIZE="6"]I hope you get your working. As a matter of interest, how were you able to post your message if you could not get on the Internet?[/SIZE]

All the best,

OzOle
i think when u work with free stuff u'll end up like this, amenezia 
bye bye
dragon hope they help u
even crap like vista is better than new jaunty
--------------------------
8.10 was great, i'll think to go back to it

---

### Post by lisati on 2009-04-29
Now, now, children, let's get on with seeing if we can help dragonbest25!

dargonbeast25: What model d-link router/modem are you using? We might be able to look it up and make suggestions on how to get it working with Ubuntu.

---

### Post by dragonbeast25 on 2009-04-29
Thanks.

I have a WBR-1310 D-link router and a Home Speed Touch modem

[IMG]http://www.alcadis.nl/img/products/en/large/thomson_speedtouch_608_4poorts_voorkant_500x375.jpg[/IMG]
^ Like that but sorta differnce.

And router

[IMG]http://store.redbarncomputers.com/mmRBC/Images/WBR1310.jpg[/IMG]

---

### Post by OzOle on 2009-04-29
No amnesia there, dear muhannadfa,

I first addressed Dragon pointing out that if he wanted help then there were certain point he needed to remember. The same of course goes for you too. But instead of letting Dragon reply to my post you broke in with your somewhat curt message.

Anyway, I don't really care whether you run XP or Ubuntu or BSD or Mac OS-X or an interely different operating system! You are a free moral agent, so you can run whichever operating system you like and can afford.

I wish you all the best.

Happy computing!

---

### Post by dragonbeast25 on 2009-04-29
Thanks for those tips. But look at the router and modem picture above ur post

---

### Post by OzOle on 2009-04-29
Dear lisati,

Are you calling me a child? Thank you for that, I'm honored!
I'm 67 year old and I have worked with computer software for over 40 years but I still don't consider myself an expert. I have been long enough in the game to know that nobody knows everything.

Thank you for your willingness to assist Dragon and others.

Cheers fromt the other side of the Tasman,

Ole

---

### Post by brunogirin on 2009-04-29
@dragonbeast25: I suspect the D-Link router is connected to the SpeedTouch modem through a cable and you then connect your PC to the D-Link router?

@lisati: here is the output of ifconfig on Jaunty:

> 
REsults for : IfConfig
eth0 Link encap:Ethernet HWaddr 00:11:09:1a:e5:cc
inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xc800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


and the output of ipconfig on XP

> **dragonbeast25 said:**
> Windows IP Configuration

        Host Name . . . . . . . . . . . . : Desktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : TRENDnet, TE100-PCIWN  32-bit 10/100
Mbps PCI ADAPTER
        Physical Address. . . . . . . . . : 00-11-09-1A-E5-CC
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Wednesday, April 29, 2009 6:12:28 AM

        Lease Expires . . . . . . . . . . : Wednesday, May 06, 2009 6:12:28 AM

So it looks like XP properly acquires an IPv4 address through DHCP whereas Jaunty only acquires an IPv6 address. Where do we go from here?

---

### Post by dragonbeast25 on 2009-04-29
That dosnt sound good :(. I love ubuntu if i get connected then ill be so happy... Thx for all the support guys.

---

### Post by lisati on 2009-04-29
> **dragonbeast25 said:**
> Results"
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
**01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**



And well in XP my router remebers my password username PPPoP so i think its DCHP, Thanks. Reply soon.
> **dragonbeast25 said:**
> Thanks.

I have a WBR-1310 D-link router and a Home Speed Touch modem

^ Like that but sorta differnce.

And router



OK - the combination seems to be working with Windows, right? so there is a possibility of getting things working with Ubuntu.

Your ethernet card seems to be the same as the one in the laptop I'm using right now, at least as far as what the lspci command is concerned. On my machine it worked "out of the box" I'm a bit baffled, and would appreciate suggestions from other forum users.


EDIT: I did have Jaunty on this machine for a while, (I currenrly have 8.10 on it) and noticed that the network manager reported "network unmanaged". Please stand by......
EDIT 2: I have Ubuntu Studio v9.04 on another machine, where lspci reports the same ethernet card. I've temporarily disabled wireless on that machine, and internet seems to be working. For the life of me I can't remember where to look for settings....... It's after midnight and my concentration is beginning to wander.....

---

### Post by dragonbeast25 on 2009-04-29
Ok first. Ill supply you with more information b4 i go to school ill be on another half hour. Well on xp what i did is, hooked my modem in router then router to pc I installed the driver of WBR-1310 in xp and i saved my password from they're. now every time i dont have to connect using my password and username Not dial up, but i have to , now my router remebers my PPPoP i pretty sure. But i heard i have to bridge them, My connections show:
Internet Gateway:
Connected

LAN- or highspeed internet
Local area connection

Dont no if that works but yeah

P.S im using 9.04

One more thing, i have not installed it yet, im on xp. I try option try without making any changes to computer

---

### Post by dragonbeast25 on 2009-04-29
Ubuntu is far more complicated then xp is. What if a bridge them and make a gateway like my xp machine?

---

### Post by brunogirin on 2009-04-29
> **dragonbeast25 said:**
> Ok first. Ill supply you with more information b4 i go to school ill be on another half hour. Well on xp what i did is, hooked my modem in router then router to pc I installed the driver of WBR-1310 in xp and i saved my password from they're. now every time i dont have to connect using my password and username Not dial up, but i have to , now my router remebers my PPPoP i pretty sure.

OK, that's the bit that stumps me: if it's a standard router, you should be able to connect to it out of the box, without any driver, even on XP. So I'm not sure what the XP driver does.

To move things forwards, under XP, can you go to the router's management page by opening a browser and going to [http://192.168.0.1/](http://192.168.0.1/) please? Then post a screenshot here.

I'm not sure what you mean by that:

> What if a bridge them and make a gateway like my xp machine?

---

### Post by dragonbeast25 on 2009-04-29
Here

[IMG]http://img528.imageshack.us/img528/639/picturelfk.jpg[/IMG]

---

### Post by dragonbeast25 on 2009-04-29
But yeah it said PPPoP Configured, ENABLED

And DCHP ENABLED.

Maby if i access 192.168.0.1 from ubuntu?

g2g to school please respond bye.

---

### Post by lisati on 2009-04-29
I'm about to sign off for the night, but before I head off, here are a couple of thoughts.

My home network is a similar setup (computers->router->router/modem->network), and two of my Ubuntu machines have lspci report the same kind of ethernet card as the OP. I have DHCP set to "automatic" on both machines, one of which runs 8.10 (the one I'm using now) and one has Ubuntu Studio 64-bit 9.04. Both worked "out of the box" with Ubuntu being able to connect to the internet, since I'd already set up the network via Windows.

I've had a look at the screenshot: I'd probably choose the "setup wizard" over the manual settings.

I'm nearly off to bed: good luck!

---

### Post by brunogirin on 2009-04-29
> **dragonbeast25 said:**
> But yeah it said PPPoP Configured, ENABLED

And DCHP ENABLED.

Yes, from the symptoms you have, your router is probably configured correctly for PPPoP and has DHCP enabled. I'm just not sure it's answering the DHCP queries when you connect via Ubuntu though. So, in Ubuntu, can you open a terminal window, run the following and post the results here please?

```
sudo dhclient eth0
```

```
cat /etc/dhcp3/dhclient.conf
```

```
netstat -rn
```

> **dragonbeast25 said:**
> Maby if i access 192.168.0.1 from ubuntu?

You can try that but it looks like the PC doesn't have an IP address so it may not work. If it doesn't work, can you open that page in XP again, click on the "Network settings" menu on the left and post a screenshot please?

> **dragonbeast25 said:**
> g2g to school please respond bye.

Have a good day at school then. I'm not sure I'll be online when you come back but hopefully someone else will be able to pick up from there.

---

### Post by freonchill on 2009-04-29
what is your modem?

typically you wire directly to it, static the ip on your computer
then go (for westell) to 192.168.1.254 in a webpage
then change the setting in the webgui from pppoe to bridge

wire the modem ethernet to the modem
then wire ethernet lan to your laptop, change static ip if required

then set the router to do pppoe with login and password for the wan connection

change your computer back to dhcp and get a dhcp from your router

PS - if you bump again, i will abandon helping you

---

### Post by max_power on 2009-04-29
"we didnt start the flame war..."

dragonbeast25 plug in your ubuntu to the network then go to terminal and type this:

> ifconfig

paste the results back in this thread

---

### Post by dragonbeast25 on 2009-04-29
Max power if you look in previous post youll see , ive tried that already

---

### Post by max_power on 2009-04-29
ok well you are not getting an IP address from you router. You said that the router has DHCP enabled.

Have you changed anything on the Ubuntu side (edit config files etc...) that would screw up your hardware settings?

if so i recommend just starting from a fresh install (considering its a new system anyway).

---

### Post by dragonbeast25 on 2009-04-29
No i do have DCHP it even says on my page router. And no i have no messed with anything on ubuntu. Any possible way to imput a ip adress for my router atleast on ubuntu any way?

---

### Post by max_power on 2009-04-29
you can set up a static ip address.

go to System -> preferences -> network connections

What do you have in "Wired" list box?

if you have somethign like "Auto Eth 0" then click on the edit button 

then click on the "ipv4  settings" tab

change DHCP to Manual

put your ip address to 192.168.1.5 (or whatever your netowrk scheme is) and your netmask to 255.255.255.0 and your gateway to 192.168.2.1

---

### Post by dragonbeast25 on 2009-04-29
Good news and Bad news

Good news:

It enstablished, Connnected.

Bad news:

I tryed firefox and it did not work.

Soloution ( Need your help )
My d-link router picks up what computers are connect for E.G( PC it glows and shows on router, Xbox 360 Shows and glows on router)
but when im on ubuntu it does not show on my router. They're fore that would be the bad thing. But what i understand is that im using the option " Try without changes to computer " Maby that is why, Because its running on a cd and the router would not pick it up. But on XP its on my hardrive and i start up it goes on, so they;re fore id probly have to install it Dual-boot. But i dont no how? Understand guys?

---

### Post by muhannadfa on 2009-04-29
firefox aint load websites >> cuase u're using static ip
ur ISP provides dynamic one >> here u go
------------------------------------------------------------
okey try this and give feedback
---------------------------------------------------------
right click on the network icon on the upper panel and make sure "enable networking" is checked

---

### Post by muhannadfa on 2009-04-29
is it checked or not

---

### Post by muhannadfa on 2009-04-29
> **dragonbeast25 said:**
> Good news and Bad news

Good news:

It enstablished, Connnected.

Bad news:

I tryed firefox and it did not work.

Soloution ( Need your help )
My d-link router picks up what computers are connect for E.G( PC it glows and shows on router, Xbox 360 Shows and glows on router)
but when im on ubuntu it does not show on my router. They're fore that would be the bad thing. But what i understand is that im using the option " Try without changes to computer " Maby that is why, Because its running on a cd and the router would not pick it up. But on XP its on my hardrive and i start up it goes on, so they;re fore id probly have to install it Dual-boot. But i dont no how? Understand guys?

has nothing to do with full setup of ubuntu
it has to work fine with live cd
-------------------------------------------

---

### Post by dragonbeast25 on 2009-04-29
It is checked

---

### Post by dragonbeast25 on 2009-04-29
O wait, Wired connection is disabled no checked but networking enabled its checked

---

### Post by dragonbeast25 on 2009-04-29
If i left click its disabled WIRED CONNECTION
But right click network is CHECKED :D

---

### Post by brunogirin on 2009-04-29
dragonbeast25: is it working now?

---

### Post by dragonbeast25 on 2009-04-29
No my windows xp just f'ed up its messing up somone help me with the ubuntu thing so i can install it as primary OS please.

---

### Post by brunogirin on 2009-04-30
OK, so back to square one but let's start with the simple things first. Start up Ubuntu on the Live CD. When you are on the desktop, in the top right, next to the date, you should see the Network Manager applet.

If you right-click on it, you should see a menu with a number of options. Can you confirm that "Enable Networking" is checked? We don't really care about the "Enable Wireless" box because you're not using wireless.

Then if you left-click on the same icon, you should see a drop-down with several sections in it: "Wired Network" and "Wireless Network" at the very least. In "Wired Network", can you confirm that you have a line that says "eth0" with a radio button next to it? Is the radio button on or off?

---

### Post by dragonbeast25 on 2009-04-30
One sec ill check. I have not seen one but ill check

---

### Post by dragonbeast25 on 2009-04-30
Cannot see any radio button.

---

### Post by dragonbeast25 on 2009-04-30
And by the way its Auto_ETH0 or somthing like that. Yeah no sign of the radio button at all.

---

### Post by dragonbeast25 on 2009-04-30
Well i g2g to school ,ttyl, please respond b4 i get home bye.

---

### Post by brunogirin on 2009-04-30
OK so on the grounds that a picture is worth 1000 words, I've taken screenshots to show you exactly what I mean.

The first screenshot shows what you should see when you **left**-click on the Network Manager icon. You notice that it says Auto eth0 and has a radio button next to it.

The second screenshot shows what you should see when you **right**-click on the same Network Manager icon. Make sure that "Enable Networking" (circled in blue) is checked. Then to check how your connection is set up, click on "Edit Connections" (circled in green).

A windows that should look like the 3rd screenshot will open. Select the Wired tab if not already selected, then select Auth eth0. Click on Edit. If you're running from a full install, it should ask you for your password at that point but if you're running on the live CD it shouldn't. You should then see a window like the 4th screenshot. Make sure that "Connect Automatically" is checked. Open the IPv4 tab: the window should then look like the 5th screenshot. Makes sure that the "Method" drop down box is set to "Automatic (DHCP)".

If any of the above differs on your machine, take a screenshot and post it. If the PrtSc key doesn't do any thing, go to Applications -> Accessories -> Take Screenshot. You should then be able to put the screenshot on your XP partition or on a USB key and post it from XP.

Lastly, one easy thing you can try is this: while you're running Ubuntu, unplug and re-plug the network cable, it may force Network Manager to check the interface again. If that doesn't work, just try to check and un-check the "Enable Wireless" or the "Enable Networking" checkbox that you see when you right-click on the icon: that will also force NM to re-check all connections.

---

### Post by dragonbeast25 on 2009-04-30
If i pose correctly, i see what you mean, and yes the radio button is they're. As you see in this screen shot DCHP will not enstablish
[IMG]http://img404.imageshack.us/img404/5293/screenshotx.jpg[/IMG]

And with manual this is what i get enstabled witch is better.
[IMG]http://img404.imageshack.us/img404/1958/screenshot2f.jpg[/IMG]

My d-link router is still not picking up ubuntu that is probly the problem, i did the unplug and stuff and still same issue, i think its the ethernets cord problem:
Dlink router is not glowing up for ubuntu meaning it is probly not sending connections from they're to enthernet cord. If i just plug it in my modem directly, DSL it does not glow either so its a reconization problem im guessing but yeah. Thanks for helping tho i appreciate it.

---

### Post by brunogirin on 2009-04-30
Yes, if you've got no light showing on the router, it means it considers the cable to be unplugged. However, if it is the ethernet cable that is at fault, it doesn't explain why it works on XP and not on Ubuntu. Have you tried plugging your cable to a different LAN port on the router?

However, if I look at your screenshots, in the first one, you have "Method" set to "Automatic (DHCP)" but you have "Connect automatically" unchecked. Have you tried to have both "Connect automatically" checked and "Method" set to "Automatic (DHCP)" as in my screenshot?

If that doesn't work, set you IP address to a static one as you did in your second screenshot: Method = Manual, Address = 192.168.0.100, Netmask = 255.255.255.0, Gateway = 192.168.0.1. Then run the following in a terminal and post the output here:

```
ping 192.168.0.1
```

---

### Post by max_power on 2009-04-30
is dragonbeast25 the "how is babby formed" guy?

---

### Post by dragonbeast25 on 2009-04-30
Tried everything u said terminal is

Connect: network is unreachable

---

### Post by dragonbeast25 on 2009-04-30
Hello?

---

### Post by brunogirin on 2009-04-30
With your address set up as a static one, can you run the following and post the output please?

```
ifconfig eth0
```

```
netstat -rn
```

I'll have to go for the night but if you can do that I'll have a look tomorrow morning.

---

### Post by dragonbeast25 on 2009-04-30
ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:11:09:1a:e5:cc  
          inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc800

netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

 
Please respond , Ill be on also for morning because i got schools

---

### Post by dragonbeast25 on 2009-04-30
Ok going to bed bye, ill be on alround 6:30 in morning pacific time flordia time to be asact or toronto. In northamerica

---

### Post by brunogirin on 2009-05-01
Try the following:

```
sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up
sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0
sudo route add default gw 192.168.0.1
```

Post the output and whether you can ping 192.168.0.1 after that.

---

### Post by dragonbeast25 on 2009-05-01
i copyed and paste in ternimal. and i got this
[IMG]http://img8.imageshack.us/img8/5001/screenshot4y.png[/IMG]

---

### Post by brunogirin on 2009-05-01
OK, that's good so far so press enter to execute the last command and then post the output of:

```
ifconfig eth0
netstat -rn
ping 192.168.0.1
```

---

### Post by dragonbeast25 on 2009-05-01
Already have done those promts but here again:
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:09:1a:e5:cc  
          inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc800 

ubuntu@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
ubuntu@ubuntu:~$ ping 192.168.0.1
connect: Network is unreachable

---

### Post by brunogirin on 2009-05-01
I know you've already done those but what I got you to do before should have changed the output. You didn't reboot between the two did you? If you did, can you redo the whole thing in one go please?

```
sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up
sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0
sudo route add default gw 192.168.0.1
ifconfig eth0
netstat -rn
ping 192.168.0.1
```

Just to explain what we're trying to do here: the first command sets up the eth0 interface and brings it up, the second adds a route to your local network via this interface, the 3rd adds a default route via your router, the 4th checks the status of the eth0 interface, the 5th checks the routes and the last one tries to ping your router.

I've got to go out and will be back in 5 or 6 hours so I won't be able to answer before that.

---

### Post by dragonbeast25 on 2009-05-01
So you want me to copy paste that all and put in ternimal than post results? fast reply plz

---

### Post by brunogirin on 2009-05-01
Yes please.

---

### Post by dragonbeast25 on 2009-05-01
Ok just did an ipconfig on my XP computer my ip adress is : 192.168.0.101, But i also tried that for manual in ubuntu so no differnce, just to let you know, the results are.:
ubuntu@ubuntu:~$ sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo route add default gw 192.168.0.1
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:09:1a:e5:cc  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe1a:e5cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc800 

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
From 192.168.0.100 icmp_seq=3 Destination Host Unreachable
From 192.168.0.100 icmp_seq=4 Destination Host Unreachable

---

### Post by dragonbeast25 on 2009-05-01
YeH BUT ONCE I DID THOSE COMMANDS IT WENT FARTHER LIKE IN TERNIMAL MORE POPED UP. Hope this issue is fix soon so i can install it as primary OS. Thanks please reply soon because i got school shortly

---

### Post by dragonbeast25 on 2009-05-01
Well i g2g to school, please respond b4 i get home bye guys

---

### Post by brunogirin on 2009-05-01
At least we're getting somewhere and there's progress! The important line in the output you provided below is this one:

> inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0

This shows that your ethernet connection has been given an IP address, which wasn't happening before. However, the output of netstat shows two identical lines, which it shouldn't. So it looks like the first "route" command I gave you is unnecessary and may even confuse things, so try without:

```
sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1
ifconfig eth0
netstat -rn
ping 192.168.0.1
```

I also assume above that 192.168.0.1 is the address of your router. Can you confirm?

One of the problems we've got at the moment is that we can't make any of those changes permanent because you're running on the live CD. Once we've managed to ping the router, you'll need to install to disk without removing XP so that we can solve it permanently.

However, I am going on vacation tomorrow morning for 2 weeks and won't have access to a computer or the internet during that time so won't be able to help you. If we don't manage to get it sorted tonight (on GMT time), someone else will have to pick up or you'll have to wait until I come back.

---

### Post by dragonbeast25 on 2009-05-01
Well have very much fun, so i do that command you just showed me the one line new one. and if it works then i ping 192.168.0.1 and if it works i connect and should work? Then i istall wubi?

---

### Post by dragonbeast25 on 2009-05-01
Or do you possibly have an email account so i can see when your online and we can talk instant?

---

### Post by dragonbeast25 on 2009-05-01
And one more thing thanks for helping, i really appreciate it, for all the time you had helping me. Be safe on your vacation good luck.

---

### Post by brunogirin on 2009-05-01
> **dragonbeast25 said:**
> Well have very much fun, so i do that command you just showed me the one line new one. and if it works then i ping 192.168.0.1 and if it works i connect and should work? Then i istall wubi?

Run the 5 lines I posted last. If ping works, you should see something like this (obviously with your address rather than mine):

```
bruno@nuuk:~$ ping 192.168.1.252
PING 192.168.1.252 (192.168.1.252) 56(84) bytes of data.
64 bytes from 192.168.1.252: icmp_seq=1 ttl=255 time=4.38 ms
64 bytes from 192.168.1.252: icmp_seq=2 ttl=255 time=2.39 ms
64 bytes from 192.168.1.252: icmp_seq=3 ttl=255 time=2.32 ms
64 bytes from 192.168.1.252: icmp_seq=4 ttl=255 time=2.29 ms
64 bytes from 192.168.1.252: icmp_seq=5 ttl=255 time=2.37 ms
```

Once ping returns something like the above, it means that your eth0 interface is working and can communicate with your router. Once this is done, install Ubuntu to the hard disk and during the install, ask it to resize the XP partition and install itself next to it. It should install and configure GRUB so that you can boot either Ubuntu or XP. There should be no need for Wubi on a basic install: Ubuntu Jaunty is quite smart at working out what needs to be done and configuring GRUB accordingly. You can always remove XP later once Ubuntu is fully working and installed if that's what you want but you should keep it for now.

Once Ubuntu is running from the hard disk, we will need to set up the network interface so that the settings are permanent. And after that, the DNS details. But first, we need to ensure that some data comes out of your network card, reaches the router and comes back, which is the aim of the ping command. The 4 lines before ping are just there to set things up and check the status of the interface. They are necessary at the moment because you're running from the live CD.

If I have access to the net while on vacation, I'll check my email so I should see if you've posted anything more to this thread and if I can I will help.

---

### Post by brunogirin on 2009-05-01
Sorry, I forgot: if ping works, it will keep running until you stop it: just press CTRL-C to do so.

---

### Post by dragonbeast25 on 2009-05-01
Its pinged and it worked but then after i did it again and it didnt work?? Hmm so when it pings then its connected bascily? so i can go on firefox from the live cD and if it does i install it and make 2 partitions one of them xp already and new one that i install ubuntu on and then install it th ere and when i boot i get boot menu right?

---

### Post by brunogirin on 2009-05-01
Yes, if it pings it means that your network interface works. So boot on the live CD and install to hard disk. It will give you an option to resize the Windows partition and install Ubuntu next to it. It should then create 2 partitions for Ubuntu: one for the OS itself (called the root partition) and one for swap.

The installation will configure GRUB so that it boots Ubuntu by default. So if you want to boot XP, you will need to press ESC when you see the wait message that counts down from 2 to 0, it will then bring up the GRUB menu where you can select Windows.

---

### Post by Slim Odds on 2009-05-01
> **dragonbeast25 said:**
> ok 1 sec

This is NOT chat.

And your BUMPING is really annoying.

---

### Post by dragonbeast25 on 2009-05-01
Ive done like 5 threads, that is why i was bumbing now i got help i dont, and who cares its a free forum i can chat all i want. Ur not helping

---

### Post by Slim Odds on 2009-05-02
Bump

---

### Post by dragonbeast25 on 2009-05-02
Kay now your helping, you should upgrade to 9.04

---

### Post by dragonbeast25 on 2009-05-03
i dont want to leave this problem here, but any way else you can help? It pinged once and i cant get it to ping again, but were making progress like you said. But anyGuru or any idea to make it ping again or working my stats are all in the forums bout ifconfig ETC. Thanks

---

