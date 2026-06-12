---
title: "Ubuntu 5.10 and SonyEricsson Edge GC82"
date: 2005-11-14
forum: Desktop Environments
---

### Post by nerdroger on 2005-11-14
I have been trying to find info on getting this cellular modem to work.   Many pages suggest looking at a page at attwireless.com, but it does not exist anymore.

Any help would be appreciated.  This is one on my last barriers that I must pass in order to switch completely to linux from WinXP.,

Thank you
Roger     :confused:

---

### Post by routerstu on 2005-11-14
rumor has it that it works.  i jst bought a gc83 and have been looking for notes.  i google'd and searched this forum for gc83 and found some things.  i will let you know if i make any progress.  but it looks like you see it as a serial device, then use provided chat scripts.  i think a gc83 is just a 82 with newer firmware? anyhow, here are some directions i found, NOT MINE..



:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

I have a Sony Ericsson GC83 with cingular service working on Fedora Core 3. Here is how I did it

make sure you have pppd installed. if your not sure if its installed, you can look for pppd in /usr/sbin.

1. Put card in and ran kudzu. Fedora found a generic serial modem.
2. make a file called /etc/ppp/peers/cingular heres what my file looks like:


# information about your device
/dev/ttyS3 # device file assigned to GC83 modem (Serial modem)
230400 # pcmcia negotiation speed
#115200 # slower negotiation speed

# ----------------------------------------------------------------
# Initial authentication -----------------------------------------

user [email]ISPDA@CINGULARGPRS.COM[/email] # username (data acceleration)
#user [email]ISP@CINGULARGPRS.COM[/email] # username (no data acceleration)
#user [email]WAP@CINGULARGPRS.COM[/email] # username WAP, not common!
password CINGULAR1 # a common GPRS/EDGE password

# ----------------------------------------------------------------

defaultroute # use cellular network's gateway
noipdefault # force peer to specify local IP (GC83 only)
usepeerdns # use DNS servers from remote host

remotename attws # assume 'attws' as name of remote system
ipparam attws # add 'attws' to ip-up & ip-down script

crtscts # enable hardware flow control
lock # lock the serial port when in use
noauth # don't expect peer to authenticate
persist # re-dial connection if dial fails
#local # ignore Carrier Detect and DTR signals

# -----------------------------------------------------------------
# uncomment these options when roaming or when signal is low ------
# leaving these options commented increases data throughput -------

#novj # disable TCP/IP header compression
#novjccomp # disable connection ID compression

# -----------------------------------------------------------------

# -----------------------------------------------------------------
# These compression styles can cause problems over GPRS/EDGE
# Uncomment these lines for troubleshooting

#nodeflate # Disable deflate compression
#nobsdcomp # Disable bsd-compress compression

# ----------------------------------------------------------------

# Leave uncommented, at least until your connection works consistently
debug # provides verbose output to stderr

# ---------------------------------------------------------------
# Uncomment this option if you don't have the screen window manager
# screen is a helpful tool
# it can be obtained from [http://www.gnu.org/software/screen](http://www.gnu.org/software/screen)

nodetach # do not allow terminal to detach

ipcp-max-configure 20 # increase the maximum IPCP config requests
maxfail 0 # do not stop retrying connection

# Move on to the chat script after connection
connect '/usr/sbin/chat -v -V -t3 -f /etc/ppp/peers/chat-gc83'


3. Create file called /etc/ppp/peers/chat-gc83 Here is my file:


#
SAY 'Starting GPRS connect script...\n'
SAY '\n'
# ispauth CHAP # define auth method (optional)

SAY 'Setting the abort string\n'
SAY '\n'

# Abort String ---------------------------------

#ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
#TIMEOUT 10
#ABORT 'BUSY' ABORT 'NO ANSWER' ABORT 'NO CARRIER'

# ----------------------------------------------
SAY 'Initializing modem\n'

# Modem Initialization -------------------------
#'' ATZ
# Eo=No echo, V1=English result codes
#OK 'ATE0V1'
'' AT+cfun=1
OK AT+cfun=1
OK AT+cgreg=1
OK AT
#TIMEOUT 40
# ----------------------------------------------

# Additional initialization (optional) ---------
# /begin att
OK AT&F&D2&C1E0V1S0=0
OK AT+IFC=2,2
OK ATS0=0
OK AT
OK AT&F&D2&C1E0V1S0=0
OK AT+IFC=2,2
# /end att
#AT&FE0S0=0
#AT&F0&D2+IFC=2,2V1Q0XIS0=0S7=50+CMEE=1

# ----------------------------------------------

SAY '\n'
SAY 'Setting APN\n'

# Set Access Point Name (APN) ------------------
# Incorrect APN or CGDCONT variable is a
# frequent cause of peer LCP TermReqs
# So try each setting at least once! =)

#REG:\s1 AT+cgdcont=1,"IP","proxy"
#OK 'AT+CGDCONT=0,"IP","proxy"'
OK 'AT+CGDCONT=1,"IP","proxy"'
OK 'AT+CGDCONT=2,"IP","proxy"'
#OK 'AT+CGDCONT=0,"IP","isp.cingular"'
#OK 'AT+CGDCONT=1,"IP","isp.cingular"'
#OK 'AT+CGDCONT=2,"IP","isp.cingular"'

# ----------------------------------------------


SAY '\n'
SAY 'Dialing...\n'
# Dial the ISP ---------------------------------
# a few different dial commands are shown
# the default should work fine

#REG:\s1 'ATD*99***1#'
OK ATDT*99***1#
#OK ATD*99***1#
#OK ATD*99#
#OK 'ATD*##***##'
#OK
CONNECT ' '


4. I had an issue with dns. Basically I was getting assigned dns but resolv.conf wasn't being written to. To fix this I created a file /etc/sysconfig/network-scripts/ifcfg-attws
This caused ifup-ppp to activate when the modem connects.

5. Don't know if this truely helps but do a ifconfig sit0 up. This seemed to help when trying to get a connection.

5. To connect type pppd call cingular to connect
you will see modem connect strings and eventually see ip info passed to you. If you hit ctl+c it will disconnect.


I found most of this documentation here:
[http://advantedgecomputing.com/opensource/gc83linux.html](http://advantedgecomputing.com/opensource/gc83linux.html)
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

---

### Post by routerstu on 2005-11-15
writing this from the cingular card.  works just as stated, but i did have to test with different "APN" settings as it said. 
this worked

'AT+CGDCONT=1,"IP","isp.cingular"'



 make sure you read those 2 files for troubleshooting tips and config tips.  good luck!!!

---

### Post by kris kincaid on 2005-12-15
Are you impressed with the performance of the Cingular ISP?? I am tempted to sign up, but I don't really want to jump through hoops getting it to work only to find out it is a turd. I want to make it work with [a PCI to PCMCIA Controller Card]("http://www.newegg.com/Product/Product.asp?Item=15-104-222&depa=0%20") for my home PC, then take the card with me on the road.

---

### Post by nerdroger on 2005-12-21
OK, I have finally got back to tackling this.  I am so close... here is the output I get...

Starting GPRS connect script...
Setting the abort string
Initializing modem
OK
OK
OK
+CGREG: 1
OK
OK
OK
OK
OK
OK
Setting APN


OK

OK

CONNECTSerial connection established.
using channel 19
Using interface ppp0
Connect: ppp0 <--> /dev/ttyS2
rcvd [LCP ConfReq id=0xab <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x16df44> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x1e5c818b> <pcomp> <accomp>]
sent [LCP ConfAck id=0xab <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x16df44> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x1e5c818b> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x1e5c818b]
sent [PAP AuthReq id=0x1 user="wapuser1" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x1e5c818b]
appear to have received our own echo-reply!
rcvd [PAP AuthAck id=0x1 "PAP access OK"]
Remote message: PAP access OK
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfReq id=0xab <addr 172.29.1.0> <compress VJ 0f 01>]
sent [IPCP ConfAck id=0xab <addr 172.29.1.0> <compress VJ 0f 01>]
rcvd [LCP ProtRej id=0xac 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfNak id=0x2 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfNak id=0x3 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfNak id=0x4 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfNak id=0x5 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x6 <compress VJ 0f 01>]
rcvd [IPCP ConfNak id=0x6 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x7 <compress VJ 0f 01> <addr 192.168.201.1>]
rcvd [IPCP ConfNak id=0x7 <addr 172.29.1.46>]
sent [IPCP ConfReq id=0x8 <compress VJ 0f 01>]
rcvd [IPCP ConfAck id=0x8 <compress VJ 0f 01>]
Peer refused to agree to our IP address
Connect time 0.1 minutes.
Sent 147 bytes, received 100 bytes.
sent [IPCP TermReq id=0x9 "Refused our IP address"]
rcvd [IPCP TermReq id=0xac]
sent [IPCP TermAck id=0xac]
Modem hangup
Connection terminated.
tcgetattr: No such device or address (line 917)
tcsetattr: No such device or address (line 1011)


Please help!
Thank you.

---

### Post by nerdroger on 2005-12-21
Almost forgot, here is my /etc/ppp/peers/rogers1 file...
# Script source:  [http://advantedgecomputing.com/opensource/gc83linux.html](http://advantedgecomputing.com/opensource/gc83linux.html)
# Assembled by Riyan Mynuddin - e-mail: [email]opensource@advantedgecomputing.com[/email]
# Feel free to e-mail Riyan with questions, comments or suggestions.

# If you have a GC82, try uncommenting before hacking and recompiling pppd!
192.168.201.1:			# forces IP address (enable for GC82 only)

# information about your device
/dev/ttyS2			# device file assigned to GC8x modem
230400				# pcmcia negotiation speed
#115200				# slower negotiation speed

# ----------------------------------------------------------------
# Initial authentication -----------------------------------------
 
user wapuser1     # username (data acceleration)
#user [email]ISP@CINGULARGPRS.COM[/email]	# username (no data acceleration)
#user [email]WAP@CINGULARGPRS.COM[/email]	# username WAP, not common!
password wap		# a common GPRS/EDGE password

# ----------------------------------------------------------------

# defaultroute			# use cellular network's gateway
# noipdefault			# force peer to specify local IP (GC83 only)
# usepeerdns			# use DNS servers from remote host

# remotename attws		# assume 'attws' as name of remote system
# ipparam attws			# add 'attws' to ip-up & ip-down script

crtscts				# enable hardware flow control
lock				# lock the serial port when in use
noauth				# don't expect peer to authenticate
persist				# re-dial connection if dial fails
#local				# ignore Carrier Detect and DTR signals

# -----------------------------------------------------------------
# uncomment these options when roaming or when signal is low ------
# leaving these options commented increases data throughput -------

#novj				# disable TCP/IP header compression
#novjccomp			# disable connection ID compression

# -----------------------------------------------------------------

# -----------------------------------------------------------------
# These compression styles can cause problems over GPRS/EDGE
# Uncomment these lines for troubleshooting

# nodeflate			# Disable deflate compression
# nobsdcomp			# Disable bsd-compress compression

# ----------------------------------------------------------------

# Leave uncommented, at least until your connection works consistently
debug				# provides verbose output to stderr

# ---------------------------------------------------------------
# Uncomment this option if you don't have the screen window manager
# screen is a helpful tool
# it can be obtained from [http://www.gnu.org/software/screen](http://www.gnu.org/software/screen)

nodetach			# do not allow terminal to detach

ipcp-max-configure 20		# increase the maximum IPCP config requests
maxfail 0			# do not stop retrying connection

# Move on to the chat script after connection
# connect '/usr/sbin/chat -v -V -t3 -f /etc/ppp/chat-gc83'
connect '/usr/sbin/chat -v -V -t3 -f /etc/ppp/peers/rogers.chat'

---

### Post by nerdroger on 2005-12-22
OK, I had the GC82 going for just over 1.5 minutes then it disconnected.  I had to issue the "sudo ifconfig eth1 down" command in order to get ppp0 to connect.

Here is a copy of my results.  What is "appear to have received our own echo-reply!" mean?
Why is it disconnecting?

-----------Start of results------------
Starting GPRS connect script...

Setting the abort string

Initializing modem

+CME ERROR: 134

*MTZ: 2, "12/22/2005, 23:33:34-20", 0

*MRDY: 3

OK

OK

OK

+CGREG: 1

OK

OK

OK

OK

OK

OK
Setting APN


OK

OK

CONNECTSerial connection established.
using channel 15
Using interface ppp0
Connect: ppp0 <--> /dev/ttyS2
rcvd [LCP ConfReq id=0x53 <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x13138> <                         pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9364bbc5> <pcomp> <accomp>]
sent [LCP ConfAck id=0x53 <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x13138> <                         pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x9364bbc5> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x9364bbc5]
sent [PAP AuthReq id=0x1 user="wapuser1" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x9364bbc5]
appear to have received our own echo-reply!
rcvd [PAP AuthAck id=0x1 "PAP access OK"]
Remote message: PAP access OK
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <                         ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x53 <addr 172.29.7.0> <compress VJ 0f 01>]
sent [IPCP ConfNak id=0x53 <addr 10.0.0.2>]
rcvd [IPCP ConfNak id=0x1 <addr 172.29.7.72> <ms-dns1 207.181.101.4> <ms-dns3 20                         7.181.101.5>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 172.29.7.72> <ms-dns1 207.18   1.101.4> <ms-dns3 207.181.101.5>]
Cannot determine ethernet address for proxy ARP
local  IP address 172.29.7.72
remote IP address 10.0.0.2
primary   DNS address 207.181.101.4
secondary DNS address 207.181.101.5
Script /etc/ppp/ip-up started (pid 10378)
Script /etc/ppp/ip-up finished (pid 10378), status = 0x0
appear to have received our own echo-reply!
appear to have received our own echo-reply!
appear to have received our own echo-reply!
Modem hangup
Connect time 1.6 minutes.
Sent 27378 bytes, received 95359 bytes.
Script /etc/ppp/ip-down started (pid 10415)
Connection terminated.
Script /etc/ppp/ip-down finished (pid 10415), status = 0x0
tcgetattr: No such device or address (line 917)
tcsetattr: No such device or address (line 1011)
-------------end of results---------------

Any thoughts?

---

### Post by nerdroger on 2006-01-04
Well, by changing a couple of items in the /etc/ppp/options it now works for between 5-8 minutes at a time.  After it drops connection I have to unplug and plug the card back in for it to be recognized again.

So it is almost there!

Any pppd gurus out there?

Roger

---

### Post by will1384 on 2006-01-15
Did any one get this to work - I would like to use Ubuntu to share 
my internet connection - But because I live out in the woods -
All I have for internet is the GC83 card - and no there is nothing else

and even tho windows will share the internet - it does a poor job
of it and likes to just stop working all the time - I have to reset
the computer to get it to start working again, and it dies all the time,
another plus of using linux to share my internet would be more secure
and easy to map ports ect ect 

- BTW - I have tried Fedora Core 3, and smoothwall with the same 
scripts here - and it did the same thing - so whats wrong - I decided 
on Ubuntu because its a easer for me to use - and I need to use the
laptop as a server at home, and a desktop on the road

---

### Post by dirtvoyles on 2006-06-11
I would like to get a GC83 working on my laptop as well. Unfortunately, these instructions aren't that helpful since I have service with a local provider.

Can anyone supply where I would change the APN, port proxy, etc. to make this work? Also, the network does not require a UN or password, can I just comment out that line?

Any help would be appreciated. Thanks!

---

### Post by masinger53 on 2006-06-26
[QUOTE=routerstu]
1. Put card in and ran kudzu. Fedora found a generic serial modem.
[/QUOTE]

routerstu, what did you use instead of kudzu?  I have trolled the IRC and searched the forums for the Ubuntu equivalent for post-boot hardware detection and can't find anything.

I have regular wifi working with the access point on my home LAN; I have the VPN to my Windoze desktop at work functioning; once the Cingular Air Card works, I'm fully functional on this Dell Inspiron 9100 laptop (minus a few keyboard shortcuts tweaks that are non-critical).

---

