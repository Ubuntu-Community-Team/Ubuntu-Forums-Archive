---
title: "Single Sign on"
date: 2008-08-03
forum: Desktop Environments
---

### Post by wamrobert on 2008-08-03
Single sign on.  I have experimented on 2 platforms.
a)  Using samba, winbind, kerberos . I am able to succesfully join the domain but the major issue here is the configuration involved for a successful roll out - 100 plus comps. This is simply not the way to go.

b) Likewise-open . I log on locally to the domain ok , set Samba to ignore the preceeding domain name ie DOMAIN\User and this works. On a system reboot domain logons is not working. I have to log in a local user and restart the likewise-open service. Then I am able via the shell to switch to a domain user home directory ( %D%U) else it does not recognise the user ID. Problem here seems to be likewise has to be restarted just before the user logs in. 
I have to changed the run level of likewise-open to S29  ie just before the gdm at S30 on rc3.d and rc5.d directories. I also restart the service on /etc/rc/local script. ntp sync is also running at /etc/networking/if-up/ntpdate with the domain controller as the ntp server and also forced a restart of ntpdate via rc.local.
I have also run updater-rc.d likewise-open defaults which created the start up links  S90 on the /etc/rcN.d/ directories/  that i changed to S29 level.

On a reboot I get a domain controller unreachable login in with cached credentials. for a user that has not logged in before this means that they cant log in. 
After restarting the likewise-open service I do am able as root on the command shell to 'su' any user on the AD ( not via the graphical logon) and surprisingly this user is logged in with cached credentials on the next reboot.

There was a bug reported about the likewise repository and someone suggested to use the one the developers site- which I have done but it still logs me on with the cached credentials after a reboot.

A user here said the likewise takes a few minutes to log on 

does someone here have a working likewise-open problem free.

I must mention that domain logons work OK at times and the only error messages I get are domain controller unreachable or time server differences( My domain controller was 5 min ahead  which I reset).

I will be posting more on the migration process .. but that is as long as likewise-open works without any problem. 

As an educational institution all students have roaming profiles which makes this single sign on a must before a network rollout.
I already have hundred of users on Active Directory and SQL databases hence changing servers to purely Linux is out of question.




Custom LiveCD
This works OK using remastersys package. Amazing program that even transfers all changed /etc/pam.d/common* files.

---

### Post by fwre01 on 2008-08-03
have you ever used/thought of using LTSP? i used it in the lab at work and was very impressed (in my very naive ways i thought it would be very good in a school environment)

---

### Post by wamrobert on 2008-08-03
Sorry I should have mentioned that I am using Hardy 8.04 Long Term Support.

I am in the process of changing .. so unless this likewise-open issue works I am not going to change.

I would rather use likewise. some users have laptops, wireless etc


> **fwre01 said:**
> have you ever used/thought of using LTSP? i used it in the lab at work and was very impressed (in my very naive ways i thought it would be very good in a school environment)

---

### Post by hazy_penguin on 2008-08-08
I am implementing Likewise-open on linux and Solaris.  Currently I have the default configuration.  So far everything seems to be working great with little configuration.

I have noticed if the box is configured with DHCP then I will get the Domain controller unreachable message and get logged in with cached credentials right after a reboot.  I do not get this when the machine has a static address.  If I wait 2 minutes prior to logging on I won't get the error messages since DHCP config has completed.

1. What version of likewise-open are you using?
2. Have you configured the machine with a static address?
3. When you logon as a local user what is the status of the likewise daemon prior to the restart?
4. What happens if you reverse the change for the default domain and login as DOMAIN\domainuser?

---

