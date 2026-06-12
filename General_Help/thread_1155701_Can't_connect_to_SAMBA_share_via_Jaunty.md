---
title: "Can't connect to SAMBA share via Jaunty"
date: 2009-05-11
forum: General Help
---

### Post by Nixie Pixel on 2009-05-11
Hello, I've set up a SAMBA share on Ubuntu Server 8.10, with the security set to share and permissions opened up on the directory to allow all to read, write, execute.

I have Windows machines that can all see the share, but only one of my two Jaunty laptops can connect to the server.

I do this by Places -> Connect to Server -> Windows Share -> (enter server name, share name)

This works on one, but the other is giving me a "can't connect" error.  Both have the latest version of smbfs installed...what could be the problem?

Thanks!

---

### Post by Peter09 on 2009-05-11
does the faulty machine see the others at all? Can you ping a windows machine.

---

### Post by Nixie Pixel on 2009-05-11
I can ping both a windows machine and the Ubuntu Server from the faulty laptop, I just can't connect via SMB...

I also get an error when I try to open networking, it says "Cound not display "network:///".

Error:  DBus error or.freedesktop.DBus.Error.NoReply: Did not receive a reply.

---

### Post by Peter09 on 2009-05-11
There is a command line utility called 'smbtree' I am not sure if it is installed by default. Try it on the command line, it will list all visible Samba shares.

---

### Post by Nixie Pixel on 2009-05-11
Ok, I've run it, and it shows my server (//LION) on that list.  Each computer on the list returned "cli_start_connection: failed to connect to COMPUTERNAME (0.0.0.0).  Error NT_STATUS_ACCESS_DENIED"

On the "good" laptop everything is the same except this is returned for //LION:

Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK

---

### Post by Peter09 on 2009-05-11
Try adding

> client lanman auth = Yes 
lanman auth = Yes 
to smb.conf

---

### Post by Nixie Pixel on 2009-05-11
I assume you mean add it to smb.conf on the server?

Done so...no change to the results.

It has to be a networking problem on the laptop, right?  I can open networking on the "good" laptop, so I'm guessing there is an issue on the one that can't...

---

### Post by Peter09 on 2009-05-11
Hi just realized that your server error was a report against your 'Good' Server'. However I suggest that you compare the file between your machines 

```
/etc/nsswitch.conf
```

check 'wins' is in there.

---

### Post by Nixie Pixel on 2009-05-11
Both laptops have the same /etc/nsswitch.conf:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by Peter09 on 2009-05-11
As a though you will need to restart winbind and samba after the edit.

```
sudo /etc/init.d/winbind restart
sudo /etc/init.d/samba restart

```

---

### Post by Nixie Pixel on 2009-05-11
Sorry, I'm restarting after which edit?  Adding the client/lanman info?  I restarted samba, I'll restart winbind now...

I did get that error from the "good" computer, the other computer just says "ACCESS_DENIED."

---

### Post by Peter09 on 2009-05-11
As a check, can you ping a windows machine by name from each of the Linux machines.

As you are on a mixed network is worth doing below


Add wins after dns so that the line looks like

> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4

---

### Post by Peter09 on 2009-05-11
As far as I can tell - and this is somewhat a fuzzy guess - the errors that you are getting are around name resolution. This involves, winbind, nsswitch, and /etc/hosts (which should not be used in a proper setup).

Still thinking - allthough this is a painful process :)

---

### Post by Nixie Pixel on 2009-05-11
Hmm, just "ping hostname?"

Pinging a windows computer returns packets in about 40ms.  My router's DNS settings are for OpenDNS, and the IP returned is an OpenDNS IP:

```
nixie@dove:~$ ping bateleur
PING bateleur.wavecable.com (208.67.216.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (208.67.216.132): icmp_seq=1 ttl=52 time=42.9 ms
64 bytes from hit-nxdomain.opendns.com (208.67.216.132): icmp_seq=2 ttl=52 time=44.1 ms
```

---

### Post by dmizer on 2009-05-11
> **Peter09 said:**
> Add wins after dns

This is incorrect. WINS should be _before_ DNS. Some DNS providers (like [OpenDNS](http://www.opendns.com)) forward unknown DNS queries to a "[did you mean](http://www.opendns.com/solutions/smb/guide/)" search page. To the system, this counts as a resolved host name. So in this situation, if DNS is queried before WINS then you will get a failure when trying to browse networked systems. This is becoming more and more popular by many ISP's because it's one way of avoiding [typo-squatting](http://en.wikipedia.org/wiki/Typosquatting).

---

### Post by Peter09 on 2009-05-11
Thanks for the correction dmizer

---

### Post by Peter09 on 2009-05-11
Just noticed the IP of the computer that you pinged 
208.67.216.132 - is that an internal IP?

---

### Post by Nixie Pixel on 2009-05-11
Ok, so putting wins before dns changes the equation on the "good" laptop - pinging a windows machine on the network pings a network address (192.168.0.x).

However, it makes no change on the "bad" laptop, pings there to a hostname on the local network still return an OpenDNS IP address even after adding wins.

I should note that the only WINS server on the network is the Ubuntu Server where I set wins support to be yes in smb.conf.

---

### Post by Peter09 on 2009-05-11
Have you checked winbind is running on the 'bad' machine.

---

### Post by Peter09 on 2009-05-11
Can you compare the output of the route command between machines.

```
route
```

---

### Post by dmizer on 2009-05-11
> **Peter09 said:**
> Thanks for the correction dmizer

No problem :)

Here's more information on the name resolution problem: [http://www.backports.ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://www.backports.ubuntuforums.org/showpost.php?p=7157868&postcount=12)

If none of that works, a firewall (On the server or on the client) may be interfering.

---

### Post by Nixie Pixel on 2009-05-11
Here are the results, the same for both laptops:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
```

How can I tell if winbind is running?

---

### Post by Peter09 on 2009-05-11
perhaps the easiest way is attempt to restart it with

```
sudo /etc/init.d/winbind restart
```

watch for any messages.

---

### Post by dmizer on 2009-05-11
> **Nixie Pixel said:**
> I should note that the only WINS server on the network is the Ubuntu Server where I set wins support to be yes in smb.conf.

In smb.conf, "wins support" should be set to no. This option is only for use when the server is being used as a WINS server across a multi-subnetted network (so names will resolve across different subnets).

Though, this mistake is probably not hurting anything or preventing you from connecting.

Can you post your entire smb.conf file?

---

### Post by Peter09 on 2009-05-11
Dmizer,
the thing of interest to me is that when she tries to ping an internal windows machine it goes out to an external DNS server - it seems to come down to name resolution.

---

### Post by Nixie Pixel on 2009-05-11
The client is a vanilla 9.04 Jaunty Jackalope desktop installation.  The server was just installed the other day, Ubuntu Server 8.10.  Neither have firewalls running, nor have I messed with the IP tables.

Trying to start winbind on the "bad" machine returns:
"sudo:  /etc/init.d/winbind: command not found"

I'll post smb.conf in a few minutes, but I thought I could use SAMBA as a WINS server for a single subnet?

---

### Post by Peter09 on 2009-05-11
You need to install winbind - thats most probably it.

```
sudo apt-get install winbind
```

---

### Post by dmizer on 2009-05-11
> **Peter09 said:**
> Dmizer,
the thing of interest to me is that when she tries to ping an internal windows machine it goes out to an external DNS server - it seems to come down to name resolution.

Yes, that *could* be a result of a few things.

[LIST=1]
[*]Winbind is not actually installed, or is not running on the client.
[*]WINS is not being queried before DNS.
[*]The client is not finding the server because the client and server are not members of the same workgroup (Nautilus GVFS cannot search inside workgroups that it is not a member of).
[*]A firewall is preventing WINS queries.
[/LIST]

When using OpenDNS, this is expected behavior for the above problems (for the reasons I explained earlier).

---

### Post by Nixie Pixel on 2009-05-11
Thanks very much for your help, I appreciate it very much - I installed winbind on the "bad" laptop (it was already on the "good" one) and now I can connect to the server!

Since you mentioned it, how can I set the windows workgroup on an Ubuntu machine?

Thanks again!

---

### Post by Peter09 on 2009-05-11
There is a workgroup setting in /etc/samba/smb.conf. 
Almost first line in the configuration

---

### Post by Nixie Pixel on 2009-05-11
On the server, yes, but I mean on the clients?

Edit:  Nevermind, I'm silly.

---

### Post by pablosanchezuy on 2009-05-11
aptitude install pyneighborhood

best way to find and mount windows shares.

pablo

---

### Post by mktoni on 2009-05-11
Try smbtree -d 3 to display some debug information. Look for something like this:

Connecting to host=<HOSTNAME>
resolve_lmhosts: Attempting lmhosts lookup for name <HOSTNAME><0x20>
resolve_wins: Attempting wins lookup for name <HOSTNAME><0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name <HOSTNAME><0x20>

Post the results here. 
Maybe this can help.

---

