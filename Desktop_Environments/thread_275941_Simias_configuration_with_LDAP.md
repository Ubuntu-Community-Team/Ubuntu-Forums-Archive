---
title: "Simias configuration with LDAP"
date: 2006-10-12
forum: Desktop Environments
---

### Post by nizarhandal on 2006-10-12
Dear All,

I have LDAP server installed and up on my ubuntu, i am trying to build and install iFolder 3.5 from source and then configure the simias server to use LDAP for users authentication, i've followed this manual ([http://www.ifolder.com/index.php/HowTo:Configure_iFolder_Enterprise_Server_on_Dapper](http://www.ifolder.com/index.php/HowTo:Configure_iFolder_Enterprise_Server_on_Dapper))
but i always get the following error when run "sudo simias-server-setup":

Configure Apache? [Y]:

Working...

Configuring /var/lib/simias/Simias.config...SetupSimias - Done
Setting up permissions...Done
Configuring /etc/apache2/conf.d/simias.conf...Done
Installing certificate from ldap://192.168.52.135/...Skipped (Not Required)
Connecting to ldap://192.168.52.135/...Done
Querying for directory type... OpenLDAP
Creating admin...Failed

LdapException: (34) Invalid DN Syntax
LdapException: Server Message: invalid DN
LdapException: Matched DN:
in <0x00036> Novell.Directory.Ldap.LdapResponse:chkResultCode ()
in <0x0009c> Novell.Directory.Ldap.LdapConnection:chkResultCode (Novell.Directory.Ldap.LdapMessageQueue queue, Novell.Directory.Ldap.LdapConstraints cons, Novell.Directory.Ldap.LdapResponse response)
in <0x000a3> Novell.Directory.Ldap.LdapConnection:Add (Novell.Directory.Ldap.LdapEntry entry, Novell.Directory.Ldap.LdapConstraints cons)
in <0x00017> Novell.Directory.Ldap.LdapConnection:Add (Novell.Directory.Ldap.LdapEntry entry)
in <0x003cd> Novell.iFolder.Utility.LdapUtility:CreateUser (System.String dn, System.String password)
in <0x00474> Novell.iFolder.SimiasServerSetup:SetupLdap ()
in <0x00040> Novell.iFolder.SimiasServerSetup:Configure ()
in <0x00051> Novell.iFolder.SimiasServerSetup:Main (System.String[] args)

FAILED

My slapd.conf file:

#######################################################################
# BDB database definitions
#######################################################################

database        bdb
suffix          "dc=malafat,dc=ps"
rootdn          "cn=manager,dc=malafat,dc=ps"
defaultaccess   read
schemacheck     on
lastmod         on
# Cleartext passwords, especially for the rootdn, should
# be avoid.  See slappasswd(8) and slapd.conf(5) for details.
# Use of strong authentication encouraged.
rootpw          {SSHA}G1NljorGWJ8+9MdfeKNOUOdur8BoxLlj
# The database directory MUST exist prior to running slapd AND
# should only be accessible by the slapd and slap tools.
# Mode 700 recommended.
directory       /usr/local/var/openldap-data
# Indices to maintain
#index  objectClass     eq
index   cn,sn,st                                eq,pres,sub

NOTE: attached with this post my simias server setup entry specification.

Any help?

---

