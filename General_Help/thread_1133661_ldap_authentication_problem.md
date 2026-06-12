---
title: "ldap authentication problem"
date: 2009-04-23
forum: General Help
---

### Post by dodgem on 2009-04-23
Hi,

I'm really starting to tear my hair out here!  I cannot get Ubuntu 8.10 to authenticate against my CentOS LDAP server...

I have both the server and client running as VMs in Sun Virtualbox using host interface as the network option.  The server has its firewall allowing all traffic through and has OpenLDAP running and populated using migrate_all_offline.ph script.

The client is a freshly installed and updated Ubuntu 8.10 with sshd, libnss-ldap, libpam-ldap, auth-client-config, ldap-auth-config, pam-auth-update installed.

/etc/ldap.conf has the uri to my ldap server and the base dn correctly set, pam.d/common-account etc all have entries which mention ldap (presumably setup by pam-auth-update), and when i run getent passwd/group/shadow, i can see the users, groups, and passwords listed who are in my ldap database.

However, attempting to su on the client to any user from the ldap db results in an 'unknown id' error, and trying to log in to the client either using ssh user@localhost, or from a remote machine fails...

I'm getting really fed up with it - no-one else seems to be having this issue, and i wonder if i've just missed something that should be really obvious?  I want to get the samba server on the CentOS machine to use LDAP as well, so that users can authenticate using the same password in windows or ubuntu, and change the password for both from either OS, but until i can get Ubuntu to login using ldap there's little chance of that... :(

---

