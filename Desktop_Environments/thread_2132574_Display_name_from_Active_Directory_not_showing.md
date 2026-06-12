---
title: "Display name from Active Directory not showing"
date: 2013-04-05
forum: Desktop Environments
---

### Post by notJaxilian on 2013-04-05
Hi all,
I hope someone can help me with this issue I have.
I recently managed to get a Ubuntu 12.04 computer to login good against our AD using Winbind and Samba. I even got the uid to match our AD so everything good that far, but suddenly the display name disappeared (it was only there for short moment). It is no longer showing when I click the small user account icon in top right corner. The name doesn't want to show either when I try to unlock the computer and only the username is showing then.

see pic
[ATTACH=CONFIG]240972[/ATTACH]

Any know what file I need to fix?

Thanks

/J

---

### Post by luvshines on 2013-04-07
What is the output for following```
id

testparm -s

```

---

### Post by notJaxilian on 2013-04-07
id shows just all groups my users is member of with all correct id numbers next to them.

testparm -s shows (obscured real domain info):

   ```
~$ testparm -s 

 Load smb config files from /etc/samba/smb.conf 
 rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
 Processing section "[printers]" 
 Processing section "[print$]" 
 Loaded services file OK. 
 'winbind separator = +' might cause problems with group membership. 
 Server role: ROLE_DOMAIN_MEMBER 
 [global] 
 	workgroup = DOM 
 	realm = DOM.MM.SE 
 	server string = %h server (Samba, Ubuntu) 
 	security = ADS 
 	map to guest = Bad User 
 	obey pam restrictions = Yes 
 	pam password change = Yes 
 	passwd program = /usr/bin/passwd %u 
 	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
 	unix password sync = Yes 
 	ntlm auth = No 
 	syslog = 0 
 	log file = /var/log/samba/log.%m 
 	max log size = 1000 
 	local master = No 
 	dns proxy = No 
 	usershare allow guests = Yes 
 	panic action = /usr/share/samba/panic-action %d 
 	template shell = /bin/bash 
 	winbind separator = + 
 	winbind use default domain = Yes 
 	winbind refresh tickets = Yes 
 	winbind offline logon = Yes 
 	idmap config DOM : base_rid = 0 
 	idmap config DOM : range = 10000-49999 
 	idmap config DOM : backend = rid 
 	idmap config * : range = 10000-49999 
 	idmap config * : backend = tdb 
  
 [printers] 
 	comment = All Printers 
 	path = /var/spool/samba 
 	create mask = 0700 
 	printable = Yes 
 	print ok = Yes 
 	browseable = No 
  
 [print$] 
 	comment = Printer Drivers 
 	path = /var/lib/samba/printers 


```

---

### Post by luvshines on 2013-04-08
> **Jaxilian said:**
> id shows just all groups my users is member of with all correct id numbers next to them.
I meant, does 'id' command shows names ? or just the IDs

---

### Post by notJaxilian on 2013-04-08
Sorry "id" shows both names and IDs.

---

### Post by luvshines on 2013-04-08
I am not sure if this will help, I haven't tried this.
Maybe you can try increasing winbind log level ```
sudo smbcontrol winbindd debug 10
```
Clean the winbind log file[might be in /var/log/samba].
Then pull down that menu from panel and check if winbind log files show any activity/errors.

PS:
- Do you need winbind separator '+' ? Might delete this if not required
- Your both the backends have same ID ranges. Are you sure you are getting a proper ID ?

---

### Post by notJaxilian on 2013-04-09
Regarding the winbind separator '+', I took that setting when I looked at smb.conf on one of our Redhat servers.  I can try without it.
Same goes for the ID ranges. I looked at on our Redhat server on how they were configured and copied it. That made it work. I have been sitting for a week or so until I got it working by copying those settings.
I get the proper IDs, but it is only display name of the logged in user I cannot get working.

about the log file, I am not sure what you want me to do there.  Can you explain a bit more?

---

### Post by notJaxilian on 2013-04-09
I tried to remove the users that had logged in, but I got this error [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/988072](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/988072)
I managed to workaround it with temporarily remove winbind from /etc/nsswitch.conf and restart computer.

After I re-enabled it, it is still the same with my domain loginbs. No display names

---

### Post by notJaxilian on 2013-04-10
I managed to find out some I think

If I run this command:

```
~$ wbinfo -i username
```

I get this on the computer that doesn't work

```
username:*:26029:10513::/home/DOM/username:/bin/bash
```

but if I run it on the computer that works with the display name (yes I managed to get one to work but it's not consistant), the output is this

```
username:*:26029:10513:Display Name from AD:/home/DOM/username:/bin/bash
```

However I try wbinfo on the same domain username and I get different results on each of the two computers.

Anyone know why?

---

### Post by notJaxilian on 2013-04-10
I found this on RedHat which is exactly same issue I have

[https://bugzilla.redhat.com/show_bug.cgi?id=631617](https://bugzilla.redhat.com/show_bug.cgi?id=631617)

---

### Post by notJaxilian on 2013-04-10
I think I managed to solve it myself

I logged in as local admin and did:

```
[FONT=Courier New]sudo service smbd stop
[FONT=Courier New]sudo service w[/FONT]inbind stop
sudo rm -f /var/cache/samba/*.tdb
sudo rm -f /var/lib/samba/winbindd_idmap.tdb
[FONT=Courier New]sudo service smbd[/FONT] start
[FONT=Courier New]sudo service[/FONT] winbind start[/FONT]
```

and then

```
sudo net ads join -U username
```

after doin a

```
sudo net ads info
```

I saw domain info and the

```
wbinfo -i username
```

displayed full name like it supposed to be
and then logging in with that user it now showed first+lastname in top right corner

---

### Post by luvshines on 2013-04-12
Hi

Sorry, I was away so couldn't respond.
Anyways, it's good to know that you have resolved it.

On my testmachine, I can reproduce this.
See this```

# This displays the name
wbinfo -i sirius\\siriususer2
SIRIUS\siriususer2:*:13001102:13000513:siriususer2:/home/siriususer2:/bin/bash

# I try a CIFS access with this user
smbclient -L localhost -Usirius\\siriususer2%testpassword
Domain=[SIRIUS] OS=[Unix] Server=[Samba 3.6]


    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC        
    sharing         Disk      
Domain=[SIRIUS] OS=[Unix] Server=[Samba 3.6]


    Server               Comment
    ---------            -------


    Workgroup            Master
    ---------            -------


# Now again try wbinfo, it's gone
 wbinfo -i sirius\\siriususer2
SIRIUS\siriususer2:*:13001102:13000513::/home/siriususer2:/bin/bash

# Clean samba, netsamlogon_cache, and it is resumed
tdbtool /var/lib/samba/netsamlogon_cache.tdb erase
```

The samba netsamlogon cache seems to be affecting that. I will try to figure out the reason

---

### Post by notJaxilian on 2013-05-02
I appreciate all help on this. It's not to smooth to do my solution every time it happens. I found out that I can skip the domain join step, but still annoying

---

### Post by notJaxilian on 2013-05-02
I found out that it looses the display name if I do the following:
1. unplug Laptop from network
2. close lid so it goes down in sleep mode
3. open lid so it comes back (then I see that only username shows in unlock screen)

---

