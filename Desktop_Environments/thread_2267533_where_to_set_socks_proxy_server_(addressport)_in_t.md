---
title: "where to set socks proxy server (address/port) in thunderbird"
date: 2015-03-02
forum: Desktop Environments
---

### Post by Skaperen on 2015-03-02
i need to use a **socks proxy server** (SOCKS5 as supported via ssh) to access my IMAP/SMTP server from here (where only destination ports 80 and 443 can make connections).
but the latest **Thunderbird** does not make it easy _to find where_ this is.
note that i currently have _NO accounts_ set up in **Thunderbird**.
help i found so far says to set this in the account info:frown:.
but setting up an account _FAILs_ because it cannot connect to the mail server yet.
i need to get the account setup logic to do its connection test via the **socks proxy**.
FYI: firefox is connected through this **socks proxy** right now.  i am doing *this post* via it.
FYI2: this **socks proxy** is running via **ssh** that connects via _port 443_ to an outsider server configure for sshd to listen _on port 443 on a spare IP address_.
_**the big question**_ thus is: how to configure **Thunderbird** to use a **socks proxy** *in general* for everything before any accounts are set up _so it does account tests via the_ **socks proxy**.

edit:

when i configure thunderbird like i configure firefox ... for sock proxy ... it still tries to make connects direct (e.g not using socks) for the account setup tests

---

