---
title: "Howto handle init scripts correctly"
date: 2006-01-31
forum: Desktop Environments
---

### Post by el3ktro on 2006-01-31
Ubuntu is starting a lot of things during boot up, and I want to remove some of this like cron, evms/lvm etc. I'm just not used to the Debian init system (coming from Gentoo) and I'm not sure how to handle init scripts correctly. How do I remove them? I've read somewhere that I should just chmod -x the ones I don't want to be started, but that causes a lot of error messages on logout. I've also heart about rc-update or so, but it seems in Debian you have to manually set the order in which the init scripts are started, and if I remove some and probably need them later I wouldn't remember where to put them (in which order).

So how is this all done?

Tom

---

### Post by gruepig on 2006-02-01
To remove services from initd:
'sudo update-rc.d -f <service> remove'
(removes symlinks in /etc/rc*.d/* which point to /etc/init.d/*)

To recreate symlinks:
'sudo update-rc.d <service> defaults'

You can use the '-n' flag with either of these to see what would happen without actually making any changes.

---

### Post by dcstar on 2006-02-01
[QUOTE=el3ktro]Ubuntu is starting a lot of things during boot up, and I want to remove some of this like cron, evms/lvm etc. I'm just not used to the Debian init system (coming from Gentoo) and I'm not sure how to handle init scripts correctly. How do I remove them? I've read somewhere that I should just chmod -x the ones I don't want to be started, but that causes a lot of error messages on logout. I've also heart about rc-update or so, but it seems in Debian you have to manually set the order in which the init scripts are started, and if I remove some and probably need them later I wouldn't remember where to put them (in which order).

So how is this all done?

Tom[/QUOTE]
Install sysv-rc-conf and you will have a tool to do your bidding.

---

### Post by el3ktro on 2006-02-01
Hello, thanks for your posts.

@gruepig
If I remove a service like this, and when I want to add it again, how do I know in which order it is started, or is this done automatically?

@dcstar
Thanks for this hint, I've tried it and it works great. I don't mind doing such things manually like gruepig described, but sometimes such a simle interface is nice to have a good overview which services you actually have!

Thanks two both of you!
Tom

---

