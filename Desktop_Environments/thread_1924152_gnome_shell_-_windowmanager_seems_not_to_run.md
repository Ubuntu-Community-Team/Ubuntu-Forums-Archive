---
title: "gnome shell - windowmanager seems not to run"
date: 2012-02-12
forum: Desktop Environments
---

### Post by fiedlerrene on 2012-02-12
Hi folks,

I am new to gnome(-shell). I am running oniric 64Bit and just tried gnome-shell, because I am not really satisfied with unity. So I installed gnome-shell and some extentions.

However after some days, it does not work properly anymore. I don´t have a frame-border and this whole expose-like function(left sidepane) is also gone - so I would say that maybe the windowmanager does not run anymore.
Thus I also can not log off. Currently I am logging in from remote and terminate X ( so the network-manager is running... I am using WLAN). However the upper pane is also not working.

I tried to diagnose the problem and looked for some error-msg in /var/log/lightdm/* and messages/syslog. I haven´t found any error ( though I do not know what I am looking for).

Yesterday I decided to delete .conf* and .gnome* in my home and it finally worked again. So I set it up again. Today I have the same problem again. 

I tried to search for something similar in the forum and google but did not found anything... most probaly due to the lack of any error-msg.

Does anybody know what is happening at my pc ?

Thanks


EDIT: I did found something strange in /var/log/lightdm/x-0.log. X seem to complain that the nvidia modul does not exist.

---
(EE) Failed to load module "nv" (module does not exist, 0)
---
I am not sure what this means... X is starting ( the login-manager seems fine). Also the other environments( unity,lxde,) are not complaining and working as expected.

---

