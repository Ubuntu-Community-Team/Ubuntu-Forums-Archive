---
title: "having network problemsss!!"
date: 2006-09-26
forum: Desktop Environments
---

### Post by mothafukaa on 2006-09-26
well
my machine will not go online from within ubuntu
only from within windows
and i dont know how to fix it
help?
(i am BRAND new with linux, so DETAILED instructions/explanations would help)

---

### Post by bswilson on 2006-09-26
Can you provide **more** details?  Are you trying to connect with a wireless card?  What make and model is your Ethernet card?  What's your network configuration?

---

### Post by whizbaby on 2006-09-26
> **mothafukaa said:**
> i am BRAND new with linux, so DETAILED instructions/explanations would help
So how about **you** starting (what connection type, what modem)? Or do you think we're mind readers?

---

### Post by mothafukaa on 2006-09-26
i think your mind readers, umm lol jkjk
well, its not much of a network, its just my cable modem (made by RCA i beleive, for comcast) straigh to my computer onto the onboard ethernet

---

### Post by whizbaby on 2006-09-26
Then try (in terminal)
**sudo pppoeconf eth0**
and report any problems. If it solved, report, too.

---

