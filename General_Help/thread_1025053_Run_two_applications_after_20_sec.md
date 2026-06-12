---
title: "Run two applications after 20 sec"
date: 2008-12-29
forum: General Help
---

### Post by rozbarwinek on 2008-12-29
Hi

I have a script that runs conky after 20 seconds that looks like this:

```
#!/bin/bash
sleep 20 && conky
```

I want to also run mail-notification after 30 seconds so I did to scripts and add them to sessions, but then I log out and log in there's only conky, but when I kill conky process mail-notification appears :|
What can I do to make them working together?

---

### Post by dcstar on 2008-12-29
> **rozbarwinek said:**
> Hi

I have a script that runs conky after 20 seconds that looks like this:

```
#!/bin/bash
sleep 20 && conky
```

I want to also run mail-notification after 30 seconds so I did to scripts and add them to sessions, but then I log out and log in there's only conky, but when I kill conky process mail-notification appears :|
What can I do to make them working together?

```
#!/bin/bash
sleep 20 && conky &
```

---

### Post by HermanAB on 2008-12-29
Read up on 'job control', the 'at' and 'cron' daemons.

Try putting '&' aty the end of the line to push a process into the background.

Cheers,

H.

---

### Post by rozbarwinek on 2008-12-29
Thanks for help ^^

---

