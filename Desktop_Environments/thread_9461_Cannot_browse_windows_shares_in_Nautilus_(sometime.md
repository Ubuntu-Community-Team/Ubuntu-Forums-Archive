---
title: "Cannot browse windows shares in Nautilus (sometimes)"
date: 2004-12-29
forum: Desktop Environments
---

### Post by offby1 on 2004-12-29
Nautilus (in warty) will not allow me to view my windows shares, not even close.

I am unable to browse to them (by going from network:/// to smb:/// to... well, that's where it stops) and if I enter a valid location manually (smb://hostname/sharename, or even smb://hostname/C$ or smb://192.168.1.75/C$) I get an authentication dialog that asks me for my username, which I provide, a Domain, which I have tried A) leaving blank, B) filling in with WORKGROUP (which is the workgroup name for the windows machine) and C)... well, really, that's about all.

It also asks for a password, which I supply -- I supply the password for my username on the windows box, to no avail.  This dialog will either pop up once, or sometimes twice in quick succession, only to dump me unceremoneously with an error dialog that tells me that I cannot access the share.

Just for the record, it DOES work with command line smbclient as:
```
 smbclient //hostname/sharename 
```

which asks me for the password (the user name is the same on the laptop as it is on the other ubuntu system, and both of those are the same as the username on the windows XP machine)

More interestingly, and I am seeing this right now as I type this, from the moment I successfully connected with smbclient on the command line, I have been able to connect with Nautilus.  However, I still cannot browse to smb://hostname/ to see a list of shares, but it's a step at any rate.

So, I guess I have a workaround for this, but I'd like to know what the heck was going on at the start of my odyssey.  Has anyone got any ideas?

---

### Post by offby1 on 2004-12-29
[QUOTE=offby1]Nautilus (in warty) will not allow me to view my windows shares, not even close.

I am unable to browse to them (by going from network:/// to smb:/// to... well, that's where it stops) and if I enter a valid location manually (smb://hostname/sharename, or even smb://hostname/C$ or smb://192.168.1.75/C$) I get an authentication dialog that asks me for my username, which I provide, a Domain, which I have tried A) leaving blank, B) filling in with WORKGROUP (which is the workgroup name for the windows machine) and C)... well, really, that's about all.

It also asks for a password, which I supply -- I supply the password for my username on the windows box, to no avail.  This dialog will either pop up once, or sometimes twice in quick succession, only to dump me unceremoneously with an error dialog that tells me that I cannot access the share.

Just for the record, it DOES work with command line smbclient as:
```
 smbclient //hostname/sharename 
```

which asks me for the password (the user name is the same on the laptop as it is on the other ubuntu system, and both of those are the same as the username on the windows XP machine)

More interestingly, and I am seeing this right now as I type this, from the moment I successfully connected with smbclient on the command line, I have been able to connect with Nautilus.  However, I still cannot browse to smb://hostname/ to see a list of shares, but it's a step at any rate.

So, I guess I have a workaround for this, but I'd like to know what the heck was going on at the start of my odyssey.  Has anyone got any ideas?[/QUOTE]
 On reboot and re-test:

Yep, it's working now, don't know why, don't care -- as long as it continues.

However, I still cannot get smb://hostname/ to show me a list of shares -- I'm guessing that it should be, and smbclient -L hostname does, but...

Also of note -- in order to get this working at all with hostnames, I Was forced to add hostname to my /etc/hosts -- is this normal?  From what I recall, Windows sees these things in the local subnet (and my subnet mask is appropriate for it here) and thus doesn't require this.  However, unless I Wanted to be doing smb mounts by IP Address, I was stuck doing it this way.  Any input on this, too?

---

### Post by twisted_steel on 2005-01-03
I believe that Linux needs to have Samba running in order to lookup Windows computers by their hostname. For example, if you had a Windows computer running a web server, the way to access [http://computername]("http://computername") is either by running Samba on your own machine or by adding the name and the IP address to /etc/hosts. It is normal for you to have to add your hostname to /etc/hosts because otherwise the computer doesn't know which physical address to look up.

---

