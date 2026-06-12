---
title: "Synaptic on kubuntu"
date: 2007-08-31
forum: Desktop Environments
---

### Post by nvivo on 2007-08-31
Hi.

I migrated from Ubuntu to Kubuntu a week ago, but I really don't like Adept, neither the Kubuntu default Add/Remove programs that is based on adept.

So I installed "synaptic" and "gnome-app-install" and they work fine. But I cannot find a way to put that ubuntu update notification on the tray. I didn't remove adept, so it still shows me the updates using adept.

Does anyone know how install the update notification from gnome in Kubuntu? I have been looking for a package but couldn't find anything.

Or maybe some config file that would make adept notification open synaptic instead of adept.

Thanks

---

### Post by shuttleworthwannabe on 2007-08-31
this is a wild guess, how about gnome update manager? it should be in synaptic--I am using xubuntu right now, sorry if this is not what you were looking for

---

### Post by asipi on 2007-09-02
I am also a synaptic user but adept-updater just works fine so I left as is...
Not so plenty of updates so it not worth to to work with including the ubuntu update notificator in kubuntu...
Try to live with it :)

---

### Post by por100pre1 on 2007-09-02
Try creating a launcher for:

```
/usr/bin/update-manager
```

Hope this helps. :)

---

### Post by nvivo on 2007-09-02
> **asipi said:**
> I am also a synaptic user but adept-updater just works fine so I left as is...
Not so plenty of updates so it not worth to to work with including the ubuntu update notificator in kubuntu...
Try to live with it :)

Hi.

I found the package "update-manager" that includes the update-notifier... Couldn't test it because there was no updates since... But seens to be it. Let's wait.

Thanks.

---

### Post by por100pre1 on 2007-09-02
Here's the icon:

/usr/share/icons/Tango/scalable/apps/update-manager.svg

Be sure to have tango-icon-theme installed.

---

