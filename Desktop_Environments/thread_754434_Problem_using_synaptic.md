---
title: "Problem using synaptic"
date: 2008-04-13
forum: Desktop Environments
---

### Post by reason4man on 2008-04-13
When I tried to install my synaptic updates, an error message stating this showed up:

failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '--progress-str' 'please wait this can take some time.' '--finish-str' 'update is complete' '--set-selection-file' '/tmp/tmp1ui3q7 as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.

What are they saying and what does this mean?

---

### Post by overdrank on 2008-04-13
> **reason4man said:**
> When I tried to install my synaptic updates, an error message stating this showed up:

failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '--progress-str' 'please wait this can take some time.' '--finish-str' 'update is complete' '--set-selection-file' '/tmp/tmp1ui3q7 as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.

What are they saying and what does this mean?

HI and do you get any errors when updating through the terminal 
```
sudo apt-get update
sudo apt-get upgrade
```
The terminal is located under applications, accessories.

---

