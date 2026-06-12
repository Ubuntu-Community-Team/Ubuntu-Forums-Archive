---
title: "Adding new user deleted root?"
date: 2009-06-05
forum: General Help
---

### Post by gekko16 on 2009-06-05
I tried to add a new user to my Ubuntu 8.04 system. The GUI seemed to hang on the attempt, but the dialog box eventually went away. Following that I've been experiencing many issues. GNOME doesn't automatically start, sudo no longer works, returning ```
sudo: no passwd entry for root!

``` and System>Administration>Login Window brings up the error message ```
User root does not exist.
``` So it seems like root has been deleted. How can I fix this?

---

### Post by pauna on 2009-06-05
> **gekko16 said:**
>  So it seems like root has been deleted. How can I fix this?

Verify this by looking at the contents of /etc/passwd, does root have an entry there? 

Can you get root privs from your own account? For example, can you successfully execute "sudo less /etc/shadow" in a terminal window? Does root have an entry there?

If you can't get any kind of root privs for any of your existing accounts, you probably need to boot into USB/DVD live environment, mount the / partition from the hard disk to the live system and fix the /etc/passwd using the live environment.

---

### Post by gekko16 on 2009-06-05
> **pauna said:**
> Verify this by looking at the contents of /etc/passwd, does root have an entry there? 
 
Can you get root privs from your own account? For example, can you successfully execute "sudo less /etc/shadow" in a terminal window? Does root have an entry there?
 
There is no entry for root in /etc/passwd. I cannot get root privileges on my own account. Trying to run that command results in the same error from my OP. 
 
> **pauna said:**
> If you can't get any kind of root privs for any of your existing accounts, you probably need to boot into USB/DVD live environment, mount the / partition from the hard disk to the live system and fix the /etc/passwd using the live environment.
 
How do I fix the /etc/passwd file? Do I need to replace it/add something to it?

---

### Post by Iowan on 2009-06-05
Check [here]("http://www.psychocats.net/ubuntu/fixsudo") for some useful information.  If **root** is missing, it may be more difficult. It may be possible to use a utility like [tomsrtbt]("http://www.toms.net/rb/") to edit the /etc/passwd and /etc/shadow to put **root** back.

---

### Post by fragos on 2009-06-05
The initial user can use sudo because it belongs to the admin group. There is no root password. Subsequent users must be added to the admin group to gain sudo access. There is also a sudoers file which may need to be changed and I believe there is a special editer for that purpose.

---

### Post by Xanthomryr on 2009-06-05
> **fragos said:**
> There is also a sudoers file which may need to be changed and I believe there is a special editer for that purpose.
The editor is visudo.
You could edit /etc/sudoers with any editor but visudo is safer because he locks the file, perform sanity checks and checks for parse errors.

---

### Post by gekko16 on 2009-06-05
> **Iowan said:**
> Check [here]("http://www.psychocats.net/ubuntu/fixsudo") for some useful information.  If **root** is missing, it may be more difficult. It may be possible to use a utility like [tomsrtbt]("http://www.toms.net/rb/") to edit the /etc/passwd and /etc/shadow to put **root** back.

Tried the first link you provided, didn't work -- selecting Drop to root shell prompt returns ```
sulogin: cannot open password database
```> **fragos said:**
> The initial user can use sudo because it belongs to the admin group. There is no root password. Subsequent users must be added to the admin group to gain sudo access. There is also a sudoers file which may need to be changed and I believe there is a special editer for that purpose.

> **Xanthomryr said:**
> The editor is visudo.
You could edit /etc/sudoers with any editor but visudo is safer because he locks the file, perform sanity checks and checks for parse errors.

tried this also, and it denied me permission. The user name is the only one I know of on the system, and I would imagine it's the initial user.

I have a LiveCD. How can I go about rebuilding the /etc/passwd and /etc/shadow files or whatever else I need to do to fix this?

---

### Post by pauna on 2009-06-06
> **gekko16 said:**
> 
I have a LiveCD. How can I go about rebuilding the /etc/passwd and /etc/shadow files or whatever else I need to do to fix this?

If everything else fails, something like this should work:

[LIST=1]
[*]Find out the root (i.e. /) partition device of your bonked system (/dev/sda1 for example), "df" command should show it.
[*]Boot to live CD environment.
[*]If not already mounted, mount the bonked root partition to your live system. If your root was the /dev/sda1, the command is "sudo mount -t ext3 /dev/sda1 /mnt/foo" where /mnt/foo is an empty directory you wish to use for the mount point. Assuming you're using the default ext3 file system.
[*]Add the root entry to the bonked password file. Note that the broken password file now exists in /mnt/foo/etc/passwd, not in /etc/passwd, which is the live system's passwd file. However, you can use the live system's passwd file as a reference point how the root entry should look like. Copying the entry from file to file should work ok, uid is 0 after all.
[*]Similarly add the root entry to the bonked shadow file (/mnt/foo/etc/shadow).
[*]Check that the root's home directory (by default /root) exists on the broken file system. If not, create.
[*]Give command "sync" so that changes will be written to disk (theoretically not necessary but gives me a warm fuzzy feeling)
[*]Unmount /dev/sda1 (or whatever).
[*]Remove your live disk and boot from hard disk.
[/LIST]

Please note that you can actually hose your system when mucking around with the configs like this. But at this point you can only win, right?

The good point here is that if something goes wrong, you can theoretically go back to booting from the live system and use the above procedure again to fix things.

And this procedure illustrates the fact why physical access equals pwning the box from the security point of view.

---

