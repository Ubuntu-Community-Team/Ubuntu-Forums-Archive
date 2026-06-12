---
title: "create home folders at login (ldap)"
date: 2009-04-01
forum: General Help
---

### Post by mnem0nic7 on 2009-04-01
Here is what I have.
storage server that shares the home folder via nfs
openldap server that authenticates 8000+ users
client for testing purposes.

What I want to do is basically have roaming profiles.  I hope to accomplish this by having the home folders reside on the nfs server.

What works so far.  I can use putty to log into the client machine using a user from the ldap server.  Also the nfs share works and mounts fine at startup.

I try to log into the client using gnome and I get an error that says .dmrc needs permissions of 644.  I have changed the permissions on the file, but it says the same thing. 

Any help is appriciated.

---

### Post by dcstar on 2009-04-02
> **mnem0nic7 said:**
> Here is what I have.
storage server that shares the home folder via nfs
openldap server that authenticates 8000+ users
client for testing purposes.

What I want to do is basically have roaming profiles.  I hope to accomplish this by having the home folders reside on the nfs server.

What works so far.  I can use putty to log into the client machine using a user from the ldap server.  Also the nfs share works and mounts fine at startup.

I try to log into the client using gnome and I get an error that says .dmrc needs permissions of 644.  I have changed the permissions on the file, but it says the same thing. 

Any help is appriciated.

Any /home folder must **fully **support Linux security features, otherwise you have problems.

---

