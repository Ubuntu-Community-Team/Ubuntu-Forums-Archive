---
title: "No ntpdate file in /etc/init.d"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Lord Julius on 2006-08-30
I'm trying to authenticate an ubuntu box in ADS and can't sync with my time servers. I've installed the service but there's no way to start it. In the terminal I'm typing "/etc/init.d/ntpdate start" and then I get in reply "No such file or directory". I've checked and doublechecked that the package is installed, so I'm not sure what else to check at this point. Any and all help is appreciated.

---

### Post by mssever on 2006-08-30
I'm not sure I quite understand what you're trying to do, but I don't have an ntpdate. I do have /etc/init.d/ntp-server.

Here's a tip: When you're typing a command or filename, type tab for autocomplete. For example, if I type "sudo /etc/init.d/ntp<tab>" it automatically fills in the rest. If you get nothing, hit tab again and you'll get a list of possible matches.

---

