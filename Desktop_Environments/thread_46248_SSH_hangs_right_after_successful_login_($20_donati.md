---
title: "SSH hangs right after successful login ($20 donation reward)"
date: 2005-07-03
forum: Desktop Environments
---

### Post by Jonathan Drain on 2005-07-03
**I have had this problem since February and nobody has been able to solve it. I will donate _$20 USD_ to the ubuntulinux forums if you can solve this problem for me.**

The "ssh" command does not work for me; it stalls after I have entered my password correctly. However, if I use the exact same settings with PuTTY, I can connect without problem. I think I may have the same problem as this guy:

[http://lists.debian.org/debian-ssh/2005/02/msg00036.html](http://lists.debian.org/debian-ssh/2005/02/msg00036.html) 

Here's the result of "ssh -vv user@hostname":

```

jdigital@thundaril:~ $ ssh -vv jdigital@akarihosting.net
OpenSSH_4.1p1 Debian-4ubuntu1, OpenSSL 0.9.7e 25 Oct 2004
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to akarihosting.net [65.110.55.40] port 22.
debug1: Connection established.
debug1: identity file /home/jdigital/.ssh/identity type -1
debug1: identity file /home/jdigital/.ssh/id_rsa type -1
debug1: identity file /home/jdigital/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.4p1 Debian 1:3.4p1-1.woody.3
debug1: match: OpenSSH_3.4p1 Debian 1:3.4p1-1.woody.3 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-4ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 121/256
debug2: bits set: 534/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'akarihosting.net' is known and matches the RSA host key.
debug1: Found key in /home/jdigital/.ssh/known_hosts:1
debug2: bits set: 504/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/jdigital/.ssh/identity ((nil))
debug2: key: /home/jdigital/.ssh/id_rsa ((nil))
debug2: key: /home/jdigital/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jdigital/.ssh/identity
debug1: Trying private key: /home/jdigital/.ssh/id_rsa
debug1: Trying private key: /home/jdigital/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
jdigital@akarihosting.net's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

```

...after which it simply hangs there with a blinking cursor. This occurs regardless of which server I connect to, and Linux PuTTY, Windows PuTTY under WINE and Windows PuTTY on Windows on the same computer work perfectly. This failure to connect only occurs when using the "ssh" command (openssh-client). I do not want to use PuTTY because it's fugly and old-fashioned and doesn't handle copy-paste properly like a proper command-line program does.

I have even tried upgrading to the Breezy version of ssh, to no luck. For $20, can anyone tell me how to fix my problem?

---

### Post by cwaldbieser on 2005-07-04
I looked over some of your older posts, and it looks like you have tried lots of different things.  There were a couple things I was not clear if you have tried:

1) What version of ssh are you using?
2) Have you tried connecting with any other versions of ssh (output of ssh -v)?
3) Have you tried ssh with different ssh client machines?  For example, can you ssh to the machine from a LiveCD like knoppix?  From maybe an old Slackware installation you have sitting around?  From Cygwin on your Windows box?
4) Are there any ssh servers you can connect to successfully?  If so, (and assuming your debug output doesn't show your password or other sensetive info), could you you provide that debug dump so we have something to compare to your problem dump?

Also, do you have any experience working with a network tool like Ethereal?  Maybe monitoring the actual network traffic would give you some clues as to whats going on (e.g. is Putty handling the protocol differently than ssh?

---

### Post by Jonathan Drain on 2005-07-04
I am using this version: "OpenSSH_4.1p1 Debian-4ubuntu1, OpenSSL 0.9.7e 25 Oct 2004" - It's the Breezy version of ssh (I use Hoary but updated to Breezy's ssh to see if it would fix anything, and it didn't.) I had the same problem when using the default version that comes with Warty, and the default version that comes with Hoary.

I haven't tried sshing from another machine; I have no other Linux machines. I'll use my Gnoppix LiveCD in a few days when my Windows machines come back from a LAN party.

There are no ssh servers I can connect to successfully, out of the five I've tried. All have this problem.

I've never used Ethereal or such.

If I wait long enough after it gives me "debug2: channel 0: open confirm rwindow 0 rmax 32768" and hangs, it gives me this and quits:

```

debug1: channel 0: free: client-session, nchannels 1
Read from remote host akarihosting.net: Connection timed out
Connection to akarihosting.net closed.
debug1: Transferred: stdin 0, stdout 0, stderr 102 bytes in 1160.8 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.1
debug1: Exit status -1

```

---

### Post by cwaldbieser on 2005-07-04
It might be useful if you were to learn to use the basics of ethereal or some other packet sniffer to find out what is happening "on the wire".  It has a pretty nice GUI, and it is available for Windows.  Sometimes when I am doing some sort of network programming, I find it useful to see if the messages  I am sending to / receiving from the server are what I expect them to be.

This is how I start a simple session:  I start ethereal using sudo (so I have permission for some of the administrative features).  I set up the coloring rules for the protocol (in your case, ssh) that I want to observe.  There is a toolbar button on the right side of the toolbar for this.  I normally clear out the filter and then use the dialogs to construct a color filter like "SSH is present".  Then I start monitoring by pressing the toolbar button on the left (start a new live capture).  If you have more than one network card, you choose the one you want to monitor, check off various options (like name resolution and update in real time) and off you go!  The packets that match the protocol you set up will stand out in the colors you chose.

You can right click on a given line and choose "Follow TCP Stream" to follow a particular transmission.  I would suggest doing this for both an ssh session and a PuTTY session.  Then the output can be compared, and you can see how the two implementations are handling the protocol in different manners.

---

### Post by Jonathan Drain on 2005-07-04
I am baffled as to what these streams of hex mean, but:

With ssh, it does "Client: New Keys", and sends a bunch of encrypted reponse/request packets back and forth. Request len=48, response len=48, request len=64, response len=80. Request len=96, response len=80. Request len=144, response len=32. Request packet length 64, response packet length 48, request packet length 448. I then see a [TCP Retransmission] of the request packet length 448 (presumably the same packet again), and a [TCP Out-of-Order] response packet length 48. It continues like this over and over until I quit the program.

With PuTTY, it gets to "Client: New Keys" and does a similar kind of thing, though with different packet lengths. It doesn't get stuck on this TCP retransmission/out-of-order thing, though. As I am no network expert I cannot fathom why this is.

Does this shed any light on what's going wrong?

---

### Post by Jonathan Drain on 2005-07-04
Aha, I can be more specific here.

Using "ssh". It comes to password entry. To test, I enter the wrong password. Ethereal shows a request packet, length 144. The reply comes back "Permission denied, please try again": response packet length 80.

I enter the correct password. ssh -v:

```

debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8

```

...whereupon it hangs. Ethereal meanwhile shows this: Request packet length 144 (me entering my password), response packet length 32 (presumably "debug1: Authentication succeeded (password)."). Then is a request packet length 64, a response packet length 48, a request packet 448. Then comes the [TCP Retransmission] of the 448 length request packet, and the [TCP Out-Of-Order] on the 48 length response packet. This 448/48 repeats ad infinitum.

---

### Post by cwaldbieser on 2005-07-05
I will have to cogitate on this new information for a bit.  

Do you think you could post the ethereal session dumps for ssh and PuTTY as attachments?  I feel though that I should point out that if you do post the dumps, they would be encrypted, but include the transmitted password info.  I personally do not know what would be required to break such an encryption, but if possible, it would be a good idea to change your ssh password to something else, conduct the tests, change your password back to its original form, and then post the dumps so as to not make any sensitive info publicly available.

I tried SSHing to my loopback device and recorded it in ethereal to see what differences I may have from what you described.  My session goes something like this:

```

Server Protocol: SSH-2.0-OpenSSH 3.9p1 Debian-1ubuntu2
Client Protocol: SSH-2.0-OpenSSH 3.9p1 Debian-1ubuntu2
Client: Key Exchange Init
Server: Key Exchange Init
Client: Diffie-Hellman GEX Request
Server: Diffie-Hellman Key Echange Reply
Client: Diffie-Hellman GEX Init
Server: Diffie-Hellman GEX Reply
Client: New Keys
Encrypted Request Packet
[repeated for the length of the session]

```

I will also be interested to learn how the ssh session with your LiveCD goes.  

Do you have sshd installed on your Ubuntu box?  If so, could you see if you can ssh to the loopback (127.0.0.1)?  If you are unable to establish a session this way, we could at least be reasonably sure the issue is related to the ssh software itself (as opposed to an issue with the network card or something peculiar to your network).

---

### Post by Jonathan Drain on 2005-07-05
I installed sshd to test and I can successfully ssh into myself.

Although I'm not sure what this means, it seems to get stuck on this Encrypted Request Packet of length 448 and the Encrypted Reply Packet of length 48.

---

### Post by cwaldbieser on 2005-07-05
Well, that suggests that the ssh software isn't the problem.  It may be the way the software interacts with the NIC or something on your network (like a firewall blocking the traffic).

Do you have another network card you can try out in your Ubuntu machine?  If it still fails with a different NIC, then it is probably something to do with the network setup.

---

### Post by arosct on 2005-07-06
You may check your settings in '/etc/ssh/ssh_config'. The settings there must be compatible with the one from the foreign host (Protocol, X11, etc).

---

### Post by Jonathan Drain on 2005-07-07
I have just attempted to run ssh with the Gnoppix LiveCD, first in my own computer and then in a computer on the same network, and I had the same problem that I've been having both times.

---

### Post by alastair on 2005-07-07
I've been here before - but not as often as you :-)

We have to try and eliminate the possibilities. You say "a computer on the same network" - so the same CD booted gave the same result on a different machine?

 - same network card and same network driver?

Common - gateway? router? ISP?

Can you try booting this CD on a different network system somewhere (preferably different gateway/ISP) and try?

---

### Post by cwaldbieser on 2005-07-08
Hmm, sounds more and more like a network problem.  Can you do a traceroute from your Ubuntu computer to the ssh server?  What computers and routers on your own network does the traffic pass through?  Is there any possibility that the traffic is passing through an authenticating proxy or something of that nature?

Do you have this same sort of problem with any other protocols?  Can you telnet or ftp between these machines (warning-- those protocols are insecure).  Can you scp or sftp between those machines?

---

### Post by Jonathan Drain on 2005-07-08
To clarify, I used the same LiveCD (gnoppix-1.0-i386.iso) on two computers, one that is my Ubuntu machine, the other that is usually a Windows machine. I don't know if they have the same network card or not; they're both using cheap generic network cards as far as I know.

They both use the same ISP (BT Internet). I'm not entirely sure which piece of equipment is doing what, but my network setup is as follows: Each of the three computers is connected by a network cable into a five-port hub by a regular network cable. Also plugged into the hub is the DSL modem, a D-Link 300T, which also plugs into the phone line. The network mysteriously only functions when I have one computer set to DHCP and the rest set with manual IPs.

Traceroute:
```

traceroute to akarihosting.net (65.110.55.40), 30 hops max, 38 byte packets
 1  192.168.1.1 (192.168.1.1)  0.542 ms  4.499 ms  0.516 ms
 2  217.47.207.58 (217.47.207.58)  16.285 ms  16.089 ms  20.425 ms
 3  217.47.207.161 (217.47.207.161)  15.418 ms  16.133 ms  13.945 ms
 4  217.41.174.9 (217.41.174.9)  15.510 ms  18.864 ms  34.419 ms
 5  217.41.174.66 (217.41.174.66)  16.162 ms  24.729 ms  20.424 ms
 6  217.41.174.118 (217.41.174.118)  18.390 ms  18.300 ms  18.169 ms
 7  217.41.174.46 (217.41.174.46)  14.779 ms  15.549 ms  15.874 ms
 8  217.47.95.50 (217.47.95.50)  15.370 ms  15.359 ms  17.671 ms
 9  core2-pos15-1.edinburgh.ukcore.bt.net (62.6.199.213)  117.757 ms  185.423 ms  208.102 ms
10  core2-pos15-2.birmingham.ukcore.bt.net (194.74.16.237)  22.090 ms  22.810 ms  24.302 ms
11  core2-pos15-3.reading.ukcore.bt.net (194.74.16.250)  24.280 ms  25.005 ms  23.384 ms
12  core2-pos13-1.ealing.ukcore.bt.net (62.6.196.242)  30.952 ms  27.850 ms  27.176 ms
13  transit2-pos6-0.ealing.ukcore.bt.net (194.72.17.198)  26.166 ms  26.272 ms 27.252 ms
14  t2c2-p1-0.uk-eal.eu.bt.net (166.49.168.37)  28.820 ms  28.160 ms  27.136 ms
15  so-6-0-0-0.gar2.London2.Level3.net (212.113.11.253)  27.501 ms  26.213 ms  29.298 ms
16  ge-0-3-0.bbr2.London2.Level3.net (4.68.124.65)  26.571 ms  27.145 ms  27.084 ms
17  as-1-0.mp1.Miami1.Level3.net (64.159.0.1)  123.879 ms  124.994 ms  125.267 ms
18  as-0-0.mp2.Tampa1.Level3.net (209.247.11.198)  127.980 ms as-2-0.mp1.Tampa1.Level3.net (209.247.11.201)  127.831 ms as-0-0.mp2.Tampa1.Level3.net (209.247.11.198)  129.754 ms
19  ge-1-1-51.car3.Tampa1.Level3.net (4.68.104.6)  129.238 ms 4.68.104.102 (4.68.104.102)  128.520 ms ge-1-1-53.car3.Tampa1.Level3.net (4.68.104.70)  129.524 ms20  4.79.172.2 (4.79.172.2)  130.133 ms  129.507 ms  131.996 ms
21  gi0-1.ds01.tpa.sagonet.net (65.110.32.8)  129.293 ms  129.516 ms  129.985 ms22  unknown.sagonet.net (65.110.55.40)  128.842 ms  129.480 ms  129.226 ms

```

However, it affects all four servers I have ssh accounts on, not just this one.

I can FTP into those machines just fine. In fact, I can ssh into them if I use PuTTY for Linux, or PuTTY for Windows under WINE.

---

### Post by cwaldbieser on 2005-07-08
This one is a stumper!  The packet dumps don't especially reveal anything to me.  I don't know enough about the TCP protocol to understand what causes the out-of-order and retransmission messages we are seeing in the TCP stream.  I will try to research it a little more.

The only other experiment that comes to mind would require that you have a notebook and a friend with a connection to the same ISP.  You could boot up the laptop with the LiveCD and try plugging into your friend's network to see if you could ssh to the server from there.

---

### Post by cwaldbieser on 2005-07-09
I found that it is possible to fiddle with your TCP settings, though I am not sure if that will help.

```
$ ls /proc/sys/net/ipv4
```

shows a bunch of the ipv4 settings for your computer.  If you want to view one, you can cat it:

```
$ cat /proc/sys/net/ipv4/tcp_retries1
3
```

If you want to change it, you echo to it:

```
$ sudo sh
# echo "5" > /proc/sys/net/ipv4/tcp_retries1
```

You can get an explanation of various tcp settings with:

```
$ man tcp
```

I will have to study them a little more to really understand them, but the tcp_retries1 and tcp_retries2 settings (defaults 3 and 15) look like you could try different values and see if that affects your connection.

---

### Post by Jonathan Drain on 2005-07-15
Changing the tcp_retries1 and tcp_retries2 has no effect.

I don't have a laptop or a friend with a laptop to test the theory. I can only presume that it is a fault with my network somehow. A friend suggests that PuTTY is sending more packets, but smaller packets, while ssh is sending one big 448-length packet. I'm having this mental image of the 448-length packet as a big fat guy getting stuck in a narrow doorway.

---

### Post by cwaldbieser on 2005-07-16
Well, if that is the case, maybe you could try adjusting the Maximum Transmission Unit of your network interface?  The command

```
$ ifconfig
```

will display all sorts of information about your network cards.  The MTU setting is the maximum transmission unit.  The maximum (and default) for Ethernet is 1500.  You could try setting it to some small value like 296.  The command syntax  would be:

```
$ sudo ifconfig eth0 mtu 296
```

If that doesn't work, try posting the output of ifconfig.  Maybe someone will notice something odd about the settings that may account for your problem.

---

### Post by Jonathan Drain on 2005-07-16
That still doesn't work.

```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:0F:4A:77
          inet addr:81.156.25.196  Bcast:81.156.25.196  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1269001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1165273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:730302304 (696.4 MiB)  TX bytes:155989017 (148.7 MiB)
          Interrupt:17 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24095775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24095775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2136528289 (1.9 GiB)  TX bytes:2136528289 (1.9 GiB)

```

---

### Post by cwaldbieser on 2005-07-16
I am not sure I know what to make of that ifconfig output.  Normally, if your network is something like x.y.z.0/24, your netmask will be 255.255.255.0 and your broadcast address will be x.y.z.255.  But your netmask is 255.255.255.255, which would mean that no part of the address is reserved for individual machines on the network.

Can you explain a little bit more about your local network?  Do the other network cards connected to your LAN have any part of their IP addresses in common with your Ubuntu machine's card.  Also, what is your gateway to the Internet?  Is it a  hardware router or does one of your machines act as the gateway?

---

### Post by Jonathan Drain on 2005-07-16
Okay. I have this little green five-port hub that takes RJ45 connectors. Connected into into this are four devices. One is my Linux machine, named Thundaril. Two others are Windows 2000 machines named Floyd and Meepo. The fourth is this D-Link 300T ADSL modem, which is on an IP of 192.168.1.1.

I have my ethernet connection set to DHCP with the IP, Subnet and Gateway fields blank. Oddly, if more than one person on the network sets themself to DHCP then it causes a conflict as if they are both taking the same IP. So, everyone else sets theirs manually, instead of DHCP.

Floyd's settings are:
```

        Connection-specific DNS Suffix  . :

        IP Address. . . . . . . . . . . . : 192.168.1.184

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

```

I assume Meepo's to be the same but with a different IP.

If I type "ping floyd" or "ping meepo" I can't see them on the network (I get "unknown host" error). If I ping Thundaril I get the IP as 127.0.0.1.

My gateway to the internet is 192.168.1.1, which is my ADSL modem.

---

### Post by cwaldbieser on 2005-07-16
Well that is a somewhat strange setup, considering Thundaril's IP address.  I am not even sure why it works.  I will try to clarify my point of view.

Two network cards can talk to each other directly if they are on the same network.  If two network cards are not on the same network, they cannot talk to each other directly.  Instead, they must communicate through a router.

I mentioned Thundaril's odd network card configuration before.  Though I have never seen it's like before, I would have to say it is on a 81.156.25.196/32 network (that is, all 32 bits of the address are used for the network).  I would not have really expected that such a thing was possible.

Meepo and Floyd's network cards are on the 192.168.1.0/24 network (24 of the 32 bits are used for the network, and the last 8 identify individual machines).  Your ADSL modem is also on this network, so the modem, meepo, and floyd should all be able to talk to each other just fine.  This explains why you cannot ping meepo or floyd from thundaril.  I would expect that you couldn't ping the modem, either, though if it had a built-in router, I guess you could.

Of the 3 devices on your 192.168.1.0/24 network, you identified 2 of the addresses: 192.168.1.1 and 192.168.1.184.  There are two reserved addresses: 192.168.1.0 and 192.168.1.255.  Find out meepo's IP address as well, then pick any other address in the range 192.168.1.2 to 192.168.1.254 that has not been used and assign that address to Thundaril.

That should clear up your problem pinging meepo and flyod from thundaril.  Hopefully, it could clear up some of the other strangeness you have been having with ssh as well.

The commands to bring down your network interface and bring it back up as a specific IP address are:

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 192.168.1.27 netmask 255.255.255.0 up
```

(the 192.168.1.27 address is an example address I am just picking out of the air.  As long as it is not meepo's address, it should work).  This will change the settings until your next reboot (or you issue the command again).  You will have to edit /etc/network/interfaces to make the changes permanent.

You should also be able to set this via the GUI (make sure to fill in the 255.255.255.0 netmask).

---

### Post by Jonathan Drain on 2005-07-16
One person has to have DHCP. After a certain amount of time, nobody can connect to the internet otherwise. I don't know why. Perhaps the router is handing out DHCP but tries to give everyone the IP that the Internet sees, because if two people have it they get an "oh crap we have the same IP" conflict.

I have discovered Meepo's IP, it is 192.168.1.87. The subnet mask and default gateway are the same as Floyd's. 81.156.25.196 is my IP as the Internet sees it.

Now, my problem is that I must use DHCP, otherwise the internet's DHCP fails. Even earlier when Floyd had the DHCP and I disabled it to set my IP Address, Subnet Mask and Default Gateway manually, I had the problem with ssh.

---

### Post by cwaldbieser on 2005-07-16
It seems to me that maybe you should make one of the PCs do double duty as a router.  That would require that one of those PCs should have 2 network cards.  You would plug NIC #1 into the ADSL modem and the NIC #2 into the hub.  The other PCs could connect to the hub.  

You could set NIC #1 to use DHCP, and NIC #2 you could configure however you want to set up your network (static or dynamic).

Of course, if you don't have a spare NIC, you could probably save yourself some trouble by just going out and buying a cheap router.  Plug all of your PCs into the router, plug the router into the ADSL modem-- it works like a charm.  This is not coincidently, the kind of setup I have at home now.  

Back when I use to use dial-up, you would not believe some of the crazy software tricks I tried to share the Internet for our home PCs (we had Win95 and Win98 at the time).  Mostly, there was a lot of fooling around with proxy servers.

At this point, the only clue I have about your ssh woes is the strange state or you network.  From my (somewhat limited) viewpoint, it really just should not work the way you have it set up.  The fact that it does work (with some small exceptions) is something I am not readilly able to understand.  It may be that this is just a blind alley, but I have no other leads at this point.

If you do ever figure out what is going on with either your ssh or your network, I would be very interested to hear about it.  For now, I guess it is just back to the books for me.

Good Luck!

---

### Post by pietro_spina on 2005-07-17
Jonathan,

I think lots of internet service providers are taking steps to make it difficult to share their connections as well as limit the number of home ftp and web servers. it is likely that your provider is regularly expiring your ip address lease and reassigning a new one. (someone with command line skills could post a "cat | grep something or other"  way of showing you all the IP's you 've been assigned recently...)

Does  ssh consistently works from the dhcp computer but not the static IP's

I concur with cwaldbieser > It seems to me that maybe you should make one of the PCs do double duty as a router.
or spend that $20 on a cheap router at your local tech swap meet...

My solution was to build a little gateway out of parts I found put to the curb as trash...
P III 450
2 NIC's
a nice amount of the proper RAM
and
ati rage pro 8mb (just needed for installation - all maintenance is done through ssh and web config)

what's nice about old hardware like this is that in has no need for noisy fans... (some people like to use old point of sale computers for this.)

Just about any linux distro can be made to do what you need. But what I use is [Clarkconnect Home](http://www.clarkconnect.org/index.php) it's pretty feature rich and relatively idiot proof.

my set up: phone line connects to dsl modem then to Clarkconnect box (nic=eth0) then out of CC box (eth1) to a switch (your hub will work here) then off to all the various computers...


good luck
-p

---

### Post by Jonathan Drain on 2005-07-17
ssh did not work when Floyd used DHCP and I picked an IP myself, and does not work now that I use DHCP and Floyd picks his IP himself. I think it is that the router itself is handing out IPs every however-many seconds/minutes/etc, and if nobody's there on DHCP to take it, it doesn't know what's going on.

I just bought a graphics card for £2.50, so perhaps if I find eight more deals like this I can build a router...

---

### Post by pgas on 2005-10-04
The D-Link 300T ADSL modem causes the problem: 

[http://www.magwag.plus.com/jim/tips-300t.html](http://www.magwag.plus.com/jim/tips-300t.html)

---

### Post by dav7 on 2008-04-03
This is quite an old post, but I've had the same problem  - not on Ubuntu - but issues have been there, sshing to Debian and other boxen... I can't remember all of the distros that had this issue, but there were a couple. And the issue finally occured on my favourite distro, my distro of choice... Arch Linux.

Ouch.

Anyway, after a quick ask around on IRC and a bit of a debug of a few settings on both my end and the other end (I had VNC to the destination! :D) I set UseDNS on the **server** to 0 (after uncommenting it) in /etc/ssh/sshd_config (that's where the file is on Arch Linux, it may just possibly be elsewhere on Ubuntu), and then restarted sshd (I don't know the command for Ubuntu to do that, but on _Arch_ it's /etc/rc.d/sshd restart).

And... ssh to that machine immediately worked, no questions asked. I'll have to see if the problem pops up again, and I'm hoping it's not. Also, I'm not entirely sure what disabling UseDNS brings as side effect(s).... but since it seems to work okay, I'm not complaining. :D

-dav7

EDIT: Here's an exact duplicate of this post, complete with commands: [http://ubuntuforums.org/showthread.php?p=3189998#post3189998](http://ubuntuforums.org/showthread.php?p=3189998#post3189998)

---

