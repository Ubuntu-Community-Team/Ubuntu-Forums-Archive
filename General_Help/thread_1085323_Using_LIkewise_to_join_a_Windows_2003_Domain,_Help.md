---
title: "Using LIkewise to join a Windows 2003 Domain, Help!"
date: 2009-03-02
forum: General Help
---

### Post by cinmachina on 2009-03-02
Hi all!

I'm trying to get an Ubuntu to authenticate properly and prompt for credentials in a Windows Server 2003 Domain environment.

So far I've installed a program called 'likewise' by following the instructions found on this website:

[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

Following these instructions DID let me join the computer to the domain. It shows up in AD correctly, which makes me really happy!

HOWEVER!

I cannot get it to prompt me for username//password when I restart the computer. I've followed all of the instructions and I can't really understand what I'm doing wrong.

Anyone had any experience with this?

Thanks,


Cinmachina

---

### Post by HermanAB on 2009-03-02
I have not used Likewise, but you can have a look here, because there are a number of tricks to it:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

### Post by cinmachina on 2009-03-02
No easier solution eh? That seems like a pretty insane work around :-/

---

### Post by rbscholtus on 2009-03-03
Maybe you are using Automatic logon so you never get the chance?

Go to System > Administration > Login Window
Go to the Security tab.
Uncheck Enable Automatic Login

Good luck, I hope it works. If it doesn't, don't blame me, I started using Ubuntu 2 hours ago. Tomorrow I will try exactly the same thing at work.

---

### Post by cinmachina on 2009-03-03
It wasn't checked -- surely there is a way to get this going.

Can you let me know if it worked for you when you try it?

Thanks,

Cinmachina

---

### Post by awreneau on 2009-03-03
Couple things

Are you using trying to login with domain\userid?
Does /var/log/auth.log have any entries that might give you a hint?

Try this
[I]When joining an Ubuntu Desktop workstation to a domain, you may need to edit /etc/nsswitch.conf if your AD domain uses the .local syntax. In order to join the domain the "mdns4" entry from the hosts option. For example:

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

Change the above to:

hosts: files dns [NOTFOUND=return] [/I]

Then this

[I]sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf (move thru the list until you come upon likewise-$ move to the colums 2, 3, 4 and 5 and press the spacebar in each column to turn on the service for each run level.
sudo reboot

The service isnt running in order to authenticate you to the AD domain. Notes for this bug can be located [here]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/205111").

The full Ubuntu 8.04 notes are located [here]("https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html") [/I]

I think the 2nd one is really the trick to it but I read several instances where the nsswitch.conf file was also a key factor.

Hope that helps

---

### Post by cinmachina on 2009-03-04
Thanks! I will try this and let you know if it works when I get home.

---

### Post by cinmachina on 2009-03-04
Still didn't work. I'm beginning to think there is no solution and am ready to give up.

It's a shame, I really wanted this to work.

---

### Post by HermanAB on 2009-03-04
AD is insanely compplicated.  You need to have some inkling of how it works in order to debug a connection problem.  The most important thing is to keep a close watch on all error messages.  So investigate /var/log and look for the log files used by Likewise, then analyze them.

The problem may be as simple as a time discrepancy.

Cheers,

Herman

---

