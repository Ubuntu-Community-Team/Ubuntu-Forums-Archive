---
title: "The entered password is invalid..."
date: 2005-12-27
forum: Desktop Environments
---

### Post by Xitron on 2005-12-27
I'm attempting to access Network Settings from the menu system, but when I click on it, I get the following error...

Error
The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key.
Close

The trouble is, it hasn't asked for a password.  It's as though it has stored a password somewhere and I don't know where it's stored so I can't clear it.

I've used this successfully in the past, and it only changed after upgrading to Breezy.

Thanks,

Unca Xitron

---

### Post by dcstar on 2005-12-27
[QUOTE=Xitron]I'm attempting to access Network Settings from the menu system, but when I click on it, I get the following error...

Error
The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key.
Close

The trouble is, it hasn't asked for a password.  It's as though it has stored a password somewhere and I don't know where it's stored so I can't clear it.
.......[/QUOTE]
You may need to change/set your root password.

Open a user terminal, enter "su" and see if you can log in as the root user.

If you can, enter "passwd" to set a new root password.

---

### Post by Xitron on 2005-12-28
I ran `sudo passwd` and changed it.  No joy.  It's like it thinks it's asked me for a password, and is unsatisfied with the answer.  This is killing me since I can't easily change my network settings when I go home at night.

Unca Xitron

---

### Post by Xitron on 2005-12-29
Perhaps a different tack on this would work.  Can anyone tell me what actual command line app is being run which brings up the System-Administration-Networking app?  Perhaps if I run it from the command line, as root, it will clear up the problem.  If nothing else, at least it will show me some errors in the output.

---

### Post by arkroan on 2006-05-02
I have the same problem with many other application including Network Tools.

I have tried changing the password to both user and root but did not succeed..

I changed the password, logout, wait 5 minutes (because i read that it saves the password only for 5 minutes) , then log in , tried to open the Network Tools. It asked for the password, i gave it and then nothing happened. When i try for the second time i get the following message:" The entered password is invalid"


Any suggestions ??

---

### Post by gonzodoc1 on 2007-02-07
hi, i have the same problem with network and system-administration-disks.  i tried the things listed above, checked my sudoers file etc but no joy. no-one seems to know what this is.  

other management tools work - mostly they gnome-xxxxx tools whereas 'system-administration-disks' is a shortcut to gksu disks-admin and system-administration-networking points to gksu network-admin.

its all very disappointing. looks like it's back to M$ for me :(.
anyone got any ideas?  thanx
gonzodoc

---

### Post by sleeptonyc on 2007-02-08
same problem in my ubuntu 6.06....
the others admin tools work right, trouble only with network-admin tool!
maybe a bug?

---

