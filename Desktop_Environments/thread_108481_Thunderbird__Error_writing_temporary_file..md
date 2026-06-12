---
title: "Thunderbird:  Error writing temporary file."
date: 2005-12-26
forum: Desktop Environments
---

### Post by Footer on 2005-12-26
I'm running ver. 1.0.7 of Thunderbird and it suddenly decided to quit working on me.  Every time I go to send a message I get the error:  "Sending of message failed.  Error writing temporary file."  I tried reinstalling Thunderbird using Synaptic but no change.  As far as I know, nothing has changed on my system.      Thunderbird has been working just fine for the 6+ months I've been running it until now.

Any help or suggestions, greatly appreciated!

---

### Post by daschl on 2005-12-26
this sounds like a permission-problem. 

check this out

```

$ ls-alh | grep .thunderbird

```

(or .mozilla-thunderbird i dont know exactly)

and look at the permissions, maybe something has changed

---

### Post by Footer on 2005-12-26
Yes, I think it's a permissions problem too but I didn't change anything AFAIK.  Here's the results of that command:

footer@kubuntu:~$ ls -alh | grep .mozilla-thunderbird
drwxr-xr-x   5 footer footer  139 2005-09-24 06:39 .mozilla-thunderbird
footer@kubuntu:~$

Any other ideas?  Looks like the permissions are correct.

Thanks.

---

### Post by Footer on 2005-12-26
Reboot fixed the problem.  Maybe tmp space was filled up and rebooting cleared it out?  I had only been running for about 5 days or so since the last reboot.

Oh well, I'm glad it's fixed.

:)

---

