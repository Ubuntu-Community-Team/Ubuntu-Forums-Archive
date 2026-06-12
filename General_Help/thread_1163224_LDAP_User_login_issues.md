---
title: "LDAP User login issues"
date: 2009-05-18
forum: General Help
---

### Post by slyost on 2009-05-18
LDAP user login problem. 

I have been using Ubuntu 9.04 and authenticating with a SUN LDAP server and mounting NFS home directories from a SUN NFS server.  Some users can login fine on both the Ubuntu and SUN hosts.  However some users cannot login to the Ubuntu client successfully and are still able to login to the SUN's. 

Previously no LDAP users were able to logon and I was getting a GDM error but I resolved that.  Now some can and some can't.  The ones that cannot login get the following error: 

[COLOR=Red][B]You are required to change your password immediately (root enforced)
You are required to change your LDAP password immediately.
Enter login(LDAP) password[/B][/COLOR]

If I sudo su into one of these accounts I get the following additional message:

[B][COLOR=Red]su: Authentication token is no longer valid; new one required
(Ignored)[/COLOR][/B]

---

### Post by stp_abhi on 2009-05-22
**Ldap client authentication problem**!!!!

I followed the tutorial given in ubuntu forums.  but i didnt find the files **/etc/libnss-ldap.conf** and **/etc/libpam-ldap.conf** inorder to edit the files. My ldap server is working fine.. can anyone give a working description for ldap client setup for ubuntu 8.10 ..

---

### Post by slyost on 2009-05-22
> **stp_abhi said:**
> **Ldap client authentication problem**!!!!
 
I followed the tutorial given in ubuntu forums. but i didnt find the files **/etc/libnss-ldap.conf** and **/etc/libpam-ldap.conf** inorder to edit the files. My ldap server is working fine.. can anyone give a working description for ldap client setup for ubuntu 8.10 ..
 
The file name is actually /etc/ldap.conf not the lib.. as stated in the article.  I did not have to edit mine because it all worked after answering the questions durint the install.  My problem was due to the shadowlastchange entry in the LDAP for the user was set to 0.  I guess Sun ignores this and Ubuntu complains about it.  Mine is running fine now.

---

### Post by stp_abhi on 2009-05-24
thank you.. can you please tell me the procedure to setup as ldap client..

---

### Post by slyost on 2009-05-24
> **stp_abhi said:**
> thank you.. can you please tell me the procedure to setup as ldap client..
 
 
Why don't you post your ldap.conf file (less the password entry if any) and I will try and help.
 
What message do you get when you su - into a LDAP user?  Did you edit your nsswitch.conf file?  What is the result of running getent passwd?  Is the LDAP server a SUN?

---

### Post by stp_abhi on 2009-05-25
My ldap server is centos and i edited my nsswitch.conf file too.. I am able to connect to the ldap server through terminal only.. But i am unable to authenticate through GUI i.e at user login

---

### Post by stp_abhi on 2009-05-25
I successfully authenticated my client.. I just replaced the ip with FQDN in ldap.conf file.. thank you..

---

