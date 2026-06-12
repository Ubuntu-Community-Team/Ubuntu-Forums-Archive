---
title: "Multi Monitor RDP (Ubuntu 22)"
date: 2024-04-25
forum: Desktop Environments
---

### Post by Al Grant on 2024-04-25
I would like to be able to connect to Ubuntu 22 from Windows RDP with multiple monitors supported.

What I have read so far suggests it can be done with Remmina and I should enable multi monitor support. I also read that remmina is already installed in Ubuntu 22.

However:

1. I can find no option for multi monitor support (in Ubuntu Settings)
2. If I type remmina at the cli the command is not found

Any suggestions for getting this to work?

Al

---

### Post by MAFoElffen on 2024-04-26
As I remember, Ubntu 22.04 did not have Remmina installed as a default. 

You could check that with
```

which remmina

```
If blank returned, it's not installed. Mine says its in /usr/bin/, because I installed it...

I had to install it
```

sudo apt install remmina remmina-plugin-rdp

```
Here is all the pluggins:
```

remmina-plugin-exec/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64
remmina-plugin-kiosk/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64
remmina-plugin-kwallet/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64
remmina-plugin-rdp/jammy-updates,jammy-security,now 1.4.25+dfsg-1ubuntu0.1 amd64 [installed,automatic]
remmina-plugin-secret/jammy-updates,jammy-security,now 1.4.25+dfsg-1ubuntu0.1 amd64 [installed,automatic]
remmina-plugin-spice/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64
remmina-plugin-vnc/jammy-updates,jammy-security,now 1.4.25+dfsg-1ubuntu0.1 amd64 [installed]
remmina-plugin-www/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64
remmina-plugin-x2go/jammy-updates,jammy-security 1.4.25+dfsg-1ubuntu0.1 amd64

```

---

