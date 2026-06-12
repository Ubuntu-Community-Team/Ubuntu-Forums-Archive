---
title: "Ubuntu samba interfering on network"
date: 2009-06-15
forum: General Help
---

### Post by brunoskrebs on 2009-06-15
Hi there,

I have just installed ubuntu in my computer at work and then I setup samba to share a folder with my colleagues, but this is making a mess in the network around here. The problem is that we already have another samba running in another server that work as home folder to the windows users, and to share printers.

What I want to know is how to setup my samba correctly so it stops interfering, and share properly my folders on the network?

Thanks in advance,
Bruno Krebs.

---

### Post by Celauran on 2009-06-15
What do you mean by making a mess/interfering? What's going on? Also, how is Samba set up? So long as both Samba machines aren't trying to use shares with the same name, I don't see what the problem would be. Please elaborate.

---

### Post by brunoskrebs on 2009-06-15
Well, it is like this, we have a domain in here, that the name is BRASMARINEBR, so when I setup this samba, which have the default values, my samba started interfering like when someone in another machine, using windows was trying to print, they couldn't. And that is because this samba that setup here in my machine, I'm pretty sure that the problem is my samba, because when I stop it, everything else works fine.
Well, someone here told me that my samba is in working in the same level as the other network master, and that I would have to put in a secondary level. But the person who told me that does not know how to do that...

I'm wondering if it still is too confusing, or you can understand now...

---

### Post by scrooge_74 on 2009-06-15
Check if both machines are being use as Domain Master, when election time comes around one may be stealing it from the other.

**Forcing Samba to Be the Master**

Who becomes the master browser is determined by an election process using broadcasts. Each election packet contains a number of parameters that determine what precedence (bias) a host should have in the election. By default Samba uses a low precedence and thus loses elections to just about every Windows network server or client.

If you want Samba to win elections, set the os level global option in smb.conf to a higher number. It defaults to 20. Using 34 would make it win all elections over every other system (except other Samba systems).

An os level of two would make it beat Windows for Workgroups and Windows 9x/Me, but not MS Windows NT/200x Server. An MS Windows NT/200x Server domain controller uses level 32. The maximum os level is 255.

If you want Samba to force an election on startup, set the preferred master global option in smb.conf to yes. Samba will then have a slight advantage over other potential master browsers that are not preferred master browsers. Use this parameter with care, because if you have two hosts (whether they are Windows 9x/Me or NT/200x/XP or Samba) on the same local subnet both set with preferred master to yes, then periodically and continually they will force an election in order to become the LMB.

If you want Samba to be a DMB, then it is recommended that you also set preferred master to yes, because Samba will not become a DMB for the whole of your LAN or WAN if it is not also a LMB on its own broadcast isolated subnet.

It is possible to configure two Samba servers to attempt to become the DMB for a domain. The first server that comes up will be the DMB. All other Samba servers will attempt to become the DMB every 5 minutes. They will find that another Samba server is already the DMB and will fail. This provides automatic redundancy should the current DMB fail. The network bandwidth overhead of browser elections is relatively small, requiring approximately four UDP packets per machine per election. The maximum size of a UDP packet is 576 bytes. 

[[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#browse-force-master](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#browse-force-master)]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#browse-force-master")

---

### Post by brunoskrebs on 2009-06-15
yes, I think that is the way, I am going to take a look in this how to, thank you very much.

---

### Post by swerdna on 2009-06-15
Make sure that the [global] stanza of smb.conf does not contain any of these lines
```
preferred master = yes
domain master = yes
wins support = yes
```

---

### Post by brunoskrebs on 2009-06-15
Well unfortunately I didn't have time to read all the How To, but I read a few parts and the I have solved by changing my smb.conf file like this:
> 
[global]

domain master = no
local master = no
preferred master = no
os level = 0


Before that I still had problems, because I another configuration parameter, like this:
> 
[global]

workgroup = BRASMARINEBR

domain master = no
local master = no
preferred master = no
os level = 0


With that I was still having problem, does anyone know why?

---

### Post by scrooge_74 on 2009-06-15
I'm going to sound dumb here, but did you restarted the samba deamons?

---

### Post by brunoskrebs on 2009-06-15
Ok, then I am going to sound dumber, do you mean:

sudo /etc/init.d/samba restart ?

If is that what you mean, then yes I restarted it. When I put workgroup, my other computer, cannot connect to printers in the network, when I remove, and restart samba it finds...

---

### Post by swerdna on 2009-06-15
The workgroup name must be the same for all computers. And the netbios name must be unique to your computer, not duplicated elsewhere on the LAN.
Name resolution and browse control needs to be tightened up a bit. These lines (among others) should be in the [global] stanza:
```
[global]
workgroup = SAME_FOR_ALL
netbios name = UNIQUE_TO_THIS_MACHINE
name resolve order = bcast host lmhosts wins
map to guest = Bad User
local master = yes
preferred master = no
os level = 20
domain master = no
```

Don't forget the /etc/init.d/samba restart (or a reboot).
If that doesn't work then post here the contents of smb.conf and ask the system administrator if the LAN is using a "wins server". If that's in use, the problem is a completely different issue.

---

### Post by brunoskrebs on 2009-06-17
Yeah well,

I'm a little bit concerned about putting this "local master = yes" because this was bringing some issues like I said before...

---

### Post by swerdna on 2009-06-17
> **brunoskrebs said:**
> Yeah well,

I'm a little bit concerned about putting this "local master = yes" because this was bringing some issues like I said before...

Should be OK with the other settings being no for preferred master and domain master.

---

