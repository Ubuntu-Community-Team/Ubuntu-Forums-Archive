---
title: "GUI For mozillavpn Lost After 20.04 Update"
date: 2023-10-09
forum: Desktop Environments
---

### Post by jsland on 2023-10-09
What may cause the GUI not to be available.
Removing and reinstalling mozillavpn did not change anything.
The VPN is there and it can be run from the command line but cli is slower to use.

---

### Post by ActionParsnip on 2023-10-10
I'd contact Mozilla VPN for support. They should be able to help

---

### Post by ActionParsnip on 2023-10-10
If you run:
```

mozillavpn

```
from the terminal, does it load OK? Are there any errors in the terminal or is it purely that an icon isn't visible to launch the app and the application runs OK from the terminal?

---

### Post by jsland on 2023-10-11
mozillavpn as a stand alone cli statement is not how things work.
You need an action such as activate or deactivate as in mozillzavpn status or mozillavpn deactivate.
It all seems to work because the account key was carried over and not corrupted by the update.
Cli is slow so we like being lazy and based on some of the advertising received it makes you wonder if the tunnel is actually working.

---

### Post by ActionParsnip on 2023-10-12
Is this how you installed it
[https://support.mozilla.org/en-US/kb/how-install-mozilla-vpn-linux-computer](https://support.mozilla.org/en-US/kb/how-install-mozilla-vpn-linux-computer)

---

### Post by jsland on 2023-10-14
It was installed during the early rollout of mozillavpn so I don't recall exactly how it was done.
Normally I use synaptic.  Removal and reinstallation from there to fix the problem made no change.
Adding the repository and using apt from cli also made no fix.  However each of the 2 methods did not break the login credentials.
It strikes me the problem of the gui missing has to do with a conflict on or in the desktop manager of the recent 20.04 update. Since I don't revise things very often once they are working they generally are left alone.  This is simply because the issue of breaking what was working is very common and a big time waster for frequent updates.

---

### Post by jsland on 2023-11-02
Mozillavpn just released v 2.18.0 to address a known bug.
Using synaptic the new version did not show as a possible update.
Using CLI the new version loaded correctly and has taken care of the problem.

---

### Post by ActionParsnip on 2023-11-03
> **jsland said:**
> Mozillavpn just released v 2.18.0 to address a known bug.
Using synaptic the new version did not show as a possible update.
Using CLI the new version loaded correctly and has taken care of the problem.

If the way you installed the package doesn't add it own sources to manage updates automatically then synaptic won't see the update. If you install the new deb it should update the package you have to the newer version

---

