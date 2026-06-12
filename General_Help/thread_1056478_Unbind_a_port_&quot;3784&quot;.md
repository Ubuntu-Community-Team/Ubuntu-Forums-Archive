---
title: "Unbind a port &quot;3784&quot;?"
date: 2009-01-31
forum: General Help
---

### Post by Presto-X on 2009-01-31
Hello everyone,

I'm trying to install Ventrilo server (free version) and the port number is hard coded. When I try and start the service I get the following message "ERROR: Unable to bind to TCP socket." so I need to find out what service is using that port and if it is nothing that I'm using any more I would like to unbind it so that I can install ventrilo...

Do you have any tips?

Thanks guys.

**Update:**
*Nevermind I found the awser to my question, it was ventrilo... I found this by typing in "lsof -i -n" this showed me all of the services running, I rebooted the system and the port was open again, and I was able to get ventrilo started this time.*

---

### Post by pytheas22 on 2009-01-31
The output of:
```

netstat -a | grep 3784
```

should tell you which service, if any, is running on that port.  But I'd also make sure that the error message isn't caused by something else--i.e. google the error message that you get.

---

