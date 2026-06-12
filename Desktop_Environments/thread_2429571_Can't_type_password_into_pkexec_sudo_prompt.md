---
title: "Can't type password into pkexec sudo prompt"
date: 2019-10-19
forum: Desktop Environments
---

### Post by jklarson on 2019-10-19
Running 19.10 with gnome-shell, I can't type my password into pkexec sudo prompts. When I select the text field and type, nothing whatsoever comes up. The mouse still works to hit the cancel button. This is directly on the console, not through VNC, although it doesn't work there either.

Running GUI programs as root via sudo from the terminal works fine.

Syslog has the following error:

```
Oct 19 20:08:14 myhost gnome-shell[5618]: JS ERROR: TypeError: this._grabStack[i] is undefined#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:317:27#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:12
Oct 19 20:08:21 myhost gnome-shell[5618]: message repeated 2 times: [ JS ERROR: TypeError: this._grabStack[i] is undefined#012onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:317:27#012_onCapturedEvent@resource:///org/gnome/shell/ui/grabHelper.js:13:12]
Oct 19 20:08:21 myhost bleachbit-root.desktop[5618]: Error executing command as another user: Request dismissed
```

Has anyone else run into this problem?

---

### Post by jklarson on 2019-10-19
Bizarrely, a reboot fixed the problem. If it comes up again I'll return.

---

### Post by TheFu on 2019-10-22
There was a sudo patch last week. Could having the new version installed, but not restarting the sudo subsystem have been the problem?

My servers haven't been rebooted in about 9 days. I patch on the weekends. Haven't see this issue here, but I don't use pkexec or sudo with GUI tools or run 19.10.

---

