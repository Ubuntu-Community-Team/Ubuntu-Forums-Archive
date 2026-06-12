---
title: "remote file transfer to vista from 8.10"
date: 2009-03-11
forum: General Help
---

### Post by john@proficientpc on 2009-03-11
Hi I need help I want to transfer files to a vista system, also the vista system is off site at school, need help, Im running the live CD and if this works ill make it my main OS.

---

### Post by geirha on 2009-03-11
Well, in order to transfer file to your vista, you'll need some way to access it. Does it have any folders shared? Can you connect to it with remote desktop? Is it running an FTP-server?

If you can connect to it with remote desktop, then install an sftp/scp client in vista (like winscp or filezilla), and on your ubuntu, install openssh-server. Then you can connect to your ubuntu computer with scp/sftp from vista ...

---

