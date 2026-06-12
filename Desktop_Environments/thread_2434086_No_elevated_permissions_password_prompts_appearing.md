---
title: "No elevated permissions password prompts appearing"
date: 2019-12-30
forum: Desktop Environments
---

### Post by fallen-luciel on 2019-12-30
Hi all,

This is an, almost fresh install of Xubuntu. The problem I'm having is, whenever I do something through the Gui that asks for my sudo password (install something, uninstall something, attempt to change a setting, etc) the prompt that normally should appear where I would write my password, doesn't. Meaning I literally can't do anything that requires elevated permissions on the gui, I need to go to the CLI to do it.

Example,
- Click on the menu button
- Click on software
- Click on Installed
- Click on any piece of software you no longer want.
- Click on Remove

Normal behaviour would be, you now get the password prompt. I don't, so clicking on Remove does nothing.

Thanks for any help or ideas in advance!

(PS: I've tried creating other users, in case it was an issue with the profile to no avail, same issue).

---

### Post by TheFu on 2019-12-30
No clue if this matters or not, but is the problem userid in the adm or sudo groups?
**id** will let you check that.

---

### Post by fallen-luciel on 2019-12-30
Hi TheFu,

It is

"uid=1000(username) gid=1000(username) groups=1000(username),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),118(lpadmin),126(sambashare)"

---

### Post by sisco311 on 2019-12-30
What happens when you run pkexec from a terminal:
```
pkexec echo
```

---

### Post by fallen-luciel on 2019-12-30
Hi Sisco311,

> **sisco311 said:**
> What happens when you run pkexec from a terminal:
```
pkexec echo
```

This:

```
==== AUTHENTICATING FOR org.freedesktop.policykit.exec ===
Authentication is needed to run `/bin/echo' as the super user
Authenticating as: RSO Systems Administrator,,, (rso-sysadmin)
Password:
```

After the password is introduced:

```
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.
```

Running it with sudo, nothing happens aside from it asking for the password on the terminal.

---

### Post by sisco311 on 2019-12-30
Make sure that policykit-1-gnome is installed and PolicyKit Authentication Agent (/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1) is added to the startup applications.

---

### Post by fallen-luciel on 2020-01-02
Good morning,

> **sisco311 said:**
> Make sure that policykit-1-gnome is installed  and PolicyKit Authentication Agent  (/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1) is  added to the startup applications.

policykit-1-gnome is installed and added to startup applications, still no joy unfortunately.

---

### Post by sisco311 on 2020-01-03
Check if the auth agent and the daemon is running:
```
ps -ef | grep polkit
```
```
systemctl status polkit.service 
```


If the agent is not running, try to start it manually an see if it produces any error message:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

---

