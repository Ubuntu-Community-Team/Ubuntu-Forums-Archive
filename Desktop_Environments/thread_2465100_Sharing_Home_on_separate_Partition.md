---
title: "Sharing Home on separate Partition"
date: 2021-07-22
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-07-22
I know some users have their /home directory on a separate partition and understand the mounting requirements in fstab

Just wondering, could the /home partition be used with different Linux distros?  I am thinking similar to Ubuntu like Mint or Debian.  Also appreciate the /home directory stores some application settings which may differ but curious if this is an easy option or problematic.

Ubuntu is and has been my main system for around 10 years, I experiment with other Linux distros on external drive but am currently using 18:04LTS - not sure about upgrading to 20:04 or wait untill 22:04 but am wondering about the /home partition option.

Geoff

---

### Post by vanadium on 2021-07-22
This would not be a problem if it were only for your user data (i.e., your personal files in Documents, Pictures, etc.) However, also configuration data is stored there. 1) That configuration may depend on  the particular setup of the system in which it was created 2) The format of that configuration data may have changed between the version that has written it, and the version of another linux distro that accesses it later. So expect problems if you attempt that.

Instead, have each distro keep its own home directory, and replace the folders to your personal data by symbolic links pointing to the data stored elsewhere. That way, the distro's will not interfere with each others settings, whereas you will be able to transparently access your data from anywhere.

---

### Post by yancek on 2021-07-22
It would be problematic unless you were experienced at configuring your system.  Never done it myself but lots of Linux users do.  Depends on your wants and needs.  If you want to simply share data between your different system, creating a separate data partition would be the way to go.  Having different desktop environments on the various Linux installs would add to the complexity.

---

### Post by oldfred on 2021-07-22
More info and previous discussions of data partition(s). 

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by ActionParsnip on 2021-07-22
I suggest a small partition for /home (say 20Gb) then a large Ext4 partition where all casual data is stored. This can be accessed by many distributions on the same system and reduce issues. It also makes backups easier

---

### Post by ajgreeny on 2021-07-22
In the days when I had a triple booting system I kept one separate partition for data only and left the home (folder, not partition) for each distro in the root partition as is default for Ubuntu.

I then simply created symbolic links (soft links) to all the data folders in the data partition in the home folder of the root partition of each distro.
In this way all the data, although it appears to be in each distro, is not duplicated at all and sits in that one place; it just appears in each distro's home as if it was sitting there.

Doing it this way is almost 100% failsafe, though very occasionally, (and I can't even remember what the data was or the application, as it was well over a decade ago,) I have had data files updated by a new version of an application and those updated files will not open in an earlier version of that application.

---

### Post by TheFu on 2021-07-22
In the 1990s, it was common for a single HOME to be mounted across multiple systems, concurrently, over NFS. Businesses still do this along with having LDAP maintained users and groups.  This is important to ensure the uid/gid numbers all match across systems, especially for human users.  The numbers are used on Unix file system to determine access and permissions, not the names.

This applies to dual-quad-and more booting with a shared HOME.

If different DEs are used, or even different DE versions, then incompatibilities are likely.  Historically, the way that was handled was by setting environment variables to point to different configs and programs based on the hostname of the system.  I have no idea how to do that with Gnome.  There are all the XDG* environment variables. The default location appears to be hard-coded based on $HOME which gets set by the login program and is inherited by all sub-shells. [https://wiki.gnome.org/Initiatives/GnomeGoals/XDGConfigFolders](https://wiki.gnome.org/Initiatives/GnomeGoals/XDGConfigFolders) has more about this. Look through the list of problem applications. 

> User data should go into $XDG_DATA_HOME (which default to .local/share), user preferences should go into $XDG_CONFIG_HOME (which default to .config) and cached data should go to $XDG_CACHE_HOME (which default to .cache).

So, just control those 3 variables based on the hostname?  That should mostly work, right?
I'd use ~/.config-${hostname}/   so the configs would be stored in separate top-level directories, for example. 

Be certain that all the Linux systems booted have different hostnames.

---

### Post by Geoff_Lane on 2021-07-22
> **vanadium said:**
> This would not be a problem if it were only for your user data (i.e., your personal files in Documents, Pictures, etc.) However, also configuration data is stored there. 1) That configuration may depend on  the particular setup of the system in which it was created 2) The format of that configuration data may have changed between the version that has written it, and the version of another linux distro that accesses it later. So expect problems if you attempt that.

Instead, have each distro keep its own home directory, and replace the folders to your personal data by symbolic links pointing to the data stored elsewhere. That way, the distro's will not interfere with each others settings, whereas you will be able to transparently access your data from anywhere.

Ah, that is an interesting option, thanks for suggestion.

Geoff

---

### Post by Geoff_Lane on 2021-07-22
> **ajgreeny said:**
> In the days when I had a triple booting system I kept one separate partition for data only and left the home (folder, not partition) for each distro in the root partition as is default for Ubuntu.

I then simply created symbolic links (soft links) to all the data folders in the data partition in the home folder of the root partition of each distro.
In this way all the data, although it appears to be in each distro, is not duplicated at all and sits in that one place; it just appears in each distro's home as if it was sitting there.

Doing it this way is almost 100% failsafe, though very occasionally, (and I can't even remember what the data was or the application, as it was well over a decade ago,) I have had data files updated by a new version of an application and those updated files will not open in an earlier version of that application.

That is an interesting way to do it.

Geoff

---

### Post by Geoff_Lane on 2021-07-22
> **vanadium said:**
> 

Instead, have each distro keep its own home directory, and replace the folders to your personal data by symbolic links pointing to the data stored elsewhere. That way, the distro's will not interfere with each others settings, whereas you will be able to transparently access your data from anywhere.

That is seeming like a good suggestion.

Thanks,

Geoff

---

### Post by garvinrick4 on 2021-08-05
When i used to run the sudo flavor along with the yum flavors 
would have trouble using Home partition with the yum flavors right out of box
using the Home partition with all logical partitions. Now with  GPT 
don't really know but i would imagine still trouble. I am going 
to install one and see be interesting for me.

---

### Post by Geoff_Lane on 2021-08-08
> **garvinrick4 said:**
> When i used to run the sudo flavor along with the su flavors 
would have trouble using Home partition with the su flavors right out of box
using the Home partition with all logical partitions. Now with  GPT 
don't really know but i would imagine still trouble. I am going 
to install one and see be interesting for me.

Be interested in outcome.

You mention sudo and su flavours?  I understand sudo just gives admin rights to same user (provided part of sudo group) whereas su switches user, usually to root so am guessing actually switching users throws up permission issues.

Geoff

---

### Post by garvinrick4 on 2021-08-08
I am sorry Geoff_Lane i meant yum's sharing same Home partition not su.

---

### Post by TheFu on 2021-08-08
> **garvinrick4 said:**
> I am sorry Geoff_Lane i meant yum's sharing same Home partition not su.

Sorry. I don't understand either statement.

Are you talking about package manager differences or whether root logins are enabled by default?  

I typically don't use root on any linux, preferring to setup sudoers and make the root password a random 100 characters that I don't record. 

Regardless, I disable all remote root logins, unless ssh-keys are used and that is only for backups from a designated backup server's IP.  I think backups need to be "pulled", never pushed, for protection against malware.

BTW, both su and sudo can be used to change to other userids, just as easily.  I use this all the time when updating php websites.
```
sudo -u www-data php updater/updater.phar
```

Though I also use **sudo -i** when setting up new systems for the first 15 minutes or so.

---

