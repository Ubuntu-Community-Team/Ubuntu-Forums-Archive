---
title: "Domain Account management"
date: 2022-01-02
forum: Desktop Environments
---

### Post by jag77202 on 2022-01-02
I'm aware of Linux systems using Active Directory for user authentication from some old jobs.

Currently, in a new and small org.  

I'd like to know if there is user authentication system for a domain where each user can log into all desktops? I'd like to not have local authentication on each desktop per user.

Our current desktops are Windows, Mac and Linux. We are going to gradually move all desktops to Linux and still have small amount of Mac.

We would like to not use any Microsoft Authentication servers.

Thanks

---

### Post by grahammechanical on 2022-01-02
My only experience of what you are talking about was more than 30 years ago when I was employed by a high street retailer and the company brought in desktop PCs and customer tills that were actually a PC and ran Microsoft NT on it all. After I was given a level of access to the system I could login to any desktop PC and any till.

I think I understand correctly that Active Directory is a Microsoft system and that you do not want to use anything from Microsoft. You want a Linux alternative. I have no experience in this area. I see two ways of doing this. A small organization might want a Do It Yourself or In House approach. Someone will have to do a lot of studying and some experimentation. Or, pay a professional to advise and train some employees.

I have some some links

[https://ubuntu.com/server/docs/service-kerberos](https://ubuntu.com/server/docs/service-kerberos)

[https://ubuntu.com/server/docs/service-sssd](https://ubuntu.com/server/docs/service-sssd)

[https://ubuntu.com/server/docs/service-ldap](https://ubuntu.com/server/docs/service-ldap)

Those links are from a commercial organization called Canonical. It is the sponsor of Ubuntu. It might be practical for a representative of your organization to contact Canonical to see if they can offer a cost effective solution that will be ready made for your organization.

[https://canonical.com/](https://canonical.com/)

Regards

---

### Post by rsteinmetz70112 on 2022-01-04
For Windows Clients you can use Samba which can serve as an AD domain controller. With Samba any Windows or Linux users can log into any system, not familiar with Mac since I don't use them, but a quick Google says a Mac can join an AD domain. There are probably other ways to accomplish the same thing using LDAP Kerberos and other protocols, again I'm not sure since I don't use it. Samba is not the best way to share files between Linux computers, that is usually NFS, again I'm not familiar with Mac but a quick google says you can use NFS.

Good luck with you project.

---

### Post by greene-dog on 2022-01-06
Ok.  After thinking about this and looking around, It has come that we  are just looking for a single login ability (SSO) for Linux desktops.   When and if there are MS or Mac is not a concern. 

And when/if it is available, we wold like it to not be complicated like Active Directory seems to be.

Maybe we are thinking and wanting too much

---

### Post by ActionParsnip on 2022-01-07
[h=1]1Domain Join[/h][h=2]1.1Prerequisites[/h]
[LIST=1]
[*]Install required packages and accept the defaults for the LDAP configuration
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo apt install krb5-user samba sssd
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]When prompted for LDAP configuration, accept the defaults
[*]When prompted to override PAM file changes, leave No selected
[/LIST]
 
[h=2]1.2Configuration[/h][h=3]1.2.1Kerberos[/h]
[LIST=1]
[*]Open the Kerberos config file
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo vim /etc/krb5.conf
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Under default_realm add the following two settings
[/LIST]
[TABLE="width: 567"]
[TR]
[TD]       ticket_lifetime = 24h
       renew_lifetime = 7d
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Save the file
[/LIST]
[h=3]1.2.2Samba[/h]
[LIST=1]
[*]Edit the samba configuration file
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo vim /etc/samba/smb.conf
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Comment out the line following line in the [global] section
[/LIST]
[TABLE="width: 567"]
[TR]
[TD]workgroup = WORKGROUP
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Add the following lines beneath it. Note that the workgroup is the domain name in uppercase (e.g., MS) and not the FQDN (e.g., MS.PRIVATE).
[/LIST]
[TABLE="width: 567"]
[TR]
[TD]workgroup = PARSNIP
client signing = yes
client use spnego = yes
kerberos method = secrets and keytab
realm = PARSNIP.COM
security = ads
disable netbios = yes
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Save the file
[/LIST]
[h=3]1.2.3SSSD[/h]
[LIST=1]
[*]Create the SSSD configuration file
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo mkdir /etc/sssd
sudo vim /etc/sssd/sssd.conf
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Enter the following lines with the settings in red needing to be defined for the domain to be joined to.
[/LIST]
[TABLE="width: 567"]
[TR]
[TD][sssd]
domains = parsnip.com
config_file_version = 2
services = nss, pam, ssh, sudo
 
[domain/parsnip.com]
id_provider = ad
access_provider = ad
cache_credentials = True
use_fully_qualified_names = false
ad_gpo_access_control = permissive
default_shell = /bin/bash
override_homedir = /home/%d/%u
dyndns_update = true
dyndns_refresh_interval = 43200
dyndns_update_ptr = true
dyndns_ttl = 3600
[/TD]
[/TR]
[/TABLE]
 
[TABLE="width: 605"]
[TR]
[TD]!
[/TD]
[TD]**Critical Note **
While we work to control Linux via GPO, ad_gpo_access_control being set to permissive is critical. If is it not defined to set to enforced then you will not be able to log in with your domain account and the system will become unstable.
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Save the file
[*]Change the permissions of sssd.conf
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo chown root:root /etc/sssd/sssd.conf
sudo chmod 600 /etc/sssd/sssd.conf
[/TD]
[/TR]
[/TABLE]
 
[TABLE="width: 605"]
[TR]
[TD]!
[/TD]
[TD]**Important Note **
The first time you start SSSD it may appear to fail with the following error:
 
Job for sssd failed because the control process exited with error code. See "systemctl status sssd" and "journalctl -xe" for details.
 
This is expected due to the server not yet being domain joined.
[/TD]
[/TR]
[/TABLE]
 
[h=2]1.3Final Checks[/h]
[LIST=1]
[*]Confirm that SSS had been added as an identity provider
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]grep 'sss' /etc/nsswitch.conf
[/TD]
[/TR]
[/TABLE]
 
passwd:         compat sss
group:          compat sss
shadow:         compat sss
services:       db files sss
netgroup:       nis sss
sudoers:        files ssss

[LIST=1]
[*]Confirm that the hosts file entry for the server&#8217;s IP address has the domain FQDN as well as the hostname.
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]grep $HOSTNAME /etc/hosts
[/TD]
[/TR]
[/TABLE]
 
10.0.0.4 servername.parsnip.com servername

[LIST=1]
[*]Restart services
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo systemctl restart smbd nmbd
[/TD]
[/TR]
[/TABLE]
 
[h=2]1.4Test & Join[/h]
[LIST=1]
[*]Test the configuration by obtaining a Kerberos ticket. You will be prompted to enter your password.
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo kinit mydaaccount
[/TD]
[/TR]
[/TABLE]
 

[LIST=1]
[*]Verify the ticket
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo klist
[/TD]
[/TR]
[/TABLE]
 
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: mydaaccount@PARSNIP
 
Valid starting     Expires            Service principal
14/11/21 18:04:02  15/11/21 04:04:02  krbtgt/ [email]PARSNIP.COM@PARSNIP.COM[/email]
        renew until 15/12/21 18:03:58

[LIST=1]
[*]Join the domain. Note that it may take several minutes to complete even after the joined message has appeared.
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo net ads join -k
[/TD]
[/TR]
[/TABLE]
 
Using short domain name &#8211; PARSNIP
Joined 'SERVERNAME' to dns domain 'parsip.com'
 
 
 
 
 

[LIST=1]
[*]Confirm in Active Directory Users and Computers that the computer account appears and then move it to the required OU
[*]Start the SSSD service
[/LIST]
[TABLE="width: 586"]
[TR]
[TD]$
[/TD]
[TD]sudo systemctl start sssd
[/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2022-01-07
> **greene-dog said:**
> Ok.  After thinking about this and looking around, It has come that we  are just looking for a single login ability (SSO) for Linux desktops.   When and if there are MS or Mac is not a concern. 

And when/if it is available, we wold like it to not be complicated like Active Directory seems to be.

Maybe we are thinking and wanting too much

Use LDAP for centralized user/group POSIX accounts.
Use NFS  (really autofs)  for shared end-user HOME directory mounts.  When a user sits behind any system, they can login, be authenticated via LDAP, then have their HOME mounted automatically.

There are guides to do these things at help.ubuntu.com.  Autofs is relatively easy.  LDAP sorta sucks, so many people will use 3rd party LDAP managers. A few years ago, I'd have suggested FreeIPA, but that seems to be dead.  Check out "LDAP Account Manager". I've never used it. We have a different solution that comes with our enterprise email server for LDAP and it isn't something I'd suggest anyone else deploy for LDAP management.

25 yrs ago, the answer was NIS and it was really great and easy, except for all the poor security aspects.  The replacement, NIS+, doesn't have a free NIS+ server available - Sun Microsystems gave away the client software, but not the server. They effectively killed NIS+ for company that won't use Solaris.

It is embarrassing that Canonical doesn't have a great LDAP admin tool, really.

---

