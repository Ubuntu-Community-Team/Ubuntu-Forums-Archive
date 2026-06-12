---
title: "Small Compiz Issue..."
date: 2007-03-09
forum: Desktop Environments
---

### Post by starcraft.man on 2007-03-09
Hi again, I followed the guide thoroughly on Ubuntuguide.org for XGL/Compiz, and got through it all without any problems (except for a minor gpg key issue, thanks Kateikyoushi ). 

This is a two fold issue... I'm not exactly sure how to set compiz to execute by default (instructions say execute in terminal with "compiz-tray-icon" and I made an launcher...) is there a folder I drop the launcher to get it to run at startup?

Secondly... I get this garble when I execute my launcher, what does it mean?

```

(compiz-tray-icon:6070): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6070): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:6070): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6070): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

---

### Post by starcraft.man on 2007-03-09
Hi again, I followed the guide thoroughly on Ubuntuguide.org for XGL/Compiz, and got through it all without any problems (except for a minor gpg key issue, thanks Kateikyoushi ). 

This is a two fold issue... I'm not exactly sure how to set compiz to execute by default (instructions say execute in terminal with "compiz-tray-icon" and I made an launcher...) is there a folder I drop the launcher to get it to run at startup?

Secondly... I get this garble when I execute my launcher, what does it mean?

```

(compiz-tray-icon:6070): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6070): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:6070): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6070): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

I reinstalled once to see if it was bad install but seems that wasn't it...

Also sometimes when I was editting preferences I get this message saying compiz.real closed unexpectedly... I'm pretty sure its related.

---

### Post by lamalex on 2007-03-09
for it to run at startup go to system >> preferences >> sessions > startup tab and add it there.

i've got no idea what that stuff means, if it's running fine it's probably just more or less meaningless debugging messages of some sort.

---

### Post by K.Mandla on 2007-03-09
(Moved to Desktop Environments. :) )

---

### Post by K.Mandla on 2007-03-09
(Moved to Desktop Environments. ;) )

(Edit: And merged a double-post. ;) )

---

### Post by starcraft.man on 2007-03-09
Ah ok, thanks both of ya... sorry for double post had a small browser error ><.

---

