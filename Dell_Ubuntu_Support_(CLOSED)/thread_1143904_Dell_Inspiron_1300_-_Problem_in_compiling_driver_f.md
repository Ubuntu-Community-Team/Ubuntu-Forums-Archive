---
title: "Dell Inspiron 1300 - Problem in compiling driver for HSF modem"
date: 2009-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kazemi on 2009-04-30
Hello everyone,

I just installed Ubuntu 9.04 on my Dell Inspiron 1300 with a Conexant HSF modem. In Ubuntu 8.10, I used to make this modem with compiling a customized driver (according to this link [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant) ) and everything was working fine.

However, when I try to compile the driver in 9.04, I recieve the following error log:

-----------------------------------------------------------------------------------------------------
driver version 7.68.00.09oem
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfosspec.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfserial.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfengine.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfpcibasic2.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfpcibasic3.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfhda.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ich.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97via.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ali.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ati.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97sis.mod  /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

----------------------------------------------------------------------------------------------------

I suppose the error is due to wrong "linux-headers-2.6.28-11-generic" path. I have the linux headers installed but not sure about the right path to it ( I used /usr/src/linux-headers-2.6.28-11-generic ).

Can anyone instruct me how to resolve this problem? As I said, the driver compiling for this modem was okay on Ubuntu 8.10 without any problem.

---

### Post by sir_nasty on 2009-04-30
what package are you using?

I just noticed from a quick read this line:


For the lazy, just download this ready-made package; after unpacking it and entering the resulting directory, do sudo make install and sudo /usr/sbin/hsfconfig


are you doing sudo make install?

---

### Post by kazemi on 2009-05-01
I am using the latest original TAR package from Linuxant (hsfmodem-7.80.02.04full.tar.gz) and original package from Dell (hsfmodem-7.68.00.09oem.tar.gz). I have replaced the /modules/imported directory from Linuxant driver with that of Dell (as explained in the following instructions):

--------------------------------BEGINNING OF INSTRUCTIONS--------------------------------------

Unpack the driver tars with,
 	Code:
 	tar -xvf /home/ryan/hsfmodem-7.68.00.09oem.tar.gz 
and again for the Linuxant driver(hsfmodem-7.80.02.02full.tar.gz in my case),
 	Code:
 	tar -xvf /home/ryan/hsfmodem-7.80.02.02full.tar.gz 
Then remove the modules/imported directory from Linuxant driver,
 	Code:
 	rm -R /home/ryan/hsfmodem-7.80.02.02full/modules/imported 
Then copy over the modules/imported directory from Dell,
 	Code:
 	cp -R /home/ryan/hsfmodem-7.68.00.09oem/modules/imported /home/ryan/hsfmodem-7.80.02.02full/modules/imported 
Then change working directory to the Linuxant driver folder,
 	Code:
 	cd /home/ryan/hsfmodem-7.80.02.02full 
Then install like normal,
 	Code:
 	sudo make install 
 	Code:
 	sudo hsfconfig 
-----------------------------END OF INSTRUCTION-----------------------------------

As the error log implies, the problem is maybe with missing "string.h", but how can I find it and what is the resolution?

---

### Post by rocky5051 on 2009-05-16
Okay, I had this same problem two (one of two blockers which prevented me from using Ubuntu 8.10), and I've figured out a workaround.

Download the pre-made package mentioned here. Don't bother making it yourself, as it is unnecessary:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

Download and save the archive to your desktop, and extract it.
```
tar -xvf $HOME/Desktop/hsfmodem-7.80.02.03full-dellhybrid.tar.gz
```

Now go into the directory of the extracted folder, make install it.
```
cd hsfmodem-7.80.02.03full && sudo make install
```

This next part wasn't entirely obvious, but you'd be surprised what one little hack can do. The osservices header file which is installed as part of the hsfmodem module references the stings header files from the generic linux headers. For whatever reason, it seems in Ubuntu 9.04 it references the wrong directory for the file, and thus much be changed for the hsfmodem module to compile successfully. Change "string.h" in line 356 of the "osservices.h" file to "linux/string.h".
```
sudo gedit /usr/lib/modules/hsfmodem/imported/include/osservices.h
```

Save it as normal and close gedit. Now, run hsfconfig, follow it's instructions and there should be no more errors.
```
sudo hsfconfig
```

In fact, to back the success I've had with this little change, I can say with all honesty that I'm posting in Ubuntu 9.04 with the hybrid dell/linuxant driver working. :D

Hope that helps.

---

### Post by Nyken on 2009-05-16
3 days to find something like this. It worked, got wvdial to dial in to an ISP, and just wanted to drop a thank you from a grateful new Linux AND Ubuntu user. Getting things up and running after an install with no internet connection is the only gripe I've really had about this OS so far and now I got that one out of the way. It's been frustrating and fun at the same time, not to mention a good deal educational.

---

### Post by NZJon on 2009-05-20
Hi rocky5051,

I have sucessfully installed the HSF driver using the "Dell Hybrid" solution that you have also used. But, I am having problems, I think with the PPPD.

When I use either gnome-ppp or wvdial to create a dial up connection to my ISP, I get the following output:

> 
jon@white:/usr/share/hsfmodem-7.80.02.03full-dellhybrid$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT086725327
--> Waiting for carrier.
ATDT086725327
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
** Lucent APX Terminal Server **
Login: 
Login: 
Login: 
Login: 
--> Looks like a login prompt.
--> Sending: jon.pawley
jon.pawley
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 218.101.97.250
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Tue May 19 21:19:20 2009
--> Pid of pppd: 17568
--> Disconnecting at Tue May 19 21:19:21 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


Looking at "man pppd" tells me that exit code 2 indicates an error with the options. I haven't edited my /etc/ppp/options , and it's contents are:

> 
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specify which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Servers can be remotely configured
# ms-dns 192.168.1.1
# ms-dns 192.168.1.2

# Specify which WINS Servers the incoming connection Win95 or WinNT should use
# ms-wins 192.168.1.50
# ms-wins 192.168.1.51

# Run the executable or shell command specified after pppd has
# terminated the link.  This script could, for example, issue commands
# to the modem to cause it to hang up if hardware modem control signals
# were not available.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

# async character map -- 32-bit hex; each bit is a character
# that needs to be escaped for pppd to receive it.  0x00000001
# represents '\x01', and 0x80000000 represents '\x1f'.
asyncmap 0

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth
# ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

# Use hardware flow control (i.e. RTS/CTS) to control the flow of data
# on the serial port.
crtscts

# Use software flow control (i.e. XON/XOFF) to control the flow of data
# on the serial port.
#xonxoff

# Specifies that certain characters should be escaped on transmission
# (regardless of whether the peer requests them to be escaped with its
# async control character map).  The characters to be escaped are
# specified as a list of hex numbers separated by commas.  Note that
# almost any character can be specified for the escape option, unlike
# the asyncmap option which only allows control characters to be
# specified.  The characters which may not be escaped are those with hex
# values 0x20 - 0x3f or 0x5e.
#escape 11,13,ff

# Don't use the modem control lines.
#local

# Specifies that pppd should use a UUCP-style lock on the serial device
# to ensure exclusive access to the device.
lock

# Don't show the passwords when logging the contents of PAP packets.
# This is the default.
hide-password

# When logging the contents of PAP packets, this option causes pppd to
# show the password string in the log message.
#show-password

# Use the modem control lines.  On Ultrix, this option implies hardware
# flow control, as for the crtscts option.  (This option is not fully
# implemented.)
modem

# Set the MRU [Maximum Receive Unit] value to <n> for negotiation.  pppd
# will ask the peer to send packets of no more than <n> bytes. The
# minimum MRU value is 128.  The default MRU value is 1500.  A value of
# 296 is recommended for slow links (40 bytes for TCP/IP header + 256
# bytes of data).
#mru 542

# Set the interface netmask to <n>, a 32 bit netmask in "decimal dot"
# notation (e.g. 255.255.255.0).
#netmask 255.255.255.0

# Disables the default behaviour when no local IP address is specified,
# which is to determine (if possible) the local IP address from the
# hostname. With this option, the peer will have to supply the local IP
# address during IPCP negotiation (unless it specified explicitly on the
# command line or in an options file).
#noipdefault

# Enables the "passive" option in the LCP.  With this option, pppd will
# attempt to initiate a connection; if no reply is received from the
# peer, pppd will then just wait passively for a valid LCP packet from
# the peer (instead of exiting, as it does without this option).
#passive

# With this option, pppd will not transmit LCP packets to initiate a
# connection until a valid LCP packet is received from the peer (as for
# the "passive" option with old versions of pppd).
#silent

# Don't request or allow negotiation of any options for LCP and IPCP
# (use default values).
#-all

# Disable Address/Control compression negotiation (use default, i.e.
# address/control field disabled).
#-ac

# Disable asyncmap negotiation (use the default asyncmap, i.e. escape
# all control characters).
#-am

# Don't fork to become a background process (otherwise pppd will do so
# if a serial device is specified).
#-detach

# Disable IP address negotiation (with this option, the remote IP
# address must be specified with an option on the command line or in
# an options file).
#-ip

# Disable IPCP negotiation and IP communication. This option should
# only be required if the peer is buggy and gets confused by requests
# from pppd for IPCP negotiation.
#noip

# Disable magic number negotiation.  With this option, pppd cannot
# detect a looped-back line.
#-mn

# Disable MRU [Maximum Receive Unit] negotiation (use default, i.e.
# 1500).
#-mru

# Disable protocol field compression negotiation (use default, i.e.
# protocol field compression disabled).
#-pc

# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
#+chap

# Don't agree to authenticate using CHAP.
#-chap

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
#-vj

# Increase debugging level (same as -d).  If this option is given, pppd
# will log the contents of all control packets sent or received in a
# readable form.  The packets are logged through syslog with facility
# daemon and level debug. This information can be directed to a file by
# setting up /etc/syslog.conf appropriately (see syslog.conf(5)).  (If
# pppd is compiled with extra debugging enabled, it will log messages
# using facility local2 instead of daemon).
#debug

# Append the domain name <d> to the local host name for authentication
# purposes.  For example, if gethostname() returns the name porsche,
# but the fully qualified domain name is porsche.Quotron.COM, you would
# use the domain option to set the domain name to Quotron.COM.
#domain <d>

# Enable debugging code in the kernel-level PPP driver.  The argument n
# is a number which is the sum of the following values: 1 to enable
# general debug messages, 2 to request that the contents of received
# packets be printed, and 4 to request that the contents of transmitted
# packets be printed.
#kdebug n

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>

# Set the name of the local system for authentication purposes to <n>.
# This is a privileged option. With this option, pppd will use lines in the
# secrets files which have <n> as the second field when looking for a
# secret to use in authenticating the peer. In addition, unless overridden
# with the user option, <n> will be used as the name to send to the peer
# when authenticating the local system to the peer. (Note that pppd does
# not append the domain name to <n>.)
#name <n>

# Enforce the use of the hostname as the name of the local system for
# authentication purposes (overrides the name option).
#usehostname

# Set the assumed name of the remote system for authentication purposes
# to <n>.
#remotename <n>

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.
proxyarp

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
# login

# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.
lcp-echo-interval 30

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.
lcp-echo-failure 4

# Set the LCP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#lcp-restart <n>

# Set the maximum number of LCP terminate-request transmissions to <n>
# (default 3).
#lcp-max-terminate <n>

# Set the maximum number of LCP configure-request transmissions to <n>
# (default 10).
#lcp-max-configure <n>

# Set the maximum number of LCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#lcp-max-failure <n>

# Set the IPCP restart interval (retransmission timeout) to <n>
# seconds (default 3).
#ipcp-restart <n>

# Set the maximum number of IPCP terminate-request transmissions to <n>
# (default 3).
#ipcp-max-terminate <n>

# Set the maximum number of IPCP configure-request transmissions to <n>
# (default 10).
#ipcp-max-configure <n>

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#ipcp-max-failure <n>

# Set the PAP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#pap-restart <n>

# Set the maximum number of PAP authenticate-request transmissions to
# <n> (default 10).
#pap-max-authreq <n>

# Set the maximum time that pppd will wait for the peer to authenticate
# itself with PAP to <n> seconds (0 means no limit).
#pap-timeout <n>

# Set the CHAP restart interval (retransmission timeout for
# challenges) to <n> seconds (default 3).
#chap-restart <n>

# Set the maximum number of CHAP challenge transmissions to <n>
# (default 10).
#chap-max-challenge

# If this option is given, pppd will rechallenge the peer every <n>
# seconds.
#chap-interval <n>

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Disable the IPXCP and IPX protocols.
# To let pppd pass IPX packets comment this out --- you'll probably also
# want to install ipxripd, and have the Internal IPX Network option enabled
# in your kernel.  /usr/doc/HOWTO/IPX-HOWTO.gz contains more info.
noipx

# Exit once a connection has been made and terminated. This is the default,
# unless the `persist' or `demand' option has been specified.
#nopersist

# Do not exit after a connection is terminated; instead try to reopen
# the connection.
#persist

# Terminate after n consecutive failed connection attempts.
# A value of 0 means no limit. The default value is 10.
#maxfail <n>

# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.
#demand

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  Note: it is not advisable to use this option with the persist
# option without the demand option.  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
#idle <n>

# Specifies how many seconds to wait before re-initiating the link after
# it terminates.  This option only has any effect if the persist or demand
# option is used.  The holdoff period is not applied if the link was
# terminated because it was idle.
#holdoff <n>

# Wait for up n milliseconds after the connect script finishes for a valid
# PPP packet from the peer.  At the end of this time, or when a valid PPP
# packet is received from the peer, pppd will commence negotiation by
# sending its first LCP packet.  The default value is 1000 (1 second).
# This wait period only applies if the connect or pty option is used.
#connect-delay <n>

# Packet filtering: for more information, see pppd(8)
# Any packets matching the filter expression will be interpreted as link
# activity, and will cause a "demand" connection to be activated, and reset
# the idle connection timer. (idle option)
# The filter expression is akin to that of tcpdump(1)
#active-filter <filter-expression>

# ---<End of File>---


Does anyone know what I'm doing wrong, or why I can't get dial-up working? Many thanks,

   Jon

---

### Post by rocky5051 on 2009-05-22
I can't say since I've little experience with pppd. What I can say is I use simple pon/poff to connect. You could try setting up a connection using pppconfig using pon to connect with the configured connection, and see if that helps.

Other than that, I don't know.

Instructions for what I mentioned.

1) Use pppconfig in terminal to setup a connection
```
sudo pppconfig
```

2) Use pon to connect, exchanging <yourconnection> for what you named your connection in pppconfig
```
sudo pon <yourconnection>
```

3) Assuming it works, open a terminal later when you are done using the internet and use poff to end the connection
```
sudo poff
```

---

### Post by NZJon on 2009-05-24
Hi Rock5051,

Thanks for your suggestion. I'll try it at home this evening. Fingers crossed... ;)

Jon

---

### Post by NZJon on 2009-05-25
Hi rocky5051,

Your suggestion works--I can now "pon" and "poff" a dial up connection!!

I just need to work out how to make it "user friendly" for my wife...

Many thanks,

   Jon

---

### Post by rocky5051 on 2009-05-27
> **NZJon said:**
> Hi rocky5051,

Your suggestion works--I can now "pon" and "poff" a dial up connection!!

I just need to work out how to make it "user friendly" for my wife...

Many thanks,

   Jon

Well, the simplest way I could think of making it user friendly (not that pon/poff isn't user friendly considering writing out variables manually to connect with pppd is a much more straining process) would probably be to create two program launchers.

One program launcher can set off the command to connect, and one to stop it. I wonder if that will work considering it involves sudo, but it'd be worth a shot.

The other alternative (if you know how to make a gui with a script or in some other coding language) would be to make a graphical interface with Connect and Disconnect buttons. I'd do it for you but I don't know enough scripting to do that I'm afraid.

Best of luck. ):P

---

### Post by NZJon on 2009-05-27
Ah yes, it should indeed be simple... My next quest begins... Cheers, Rocky.

   Jon

---

### Post by maddogz420 on 2009-06-15
hello, im having trouble getting my winmodem to work properly, ive followed post #4 and it connects, but nothing will work (firefox, etc), using 9.04

connection log (2 attempts): [http://pastebin.com/m253884c0](http://pastebin.com/m253884c0)

modem info: [http://pastebin.com/m10d96aee](http://pastebin.com/m10d96aee)


Edit: added in dns, now this [http://pastebin.com/m366dd480](http://pastebin.com/m366dd480)

---

### Post by maddogz420 on 2009-06-17
I'm not one to 'bump', but ffs, please help me get off windows.

Maybe its a simple setting im missing. Maybe i didnt compile drivers correctly, but please. WTB Ubuntu.

---

### Post by GeorgeVita on 2009-06-17
Hi **maddogz420**,
as you are connected, start Firefox and check if it is in Offline Mode.

Press **ALT-F** (File) and then **W** to toggle offline mode.

Regards,
George

---

### Post by maddogz420 on 2009-06-17
Thanks, but thats not the problem. It just hangs on 'Looking up whatever.com...' Other applications will also not connect. 

It seems the dial up has made a full connection, but no data will transfer >< I can only get a ping response from the IP address in 'destination' when connected.




EDIT:

sudo route add default ppp0
^ that was the problem. Now to figure out how I can have it set so I don't have to do that each time I connect.

---

### Post by rocky5051 on 2009-06-23
> **maddogz420 said:**
> sudo route add default ppp0
^ that was the problem. Now to figure out how I can have it set so I don't have to do that each time I connect.

Make an .sh file in your home directory, and, assuming you're using pon/poff, you could do something like this:

```
sudo route add default ppp0
sudo pon <yourconnection>
```

Then run the script like this, expecting it to run the command you need and connect:

```
sh script.sh
```

There's probably a better way, but I can't think of anything.

---

### Post by jasmineaura on 2009-07-18
> **rocky5051 said:**
> Okay, I had this same problem two (one of two blockers which prevented me from using Ubuntu 8.10), and I've figured out a workaround.

Download the pre-made package mentioned here. Don't bother making it yourself, as it is unnecessary:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

Download and save the archive to your desktop, and extract it.
```
tar -xvf $HOME/Desktop/hsfmodem-7.80.02.03full-dellhybrid.tar.gz
```Now go into the directory of the extracted folder, make install it.
```
cd hsfmodem-7.80.02.03full && sudo make install
```This next part wasn't entirely obvious, but you'd be surprised what one little hack can do. The osservices header file which is installed as part of the hsfmodem module references the stings header files from the generic linux headers. For whatever reason, it seems in Ubuntu 9.04 it references the wrong directory for the file, and thus much be changed for the hsfmodem module to compile successfully. Change "string.h" in line 356 of the "osservices.h" file to "linux/strings.h".
```
sudo gedit /usr/lib/modules/hsfmodem/imported/include/osservices.h
```Save it as normal and close gedit. Now, run hsfconfig, follow it's instructions and there should be no more errors.
```
sudo hsfconfig
```In fact, to back the success I've had with this little change, I can say with all honesty that I'm posting in Ubuntu 9.04 with the hybrid dell/linuxant driver working. :D

Hope that helps.

Minor correction to some typos in Rocky5051's instructions:

The correct file to edit is:
```
nano /usr/lib/hsfmodem/modules/imported/include/osservices.h
```*Note in the original instructions "hsfmodem" and "modules" were reversed*

On line 356, change "**string.h**" to "**linux/string.h**"
*Note in the original instructions it said to change it to "linux/string**s**.h" which is incorrect...*

---

