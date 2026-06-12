---
title: "Error installing updating repositories"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Eckstona on 2006-09-22
I have done some messing around with my sources.list, but I started using a generated one from the ubuntu source o matic. I can't install anything or update. I run kubuntu AMD64 Dapper

updating gives me this error in Konsole:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done


and installing gives a similar error. Does anyone know what the problem is?

---

### Post by mssever on 2006-09-22
First, please post your sources.list.

If you type ping kubuntu.org (or other hosts listed in sources.list), does ping use the address 127.0.0.1? It shouldn't, but apt-get is. 127.0.0.1 is your computer, not the server.

Finally, have you modified /etc/hosts? Posting that file would be great, too.

---

### Post by Eckstona on 2006-12-05
Well, I finally noticed that I had my firewall so tight I couldn't update. I had that sorted out a long time ago, forgive me for not updating.

---

