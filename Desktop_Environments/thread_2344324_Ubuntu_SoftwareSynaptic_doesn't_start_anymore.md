---
title: "Ubuntu Software/Synaptic doesn't start anymore"
date: 2016-11-24
forum: Desktop Environments
---

### Post by f(fanta) on 2016-11-24
I don't manage to start the Ubuntu Software (synaptic) anymore. If I click on the bar icon, the icon flashes and nothing else happens. With** gksudo synaptic **from command line, it asks for the admin password, but then again nothing happens. What else can I try? Or information I can collect to troubleshoot the issue? Running version 16.04 64-bit.

---

### Post by bearlake on 2016-11-24
What version of Ubuntu are you using?

Post the errors from the terminal you receive after running "synaptic"

---

### Post by CantankRus on 2016-11-25
ubuntu-software is not synaptic.
I haven't been able to run ubuntu-software for some time but I don't use so haven't worried about it.
Seems to be a user config problem as I can run it in my test account and guest account.


Install synaptic...
```
sudo apt install synaptic
```

Should start from dash.
If not, test in terminal (no sudo needed)...
```
synaptic-pkexec
```

---

