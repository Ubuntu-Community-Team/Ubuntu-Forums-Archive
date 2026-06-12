---
title: "NFS client &quot;mount: RPC: Program not registered&quot;"
date: 2005-10-17
forum: Desktop Environments
---

### Post by JLTB on 2005-10-17
This doesn't seem too complicated, but I just can't get an NFS client going for some reason (on Breezy, all updates done).

I have an NFS server (working correctly for sure, another NFS client can connect to it) that I can't connect to with my breezy computer.  All my requests ARE going through (they show up in the firewall logs on the server), however whenever I try to mount shares I get "mount: RPC: Program not registered" thrown back at me.

Things I have installed on the client include: nfs-kernel-server nfs-common portmap autofs .... etc.

The rpc.portmap process does not appear to be running ('ps aux|grep rpc.' only gives me 'rpc.statd').

Trying to run 'sudo /etc/init.d/nfs-common start' fails.

**** EDIT ****
  The server is Debian stable and is hosted somewhere else, security is alright (firewalls only allowing connections between the 3 IPs .. server, client1, and client2 ... etc).
**** /EDIT ****

Hopefully someone knows how to get NFS going with Ubuntu Breezy :-D

.... and thank you thank you thank you if you do! :-D

---

### Post by JLTB on 2005-10-18
anybody .. anybody?

I really need this one solved.  Any tips comments ... even suggestions of other approaches are welcome!

---

### Post by gdcondor on 2005-10-18
i've exactly the same pb between two breezy and it was working with hoary :((

updating to breezy is really a complicated process :( it was really easier between warty and hoary !!

---

### Post by matthias_k on 2005-10-18
I had the same problem with Hoary, unfortunately I can't reproduce the steps exactly how I fixed it, because it was rather strange.
First, you need the portmap daemon running. This is most probably already the case. I searched the web and read something about a tool called "autofs" which was claimed to be needed for that to work. According to the poster, he installed autofs, rebooted and it worked for him. So I installed autofs, rebooted, but no luck. Being frustrated, I powered off my notebook and didn't do anything for a couple of hours. When I booted the notebook again after some time, it all of a sudden worked.

Anyway, look for autofs in apt and install it, maybe it also fixes the problem for you (sooner or later heh). If it doesn't work immediately, try waiting a couple of hours lol.

You will also want to edit your /etc/hosts.allow and /etc/hosts.deny, since I noticed that they aren't set up properly (they're empty).

---

### Post by matthias_k on 2005-10-18
Actually, I just noticed that autofs is not installed on my Breezy installation, and on Breezy, NFS worked out of the box, so just forget about that, it was probably bullsh**...

---

### Post by JLTB on 2005-10-18
Hey,

Thanks so much for the replies!  As one poster noticed I do have autofs installed and no ammount of rebooting or waiting has helped the situation.  Portmap is indeed running (ps aux|grep portmap says so) ... however some tutorials I have read mention that there should be a process called rpc.portmap running (I don't have that).

rpcinfo gives
```

james@home: sudo rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    607  status
    100024    1   tcp    610  status

```

Also, as I mentioned before, 'sudo /etc/init.d/nfs-common start' fails.  This seems bad, does it not fail for any of you?  (nfs-kernel-server seems to start fine).

sigh.

---

### Post by EstebanT on 2005-10-18
Dear,

  Try install "NFS-kernel-server" package !


 Esteban.

---

### Post by matthias_k on 2005-10-18
I think he said it is running fine, so it's probably installed...

Anyway, did you set up your /etc/hosts.allow and /etc/hosts.deny? Maybe that helps. You have to allow remote hosts to connect to your PC using NFS. I'm not sure if I remember the syntax 100% (see manpages). For example, if you're in a LAN, type:

```

# hosts.allow
in.nfsd: LOCAL

# hosts.deny
ALL: ALL

```

---

### Post by john_c on 2005-10-18
I had the same problem last night with two computers running Hoary.  Found this entry:

 If you get the message 'RPC: Remote system error - Connection refused error' then you should ensure that your NFS client has been included in /etc/hosts on the server.

Above is on the ubuntu wiki at:
[https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29](https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29)

It worked for me if that's any help.

John_c

---

### Post by JLTB on 2005-10-19
Hi Guys,

EstebanT: Yes I have nfs-kernel-server installed as previously stated

matthias_k: The remote host is fine (I can connect to remote host via another fedora computer on a different network). When i try to connect via broken-client I can see the connection attempts (ACCEPTED packets) comming through on remote-server's firewall log.  So I think all data is being transmitted okay, but I need to look into this further still I think.

john_c: There isn't a connection error (ie: it hasn't anything to do with authentication).  Rather the client doesn't seem able to connect to any RPC resources.  The error was 'RPC: Program not registered' on broken-client, remote-server is working fine I'm pretty sure.

I'm still stuck.  If anyone has anymore tips I'd love to hear them!

PS: I'm at work right now, which is why my responses are "to the point," I am appreciative of your feedback.

---

### Post by wgscott on 2005-10-19
I've had this problem on Mac OS X before.  It was a problem with tcpwrappers.   Temporarily move the files /etc/hosts.allow and hosts.deny out of the way and see if that cures it.  If it does, then you may need one or more of the following lines:

portmap: 158.114. : ALLOW
lockd:  158.114. : ALLOW   
rquotad: 125.114. : ALLOW   
statd:  158.114. : ALLOW 

158.114.xxx.xx  are domain IP addresses (you have to change to use yours).  For some reason you have to supply these numerically instead of with domain names.  (Maybe putting these in /etc/hosts  would cure that.)

Also, I read somewhere that NSF on breezy doesn't use the protmapper.  I upgraded, and mine still runs, so I don't want to mess with it...

---

### Post by JLTB on 2005-10-20
Hey wgscott,

I'll give that a shot.  As far as I know NFS does use the port mapper, but what do I know lol.  I'll look into that.

Cheers!

---

### Post by JLTB on 2005-10-20
Ah no luck, I should have remembered since I have tried this already, even with hosts.* empty it doesn't work.

---

### Post by le0buntu on 2005-10-23
I used a combination of [https://wiki.ubuntu.com/NFSServerHowTo](https://wiki.ubuntu.com/NFSServerHowTo) and [http://nfs.sourceforge.net/nfs-howto/server.html](http://nfs.sourceforge.net/nfs-howto/server.html) when setting up NFS on Breezy (I've only been playing with Linux for about a month now, and this is one of two flavors of linux I've tried, the other being Gentoo).

My [FONT="Lucida Console"]/etc/hosts.deny[/FONT] has
```
# - Deny Access to NFS related services for all addresses
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

```

My [FONT="Lucida Console"]/etc/hosts.allow[/FONT] has 
```
# - Allow access to NFS related services for LAN addresses
portmap: 192.168.211.0/255.255.255.0
lockd:   192.168.211.0/255.255.255.0
rquoted: 192.168.211.0/255.255.255.0
mountd:  192.168.211.0/255.255.255.0
statd:   192.168.211.0/255.255.255.0
```

With nfs started [FONT="Lucida Console"]rpcinfo -p localhost[/FONT] shows
```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    693  status
    100024    1   tcp    696  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  33443  nlockmgr
    100021    3   udp  33443  nlockmgr
    100021    4   udp  33443  nlockmgr
    100021    1   tcp  32889  nlockmgr
    100021    3   tcp  32889  nlockmgr
    100021    4   tcp  32889  nlockmgr
    100005    1   udp   1006  mountd
    100005    1   tcp   1009  mountd
    100005    2   udp   1006  mountd
    100005    2   tcp   1009  mountd
    100005    3   udp   1006  mountd
    100005    3   tcp   1009  mountd
```

As I wanted mountd to run on a known (not random) port, I edited [FONT="Lucida Console"]/etc/default/nfs-kernel-server[/FONT] to set the port rpc mount was using, and configured a rule in FireStarter to allow the local subnet access. ([FONT="Lucida Console"]/etc/default/nfs-kernel-server[/FONT] is referenced by [FONT="Lucida Console"]/etc/init.d/nfs-kernel-server[/FONT] when starting [FONT="Lucida Console"]mountd[/FONT])

```
# Number of servers to start up
RPCNFSDCOUNT=8

# Options for rpc.mountd
# 2005-10-23 Leo
# Added option to set port to 635 (instead of a random port) and for no TCP (thus only UDP) 
#RPCMOUNTDOPTS=
RPCMOUNTDOPTS="--port 635 --no-tcp"

# If you are not running NFS with RPCSEC_GSS security, and wish to
# disable the gssd server daemon, then set NEED_SVCGSSD to "no".
NEED_SVCGSSD=no
```

After stopping nfs [FONT="Lucida Console"]/etc/init.d/nfs-kernel-server stop[/FONT] 

```
# rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    693  status
    100024    1   tcp    696  status
```

And starting NFS again, [FONT="Lucida Console"]/etc/init.d/nfs-kernel-server start[/FONT], [FONT="Lucida Console"]rpcinfo -p localhost[/FONT] now shows
```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    693  status
    100024    1   tcp    696  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  34253  nlockmgr
    100021    3   udp  34253  nlockmgr
    100021    4   udp  34253  nlockmgr
    100021    1   tcp  32904  nlockmgr
    100021    3   tcp  32904  nlockmgr
    100021    4   tcp  32904  nlockmgr
    100005    1   udp    635  mountd
    100005    2   udp    635  mountd
    100005    3   udp    635  mountd
```

Does anyone know if I also need to set nlockmgr to a non random port?
(I think I'll need to do more research)

-Leo

---

### Post by JLTB on 2005-10-24
Hey thats a good howto le0buntu,

I'll look into some of the things you mentioned more; however, I think I've found a way around the whole NFS thing with another (better) solution.

Just need to do all the work of implementing it, heh, but that will have to wait since there are some other more pressing matters.

Thanks everyone!

---

### Post by megamania on 2005-10-27
While looking for other stuff, I found this and thought it might be of some use to some of you:

[http://www.freebsddiary.org/nfs-portmap.php](http://www.freebsddiary.org/nfs-portmap.php)

hth...

---

### Post by Dimitri101 on 2005-10-28
Very weird, something like:

hosts.deny
portmap: ALL

hosts.allow
portmap: 192.168.1.0/255.255.255.0

gives a "RPC: Program not registered" error, but

hosts.deny 
ALL: ALL

hosts.allow
ALL: 192.168.1.0/255.255.255.0

works fine ???

---

### Post by cvmostert on 2006-01-13
[QUOTE=JLTB]
Also, as I mentioned before, 'sudo /etc/init.d/nfs-common start' fails.  This seems bad, does it not fail for any of you?  (nfs-kernel-server seems to start fine).
sigh.[/QUOTE]

I also had a problem starting nfs... try to stop or restart it... worked for me... but i still have not transferred files with nfs... still playing around with it... samba didnt wanna work.. so tryning nfs... still nothing... but we will learn!

---

### Post by billgovols on 2006-02-22
I had the same problem and read and tried things found in all the replies in this thread.  Then I thought I'd set nfs aside for a while and try samba.  I was looking for how to specify password for samba shares and found a mount command that specified username and password for a smb share.  It specified file type in the mount command.  When I tried that for NFS, it worked:

mount -t nfs 192.168.2.105:/ /nfs/system2

---

