---
title: "capisuite problem"
date: 2006-08-14
forum: Desktop Environments
---

### Post by fdimmling on 2006-08-14
I have successfully installed capisuite and can send and receive faxes but the mail delivery does not work. Capisuite.error shows the following message: 

Mon Aug 14 20:33:47 2006 CapiSuite 0xbfd5711c: Error while trying to send mail: (111, 'Connection refused')

As a dependency for capisuite exim was installed and configured for local delivery of mail only. If I send a message by sendmail from a terminal the mail is delivered.

Any idea how to fix it. I desperately need fax services on the system.

Friedrich

Solution: The exim package obviously does not install a working mail transfer agent. No MTA process is started by the start script but no error message is given. However sendmail is working correctly. 

Replacing exim by procmail solved the problem.

FD

---

