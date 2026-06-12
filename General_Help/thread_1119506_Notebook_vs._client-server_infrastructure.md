---
title: "Notebook vs. client-server infrastructure"
date: 2009-04-08
forum: General Help
---

### Post by freddy666 on 2009-04-08
Hi,

consider the following scenario: A user can login to a machine connected to a company network. The client machine uses LDAP for authentication which is provided by a server machine. The server also hosts the users home directories. The home directories are mounted on the client via NFS.

Now I want to use a notebook as a client machine. When I'm out of office and have no network connection I also want to login to the notebook and want to have access to my home directory. When I go back to office and connect to the company network the client local home directories should be synchronized with the ones stored on the server.

Also passwords, groups, etc. must be synchronous on the local machine.

The scenario described is common for windows machines but I'd like to use (K)Ubuntu. How can I accomplish that?

---

### Post by HermanAB on 2009-04-08
That is what NIS is for.  It has been around for many years, so there are many versions.

---

### Post by freddy666 on 2009-04-08
> **HermanAB said:**
> That is what NIS is for.  It has been around for many years, so there are many versions.

I'm not an administrator thus I know NIS only a bit. Does this solve the problem having access to one's home directory even when the machine is not connected to the network? Are password, group and user information also available when the machine is not connected to the network?

---

