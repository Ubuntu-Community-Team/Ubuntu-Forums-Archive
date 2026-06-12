---
title: "no login after changing username on encrypted home folder"
date: 2020-02-05
forum: Desktop Environments
---

### Post by Gingalone on 2020-02-05
I got a laptop with Ubuntu 16.04 with encrypted home, for sake of easiness of file exchange with another pc, I changed the username (the sudo one) following the intructions I found here: [https://askubuntu.com/questions/228696/how-to-change-administrator-username]("https://askubuntu.com/questions/228696/how-to-change-administrator-username")
All looked OK, but now I get into a login loop (continuous return to login screen).
Any idea?

---

### Post by TheFu on 2020-02-05
Change it back?  HOME directory encryption was deprecated for a number of reasons. You've found 1. There are others. To change it back, probably need to boot off a "Try Ubuntu" disc or flash drive, then manually edit the passwd, shadow, group, and gshadow files.  If you aren't 100% certain, make backups of those files before.  They are trivial 'field-based' text databases.  Each has a manpage explaining the file contents by field.

If you want to exchange files with other computers, setup ssh-keys between them and setup your ~/.ssh/config file so you never need know the userid between them.  If you use NFS, just the uid/gid need to match, not the usernames.

On any Unix machine, there are just 2 commands to create and share ssh-keys:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
where "userid" and "remote" are the values for the other system.  

Doing this will make ssh, scp, sftp, rsync, sshfs, and another ssh-based connections use the ssh-keys automatically.

As for the config file:
```
host n800-local
  hostname n800
  user thefu874
  port 22
```
This file means I use **ssh n800** which will use a command like **ssh -p 22 thefu874@n800-local** automatically.  I never need to know that username or port again.  Have different userids to the same host?  Just add another stanza with a different "host" alias.
```
host **n800-internet**
  hostname 170.xx.tt.123
  user thefu874
  port 60001
```
**ssh n800-internet** will use the other IP, other port, and username specified.  

Linux file managers wth a sftp:// URI will use these keys and settings too.
**sftp://n800-internet/**  simple.

---

### Post by Gingalone on 2020-02-05
Thank you TheFu for the wise advice and relative instructions.
Do you think I have no way to get back my data on the old laptop?
That would be really sad!

---

### Post by TheFu on 2020-02-05
What old laptop?

If you change the username back and have the same password, then I expect it will all be there.

I haven't used HOME directory encryption in a long time and only used it long enough to find problems that made it completely unusable to me, but .... I'd bet the combination of username and password are used to decrypt it.  Since changing the password should still allow access - companies still require users to change passwords every 60 days, I'd bet that changing the username broke it.

Whenever using any encryption, it is **critical to have excellent backups**. There are so many possible issues which can prevent access to that data.  I moved to whole install LUKS encryption immediately after determining that HOME directory encryption wouldn't fit here.  My layout:
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

But you have to make this choice.

---

### Post by Gingalone on 2020-02-05
The old laptop is the one with encrypted home (in the new one I have not encrypted the home directory!). I'll try to go back to the previous username.
With > Whenever using any encryption, it is critical to have excellent backups do you mean not encrypted backups?

---

### Post by TheFu on 2020-02-05
> **Gingalone said:**
>  
With  do you mean not encrypted backups?

Encrypted or not, backups that you can access are needed.  If the backup goes onto a USB disk, gets handed over to your lawyer for keeping  or is otherwise physically unavailable to attackers, I wouldn't worry too much about encryption.

But a case could be made for always using encrypted storage, since we might need to return a failed disk under warranty and might not be able to wipe it before mailing it off.  Backup disks fail too.  No way would I use HOME directory encryption on a backup disk. I would use LUKS.  

I struggle with whether backup storage encryption is worth the hassles or not.  All my backups are 100% automatic and the backup storage on the backup server isn't usually mounted, except during backup times.  That means it would either need to automatically decrypt the LUKS container without a human involved or someone would need to be available at 1am until 5am while the different backups run. And running weekly patches would likely require a reboot (perhaps every other week), 

Encryption of servers brings some challenges. Most definitely a trade off.
Encryption of a laptop is a no-brainer to me. It must be done, just like tablets and smartphones must be encrypted. All portable devices need to be encrypted, but that only really provides security when the systems are powered off completely. Hibernation and standby break the security of encryption.  Whenever my laptop moves locations in any vehicle, it is completely powered off. Period.  When I travel with it, I disable booting from the internal storage and require a flash drive for boot, which I keep with me to avoid the evil maid attack.

---

### Post by Gingalone on 2020-02-06
thank you TheFu, I see you are rather rigorous with backups (and their protection!).
Is it possible to encrypt (with Luks) the whole HD after Ubuntu has already been installed?

---

### Post by TheFu on 2020-02-06
> **Gingalone said:**
> thank you TheFu, I see you are rather rigorous with backups (and their protection!).
Is it possible to encrypt (with Luks) the whole HD after Ubuntu has already been installed?

no.  But good backups should be able to be restored into a fresh install that uses LUKS in about 30-45 min, including the time to do the fresh installation.

---

### Post by Gingalone on 2020-02-07
Last question TheFu: a place where to find a comprehensive step-by-step guide to encryption of a whole HD?

---

### Post by TheFu on 2020-02-07
> **Gingalone said:**
> Last question TheFu: a place where to find a comprehensive step-by-step guide to encryption of a whole HD?

During the installation, select Encryption with LVM. Post install, use LVM to reduce the size of the root LV down to 25G, then create a /home LV whatever size you need, I'd check the swap LV size and make it 4.1G (that's the only size swap), be certain to leave 20% or more of the storage inside the VG unused.  The flexibility and power of LVM comes from adding storage when needed for 3 months at a time and NEVER, EVER, using all of it until there isn't any other choice.  LVM snapshots are part of an excellent backup strategy, but non-used VG storage is required so that a new snapshot can be created nightly, backed up, then removed.
I've already posted my encrypted, LVM, layout link.

When all the VG storage is allocated, it is time to use **pvmove** onto a new, larger, disk.

With LVM, adding more storage to an LV is seconds, trivial.  Reducing storage is a pain and risky, especially when the LV is nearly full.

If you want to manually setup encryption, Paddy has a long thread in the Security subforum. It is so very complex I've never tried it. It is so easy for me to start over when I switch computers and only takes about 30 minutes to move over with all my files, settings and programs.

---

### Post by Gingalone on 2020-02-11
OK; thank you TheFu, Ubuntu 20.04 LTS is close, a good chance for a clean install on encrypted HD!

---

