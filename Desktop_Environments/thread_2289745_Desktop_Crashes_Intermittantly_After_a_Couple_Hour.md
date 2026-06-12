---
title: "Desktop Crashes Intermittantly After a Couple Hours 14.04 Flashback Compiz"
date: 2015-08-06
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-08-06
Hello,

I'm using Flashback Compiz sessions in 14.04 and the desktop will intermittently crash after a
couple hours of use or inactivity; but more frequently due to inactivity. I originally thought this
was a problem with XScreenSaver; but it appears to be related to the X server itself. From
another one of my threads, I encounter a Crash Report about the following package:

[COLOR=#0000ff][I]xserver-xorg-core-lts-utopic2:1.16.0-1ubuntu1.2-trusty2
[/I][/COLOR]
Please see attachment.

Thanks, Hannibal

---

### Post by TheFu on 2015-08-06
Try it without compiz - it will probably stop. Stability of compiz has never been very good, IME.

---

### Post by coljohnhannibalsmith on 2015-08-07
I does it in Ubuntu too. I'm at a loss.

Thanks, Hannibal

---

### Post by TheFu on 2015-08-07
reload X, reload the gpu drivers.
Check the PSU, GPU, bad RAM.  And check that you aren't running out of swap. I have a small netbook with just 2G of RAM. By default, the install gave it 2G of swap, which wasn't enough. I experienced lockups.  Doubled the swap from 2G to 4G and the lockups stopped. So - definitely watch the memory use.

---

### Post by buzzingrobot on 2015-08-07
Unity, at least at present, is built as a Compiz plugin.  The only issue I've seen there with Compiz is that it crashes the first time the desktop icon is clicked. (Across multiple releases.) 

However, CCSM is not installed by default, and there's probably a reason.  I've found that changing settings in CCSM can often produce Compiz crashes. If FLashback requires using CCSM, or just makes changes on its own, I'd look there first.

---

### Post by coljohnhannibalsmith on 2015-08-07
> **TheFu said:**
> reload X, reload the gpu drivers.
Check the PSU, GPU, bad RAM.  And check that you aren't running out of swap. I have a small netbook with just 2G of RAM. By default, the install gave it 2G of swap, which wasn't enough. I experienced lockups.  Doubled the swap from 2G to 4G and the lockups stopped. So - definitely watch the memory use.

How do I reload X, the GPU Drivers, check the PSU and Bad Ram? I did run a ram check from the boot menu and it passed after an all night run. I did reset the swappiness to 10% make the system run faster, which it does, since I have 4GB Ram. Perhaps using Ram for swap is inherently unstable and is the reason for my crashes?

Thanks, Hannibal

---

### Post by TheFu on 2015-08-07
> **coljohnhannibalsmith said:**
> How do I reload X, the GPU Drivers, check the PSU and Bad Ram? I did run a ram check from the boot menu and it passed after an all night run. I did reset the swappiness to 10% make the system run faster, which it does, since I have 4GB Ram. Perhaps using Ram for swap is inherently unstable and is the reason for my crashes?

Thanks, Hannibal

To check hardware, swap it with other hardware and see if the issue goes away.  A spotty PSU has all sorts of bad effects that cannot be predicted.  Many computer shops will test a PSU for free. I've seen failing GPUs cause system lockups.  If your RAM passed an overnight test, I'd move on.

If you use **synaptic**, find all the xorg stuff and mark it to be reinstalled, then apply. That is a shot in the dark, but bits sometimes "rot" over time. That's the easy way. Same goes for GPU drivers. Doing it with apt-get/aptitude will be a little harder, since you'll need to make a list of the packages first, then use the reinstall option.

You aren't using RAM for swap. I wouldn't worry about that.

---

### Post by coljohnhannibalsmith on 2015-08-08
> **TheFu said:**
> If you use **synaptic**, find all the xorg stuff and mark it to be reinstalled, then apply. That is a shot in the dark, but bits sometimes "rot" over time.


Thanks for the tip. This is a lot more stable. BTW, I've noticed bit-rot in the field and at home. Back in the day, I once encountered an entire box of 5 1/4" floppy disks that apparently had something wrong with the magnetic coating and would become demagnetized after about 30 mins. You wouldn't notice anything wrong right away; so you wouldn't notice anything until the next session. I've also noticed HDD controllers going bad would cause this; necessitating a mother board swap. Since I've been paying close attention, I've noticed some other unusual behaviour. I'm using a screensaver called Atlantis, which shows whales and sharks swimming. When one of the whales swims very fast, the screen will blink; and for a moment, I will get a glimps of whatever window's open on the desktop. This is usually FireFox playing music on YouTube. [COLOR=#ff0000]*The only problem is that the window will display inverted.*[/COLOR] I've watched this happen several times already. The other thing I've noticed is that when YouTube encounters an error and the music stops playing, I will sometimes get logged out.  This has happened maybe four times in the last three weeks.  I'm thinking Shockwave Flash is probably what's responsible for locking-up the desktop; but not for logging me out. I have to blame this on the distro. Any thoughts on resolving this, possibly by going to synaptic and reinstalling some packages?

Hannibal

---

### Post by TheFu on 2015-08-08
If you want to see what locks up the desktop, ssh into the machine after that happens and look at the running processes. Which is sucking all the I/O, all the RAM, all the CPU?

Generally, if there is an issue on a system and anything from Adobe is running, it is Adobe at fault.

I wouldn't be too quick to blame anything else where flash is involved. They make crap code.  I've run their code to profilers before - lots of stupid stuff in there - like calling gettimeofday() 1,000 times in a second over and over and over. Talk about a way to kill performance.

---

### Post by MartyBuntu on 2015-08-08
> **TheFu said:**
> If you want to see what locks up the desktop, ssh into the machine after that happens and look at the running processes.

That's actually a pretty good idea.

---

### Post by coljohnhannibalsmith on 2015-08-08
> **TheFu said:**
> If you want to see what locks up the desktop, ssh into the machine after that happens and look at the running processes. Which is sucking all the I/O, all the RAM, all the CPU?

Ok, I have 2 Ubuntu Laptops. Can I ssh from one into the other; and will I need a cable? I've never done this before.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-10
Bump.

I've been trying to ssh; but I don't think I'm getting the syntax right. I keep getting connection refused or time-out errors. BTW, I keep getting error reports from this package, after I log back in:

[COLOR=#0000ff][I]xserver-xorg-core-lts-utopic2:1.16.0-1ubuntu1.2-trusty2


[/I][/COLOR]

---

### Post by TheFu on 2015-08-11
If you don't provide details, how can anyone help?
Always post the actual commands used and any **relevant** output.

---

### Post by coljohnhannibalsmith on 2015-08-11
Sorry:

```
john@john-Inspiron-5520:~$ ssh sophie@99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ sophie@sophie-Inspiron-1545
sophie@sophie-Inspiron-1545: command not found
john@john-Inspiron-5520:~$ ssh sophie@sophie-Inspiron-1545
ssh: Could not resolve hostname sophie-inspiron-1545: Name or service not known
john@john-Inspiron-5520:~$ ssh sophie@sophie-Inspiron-1545:
ssh: Could not resolve hostname sophie-inspiron-1545:: Name or service not known
john@john-Inspiron-5520:~$ 
```

---

### Post by TheFu on 2015-08-11
Is 99.196.146.177 running openssh-server on port 22?
Is port 22 open in the firewall?

Where did "sophie-Inspiron-1545" come from?  Can you ping using that name? If not, you have a DNS issue to fix.

---

### Post by coljohnhannibalsmith on 2015-08-11
> **TheFu said:**
> Is 99.196.146.177 running openssh-server on port 22?
Is port 22 open in the firewall?

Where did "sophie-Inspiron-1545" come from?  Can you ping using that name? If not, you have a DNS issue to fix.

1.
```
sophie@sophie-Inspiron-1545:~$ service ssh status
status: Unknown job: ssh
sophie@sophie-Inspiron-1545:~$ sudo service ssh status
[sudo] password for sophie: 
ssh start/running, process 972
sophie@sophie-Inspiron-1545:~$ sudo ufw allow ssh
Skipping adding existing rule
Skipping adding existing rule (v6)
sophie@sophie-Inspiron-1545:~$ sudo ufw allow 22
Skipping adding existing rule
Skipping adding existing rule (v6)
sophie@sophie-Inspiron-1545:~$ sudo ufw disable
Firewall stopped and disabled on system startup
sophie@sophie-Inspiron-1545:~$ 

```

2.
sophie-Inspiron-1545 is the target machine.

3.
Here's the output from the last step:

```
john@john-Inspiron-5520:~$ ssh sophie@99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ sudo ssh sophie@99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ sudo ssh sophie@99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ ping sophie@sophie-Inspiron-1545
ping: unknown host sophie@sophie-Inspiron-1545
john@john-Inspiron-5520:~$ ping sophie@99.196.146.177
ping: unknown host sophie@99.196.146.177
john@john-Inspiron-5520:~$ ping 99.196.146.177
PING 99.196.146.177 (99.196.146.177) 56(84) bytes of data.
64 bytes from 99.196.146.177: icmp_seq=1 ttl=64 time=0.761 ms
64 bytes from 99.196.146.177: icmp_seq=2 ttl=64 time=0.814 ms
64 bytes from 99.196.146.177: icmp_seq=3 ttl=64 time=0.792 ms
^C
--- 99.196.146.177 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.761/0.789/0.814/0.021 ms
john@john-Inspiron-5520:~$ ssh 99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ ssh sophie@99.196.146.177
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$
```

I've been trying unsuccessfully to find an ssh tutorial for tunneling into another machine. Most of the tutorials I've found are for people who are trying to tunnel into a web server.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-11
I think I've gotten a little farther along:

```
john@john-Inspiron-5520:~$ ssh -vvvvv sophie@99.196.146.177
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 99.196.146.177 [99.196.146.177] port 22.
debug1: connect to address 99.196.146.177 port 22: Connection refused
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ sudo ssh -vvvvv sophie@99.196.146.177
[sudo] password for john: 
Sorry, try again.
[sudo] password for john: 
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 99.196.146.177 [99.196.146.177] port 22.
debug1: connect to address 99.196.146.177 port 22: Connection refused
ssh: connect to host 99.196.146.177 port 22: Connection refused
john@john-Inspiron-5520:~$ sudo sshd -T
port 22
protocol 2
addressfamily any
listenaddress 0.0.0.0:22
listenaddress [::]:22
usepam 1
serverkeybits 1024
logingracetime 120
keyregenerationinterval 3600
x11displayoffset 10
maxauthtries 6
maxsessions 10
clientaliveinterval 0
clientalivecountmax 3
permitrootlogin without-password
ignorerhosts yes
ignoreuserknownhosts no
rhostsrsaauthentication no
hostbasedauthentication no
hostbasedusesnamefrompacketonly no
rsaauthentication yes
pubkeyauthentication yes
kerberosauthentication no
kerberosorlocalpasswd yes
kerberosticketcleanup yes
gssapiauthentication no
gssapikeyexchange no
gssapicleanupcredentials yes
gssapistrictacceptorcheck yes
gssapistorecredentialsonrekey no
passwordauthentication yes
kbdinteractiveauthentication no
challengeresponseauthentication no
printmotd no
printlastlog yes
x11forwarding yes
x11uselocalhost yes
permittty yes
strictmodes yes
tcpkeepalive yes
permitemptypasswords no
permituserenvironment no
uselogin no
compression delayed
gatewayports no
usedns yes
allowtcpforwarding yes
useprivilegeseparation yes
pidfile /var/run/sshd.pid
xauthlocation /usr/bin/xauth
ciphers 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,arcfour128,arcfour256,aes128-cbc,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
macs hmac-sha1,hmac-sha1-96,hmac-sha2-256,hmac-sha2-512,hmac-md5,hmac-md5-96,hmac-ripemd160,hmac-ripemd160@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha1-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-md5-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-ripemd160-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com
versionaddendum 
kexalgorithms diffie-hellman-group1-sha1,diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group-exchange-sha256,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group1-sha1,curve25519-sha256@libssh.org
loglevel INFO
syslogfacility AUTH
authorizedkeysfile .ssh/authorized_keys .ssh/authorized_keys2
hostkey /etc/ssh/ssh_host_rsa_key
hostkey /etc/ssh/ssh_host_dsa_key
hostkey /etc/ssh/ssh_host_ecdsa_key
hostkey /etc/ssh/ssh_host_ed25519_key
acceptenv LANG
acceptenv LC_*
authenticationmethods
subsystem sftp /usr/lib/openssh/sftp-server
maxstartups 10:30:100
permittunnel no
ipqos lowdelay throughput
rekeylimit 0 0
permitopen any
john@john-Inspiron-5520:~$ 

```

---

### Post by TheFu on 2015-08-12
> 99.196.146.177 port 22: Connection refused
If you are on the same LAN, don't use public IPs. Use the LAN IPs for now.

Means something between you and there is blocking.
That is either the sshd_config, the firewall on the system or some network firewall.

Let's step back.
a) Does sophia have a static IP for the system on the LAN?
b) Has the edge router been setup to forward port 22/tcp from the WAN to the LAN IP?
c) Are inbound connections allowed by the router firewall?
d) Does the ISP block inbound connections?

BTW - I prefer hostnames that are shorter, no capitalization, no special characters, and have a FQDN if going over the internet.  

Why?  ssh won't have an issue, but millions of scripts written by people like me will assume these things - that is especially important for hostnames with capitals. I never force all tolower for comparisons because in professionally managed network, we don't mix case for hostnames (at least not on Unix networks). It just isn't done.

Why have a FQDN?  That way it is clear when you are on the LAN or on the WAN. It really is that simple.  I make very different security decisions with on the LAN than over the internet.

---

### Post by coljohnhannibalsmith on 2015-08-12
> **TheFu said:**
> If you are on the same LAN, don't use public IPs. Use the LAN IPs for now.

Means something between you and there is blocking.
That is either the sshd_config, the firewall on the system or some network firewall.

Let's step back.
a) Does sophia have a static IP for the system on the LAN?
b) Has the edge router been setup to forward port 22/tcp from the WAN to the LAN IP?
c) Are inbound connections allowed by the router firewall?
d) Does the ISP block inbound connections?

BTW - I prefer hostnames that are shorter, no capitalization, no special characters, and have a FQDN if going over the internet.  

Why?  ssh won't have an issue, but millions of scripts written by people like me will assume these things - that is especially important for hostnames with capitals. I never force all tolower for comparisons because in professionally managed network, we don't mix case for hostnames (at least not on Unix networks). It just isn't done.

Why have a FQDN?  That way it is clear when you are on the LAN or on the WAN. It really is that simple.  I make very different security decisions with on the LAN than over the internet.

I'm not on a LAN. I have Exede Satellite Internet at my house. The target machine is connected to the Internet through the Ethernet pass-through on my wireless router. The machine attempting to create the tunnel is connected wirelessly to my router. My ISP does not block incoming connections. Both IPs are assigned dynamically by my ISP. I have a web based tool to look this up when they change. [COLOR=#0000ff]*I could run a cat 6 cable between the two machines and try to connect that way. Will that work with ssh?*[/COLOR]

Thanks, Hannibal

---

### Post by TheFu on 2015-08-12
> **coljohnhannibalsmith said:**
> I'm not on a LAN. I have Exede Satellite Internet at my house. The target machine is connected to the Internet through the Ethernet pass-through on my wireless router. The machine attempting to create the tunnel is connected wirelessly to my router. Both IPs are assigned dynamically by my ISP. I have a web based tool to look this up when they change. [COLOR=#0000ff]*I could run a cat 6 cable between the two machines and try to connect that way. Will that work with ssh?*[/COLOR]

Thanks, Hannibal

So - I'm not sure we are talking the same things for the networking. Please post **ifconfig** for both systems and the WAN IPs for both sides. 

ssh uses normal networking. There is nothing special about it - web traffic uses the same stuff. If the two systems are connected on the same LAN, with a router, that should work.  Directly connecting means you have to deal with routing manually. Are you prepared for that?   Plus you would need a **[cross-over cable]("https://en.wikipedia.org/wiki/Ethernet_crossover_cable")** or NIC hardware that handles it automatically.

If you like, I can run a scan of your network to see what is open.
I suspect the satellite provider blocks inbound connections - so using the LAN connection will probably be required. Call your ISP and ask them which inbound ports are not blocked. I read their FAQ and it appears they proxy all web content. That is concerning.  [http://www.exede.com/off-the-grid-techie-blogs-via-exede/](http://www.exede.com/off-the-grid-techie-blogs-via-exede/) says that ssh works.

---

### Post by coljohnhannibalsmith on 2015-08-12
I just went to my router configuration page and noticed that Enable Wireless Isolation was checked. Based on Netgear's description of this feature, it would definitely interfere with ssh; so I unchecked it. I called my ISP this morning and they said that they do not block incoming connections. I'll read the information you provided; and post my findings.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-12
Nothing worked. This is going to take a lot more research on my part. I'm going to leave the thread open in the meantime.

---

### Post by workshopsystems on 2015-08-13
first you need to check some things

1 ) do you have a graphics card installed and that you have right driver installed if you have an on board graphics card then ignore this just make sure xorg drivers are updated and that your not using a bleeding edge xorg driver
2 ) check your xorg logs for what happened and debug the error

---

### Post by coljohnhannibalsmith on 2015-08-13
I'm not using a graphics card. I'm using two Dell Inspiron Laptops.

Here are the log files:

xorg.failsafe.log:

```
[  3254.352] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[  3254.352] X Protocol Version 11, Revision 0
[  3254.352] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[  3254.352] Current Operating System: Linux sophie-Inspiron-1545 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64
[  3254.352] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-45-generic root=UUID=7fcc521f-9d61-496f-b634-45b408570bf0 ro quiet splash vt.handoff=7
[  3254.352] Build Date: 12 February 2015  11:11:26PM
[  3254.352] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[  3254.352] Current version of pixman: 0.30.2
[  3254.353]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  3254.353] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3254.353] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Aug 12 22:59:09 2015
[  3254.353] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[  3254.353] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3254.353] (==) No Layout section.  Using the first Screen section.
[  3254.353] (**) |-->Screen "Default Screen" (0)
[  3254.353] (**) |   |-->Monitor "Configured Monitor"
[  3254.353] (**) |   |-->Device "Configured Video Device"
[  3254.353] (==) Automatically adding devices
[  3254.353] (==) Automatically enabling devices
[  3254.354] (==) Automatically adding GPU devices
[  3254.354] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3254.354]     Entry deleted from font path.
[  3254.354] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3254.354]     Entry deleted from font path.
[  3254.354] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3254.354]     Entry deleted from font path.
[  3254.354] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3254.354]     Entry deleted from font path.
[  3254.354] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3254.354]     Entry deleted from font path.
[  3254.354] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  3254.354] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3254.354] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3254.354] (II) Loader magic: 0x7fe8013b4c80
[  3254.354] (II) Module ABI versions:
[  3254.354]     X.Org ANSI C Emulation: 0.4
[  3254.354]     X.Org Video Driver: 18.0
[  3254.354]     X.Org XInput driver : 21.0
[  3254.354]     X.Org Server Extension : 8.0
[  3254.354] (II) xfree86: Adding drm device (/dev/dri/card0)
[  3254.356] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[  3254.356] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[  3254.357] (II) LoadModule: "glx"
[  3254.357] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3254.359] (II) Module glx: vendor="X.Org Foundation"
[  3254.359]     compiled for 1.16.0, module version = 1.0.0
[  3254.359]     ABI class: X.Org Server Extension, version 8.0
[  3254.359] (==) AIGLX enabled
[  3254.359] (II) LoadModule: "fbdev"
[  3254.359] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3254.360] (II) Module fbdev: vendor="X.Org Foundation"
[  3254.360]     compiled for 1.16.0, module version = 0.4.4
[  3254.360]     Module class: X.Org Video Driver
[  3254.360]     ABI class: X.Org Video Driver, version 18.0
[  3254.360] (II) FBDEV: driver for framebuffer: fbdev
[  3254.360] (--) using VT number 8

[  3254.364] (II) Loading sub module "fbdevhw"
[  3254.364] (II) LoadModule: "fbdevhw"
[  3254.364] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3254.364] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3254.364]     compiled for 1.16.0, module version = 0.0.2
[  3254.364]     ABI class: X.Org Video Driver, version 18.0
[  3254.364] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[  3254.364] (II) FBDEV(0): using default device
[  3254.364] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[  3254.364] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[  3254.364] (==) FBDEV(0): RGB weight 888
[  3254.364] (==) FBDEV(0): Default visual is TrueColor
[  3254.364] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[  3254.365] (II) FBDEV(0): hardware: inteldrmfb (video memory: 4128kB)
[  3254.365] (II) FBDEV(0): checking modes against framebuffer device...
[  3254.365] (II) FBDEV(0): checking modes against monitor...
[  3254.365] (--) FBDEV(0): Virtual size is 1366x768 (pitch 1366)
[  3254.365] (**) FBDEV(0):  Built-in mode "current"
[  3254.365] (==) FBDEV(0): DPI set to (96, 96)
[  3254.365] (II) Loading sub module "fb"
[  3254.365] (II) LoadModule: "fb"
[  3254.365] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3254.390] (II) Module fb: vendor="X.Org Foundation"
[  3254.391]     compiled for 1.16.0, module version = 1.0.0
[  3254.391]     ABI class: X.Org ANSI C Emulation, version 0.4
[  3254.391] (**) FBDEV(0): using shadow framebuffer
[  3254.391] (II) Loading sub module "shadow"
[  3254.391] (II) LoadModule: "shadow"
[  3254.391] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  3254.395] (II) Module shadow: vendor="X.Org Foundation"
[  3254.395]     compiled for 1.16.0, module version = 1.1.0
[  3254.395]     ABI class: X.Org ANSI C Emulation, version 0.4
[  3254.395] (==) Depth 24 pixmap format is 32 bpp
[  3254.395] (==) FBDEV(0): Backing store enabled
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.395] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.396] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.397] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[  3254.398] (==) FBDEV(0): DPMS enabled
[  3254.398] (==) RandR enabled
[  3254.404] (II) AIGLX: Screen 0 is not DRI2 capable
[  3254.404] (EE) AIGLX: reverting to software rendering
[  3255.059] (II) AIGLX: Loaded and initialized swrast
[  3255.059] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  3255.076] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3255.079] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  3255.079] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  3255.079] (II) LoadModule: "evdev"
[  3255.080] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3255.080] (II) Module evdev: vendor="X.Org Foundation"
[  3255.080]     compiled for 1.16.0, module version = 2.9.0
[  3255.080]     Module class: X.Org XInput Driver
[  3255.080]     ABI class: X.Org XInput driver, version 21.0
[  3255.080] (II) Using input driver 'evdev' for 'Video Bus'
[  3255.080] (**) Video Bus: always reports core events
[  3255.080] (**) evdev: Video Bus: Device: "/dev/input/event6"
[  3255.080] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  3255.080] (--) evdev: Video Bus: Found keys
[  3255.080] (II) evdev: Video Bus: Configuring as keyboard
[  3255.080] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input13/event6"
[  3255.080] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[  3255.080] (**) Option "xkb_rules" "evdev"
[  3255.080] (**) Option "xkb_model" "pc105"
[  3255.080] (**) Option "xkb_layout" "us"
[  3255.081] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  3255.081] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3255.081] (II) Using input driver 'evdev' for 'Power Button'
[  3255.081] (**) Power Button: always reports core events
[  3255.081] (**) evdev: Power Button: Device: "/dev/input/event1"
[  3255.081] (--) evdev: Power Button: Vendor 0 Product 0x1
[  3255.081] (--) evdev: Power Button: Found keys
[  3255.081] (II) evdev: Power Button: Configuring as keyboard
[  3255.081] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[  3255.081] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  3255.081] (**) Option "xkb_rules" "evdev"
[  3255.081] (**) Option "xkb_model" "pc105"
[  3255.081] (**) Option "xkb_layout" "us"
[  3255.082] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  3255.082] (II) No input driver specified, ignoring this device.
[  3255.082] (II) This device may have been added with another device file.
[  3255.082] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  3255.082] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  3255.082] (II) Using input driver 'evdev' for 'Sleep Button'
[  3255.082] (**) Sleep Button: always reports core events
[  3255.082] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[  3255.082] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  3255.082] (--) evdev: Sleep Button: Found keys
[  3255.082] (II) evdev: Sleep Button: Configuring as keyboard
[  3255.082] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[  3255.082] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[  3255.082] (**) Option "xkb_rules" "evdev"
[  3255.082] (**) Option "xkb_model" "pc105"
[  3255.082] (**) Option "xkb_layout" "us"
[  3255.083] (II) config/udev: Adding input device Integrated Webcam (/dev/input/event8)
[  3255.083] (**) Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[  3255.083] (II) Using input driver 'evdev' for 'Integrated Webcam'
[  3255.083] (**) Integrated Webcam: always reports core events
[  3255.083] (**) evdev: Integrated Webcam: Device: "/dev/input/event8"
[  3255.083] (--) evdev: Integrated Webcam: Vendor 0x5ca Product 0x180a
[  3255.083] (--) evdev: Integrated Webcam: Found keys
[  3255.083] (II) evdev: Integrated Webcam: Configuring as keyboard
[  3255.083] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input15/event8"
[  3255.083] (II) XINPUT: Adding extended input device "Integrated Webcam" (type: KEYBOARD, id 9)
[  3255.083] (**) Option "xkb_rules" "evdev"
[  3255.083] (**) Option "xkb_model" "pc105"
[  3255.084] (**) Option "xkb_layout" "us"
[  3255.084] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[  3255.084] (II) No input driver specified, ignoring this device.
[  3255.084] (II) This device may have been added with another device file.
[  3255.084] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[  3255.084] (II) No input driver specified, ignoring this device.
[  3255.084] (II) This device may have been added with another device file.
[  3255.085] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  3255.085] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  3255.085] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  3255.085] (**) AT Translated Set 2 keyboard: always reports core events
[  3255.085] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  3255.085] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  3255.085] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  3255.085] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  3255.085] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  3255.085] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[  3255.085] (**) Option "xkb_rules" "evdev"
[  3255.085] (**) Option "xkb_model" "pc105"
[  3255.085] (**) Option "xkb_layout" "us"
[  3255.086] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event4)
[  3255.086] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[  3255.086] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[  3255.086] (**) ALPS PS/2 Device: always reports core events
[  3255.086] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event4"
[  3255.086] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[  3255.086] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[  3255.086] (--) evdev: ALPS PS/2 Device: Found relative axes
[  3255.086] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[  3255.086] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[  3255.086] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[  3255.086] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3255.086] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event4"
[  3255.086] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 11)
[  3255.086] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[  3255.086] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[  3255.086] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[  3255.086] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[  3255.086] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[  3255.086] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[  3255.087] (II) No input driver specified, ignoring this device.
[  3255.087] (II) This device may have been added with another device file.
[  3255.087] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event5)
[  3255.087] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[  3255.087] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[  3255.087] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[  3255.087] (II) LoadModule: "synaptics"
[  3255.087] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  3255.087] (II) Module synaptics: vendor="X.Org Foundation"
[  3255.087]     compiled for 1.16.0, module version = 1.8.99
[  3255.087]     Module class: X.Org XInput Driver
[  3255.087]     ABI class: X.Org XInput driver, version 21.0
[  3255.087] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[  3255.087] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  3255.087] (**) Option "Device" "/dev/input/event5"
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[  3255.096] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[  3255.096] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  3255.096] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  3255.108] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[  3255.108] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[  3255.108] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[  3255.108] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[  3255.108] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[  3255.108] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[  3255.108] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[  3255.108] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[  3255.108] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[  3255.108] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  3255.109] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[  3255.109] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[  3255.113] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[  3255.113] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  3255.113] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[  3255.113] (**) Dell WMI hotkeys: always reports core events
[  3255.113] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[  3255.113] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[  3255.113] (--) evdev: Dell WMI hotkeys: Found keys
[  3255.113] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[  3255.113] (**) Option "config_info" "udev:/sys/devices/virtual/input/input14/event7"
[  3255.113] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[  3255.113] (**) Option "xkb_rules" "evdev"
[  3255.113] (**) Option "xkb_model" "pc105"
[  3255.113] (**) Option "xkb_layout" "us"
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```

xorg.2.log:

```
[  1113.872] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[  1113.872] X Protocol Version 11, Revision 0
[  1113.872] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[  1113.872] Current Operating System: Linux sophie-Inspiron-1545 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64
[  1113.872] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-45-generic root=UUID=7fcc521f-9d61-496f-b634-45b408570bf0 ro quiet splash vt.handoff=7
[  1113.872] Build Date: 12 February 2015  11:11:26PM
[  1113.872] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[  1113.872] Current version of pixman: 0.30.2
[  1113.872]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1113.872] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1113.872] (==) Log file: "/var/log/Xorg.2.log", Time: Sun Aug  2 23:53:06 2015
[  1113.872] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1113.872] (==) No Layout section.  Using the first Screen section.
[  1113.872] (==) No screen section available. Using defaults.
[  1113.872] (**) |-->Screen "Default Screen Section" (0)
[  1113.872] (**) |   |-->Monitor "<default monitor>"
[  1113.873] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1113.873] (==) Automatically adding devices
[  1113.873] (==) Automatically enabling devices
[  1113.873] (==) Automatically adding GPU devices
[  1113.873] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1113.873]     Entry deleted from font path.
[  1113.873] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1113.873]     Entry deleted from font path.
[  1113.873] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1113.873]     Entry deleted from font path.
[  1113.873] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1113.873]     Entry deleted from font path.
[  1113.873] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1113.873]     Entry deleted from font path.
[  1113.873] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1113.873] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1113.873] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1113.873] (II) Loader magic: 0x7f77470f5c80
[  1113.873] (II) Module ABI versions:
[  1113.873]     X.Org ANSI C Emulation: 0.4
[  1113.873]     X.Org Video Driver: 18.0
[  1113.873]     X.Org XInput driver : 21.0
[  1113.873]     X.Org Server Extension : 8.0
[  1113.873] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1113.875] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[  1113.875] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[  1113.875] (II) LoadModule: "glx"
[  1113.876] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1113.877] (II) Module glx: vendor="X.Org Foundation"
[  1113.877]     compiled for 1.16.0, module version = 1.0.0
[  1113.877]     ABI class: X.Org Server Extension, version 8.0
[  1113.877] (==) AIGLX enabled
[  1113.877] (==) Matched intel as autoconfigured driver 0
[  1113.877] (==) Matched intel as autoconfigured driver 1
[  1113.877] (==) Matched modesetting as autoconfigured driver 2
[  1113.877] (==) Matched fbdev as autoconfigured driver 3
[  1113.877] (==) Matched vesa as autoconfigured driver 4
[  1113.877] (==) Assigned the driver to the xf86ConfigLayout
[  1113.877] (II) LoadModule: "intel"
[  1113.877] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1113.878] (II) Module intel: vendor="X.Org Foundation"
[  1113.878]     compiled for 1.16.0, module version = 2.99.914
[  1113.878]     Module class: X.Org Video Driver
[  1113.878]     ABI class: X.Org Video Driver, version 18.0
[  1113.878] (II) LoadModule: "modesetting"
[  1113.878] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1113.878] (II) Module modesetting: vendor="X.Org Foundation"
[  1113.878]     compiled for 1.16.0, module version = 0.9.0
[  1113.878]     Module class: X.Org Video Driver
[  1113.878]     ABI class: X.Org Video Driver, version 18.0
[  1113.878] (II) LoadModule: "fbdev"
[  1113.879] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1113.879] (II) Module fbdev: vendor="X.Org Foundation"
[  1113.879]     compiled for 1.16.0, module version = 0.4.4
[  1113.879]     Module class: X.Org Video Driver
[  1113.879]     ABI class: X.Org Video Driver, version 18.0
[  1113.879] (II) LoadModule: "vesa"
[  1113.879] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1113.879] (II) Module vesa: vendor="X.Org Foundation"
[  1113.879]     compiled for 1.16.0, module version = 2.3.3
[  1113.879]     Module class: X.Org Video Driver
[  1113.879]     ABI class: X.Org Video Driver, version 18.0
[  1113.879] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  1113.879] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[  1113.879] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[  1113.879] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[  1113.879] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1113.879] (II) FBDEV: driver for framebuffer: fbdev
[  1113.879] (II) VESA: driver for VESA chipsets: vesa
[  1113.879] (++) using VT number 9

[  1114.957] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[  1114.957] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.5~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[  1114.957] (II) intel(0): SNA compiled for use with valgrind
[  1114.958] (WW) Falling back to old probe method for modesetting
[  1114.958] (WW) Falling back to old probe method for fbdev
[  1114.958] (II) Loading sub module "fbdevhw"
[  1114.958] (II) LoadModule: "fbdevhw"
[  1114.958] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1114.959] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1114.959]     compiled for 1.16.0, module version = 0.0.2
[  1114.959]     ABI class: X.Org Video Driver, version 18.0
[  1114.959] (WW) Falling back to old probe method for vesa
[  1114.959] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[  1114.960] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[  1114.960] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1114.960] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  1114.960] (==) intel(0): RGB weight 888
[  1114.960] (==) intel(0): Default visual is TrueColor
[  1114.961] (II) intel(0): Output LVDS1 has no monitor section
[  1114.961] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[  1114.961] (II) intel(0): Output VGA1 has no monitor section
[  1114.961] (II) intel(0): Output DP1 has no monitor section
[  1114.961] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[  1114.961] (II) intel(0): Output VIRTUAL1 has no monitor section
[  1114.961] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 1
[  1114.961] (==) intel(0): TearFree disabled
[  1114.961] (==) intel(0): DPI set to (96, 96)
[  1114.961] (II) Loading sub module "dri2"
[  1114.961] (II) LoadModule: "dri2"
[  1114.961] (II) Module "dri2" already built-in
[  1114.961] (II) Loading sub module "present"
[  1114.961] (II) LoadModule: "present"
[  1114.961] (II) Module "present" already built-in
[  1114.961] (II) UnloadModule: "modesetting"
[  1114.961] (II) Unloading modesetting
[  1114.961] (II) UnloadModule: "fbdev"
[  1114.961] (II) Unloading fbdev
[  1114.961] (II) UnloadSubModule: "fbdevhw"
[  1114.961] (II) Unloading fbdevhw
[  1114.961] (II) UnloadModule: "vesa"
[  1114.961] (II) Unloading vesa
[  1114.962] (==) Depth 24 pixmap format is 32 bpp
[  1114.962] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[  1114.962] (==) intel(0): Backing store enabled
[  1114.962] (==) intel(0): Silken mouse enabled
[  1114.962] (II) intel(0): HW Cursor enabled
[  1114.962] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1114.962] (==) intel(0): DPMS enabled
[  1114.962] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  1114.962] (II) intel(0): [DRI2] Setup complete
[  1114.962] (II) intel(0): [DRI2]   DRI driver: i965
[  1114.962] (II) intel(0): [DRI2]   VDPAU driver: i965
[  1114.962] (II) intel(0): direct rendering: DRI2 enabled
[  1114.962] (II) intel(0): hardware support for Present enabled
[  1114.962] (==) intel(0): display hotplug detection enabled
[  1114.962] (--) RandR disabled
[  1114.982] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1114.983] (II) AIGLX: enabled GLX_ARB_create_context
[  1114.983] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  1114.983] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  1114.983] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1114.983] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1114.983] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  1114.983] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  1114.983] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1114.983] (II) AIGLX: Loaded and initialized i965
[  1114.983] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1114.989] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[  1114.996] (II) intel(0): Setting screen physical size to 361 x 203
[  1115.006] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1115.012] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  1115.012] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1115.012] (II) LoadModule: "evdev"
[  1115.012] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1115.012] (II) Module evdev: vendor="X.Org Foundation"
[  1115.012]     compiled for 1.16.0, module version = 2.9.0
[  1115.012]     Module class: X.Org XInput Driver
[  1115.012]     ABI class: X.Org XInput driver, version 21.0
[  1115.012] (II) Using input driver 'evdev' for 'Video Bus'
[  1115.012] (**) Video Bus: always reports core events
[  1115.012] (**) evdev: Video Bus: Device: "/dev/input/event6"
[  1115.013] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1115.013] (--) evdev: Video Bus: Found keys
[  1115.013] (II) evdev: Video Bus: Configuring as keyboard
[  1115.013] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input13/event6"
[  1115.013] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[  1115.013] (**) Option "xkb_rules" "evdev"
[  1115.013] (**) Option "xkb_model" "pc105"
[  1115.013] (**) Option "xkb_layout" "us"
[  1115.013] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1115.013] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1115.013] (II) Using input driver 'evdev' for 'Power Button'
[  1115.013] (**) Power Button: always reports core events
[  1115.013] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1115.013] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1115.013] (--) evdev: Power Button: Found keys
[  1115.013] (II) evdev: Power Button: Configuring as keyboard
[  1115.013] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[  1115.014] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1115.014] (**) Option "xkb_rules" "evdev"
[  1115.014] (**) Option "xkb_model" "pc105"
[  1115.014] (**) Option "xkb_layout" "us"
[  1115.014] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1115.014] (II) No input driver specified, ignoring this device.
[  1115.014] (II) This device may have been added with another device file.
[  1115.014] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  1115.014] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1115.014] (II) Using input driver 'evdev' for 'Sleep Button'
[  1115.015] (**) Sleep Button: always reports core events
[  1115.015] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[  1115.015] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  1115.015] (--) evdev: Sleep Button: Found keys
[  1115.015] (II) evdev: Sleep Button: Configuring as keyboard
[  1115.015] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[  1115.015] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[  1115.015] (**) Option "xkb_rules" "evdev"
[  1115.015] (**) Option "xkb_model" "pc105"
[  1115.015] (**) Option "xkb_layout" "us"
[  1115.015] (II) config/udev: Adding input device Integrated Webcam (/dev/input/event10)
[  1115.016] (**) Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[  1115.016] (II) Using input driver 'evdev' for 'Integrated Webcam'
[  1115.016] (**) Integrated Webcam: always reports core events
[  1115.016] (**) evdev: Integrated Webcam: Device: "/dev/input/event10"
[  1115.016] (--) evdev: Integrated Webcam: Vendor 0x5ca Product 0x180a
[  1115.016] (--) evdev: Integrated Webcam: Found keys
[  1115.016] (II) evdev: Integrated Webcam: Configuring as keyboard
[  1115.016] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input17/event10"
[  1115.016] (II) XINPUT: Adding extended input device "Integrated Webcam" (type: KEYBOARD, id 9)
[  1115.016] (**) Option "xkb_rules" "evdev"
[  1115.016] (**) Option "xkb_model" "pc105"
[  1115.016] (**) Option "xkb_layout" "us"
[  1115.016] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[  1115.016] (II) No input driver specified, ignoring this device.
[  1115.016] (II) This device may have been added with another device file.
[  1115.017] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[  1115.017] (II) No input driver specified, ignoring this device.
[  1115.017] (II) This device may have been added with another device file.
[  1115.017] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1115.017] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1115.017] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1115.017] (**) AT Translated Set 2 keyboard: always reports core events
[  1115.017] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  1115.017] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1115.017] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1115.017] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1115.017] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1115.017] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[  1115.017] (**) Option "xkb_rules" "evdev"
[  1115.017] (**) Option "xkb_model" "pc105"
[  1115.017] (**) Option "xkb_layout" "us"
[  1115.018] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event4)
[  1115.018] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[  1115.018] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[  1115.018] (**) ALPS PS/2 Device: always reports core events
[  1115.018] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event4"
[  1115.018] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[  1115.018] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[  1115.018] (--) evdev: ALPS PS/2 Device: Found relative axes
[  1115.018] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[  1115.018] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[  1115.018] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[  1115.018] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1115.018] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event4"
[  1115.018] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 11)
[  1115.018] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[  1115.018] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[  1115.018] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[  1115.018] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[  1115.018] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[  1115.019] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[  1115.019] (II) No input driver specified, ignoring this device.
[  1115.019] (II) This device may have been added with another device file.
[  1115.019] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event5)
[  1115.019] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[  1115.019] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[  1115.019] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[  1115.019] (II) LoadModule: "synaptics"
[  1115.019] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1115.019] (II) Module synaptics: vendor="X.Org Foundation"
[  1115.019]     compiled for 1.16.0, module version = 1.8.99
[  1115.019]     Module class: X.Org XInput Driver
[  1115.019]     ABI class: X.Org XInput driver, version 21.0
[  1115.020] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[  1115.020] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  1115.020] (**) Option "Device" "/dev/input/event5"
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[  1115.032] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[  1115.032] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  1115.032] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  1115.044] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[  1115.044] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[  1115.044] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[  1115.044] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[  1115.044] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[  1115.044] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[  1115.044] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[  1115.044] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[  1115.044] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[  1115.044] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  1115.045] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[  1115.045] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[  1115.047] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[  1115.047] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  1115.047] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[  1115.047] (**) Dell WMI hotkeys: always reports core events
[  1115.047] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[  1115.047] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[  1115.047] (--) evdev: Dell WMI hotkeys: Found keys
[  1115.047] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[  1115.047] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
[  1115.047] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[  1115.047] (**) Option "xkb_rules" "evdev"
[  1115.047] (**) Option "xkb_model" "pc105"
[  1115.047] (**) Option "xkb_layout" "us"
[  1115.968] (II) intel(0): EDID vendor "INL", prod id 10
[  1115.968] (II) intel(0): Printing DDC gathered Modelines:
[  1115.968] (II) intel(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[  1116.532] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[  1123.048] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1123.408] (II) evdev: Dell WMI hotkeys: Close
[  1123.408] (II) UnloadModule: "evdev"
[  1123.408] (II) UnloadModule: "synaptics"
[  1123.409] (II) evdev: ALPS PS/2 Device: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.409] (II) evdev: AT Translated Set 2 keyboard: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.409] (II) evdev: Integrated Webcam: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.409] (II) evdev: Sleep Button: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.409] (II) evdev: Power Button: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.409] (II) evdev: Video Bus: Close
[  1123.409] (II) UnloadModule: "evdev"
[  1123.435] (EE) Server terminated successfully (0). Closing log file.
```

xorg.1.log:
```

[   107.102] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[   107.102] X Protocol Version 11, Revision 0
[   107.102] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[   107.102] Current Operating System: Linux sophie-Inspiron-1545 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64
[   107.102] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-45-generic root=UUID=7fcc521f-9d61-496f-b634-45b408570bf0 ro quiet splash vt.handoff=7
[   107.102] Build Date: 12 February 2015  11:11:26PM
[   107.102] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[   107.102] Current version of pixman: 0.30.2
[   107.102]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   107.102] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   107.102] (==) Log file: "/var/log/Xorg.1.log", Time: Sun Aug  2 23:55:40 2015
[   107.102] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   107.102] (==) No Layout section.  Using the first Screen section.
[   107.102] (==) No screen section available. Using defaults.
[   107.102] (**) |-->Screen "Default Screen Section" (0)
[   107.102] (**) |   |-->Monitor "<default monitor>"
[   107.103] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   107.103] (==) Automatically adding devices
[   107.103] (==) Automatically enabling devices
[   107.103] (==) Automatically adding GPU devices
[   107.103] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   107.103]     Entry deleted from font path.
[   107.103] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   107.103]     Entry deleted from font path.
[   107.103] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   107.103]     Entry deleted from font path.
[   107.103] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   107.103]     Entry deleted from font path.
[   107.103] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   107.103]     Entry deleted from font path.
[   107.103] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   107.103] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   107.103] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   107.103] (II) Loader magic: 0x7f8ca8590c80
[   107.103] (II) Module ABI versions:
[   107.103]     X.Org ANSI C Emulation: 0.4
[   107.103]     X.Org Video Driver: 18.0
[   107.103]     X.Org XInput driver : 21.0
[   107.103]     X.Org Server Extension : 8.0
[   107.103] (II) xfree86: Adding drm device (/dev/dri/card0)
[   107.105] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[   107.105] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[   107.105] (II) LoadModule: "glx"
[   107.106] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   107.107] (II) Module glx: vendor="X.Org Foundation"
[   107.107]     compiled for 1.16.0, module version = 1.0.0
[   107.107]     ABI class: X.Org Server Extension, version 8.0
[   107.107] (==) AIGLX enabled
[   107.107] (==) Matched intel as autoconfigured driver 0
[   107.107] (==) Matched intel as autoconfigured driver 1
[   107.107] (==) Matched modesetting as autoconfigured driver 2
[   107.107] (==) Matched fbdev as autoconfigured driver 3
[   107.107] (==) Matched vesa as autoconfigured driver 4
[   107.107] (==) Assigned the driver to the xf86ConfigLayout
[   107.107] (II) LoadModule: "intel"
[   107.107] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   107.108] (II) Module intel: vendor="X.Org Foundation"
[   107.108]     compiled for 1.16.0, module version = 2.99.914
[   107.108]     Module class: X.Org Video Driver
[   107.108]     ABI class: X.Org Video Driver, version 18.0
[   107.108] (II) LoadModule: "modesetting"
[   107.108] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   107.109] (II) Module modesetting: vendor="X.Org Foundation"
[   107.109]     compiled for 1.16.0, module version = 0.9.0
[   107.109]     Module class: X.Org Video Driver
[   107.109]     ABI class: X.Org Video Driver, version 18.0
[   107.109] (II) LoadModule: "fbdev"
[   107.109] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   107.109] (II) Module fbdev: vendor="X.Org Foundation"
[   107.109]     compiled for 1.16.0, module version = 0.4.4
[   107.109]     Module class: X.Org Video Driver
[   107.109]     ABI class: X.Org Video Driver, version 18.0
[   107.109] (II) LoadModule: "vesa"
[   107.110] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   107.110] (II) Module vesa: vendor="X.Org Foundation"
[   107.110]     compiled for 1.16.0, module version = 2.3.3
[   107.110]     Module class: X.Org Video Driver
[   107.110]     ABI class: X.Org Video Driver, version 18.0
[   107.110] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   107.110] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   107.110] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   107.110] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   107.110] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   107.110] (II) FBDEV: driver for framebuffer: fbdev
[   107.110] (II) VESA: driver for VESA chipsets: vesa
[   107.110] (++) using VT number 8

[   108.095] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[   108.095] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.5~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[   108.095] (II) intel(0): SNA compiled for use with valgrind
[   108.095] (WW) Falling back to old probe method for modesetting
[   108.095] (WW) Falling back to old probe method for fbdev
[   108.095] (II) Loading sub module "fbdevhw"
[   108.095] (II) LoadModule: "fbdevhw"
[   108.096] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   108.096] (II) Module fbdevhw: vendor="X.Org Foundation"
[   108.096]     compiled for 1.16.0, module version = 0.0.2
[   108.096]     ABI class: X.Org Video Driver, version 18.0
[   108.096] (WW) Falling back to old probe method for vesa
[   108.098] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[   108.098] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[   108.098] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   108.098] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   108.098] (==) intel(0): RGB weight 888
[   108.098] (==) intel(0): Default visual is TrueColor
[   108.098] (II) intel(0): Output LVDS1 has no monitor section
[   108.099] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[   108.099] (II) intel(0): Output VGA1 has no monitor section
[   108.099] (II) intel(0): Output DP1 has no monitor section
[   108.099] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[   108.099] (II) intel(0): Output VIRTUAL1 has no monitor section
[   108.099] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 1
[   108.099] (==) intel(0): TearFree disabled
[   108.099] (==) intel(0): DPI set to (96, 96)
[   108.099] (II) Loading sub module "dri2"
[   108.099] (II) LoadModule: "dri2"
[   108.099] (II) Module "dri2" already built-in
[   108.099] (II) Loading sub module "present"
[   108.099] (II) LoadModule: "present"
[   108.099] (II) Module "present" already built-in
[   108.099] (II) UnloadModule: "modesetting"
[   108.099] (II) Unloading modesetting
[   108.100] (II) UnloadModule: "fbdev"
[   108.100] (II) Unloading fbdev
[   108.100] (II) UnloadSubModule: "fbdevhw"
[   108.100] (II) Unloading fbdevhw
[   108.100] (II) UnloadModule: "vesa"
[   108.100] (II) Unloading vesa
[   108.100] (==) Depth 24 pixmap format is 32 bpp
[   108.100] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[   108.100] (==) intel(0): Backing store enabled
[   108.101] (==) intel(0): Silken mouse enabled
[   108.101] (II) intel(0): HW Cursor enabled
[   108.101] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   108.101] (==) intel(0): DPMS enabled
[   108.101] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   108.101] (II) intel(0): [DRI2] Setup complete
[   108.101] (II) intel(0): [DRI2]   DRI driver: i965
[   108.101] (II) intel(0): [DRI2]   VDPAU driver: i965
[   108.101] (II) intel(0): direct rendering: DRI2 enabled
[   108.101] (II) intel(0): hardware support for Present enabled
[   108.101] (==) intel(0): display hotplug detection enabled
[   108.101] (--) RandR disabled
[   108.119] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   108.119] (II) AIGLX: enabled GLX_ARB_create_context
[   108.119] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   108.119] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   108.119] (II) AIGLX: enabled GLX_INTEL_swap_event
[   108.119] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   108.119] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   108.119] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   108.119] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   108.119] (II) AIGLX: Loaded and initialized i965
[   108.119] (II) GLX: Initialized DRI2 GL provider for screen 0
[   108.125] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[   108.132] (II) intel(0): Setting screen physical size to 361 x 203
[   108.143] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   108.148] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   108.148] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   108.148] (II) LoadModule: "evdev"
[   108.148] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   108.148] (II) Module evdev: vendor="X.Org Foundation"
[   108.148]     compiled for 1.16.0, module version = 2.9.0
[   108.148]     Module class: X.Org XInput Driver
[   108.148]     ABI class: X.Org XInput driver, version 21.0
[   108.148] (II) Using input driver 'evdev' for 'Video Bus'
[   108.148] (**) Video Bus: always reports core events
[   108.148] (**) evdev: Video Bus: Device: "/dev/input/event6"
[   108.149] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   108.149] (--) evdev: Video Bus: Found keys
[   108.149] (II) evdev: Video Bus: Configuring as keyboard
[   108.149] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input13/event6"
[   108.149] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[   108.149] (**) Option "xkb_rules" "evdev"
[   108.149] (**) Option "xkb_model" "pc105"
[   108.149] (**) Option "xkb_layout" "us"
[   108.149] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   108.149] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   108.149] (II) Using input driver 'evdev' for 'Power Button'
[   108.149] (**) Power Button: always reports core events
[   108.149] (**) evdev: Power Button: Device: "/dev/input/event1"
[   108.149] (--) evdev: Power Button: Vendor 0 Product 0x1
[   108.149] (--) evdev: Power Button: Found keys
[   108.149] (II) evdev: Power Button: Configuring as keyboard
[   108.149] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   108.149] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   108.149] (**) Option "xkb_rules" "evdev"
[   108.150] (**) Option "xkb_model" "pc105"
[   108.150] (**) Option "xkb_layout" "us"
[   108.150] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   108.150] (II) No input driver specified, ignoring this device.
[   108.150] (II) This device may have been added with another device file.
[   108.150] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   108.150] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   108.150] (II) Using input driver 'evdev' for 'Sleep Button'
[   108.150] (**) Sleep Button: always reports core events
[   108.150] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[   108.151] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   108.151] (--) evdev: Sleep Button: Found keys
[   108.151] (II) evdev: Sleep Button: Configuring as keyboard
[   108.151] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[   108.151] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[   108.151] (**) Option "xkb_rules" "evdev"
[   108.151] (**) Option "xkb_model" "pc105"
[   108.151] (**) Option "xkb_layout" "us"
[   108.151] (II) config/udev: Adding input device Integrated Webcam (/dev/input/event10)
[   108.151] (**) Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[   108.151] (II) Using input driver 'evdev' for 'Integrated Webcam'
[   108.152] (**) Integrated Webcam: always reports core events
[   108.152] (**) evdev: Integrated Webcam: Device: "/dev/input/event10"
[   108.152] (--) evdev: Integrated Webcam: Vendor 0x5ca Product 0x180a
[   108.152] (--) evdev: Integrated Webcam: Found keys
[   108.152] (II) evdev: Integrated Webcam: Configuring as keyboard
[   108.152] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input17/event10"
[   108.152] (II) XINPUT: Adding extended input device "Integrated Webcam" (type: KEYBOARD, id 9)
[   108.152] (**) Option "xkb_rules" "evdev"
[   108.152] (**) Option "xkb_model" "pc105"
[   108.152] (**) Option "xkb_layout" "us"
[   108.152] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[   108.152] (II) No input driver specified, ignoring this device.
[   108.152] (II) This device may have been added with another device file.
[   108.153] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[   108.153] (II) No input driver specified, ignoring this device.
[   108.153] (II) This device may have been added with another device file.
[   108.153] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   108.153] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   108.153] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   108.153] (**) AT Translated Set 2 keyboard: always reports core events
[   108.153] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   108.153] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   108.153] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   108.153] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   108.153] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   108.153] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[   108.153] (**) Option "xkb_rules" "evdev"
[   108.153] (**) Option "xkb_model" "pc105"
[   108.153] (**) Option "xkb_layout" "us"
[   108.154] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event4)
[   108.154] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[   108.154] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[   108.154] (**) ALPS PS/2 Device: always reports core events
[   108.154] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event4"
[   108.154] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[   108.154] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[   108.154] (--) evdev: ALPS PS/2 Device: Found relative axes
[   108.154] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[   108.154] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[   108.154] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[   108.154] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   108.154] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event4"
[   108.154] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 11)
[   108.154] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[   108.154] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[   108.154] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[   108.154] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[   108.154] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[   108.155] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[   108.155] (II) No input driver specified, ignoring this device.
[   108.155] (II) This device may have been added with another device file.
[   108.155] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event5)
[   108.155] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[   108.155] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[   108.155] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[   108.155] (II) LoadModule: "synaptics"
[   108.155] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   108.155] (II) Module synaptics: vendor="X.Org Foundation"
[   108.155]     compiled for 1.16.0, module version = 1.8.99
[   108.155]     Module class: X.Org XInput Driver
[   108.155]     ABI class: X.Org XInput driver, version 21.0
[   108.155] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[   108.156] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[   108.156] (**) Option "Device" "/dev/input/event5"
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[   108.168] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[   108.168] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[   108.168] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[   108.180] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[   108.180] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[   108.180] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[   108.180] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[   108.180] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[   108.180] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[   108.180] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[   108.180] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[   108.180] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[   108.180] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[   108.181] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[   108.181] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[   108.185] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[   108.185] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   108.185] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[   108.185] (**) Dell WMI hotkeys: always reports core events
[   108.185] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[   108.185] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[   108.185] (--) evdev: Dell WMI hotkeys: Found keys
[   108.185] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[   108.185] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
[   108.185] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[   108.185] (**) Option "xkb_rules" "evdev"
[   108.185] (**) Option "xkb_model" "pc105"
[   108.185] (**) Option "xkb_layout" "us"
[   109.144] (II) intel(0): EDID vendor "INL", prod id 10
[   109.144] (II) intel(0): Printing DDC gathered Modelines:
[   109.144] (II) intel(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[   109.672] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   118.890] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   119.423] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   119.479] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3954.255] (II) evdev: Dell WMI hotkeys: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) UnloadModule: "synaptics"
[  3954.255] (II) evdev: ALPS PS/2 Device: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) evdev: AT Translated Set 2 keyboard: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) evdev: Integrated Webcam: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) evdev: Sleep Button: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) evdev: Power Button: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3954.255] (II) evdev: Video Bus: Close
[  3954.255] (II) UnloadModule: "evdev"
[  3955.213] (EE) Server terminated successfully (0). Closing log file.
```

xorg.0.log:
```

[    30.626] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    30.626] X Protocol Version 11, Revision 0
[    30.626] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    30.626] Current Operating System: Linux sophie-Inspiron-1545 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64
[    30.626] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-45-generic root=UUID=7fcc521f-9d61-496f-b634-45b408570bf0 ro quiet splash vt.handoff=7
[    30.626] Build Date: 12 February 2015  11:11:26PM
[    30.626] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    30.626] Current version of pixman: 0.30.2
[    30.626]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.626] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.627] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 13 03:55:48 2015
[    30.866] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.866] (==) No Layout section.  Using the first Screen section.
[    30.866] (==) No screen section available. Using defaults.
[    30.866] (**) |-->Screen "Default Screen Section" (0)
[    30.866] (**) |   |-->Monitor "<default monitor>"
[    30.867] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.867] (==) Automatically adding devices
[    30.867] (==) Automatically enabling devices
[    30.867] (==) Automatically adding GPU devices
[    30.867] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.867]     Entry deleted from font path.
[    30.867] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.867]     Entry deleted from font path.
[    30.867] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.867]     Entry deleted from font path.
[    30.867] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.867]     Entry deleted from font path.
[    30.867] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.867]     Entry deleted from font path.
[    30.867] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.867] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.867] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.867] (II) Loader magic: 0x7fc2b1a0ec80
[    30.867] (II) Module ABI versions:
[    30.867]     X.Org ANSI C Emulation: 0.4
[    30.867]     X.Org Video Driver: 18.0
[    30.867]     X.Org XInput driver : 21.0
[    30.867]     X.Org Server Extension : 8.0
[    30.867] (II) xfree86: Adding drm device (/dev/dri/card0)
[    30.870] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[    30.870] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[    30.870] (II) LoadModule: "glx"
[    30.899] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.176] (II) Module glx: vendor="X.Org Foundation"
[    31.176]     compiled for 1.16.0, module version = 1.0.0
[    31.176]     ABI class: X.Org Server Extension, version 8.0
[    31.176] (==) AIGLX enabled
[    31.176] (==) Matched intel as autoconfigured driver 0
[    31.176] (==) Matched intel as autoconfigured driver 1
[    31.176] (==) Matched modesetting as autoconfigured driver 2
[    31.176] (==) Matched fbdev as autoconfigured driver 3
[    31.176] (==) Matched vesa as autoconfigured driver 4
[    31.176] (==) Assigned the driver to the xf86ConfigLayout
[    31.176] (II) LoadModule: "intel"
[    31.176] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    31.211] (II) Module intel: vendor="X.Org Foundation"
[    31.212]     compiled for 1.16.0, module version = 2.99.914
[    31.212]     Module class: X.Org Video Driver
[    31.212]     ABI class: X.Org Video Driver, version 18.0
[    31.212] (II) LoadModule: "modesetting"
[    31.212] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.212] (II) Module modesetting: vendor="X.Org Foundation"
[    31.212]     compiled for 1.16.0, module version = 0.9.0
[    31.212]     Module class: X.Org Video Driver
[    31.212]     ABI class: X.Org Video Driver, version 18.0
[    31.212] (II) LoadModule: "fbdev"
[    31.212] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.212] (II) Module fbdev: vendor="X.Org Foundation"
[    31.213]     compiled for 1.16.0, module version = 0.4.4
[    31.213]     Module class: X.Org Video Driver
[    31.213]     ABI class: X.Org Video Driver, version 18.0
[    31.213] (II) LoadModule: "vesa"
[    31.213] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.213] (II) Module vesa: vendor="X.Org Foundation"
[    31.213]     compiled for 1.16.0, module version = 2.3.3
[    31.213]     Module class: X.Org Video Driver
[    31.213]     ABI class: X.Org Video Driver, version 18.0
[    31.213] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    31.213] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    31.213] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    31.213] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    31.213] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    31.213] (II) FBDEV: driver for framebuffer: fbdev
[    31.213] (II) VESA: driver for VESA chipsets: vesa
[    31.213] (++) using VT number 7

[    31.214] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    31.214] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.5~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    31.214] (II) intel(0): SNA compiled for use with valgrind
[    31.214] (WW) Falling back to old probe method for modesetting
[    31.214] (WW) Falling back to old probe method for fbdev
[    31.214] (II) Loading sub module "fbdevhw"
[    31.214] (II) LoadModule: "fbdevhw"
[    31.214] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.214] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.214]     compiled for 1.16.0, module version = 0.0.2
[    31.214]     ABI class: X.Org Video Driver, version 18.0
[    31.214] (WW) Falling back to old probe method for vesa
[    31.215] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    31.215] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    31.215] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    31.215] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    31.215] (==) intel(0): RGB weight 888
[    31.215] (==) intel(0): Default visual is TrueColor
[    31.215] (II) intel(0): Output LVDS1 has no monitor section
[    31.215] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[    31.216] (II) intel(0): Output VGA1 has no monitor section
[    31.216] (II) intel(0): Output DP1 has no monitor section
[    31.216] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    31.216] (II) intel(0): Output VIRTUAL1 has no monitor section
[    31.216] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 1
[    31.216] (==) intel(0): TearFree disabled
[    31.216] (==) intel(0): DPI set to (96, 96)
[    31.216] (II) Loading sub module "dri2"
[    31.216] (II) LoadModule: "dri2"
[    31.216] (II) Module "dri2" already built-in
[    31.216] (II) Loading sub module "present"
[    31.216] (II) LoadModule: "present"
[    31.216] (II) Module "present" already built-in
[    31.216] (II) UnloadModule: "modesetting"
[    31.216] (II) Unloading modesetting
[    31.216] (II) UnloadModule: "fbdev"
[    31.216] (II) Unloading fbdev
[    31.216] (II) UnloadSubModule: "fbdevhw"
[    31.216] (II) Unloading fbdevhw
[    31.216] (II) UnloadModule: "vesa"
[    31.216] (II) Unloading vesa
[    31.216] (==) Depth 24 pixmap format is 32 bpp
[    31.217] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[    31.217] (==) intel(0): Backing store enabled
[    31.217] (==) intel(0): Silken mouse enabled
[    31.217] (II) intel(0): HW Cursor enabled
[    31.217] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.217] (==) intel(0): DPMS enabled
[    31.217] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    31.217] (II) intel(0): [DRI2] Setup complete
[    31.217] (II) intel(0): [DRI2]   DRI driver: i965
[    31.217] (II) intel(0): [DRI2]   VDPAU driver: i965
[    31.217] (II) intel(0): direct rendering: DRI2 enabled
[    31.217] (II) intel(0): hardware support for Present enabled
[    31.217] (==) intel(0): display hotplug detection enabled
[    31.217] (--) RandR disabled
[    31.266] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.266] (II) AIGLX: enabled GLX_ARB_create_context
[    31.266] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    31.266] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    31.266] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.266] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.266] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    31.266] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    31.266] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.266] (II) AIGLX: Loaded and initialized i965
[    31.266] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.272] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[    31.288] (II) intel(0): Setting screen physical size to 361 x 203
[    31.298] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.302] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    31.302] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    31.302] (II) LoadModule: "evdev"
[    31.302] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.368] (II) Module evdev: vendor="X.Org Foundation"
[    31.368]     compiled for 1.16.0, module version = 2.9.0
[    31.368]     Module class: X.Org XInput Driver
[    31.368]     ABI class: X.Org XInput driver, version 21.0
[    31.368] (II) Using input driver 'evdev' for 'Video Bus'
[    31.368] (**) Video Bus: always reports core events
[    31.368] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    31.368] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    31.368] (--) evdev: Video Bus: Found keys
[    31.368] (II) evdev: Video Bus: Configuring as keyboard
[    31.368] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input13/event6"
[    31.368] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    31.368] (**) Option "xkb_rules" "evdev"
[    31.368] (**) Option "xkb_model" "pc105"
[    31.368] (**) Option "xkb_layout" "us"
[    31.369] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.369] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.369] (II) Using input driver 'evdev' for 'Power Button'
[    31.369] (**) Power Button: always reports core events
[    31.369] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.369] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.369] (--) evdev: Power Button: Found keys
[    31.369] (II) evdev: Power Button: Configuring as keyboard
[    31.369] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    31.369] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.369] (**) Option "xkb_rules" "evdev"
[    31.369] (**) Option "xkb_model" "pc105"
[    31.369] (**) Option "xkb_layout" "us"
[    31.370] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    31.370] (II) No input driver specified, ignoring this device.
[    31.370] (II) This device may have been added with another device file.
[    31.370] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    31.370] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    31.370] (II) Using input driver 'evdev' for 'Sleep Button'
[    31.370] (**) Sleep Button: always reports core events
[    31.370] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    31.370] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    31.370] (--) evdev: Sleep Button: Found keys
[    31.370] (II) evdev: Sleep Button: Configuring as keyboard
[    31.370] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    31.370] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    31.370] (**) Option "xkb_rules" "evdev"
[    31.370] (**) Option "xkb_model" "pc105"
[    31.370] (**) Option "xkb_layout" "us"
[    31.371] (II) config/udev: Adding input device Integrated Webcam (/dev/input/event10)
[    31.371] (**) Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[    31.371] (II) Using input driver 'evdev' for 'Integrated Webcam'
[    31.371] (**) Integrated Webcam: always reports core events
[    31.371] (**) evdev: Integrated Webcam: Device: "/dev/input/event10"
[    31.371] (--) evdev: Integrated Webcam: Vendor 0x5ca Product 0x180a
[    31.371] (--) evdev: Integrated Webcam: Found keys
[    31.371] (II) evdev: Integrated Webcam: Configuring as keyboard
[    31.371] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input17/event10"
[    31.371] (II) XINPUT: Adding extended input device "Integrated Webcam" (type: KEYBOARD, id 9)
[    31.371] (**) Option "xkb_rules" "evdev"
[    31.371] (**) Option "xkb_model" "pc105"
[    31.371] (**) Option "xkb_layout" "us"
[    31.372] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    31.372] (II) No input driver specified, ignoring this device.
[    31.372] (II) This device may have been added with another device file.
[    31.373] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    31.373] (II) No input driver specified, ignoring this device.
[    31.373] (II) This device may have been added with another device file.
[    31.373] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    31.373] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.373] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.373] (**) AT Translated Set 2 keyboard: always reports core events
[    31.373] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    31.373] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.373] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.373] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.373] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    31.373] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    31.373] (**) Option "xkb_rules" "evdev"
[    31.373] (**) Option "xkb_model" "pc105"
[    31.373] (**) Option "xkb_layout" "us"
[    31.374] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event4)
[    31.374] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[    31.374] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[    31.374] (**) ALPS PS/2 Device: always reports core events
[    31.374] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event4"
[    31.374] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[    31.374] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[    31.374] (--) evdev: ALPS PS/2 Device: Found relative axes
[    31.374] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[    31.374] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[    31.374] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[    31.374] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.374] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event4"
[    31.374] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 11)
[    31.374] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[    31.374] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[    31.374] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[    31.374] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[    31.374] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[    31.375] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[    31.375] (II) No input driver specified, ignoring this device.
[    31.375] (II) This device may have been added with another device file.
[    31.375] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event5)
[    31.375] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    31.375] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    31.375] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    31.375] (II) LoadModule: "synaptics"
[    31.375] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.376] (II) Module synaptics: vendor="X.Org Foundation"
[    31.376]     compiled for 1.16.0, module version = 1.8.99
[    31.376]     Module class: X.Org XInput Driver
[    31.376]     ABI class: X.Org XInput driver, version 21.0
[    31.376] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    31.376] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    31.376] (**) Option "Device" "/dev/input/event5"
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023 (res 0)
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767 (res 0)
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    31.388] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    31.388] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    31.388] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    31.400] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input9/event5"
[    31.400] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[    31.400] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    31.400] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    31.400] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.156
[    31.400] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    31.400] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    31.400] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    31.400] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    31.400] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    31.400] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    31.401] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    31.403] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    31.403] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.403] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    31.403] (**) Dell WMI hotkeys: always reports core events
[    31.403] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    31.403] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    31.403] (--) evdev: Dell WMI hotkeys: Found keys
[    31.403] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    31.403] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
[    31.403] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    31.403] (**) Option "xkb_rules" "evdev"
[    31.403] (**) Option "xkb_model" "pc105"
[    31.403] (**) Option "xkb_layout" "us"
[    35.378] (II) intel(0): EDID vendor "INL", prod id 10
[    35.378] (II) intel(0): Printing DDC gathered Modelines:
[    35.378] (II) intel(0): Modeline "1366x768"x0.0   67.10  1366 1383 1395 1434  768 771 773 781 +hsync -vsync (46.8 kHz eP)
[    36.296] (II) intel(0): switch to mode 1366x768@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    51.025] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xThanks
[    51.557] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    51.574] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

I think xorg.failsafe.log looks funny. I'm not sure about the others.

PS, how do I go about trouble shooting this?

Thanks. Hannibal

---

### Post by workshopsystems on 2015-08-13
```

sudo apt-get instaII xf86-video-fbdev

```

reboot and check for crash

---

### Post by coljohnhannibalsmith on 2015-08-13
sophie@sophie-Inspiron-1545:~$ sudo apt-get install xf86-video-fbdev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xf86-video-fbdev
sophie@sophie-Inspiron-1545:~$

---

### Post by TheFu on 2015-08-16
Will the requested information be provided?

---

### Post by coljohnhannibalsmith on 2015-08-16
> **TheFu said:**
> Will the requested information be provided?%

I've finally managed to tunnel into my target machine. I'm using an app called "top." Unfortunately, this has no triggers or alarms; so I've basically had to watch it for long periods, just to get an idea of the conditions immediately before and after a crash. Xorg appears to be the culprit; but the percent of cpu usage never appears to excede 11%. It varies from about 5 - 10% normally. Please see attachments.

---

### Post by TheFu on 2015-08-16
We don't need/want images. Plus if xorg had crashed, you won't be able to capture the screen.

Run **top  -b -n 1 > /tmp/top-file.txt ** in a terminal after you notice the crash to capture the process table. Then please copy/paste it here for 200 bytes, not 50Kb per image.  Images aren't usually necessary.  Plus, if the machine seems to have locked up, you have to come in from another machine to do it.

Those images don't make me think there is anything wrong.

Did you figure out which GPU driver is being used - proprietary or F/LOSS?  Try the other one.

---

### Post by coljohnhannibalsmith on 2015-08-17
> **TheFu said:**
> We don't need/want images. Plus if xorg had crashed, you won't be able to capture the screen.

Run **top  -b -n 1 > /tmp/top-file.txt ** in a terminal after you notice the crash to capture the process table. Then please copy/paste it here for 200 bytes, not 50Kb per image.  Images aren't usually necessary.  Plus, if the machine seems to have locked up, you have to come in from another machine to do it.

Those images don't make me think there is anything wrong.

Did you figure out which GPU driver is being used - proprietary or F/LOSS?  Try the other one.

The images are from the remote machine I'm tunneling in with.

```

sophie@sophie-Inspiron-1545:~$ sudo lshw -c video
[sudo] password for sophie: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       [COLOR=#0000ff]*configuration: driver=i915 latency=0*[/COLOR]
       resources: irq:46 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff
sophie@sophie-Inspiron-1545:~$
```

I'm waiting on a crash now.

---

### Post by coljohnhannibalsmith on 2015-08-17
Here's the output from a crash that puts the system in low graphics mode and requires a cold boot.

Xorg is way at the bottom and not using any cpu%.

```

top - 14:26:42 up  1:57,  2 users,  load average: 0.00, 0.01, 0.05
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.1 us,  1.3 sy,  0.6 ni, 94.4 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4007820 total,  1222356 used,  2785464 free,    86604 buffers
KiB Swap:  4150268 total,        0 used,  4150268 free.   800348 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 3167 sophie    20   0   29016   3004   2608 R   6.5  0.1   0:00.01 top
    1 root      20   0   34032   4556   2700 S   0.0  0.1   0:01.78 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.15 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.63 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.56 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.63 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.03 watchdog/0
   15 root      rt   0       0      0      0 S   0.0  0.0   0:00.03 watchdog/1
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/1
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.17 ksoftirqd/1
   19 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   22 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd
   24 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   25 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   26 root      39  19       0      0      0 S   0.0  0.0   0:00.53 khugepaged
   27 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   28 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   29 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   30 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   31 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   32 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khubd
   33 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   34 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   35 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:1
   36 root      20   0       0      0      0 S   0.0  0.0   0:02.65 kworker/1:1
   38 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   39 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_m+
   40 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-k+
   52 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   53 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 acpi_therm+
   54 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ipv6_addrc+
   73 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   74 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_ma+
  123 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  125 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  126 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_0
  127 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  128 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_1
  129 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  130 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_2
  131 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  132 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_3
  133 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_4
  134 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_4
  135 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_5
  136 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_5
  146 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_7
  147 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_7
  148 root      20   0       0      0      0 S   0.0  0.0   0:00.03 usb-storage
  149 root      20   0       0      0      0 S   0.0  0.0   0:03.45 kworker/0:3
  154 root       0 -20       0      0      0 S   0.0  0.0   0:00.01 kworker/1:+
  155 root       0 -20       0      0      0 S   0.0  0.0   0:00.01 kworker/0:+
  164 root      20   0       0      0      0 S   0.0  0.0   0:00.09 jbd2/sda6-8
  165 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-c+
  287 root      20   0   19480   2056   1800 S   0.0  0.1   0:00.26 upstart-ud+
  292 root      20   0   51856   3844   2904 S   0.0  0.1   0:00.24 systemd-ud+
  369 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
  373 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
  398 root      20   0       0      0      0 S   0.0  0.0   0:00.02 wl_event_h+
  535 root      20   0   15396   1632   1252 S   0.0  0.0   0:00.08 upstart-so+
  562 root      20   0  272708  14468  12596 S   0.0  0.4   0:00.23 smbd
  601 root      20   0   15280    212      0 S   0.0  0.0   0:00.07 upstart-fi+
  615 syslog    20   0  255848   2840   2360 S   0.0  0.1   0:00.04 rsyslogd
  621 message+  20   0   40576   3648   2240 S   0.0  0.1   0:00.80 dbus-daemon
  639 root      20   0  330240   9576   6384 S   0.0  0.2   0:00.01 ModemManag+
  641 root      20   0   19300   2664   2440 S   0.0  0.1   0:00.00 bluetoothd
  655 root      10 -10       0      0      0 S   0.0  0.0   0:00.00 krfcommd
  663 root      20   0   43564   3324   2928 S   0.0  0.1   0:00.03 systemd-lo+
  668 avahi     20   0   32356   2864   2560 S   0.0  0.1   0:00.04 avahi-daem+
  671 avahi     20   0   32228    252      0 S   0.0  0.0   0:00.00 avahi-daem+
  710 root      20   0  344952  10380   8844 S   0.0  0.3   0:00.62 NetworkMan+
  716 root      20   0  280984   7256   5336 S   0.0  0.2   0:00.40 polkitd
  737 root      20   0   30620   4212   3764 S   0.0  0.1   0:01.73 wpa_suppli+
  747 root      20   0  272708   8848   6976 S   0.0  0.2   0:00.03 smbd
  782 root      20   0   10236   5240   2932 S   0.0  0.1   0:00.00 dhclient
  867 root      20   0   20020   2188   2036 S   0.0  0.1   0:00.00 getty
  871 root      20   0   20020   2156   1996 S   0.0  0.1   0:00.00 getty
  879 root      20   0   20020   2124   1968 S   0.0  0.1   0:00.00 getty
  880 root      20   0   20020   2212   2052 S   0.0  0.1   0:00.00 getty
  884 root      20   0   20020   2204   2052 S   0.0  0.1   0:00.00 getty
  942 root      20   0   61372   5608   4928 S   0.0  0.1   0:00.01 sshd
  953 daemon    20   0   19144    160      0 S   0.0  0.0   0:00.00 atd
  954 root      20   0   23660   2376   2120 S   0.0  0.1   0:00.00 cron
  996 kernoops  20   0   37148   2588   2264 S   0.0  0.1   0:00.10 kerneloops
 1001 root      20   0    4372   1592   1416 S   0.0  0.0   0:00.00 acpid
 1041 root      20   0   75492   5880   4972 S   0.0  0.1   0:00.01 cups-brows+
 1063 whoopsie  20   0  363388  11740   8300 S   0.0  0.3   0:00.01 whoopsie
 1084 nobody    20   0   35228   3324   3072 S   0.0  0.1   0:00.03 dnsmasq
 1139 mysql     20   0  615784  55256  10856 S   0.0  1.4   0:04.68 mysqld
 1158 debian-+  20   0  165428 118324  41416 S   0.0  3.0   0:13.86 tor
 1240 root      20   0  230508   9400   7908 S   0.0  0.2   0:00.02 winbindd
 1268 root      20   0  191452   5020   3724 S   0.0  0.1   0:00.06 nmbd
 1275 root      20   0  230508   6964   5452 S   0.0  0.2   0:00.01 winbindd
 1365 root      20   0  276372  22044  16636 S   0.0  0.6   0:00.25 apache2
 1383 www-data  20   0  276396   7416   2000 S   0.0  0.2   0:00.00 apache2
 1384 www-data  20   0  276396   7416   2000 S   0.0  0.2   0:00.00 apache2
 1385 www-data  20   0  276396   7416   2000 S   0.0  0.2   0:00.00 apache2
 1386 www-data  20   0  276396   7416   2000 S   0.0  0.2   0:00.00 apache2
 1387 www-data  20   0  276396   7416   2000 S   0.0  0.2   0:00.00 apache2
 1412 root      20   0   20020   2132   1968 S   0.0  0.1   0:00.00 getty
 1549 root      20   0  287880   6976   5644 S   0.0  0.2   0:00.24 accounts-d+
 1571 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1664 root      20   0  239440   9648   6576 S   0.0  0.2   0:00.16 upowerd
 1685 rtkit     21   1  168920   2532   2312 S   0.0  0.1   0:00.07 rtkit-daem+
 1919 colord    20   0  301468   8808   7420 S   0.0  0.2   0:00.17 colord
 2321 root      20   0  371648   8128   5972 S   0.0  0.2   0:01.01 udisksd
 2364 root      20   0   77104   6676   5368 S   0.0  0.2   0:00.03 cupsd
 2396 root      20   0   13692   2064   1580 S   0.0  0.1   0:00.00 mount.ntfs
 2532 root      20   0  126440   6912   5820 S   0.0  0.2   0:00.03 sshd
 2535 root      20   0 1054056   6292   5140 S   0.0  0.2   0:00.03 console-ki+
 2636 sophie    20   0  126440   4120   3036 S   0.0  0.1   0:00.41 sshd
 2637 sophie    20   0   27028   5460   3280 S   0.0  0.1   0:00.08 bash
 2691 root      20   0  126440   7032   5936 S   0.0  0.2   0:00.02 sshd
 2729 sophie    20   0  126440   4116   3028 S   0.0  0.1   0:00.01 sshd
 2730 sophie    20   0   27028   5500   3324 S   0.0  0.1   0:00.11 bash
 2931 sophie    20   0   29152   3020   2492 S   0.0  0.1   0:13.82 top
 3018 root      20   0   18004   3048   2756 S   0.0  0.1   0:00.00 failsafeXS+
 3039 root      20   0   16004    952    816 S   0.0  0.0   0:00.00 xinit
 3040 root      19  -1  229952  27784  17136 S   0.0  0.7   0:00.11 Xorg
 3043 root      20   0       0      0      0 S   0.0  0.0   0:01.36 kworker/1:0
 3046 root      20   0   18044   3116   2792 S   0.0  0.1   0:00.00 failsafeXi+
 3053 root      20   0  392216  33592  27288 S   0.0  0.8   0:00.11 zenity
 3057 root      20   0   24444    248      0 S   0.0  0.0   0:00.00 dbus-launch
 3058 root      20   0   39220   2340   1964 S   0.0  0.1   0:00.00 dbus-daemon
 3060 root      20   0  346016   6052   5524 S   0.0  0.2   0:00.00 at-spi-bus+
 3064 root      20   0   39120   3292   3008 S   0.0  0.1   0:00.00 dbus-daemon
 3067 root      20   0  124916   4876   4436 S   0.0  0.1   0:00.00 at-spi2-re+
 3101 root      20   0       0      0      0 S   0.0  0.0   0:00.05 kworker/u4+
 3130 root      20   0       0      0      0 S   0.0  0.0   0:00.02 kworker/u4+
```

---

### Post by coljohnhannibalsmith on 2015-08-17
Here's another one. This was taken after the desktop froze while I was working. I've noticed that Xorg gets unstable around 11% cpu. Xorg is also listed twice with the same PID, but different metrics.

```
top - 14:44:26 up 15 min,  3 users,  load average: 0.15, 0.33, 0.32
Tasks: 203 total,   2 running, 201 sleeping,   0 stopped,   0 zombie
%Cpu(s):  8.8 us,  3.5 sy,  0.0 ni, 86.7 id,  1.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4007820 total,  1919400 used,  2088420 free,    84348 buffers
KiB Swap:  4150268 total,        0 used,  4150268 free.   846776 cached Mem

 1549 root      20   0  395376  40640  30948 R  12.9  1.0   0:49.17 Xorg        
 1549 root      20   0  411308  41884  32000 S   6.0  1.0   0:51.27 Xorg        
 2206 sophie    20   0  477652  32944  19456 S   4.6  0.8   0:33.21 compiz      
 2505 sophie    20   0  556600  23464  19192 S   3.7  0.6   0:28.57 cairo-clock 
 2620 sophie    20   0 1485804 482180  88580 S   3.0 12.0   1:59.92 firefox     
 2107 sophie    20   0  946916  25848  21068 S   2.7  0.6   0:00.28 gnome-sess+ 
 2210 sophie    20   0  698660  36992  25804 S   1.0  0.9   0:01.96 gnome-panel 
  698 root      20   0   43564   3264   2884 S   0.7  0.1   0:00.03 systemd-lo+ 
 2497 sophie    20   0  546596  14224  12156 S   0.7  0.4   0:05.13 conky       
    8 root      20   0       0      0      0 S   0.3  0.0   0:00.30 rcuos/0     
   35 root      20   0       0      0      0 S   0.3  0.0   0:00.72 kworker/0:1 
  719 root      20   0  280988   9296   5336 S   0.3  0.2   0:00.39 polkitd     
 1140 mysql     20   0  615784  57660  10868 S   0.3  1.4   0:00.78 mysqld      
 1154 debian-+  20   0  164084 116740  41348 S   0.3  2.9   0:06.49 tor         
 2177 sophie    20   0  558884  20596  16200 S   0.3  0.5   0:00.37 bamfdaemon  
 2293 sophie    20   0 1406716  43504  33784 S   0.3  1.1   0
```

---

### Post by coljohnhannibalsmith on 2015-08-26
Last time I did an upgrade, I got this:
```

Processing triggers for hicolor-icon-theme (0.13-1) ...

(gtk-update-icon-cache-3.0:4272): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Setting up libgdk-pixbuf2.0-common (2.30.7-0ubuntu1.1) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1.1) ...
Setting up gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.1) ...
Setting up gvfs-common (1.20.3-0ubuntu1.2) ...
Setting up gvfs-bin (1.20.3-0ubuntu1.2) ...
Setting up gvfs-libs:amd64 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-daemons (1.20.3-0ubuntu1.2) ...
Setting up gvfs:amd64 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-backends (1.20.3-0ubuntu1.2) ...
Setting up gvfs-fuse (1.20.3-0ubuntu1.2) ...
Setting up unity-settings-daemon (14.04.0+14.04.20150825-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
sophie@sophie-Inspiron-1545:~$ 
```

---

### Post by coljohnhannibalsmith on 2015-09-01
Xorg after crash: (please see attachment)

---

