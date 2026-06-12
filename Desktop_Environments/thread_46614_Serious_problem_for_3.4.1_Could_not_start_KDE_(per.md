---
title: "Serious problem for 3.4.1: Could not start KDE (permissions for ~/.ICEAuthority file)"
date: 2005-07-05
forum: Desktop Environments
---

### Post by sinbad782 on 2005-07-05
I had a problem starting up KDE after upgrading to the latest 3.4.1 release using the Kubuntu.org repositories. The issue came when I restarted the machine and then tried logging back into a KDE session. 

The machine seemed to get stuck at the 'Setting up interprocess communication' phase and I then got an error saying something along the lines of 'cannot read .ICEAuthority file' or 'wrong permissions on .ICEAuthority file'. This also stopped me from logging into GNOME too. 

I remedied this by logging into a failsafe terminal session and changing the permissions on this file by issuing a

sudo chmod 777 .ICEAuthority

It was then possible to log back into KDE as normal. Not sure if this is the best place to report this, but I'd be interested if anyone else has had a similar experience?

Also, can anyone tell me the regular permission that should be set on this file?

---

### Post by Xian on 2005-07-05
[QUOTE=sinbad782]t was then possible to log back into KDE as normal. Not sure if this is the best place to report this, but I'd be interested if anyone else has had a similar experience?

Also, can anyone tell me the regular permission that should be set on this file?[/QUOTE]
This is unfortunately not an unusual occurance. Generally, the actual permissions are correct on that file, but it is the ownership that is the problem. If you get that again just issue the command below and it should correct what took place and get you back to your desktop. Most people will tell you that a 755 or 751 permission is the proper config. You should go ahead and change that when possible.
```
$ sudo chown username:username ~/path/to/.ICEAuthority
```

---

### Post by sinbad782 on 2005-07-10
Thanks for the tip - I've done that and it's working fine.

---

### Post by arjay1 on 2005-07-14
PMFBI - this is EXACTLY the same problem that I have had - with nothing on my side to create it.  It happened after a straightforward reboot.

The only problem is that I have tried your suggestion (sudu chown etc) but it has made no difference at all.  I can log in through root to failsafe but not as the normal user.  Everything that I try to run says something on the lines of " var/tmp/kdecache (or k-socket blah blah) -rjoss (my user name) is uid 1000 instead of uid 0.

Anything else I could try?

TIA

EDIT: WHOOPS - MY APOLOGIES.  The proposed solution of chown of the .ICEautority worked fine - it was my fault - a small typo in the CLI command.

However, the fact remains that several people have had this unforced error - is it a bug or what?

---

### Post by chaumurky on 2005-07-15
I once SSH'ed into my machine as a normal user then started a vncserver with sudo.  [-X  various files are then overwritten in the normal user's directory as root. I learnt a lot that day  ;-)

---

