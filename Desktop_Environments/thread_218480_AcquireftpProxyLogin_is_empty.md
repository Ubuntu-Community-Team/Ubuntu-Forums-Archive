---
title: "Acquire::ftp::ProxyLogin is empty"
date: 2006-07-18
forum: Desktop Environments
---

### Post by dominikroblek on 2006-07-18
I added the following repository to Synaptic Package Manager:

deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

Because I am behind the firewall I also defined the following ftp proxy:

ftp_proxy=ftp://proxy.abc.def:21

Now I'm getting the following error when trying to reload the package information in Synaptic Package Manager:

ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg: A proxy server was specified but no login script, Acquire::ftp::ProxyLogin is empty. [IP: 136.206.1.20 21]
ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz: A proxy server was specified but no login script, Acquire::ftp::ProxyLogin is empty. [IP: 136.206.1.17 21]

What is wrong with my configuration and how to fix it?

PS. To use my FTP proxy I just have to ftp to proxy.abc.def and log in as username@remote.ftp.server.

Thanks in advance!

---

### Post by dominikroblek on 2006-07-19
Does anybody know the solution of the problem described below?

> **dominikroblek said:**
> I added the following repository to Synaptic Package Manager:

deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

Because I am behind the firewall I also defined the following ftp proxy:

ftp_proxy=ftp://proxy.abc.def:21

Now I'm getting the following error when trying to reload the package information in Synaptic Package Manager:

ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg: A proxy server was specified but no login script, Acquire::ftp::ProxyLogin is empty. [IP: 136.206.1.20 21]
ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz: A proxy server was specified but no login script, Acquire::ftp::ProxyLogin is empty. [IP: 136.206.1.17 21]

What is wrong with my configuration and how to fix it?

PS. To use my FTP proxy I just have to ftp to proxy.abc.def and log in as username@remote.ftp.server.

Thanks in advance!

---

