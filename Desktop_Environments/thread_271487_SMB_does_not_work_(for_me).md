---
title: "SMB does not work (for me)"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Frihet on 2006-10-04
SMB/Firewall Problem.

With the firewall disabled on my Ubuntu machine, I can see my network's SMB share hosts. I cannot see shared directories on them. Error message is: Sorry, couldn't display all the contents of "Windows Network: XYZZY".

I have two Cisco NSLU2 file servers and one XP special purpose machine.

With the firewall enabled, I cannot even see the hosts.

I really want a firewall on my machine (laptop). I can't use a static ip address because the machine goes with me to school when I teach. I also want to get XP off my wife's laptop (XP dual boot).

I have the inbound traffic policy set SMB 137-139 445 for 192.168.0.0 (I assume this is the whole LAN)

I don't see anything else to do.

This UBUNTU problem has been around a long time, and I don't see a solution on the forum. I'm to the point that I have to do something (classes are coming up), so I'm starting to build a Mandrake machine (it works). I don't want to do this. Any ideas, anyone?

Thanks!!!!!

---

### Post by sefs on 2006-10-04
have you got the samba extra package installed?

also I dont think 192.168.0.0 is your whole lan.

It would be either 192.168.0.0/24 or 192.168.0.0/255.255.255.0

That would give you the whole range of machines from .1 to .254

---

### Post by sefs on 2006-10-04
Another tip is with firestart (if this is the firewall gui you use) Dont set the policy in the allow service part...you'll still get problems....I find that you may have to set it in allow host section (i.e the first window) of the policy screen.

---

### Post by Frihet on 2006-10-04
Thanks for the firewall rule clarification. I implemented that. No change.

I do not know what the extras package is.

When I search "samba" in synaptic, I see no "extras" package.

I do have libgnomevfs2-extra installed.

---

### Post by Frihet on 2006-10-04
The firewall rule change does help. I can now see the hosts with the firewall running. I still cannot see the shared resources.

In Windows there is a "workgroup name" that must be common to all hosts -- am I missing something like that?

---

### Post by sefs on 2006-10-04
Yes you have to set it in your /etc/samba/smb.conf file.

Its somewhere near the top usually its MSHOME by default in samba I think, but can be changed to whatever you like by editing the smb.conf file.

NB: You'll probably need to install winbind on the ubuntu machine so that windows machines on the network can access the ubuntu machine via its friendly netbios name and vice versa.  If you do a quick search of the forum you will find a thread on setting up winbind.  You'll have to edit a line in the /etc/nsswitch.conf file and add wins to a certain line in there, but you would see all that in the thread that deals with that.

---

### Post by Frihet on 2006-10-04
> **sefs said:**
> Another tip is with firestart (if this is the firewall gui you use) Dont set the policy in the allow service part...you'll still get problems....I find that you may have to set it in allow host section (i.e the first window) of the policy screen.

I am in the allow service part. Can you tell me how to format the rule for the allow host window.

Thank you!!

---

### Post by Frihet on 2006-10-04
> **sefs said:**
> Yes you have to set it in your /etc/samba/smb.conf file.

Its somewhere near the top usually its MSHOME by default in samba I think, but can be changed to whatever you like by editing the smb.conf file.

NB: You'll probably need to install winbind on the ubuntu machine so that windows machines on the network can access the ubuntu machine via its friendly netbios name and vice versa.  If you do a quick search of the forum you will find a thread on setting up winbind.  You'll have to edit a line in the /etc/nsswitch.conf file and add wins to a certain line in there, but you would see all that in the thread that deals with that.

Ok. I changed the smb.conf file and that got rid of the error messages. We are getting close! :-)

I'll do the winbind thing tomorrow, and I'll create a little howto for the next time (assuming it all works).

Mange takk!!

---

### Post by sefs on 2006-10-04
left Click once in the allow host area.  Then right click in this same area.  From pop up menu click on add rule.  in the box for ip addresses type your network which would be something like...

192.168.0.0/24  OR ALTERNATIVELY 192.168.0.0/255.255.255.0

> **Frihet said:**
> I am in the allow service part. Can you tell me how to format the rule for the allow host window.

Thank you!!

---

### Post by Frihet on 2006-10-05
I have installed the samba server on my laptop. I ran through Stormbinger's howto. As a result, I can see the server's share from my Windows machines - if I use the ip address in the url. That's no good; I can't ask the wife to go looking for ip addresses to find a baby picture. I cannot see the samba server from my Linux machines, and my Linux machines still cannot see Windows or NSLU2 shared resources.

I think I'm back to why I went to Mandriva 2006 last year. After weeks of frustration, I could simply not get Breezy to access shared LAN resources, and it looks like Dapper is just the same. I downloaded Edgy today. Same result.

I'll keep at it for a day or two, but it looks gloomy.

---

### Post by Frihet on 2006-10-05
I just found this:

  [http://ubuntuforums.org/archive/index.php/t-88206.html](http://ubuntuforums.org/archive/index.php/t-88206.html)

There I find:

  All you have to do is:

  edit /etc/nsswitch.conf

  change the line that says

  hosts: files dns

  to this:

  hosts: files dns wins

That's fine, except I have no /etc/nsswitch.conf file.

I'm sure this is simple, but I guess I am too.

---

### Post by sefs on 2006-10-06
nsswitch.conf appears only after installing winbind.  winbind allows all the machines to see and reference each other by their netbios names instead of IP address.  and as for the line you have to change it would be best to put the "wins" infront of the "dns"

so you have 

hosts:  files wins dns

That said though I find that samba in xubuntu works perfectly but in ubuntu it works when it wants too which is less often than not. 

By perfectly i mean that natilus in xubuntu is as stable and fast in show machines coming and going as windows network neighbourhood.  On ubuntu it happes at the toss of a coin for me.  very dicey.

---

### Post by Frihet on 2006-10-09
This is an update. I'll keep the thread alive to maintain a record.

I've determined that the SAMBA share I created on my SAMBA local server as part of this de-bugging exercise only works with KDE.

I have found other Debian discussions that indicate SMB does not work with Nautilus. NO use beating a dead horse, so I've set my default session to KDE. At least I have a reliable working share that's accessible by the Windows client. 

I still cannot see the Windows shares or the NSLU2 file servers. The Konqueror error message is: Timeout on server <name>. The server name referenced by the error message is not a server, but is a Windows workgroup name.

I'll keep at it for a while.

---

