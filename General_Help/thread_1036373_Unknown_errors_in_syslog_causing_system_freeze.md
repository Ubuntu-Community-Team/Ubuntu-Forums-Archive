---
title: "Unknown errors in syslog causing system freeze?"
date: 2009-01-10
forum: General Help
---

### Post by Doc Hoss on 2009-01-10
I just had a system lockup after a little bit of weirdness the past couple of days (changing users and it locking up with only a line in the upper left saying "Starting ntp daemon..."), and I looked at the syslog and saw a bunch of lines saying this...

```

Jan 10 17:42:05 clydus nmbd[31938]: [2009/01/10 17:42:05, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:42:05 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 
Jan 10 17:57:13 clydus nmbd[31938]: [2009/01/10 17:57:13, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:57:13 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 

```

Also in the daemon.log, I see a ton of this...

```

Jan 10 17:42:05 clydus nmbd[31938]: [2009/01/10 17:42:05, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:42:05 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 
Jan 10 17:57:13 clydus nmbd[31938]: [2009/01/10 17:57:13, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:57:13 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 

```

Any ideas what's causing these errors?  They might be the cause of some of my system instability.

Thanks in advance!

---

### Post by albinootje on 2009-01-10
> **Doc Hoss said:**
> 
```

Jan 10 17:42:05 clydus nmbd[31938]: [2009/01/10 17:42:05, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:42:05 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:42:05 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 
Jan 10 17:57:13 clydus nmbd[31938]: [2009/01/10 17:57:13, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Jan 10 17:57:13 clydus nmbd[31938]:   find_domain_master_name_query_fail: 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to find the Domain Master Browser name HOSSHAUS<1b> for the workgroup HOSSHAUS. 
Jan 10 17:57:13 clydus nmbd[31938]:   Unable to sync browse lists in this workgroup. 

```

Any ideas what's causing these errors?  They might be the cause of some of my system instability. 

Those are errors from Samba.
Did you configure /etc/samba/smb.conf yourself, or did you use "Share Options" with Nautilus filemanager on folders ?
Do you have a LAN with other computers or not ?

You problem description is a little bit sparse imho, but it sounds like Samba has nothing to do with it. 
I would think about a problem related to X.

Which Ubuntu release are you using ? Please post the output of this :
```

lsb_release -a
uname -a

```
And please redo the same thing, which gave problems, again, and then post the output of this :
```

tail -f -n30 ~/.xsession-errors

```

---

### Post by Doc Hoss on 2009-01-11
I can't seem to duplicate the freeze...in general, I'm wanting to keep making Ubuntu more and more stable, so I'm posting about every little tiny thing so I can get rid of all the problems.

Edit:  Forgot to answer all your questions...I configured smb.conf according to another guide I found [here]("http://ubuntuforums.org/showthread.php?t=202605") on the forums.  I've tried just using the "Share Options" from within Nautilus, but to no avail.  

I do have a LAN with other computers, but I haven't been trying to talk to any except my local vmware machine.

The output of lsb_release -a is below:

```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

```

And uname -a:

```

Linux clydus 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

It says I'm using 8.04, but 8.10 doesn't show up in my update manager.  I know OS upgrades used to show there...what gives with that?

---

### Post by albinootje on 2009-01-11
> **Doc Hoss said:**
>  Edit:  Forgot to answer all your questions...I configured smb.conf according to another guide I found [here]("http://ubuntuforums.org/showthread.php?t=202605") on the forums.  I've tried just using the "Share Options" from within Nautilus, but to no avail.  

I do have a LAN with other computers, but I haven't been trying to talk to any except my local vmware machine.

Can you post the output of the following on your Ubuntu machine :
```

testparm

```
And please test the "Sharing Options" with smbclient.
See here :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
-> Samba Client Manual Configuration
For example :
```

smbclient //localhost/your_share_name -U your_samba_username

```

> 
It says I'm using 8.04, but 8.10 doesn't show up in my update manager.  I know OS upgrades used to show there...what gives with that?

Don't know, I'm on 8.10 at the moment, can't check right now.

---

### Post by Doc Hoss on 2009-01-14
Output from "testparm" is here:

```

Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[ClydusMusic]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = HOSSHAUS
        server string =
        interfaces = lo, eth0
        bind interfaces only = Yes
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No

[ClydusMusic]
        path = /media/Minimus/Music/
        force user = XXX
        force group = XXX
        read only = No
        create mask = 0644

```

And here's what happens with the smbclient...

```

smbclient //localhost/media/Minimus/Music -U XXX
Password:
Domain=[CLYDUS] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

The OS upgrade is no big deal, I was just curious why it doesn't show up.  If anyone else has an idea about that, I'd be happy to listen.....err, read.

---

### Post by albinootje on 2009-01-14
> **Doc Hoss said:**
> 
```

smbclient //localhost/media/Minimus/Music -U XXX
Password:
Domain=[CLYDUS] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```


Thanks. Please try with this instead :
```

smbclient //localhost/ClydusMusic -U your_samba_username

```

---

### Post by plucky on 2009-01-14
> The OS upgrade is no big deal, I was just curious why it doesn't show up. If anyone else has an idea about that, I'd be happy to listen.....err, read.

That is because it is an LTS=Long Term Support release and the update system will only ask you to update to another LTS release.

If you want to change that **System > Administration > Software Sources > Updates** and select **Normal Releases** in the "Release Upgrade" window.

Good Luck

---

### Post by Doc Hoss on 2009-01-15
Here's that output, albinootje.

```

XXX@clydus:~$ smbclient //localhost/ClydusMusic -U XXX
Password:
Domain=[CLYDUS] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_NO_SUCH_GROUP

```

And for the record I have added the samba user XXX (name protected to protect the innocent...) and set the password appropriately per the guide that I referenced earlier.  Thanks for the continued help, albinootje!

And thank you for the info on the upgrade, plucky.  I wasn't aware of that...another day, another thing learned about Linux!

---

### Post by albinootje on 2009-01-15
> **Doc Hoss said:**
> 
```

XXX@clydus:~$ smbclient //localhost/ClydusMusic -U XXX
Password:
Domain=[CLYDUS] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_NO_SUCH_GROUP

```

Interesting, I've never seen this error before.
A quick search for that error doesn't show much pointers yet, this could be useful though :
[http://www.unixresources.net/linux/lf/56/archive/00/00/11/15/111598.html](http://www.unixresources.net/linux/lf/56/archive/00/00/11/15/111598.html)

Hopefully other people can help you a bit further.

---

