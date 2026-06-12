---
title: "Authentication Failures"
date: 2010-01-06
forum: Desktop Environments
---

### Post by darksoul7 on 2010-01-06
Hello everyone,

I have multiple Ubuntu machines running Likewise to connect to an Active Directory hierarchy. 

I have recently come across something quite troubling and I can't seem to get it sorted out.

I get an Authentication Failure when trying to log on locally. 

Logging on using the AD Credentials works without a problem.

I have not forgotten the password. 

I have tried changing the password by dropping to root shell prompt, but when I do I get the error - Token Manipulation Error.

Please let me know if you have any idea on how to fix this. 

Thanks

---

### Post by darksoul7 on 2010-01-06
I figured it out. It's a Likewise issue - 
here's how to get your local account access back if you come across this problem with Likewise.

1. Log in using a domain account that is part of the sudoers
2. Open Terminal and travel to the /etc/pam.d directory
3. Using nano, open common-account and search for any lines that include lsass.so
4. Put a # at the beginning of the line to comment it out
5. Save the file and exit
6. Repeat step 4 and 5 with the following files - common-auth & common-password
7. Use passwd to change your root and local account passwords.
8. Log off of the domain user and log onto the local account.
9. Uninstall Likewise and all Likewise dependencies.
10. Reinstall the Ubuntu supported Likewise and Likewise GUI clients
11. Open Terminal
12. Type sudo bash and type in your root password when prompted.
13. Type "domainjoin-gui" (without the quotes)
14. Rejoin your domain and restart the computer when prompted.

That's it. You should now be able to log on using both domain user accounts and the local account.

I hope this is of help to someone :)

---

### Post by AJH101 on 2010-05-05
I am unable to log into my desktop on a pc that is not part of a network - would this solution work for me? Could you repeat it in v e r y s l o w  english please?! :-)

---

### Post by rajesh0975 on 2010-05-14
> **darksoul7 said:**
> I figured it out. It's a Likewise issue - 
here's how to get your local account access back if you come across this problem with Likewise.

1. Log in using a domain account that is part of the sudoers
2. Open Terminal and travel to the /etc/pam.d directory
3. Using nano, open common-account and search for any lines that include lsass.so
4. Put a # at the beginning of the line to comment it out
5. Save the file and exit
6. Repeat step 4 and 5 with the following files - common-auth & common-password
7. Use passwd to change your root and local account passwords.
8. Log off of the domain user and log onto the local account.
9. Uninstall Likewise and all Likewise dependencies.
10. Reinstall the Ubuntu supported Likewise and Likewise GUI clients
11. Open Terminal
12. Type sudo bash and type in your root password when prompted.
13. Type "domainjoin-gui" (without the quotes)
14. Rejoin your domain and restart the computer when prompted.

That's it. You should now be able to log on using both domain user accounts and the local account.

I hope this is of help to someone :)

Thanx a lot for posting. I have a similar issue. Hope it gets sorted out :-)

---

