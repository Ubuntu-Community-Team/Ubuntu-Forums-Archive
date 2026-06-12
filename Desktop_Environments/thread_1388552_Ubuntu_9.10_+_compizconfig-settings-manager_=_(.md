---
title: "Ubuntu 9.10 + compizconfig-settings-manager = :("
date: 2010-01-23
forum: Desktop Environments
---

### Post by Sun40 on 2010-01-23
Hi everyone! I'm a newbie :) I've install ubuntu jsut one week ago. Yesterday I decided to install compizconfig-settings-manager. Then I turn on some effect (don't remember witch one) and my computer hang. So I reboot it, but when X-server starts, it hangs again[COLOR=Black]. Then I reboot in revoery mode, and remove [/COLOR]compizconfig-settings-manage (apt-get remove) , but X-server still hangs((.

Sorry for my bad english. :redface:

---

### Post by Pro_D on 2010-01-23
I am by no means any type of expert on this stuff but I am pretty sure that compizconfig-settings-manager JUST does configuration stuff so by removing it you only removed a configuration utility and not the changes it made.

I did some searching for how to reset compiz setting to default on the commandline and got the following command:
$ gconftool-2 --recursive-unset /apps/compiz


I don't know if it will help though...  the command seems to be present in 9.10 still...  If that above one doesn't do it I found 2 more commands.
$ gconftool-2 --recursive-unset /schemas/apps/compiz
$ gconftool-2 --unset /apps/gnome-compiz-preferences 

Good luck!

---

### Post by Sun40 on 2010-01-24
Thanks, it works!

$ gconftool-2 --recursive-unset /apps/compiz

---

