---
title: "Error printing to cups server from Dapper"
date: 2006-06-15
forum: Desktop Environments
---

### Post by esisa on 2006-06-15
I have just install two machines with Dapper Drake and upgraded one from Breezy. On all three machines I am having problems printing to a cups server. 

I use the command ```
lp /etc/passwd
``` and I get the respond ```
lp: Bad request
```. The cups server is on a Debian mashine and the newest version is installed(should be 1.1.23 i think). The server responds with the following in its error log: ```
ReadClient: 10 IPP Read Error!
```

Does anybody know if this is a bug in Dapper or in the Cups server?

[This bug report]("http://www.easysw.com/~mike/cups/str.php?L1717+P0+S-2+C0+I10+E0+Q") seem to be related to my problem.

---

