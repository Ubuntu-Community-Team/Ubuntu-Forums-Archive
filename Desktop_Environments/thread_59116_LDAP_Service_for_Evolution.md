---
title: "LDAP Service for Evolution?"
date: 2005-08-22
forum: Desktop Environments
---

### Post by kimvall on 2005-08-22
Have I understand it correctly that LPAD is a service that can syncronize your Evoltion data with an online server?

If so, does any company supply this service? Does anyone supply it for free?

It would be really smooth to be able to syncronize your Evoltion client with an online server, so that in case of a computer crash you still have your Evolution data.

Again, I'm pretty much a newbie at the whole Linux/Ubuntu experience but if anyone has an answer, I'd grately appreciate it.

Thanks un advance.

---

### Post by KingBahamut on 2005-08-22
Just set up LDAP yourself. Ill refer you to Craige and his documentation on this. 

> So you've got an LDAP server floating around and you'd like to have your Ubuntu or Debian client authenticate against it. It's assumed here that you already have an LDAP server and you or your admin can provide the answers to some of the questions asked upon configuration. Firstly, you'll need to open up your favourite package manager and install libpam-ldap and libnss-ldap:

$ apt-get install libpam-ldap libnss-ldap

This command will bring down all the required libraries to enable you to have your machine authenticating against the LDAP server of your dreams. Once the packages start being unpacked you'll be hit up for a few questions:

    * IP address / hostname of the LDAP server. ie: ldap.my.domain
    * The search base of your LDAP domain. ie: dc=my,dc=domain
    * You'll be asked the version of LDAP server you're connecting to, "Version 3" ought to be safe in most cases.
    * A screen titled "Configuring LIBNSS-LDAP will appear with only the "OK" option. Select it :)
    * On the next screen you'll be asked if you want to make root the DB admin. The best answer is "yes".
    * Now you'll be asked whether the DB requires logging in, say "No"
    * You'll be asked for the root login account for LDAP. It is often something like: cn=manager,dc=my,dc=domain
    * Then you'll need to enter the LDAP password for the aforementioned LDAP account 

That will see all the packages installed and the base configurations satisfied. If your LDAP server is already populated with content then at this point you should be able to run commands such as "getent passwd <username>" and if that username is unique to LDAP and you get a response then you answered all the questions correctly. Now you need to customise PAM to make it use LDAP for authentication.You'll need to run the following command:

$ sudo vi /etc/pam.d/sudo

Once deep in the bowells of the sudo file, you need to add one line above the existing line, something like this:

auth    sufficient      pam_ldap.so 
auth    required        pam_unix.so

This process now gets repeated for four more files, so I'll show the vi command and then the changes required:

$ sudo vi /etc/pam.d/common-account

account sufficient      pam_ldap.so
account required        pam_unix.so

$ sudo vi /etc/pam.d/common-auth

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure

$ sudo vi /etc/pam.d/common-password

password        sufficient      pam_ldap.so
password   	required   pam_unix.so nullok obscure min=4 max=8 md5

$ sudo vi /etc/pam.d/common-session

session 	sufficient      pam_ldap.so
session 	required        pam_unix.so

Last but not least we need to edit nsswitch.conf:

$ sudo vi /etc/nsswitch.conf

and once you're in that file, run this command:

:%s/compat/ldap files/g

Tada! If you've entered in all your local configuration information correctly, you'll have a living breathing LDAP authentication client. 

---

