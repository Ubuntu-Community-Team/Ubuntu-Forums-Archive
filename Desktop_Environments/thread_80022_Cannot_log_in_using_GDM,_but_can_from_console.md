---
title: "Cannot log in using GDM, but can from console"
date: 2005-10-21
forum: Desktop Environments
---

### Post by stevea1210 on 2005-10-21
I have a strange issue with GDM right now.  I joined an ubuntu box to my win 2k3 domain.  The process was successful.  wbinfo –u or –g works.  getent works.  I can get a Kerberos ticket fine.  However only local accounts can logon via gdm.  All network accounts get an authentication failure.  Local account can log in fine from GDM.

I dropped to a console, and tried to logon.  All of the domain accounts can logon fine from a console.  I get the message that it created the home folder.  I can even startx after the console logon, and get a successful gnome session.  After successfully authenticating at a console, starting x, and making sure the account worked properly, I logged off.  When I go to GDM, those accounts still fail to authenticate.  I tried this with 5 different network accounts, with the same result.

I added the pc’s to the domain following this from the wiki [https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29) .  I had followed that exact same procedure on two other ubuntu pc’s in my domain, and didn’t have this issue.  Just for the heck of it, I added those users to the security group “gdm”.  That didn’t fix the issue either.

Does anybody have any ideas?

---

### Post by stevea1210 on 2005-10-25
Does anyone have any ideas?  One more piece of info I figured out was that even if I put the wrong password in during console login, it lets me logon with the domain accounts.  Anyone? ](*,)

---

### Post by stevea1210 on 2005-11-02
It appears this issue has to do with how the password is being passed from the workstation to the domain controller.  I know this because I have actually locked out several accounts while trying to get logged on.  That tells me it is recognizing the user, but the passwor disn't being recognized.  I can say with 100% certainty this isn't me mistyping the passwords.  I have been able to replicate this with several accounts.  

Does anyone know what I could check that would affect the transmission of the passwords to the DC?

---

### Post by stevea1210 on 2006-01-11
I revisited this issue and finally figured it out.  It had nothing to do with the passwords.  Turns out that I wasn't properly joined to the domain. 
```
wbinfo -t 
```was giving me 
```
 checking the trust secret via RPC calls failed
error code was STATUS_BUFFER_OVERFLOW (0x80000005)
Could not check secret
```

and ```
smbclient -L big-daddy-ubuntu  -U *username*
```would return
```
session setup failed: STATUS_BUFFER_OVERFLOW

```

winbind -u and -g worked.  getent, kinit, they all worked.  I thought I was properly joined to the domain.

I had gone over it a million times.  I ran trough the process dozens of time.  I spent hours on google.  I swore up and down everything was set up correct.  After all I had 4 other machines with the EXACT same configs.  The rest had full domain logins.  

I reached the point of giving up, and thought, what would cause a buffer overflow, probably too much data.  Where was there a possibility of too much data when all of the pc's were configured identically. 

Then it dawned on me.  The hostname of this pc was much longer than the others.  It was big-daddy-ubuntu (don't ask).  That's 16 letters  long.  Turns out there is a maximum length of 15 characters for the hostname.  After changing the name of the pc, and running through the process once more....... SUCCESS!!

Sometimes it is the simplest things.  I just couldn't see the forest for the hostname.  Hopefully this helps someone at some point.

---

