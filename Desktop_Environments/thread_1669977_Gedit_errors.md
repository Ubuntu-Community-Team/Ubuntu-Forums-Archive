---
title: "Gedit errors"
date: 2011-01-18
forum: Desktop Environments
---

### Post by nkhosla on 2011-01-18
When I use gedit through the terminal (most recently for fstab modification), I get

```
(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:11022): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:11022): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

What are these errors, why are they Critical, and how do I fix them?  Gedit works still, so I have no idea what is going on.

Thanks,
nkhosla

---

### Post by 3Miro on 2011-01-18
How are you calling gedit? You should use:

```
gksudo gedit /etc/fstab
```

For graphical applications you should always use "gksudo" as opposed to "sudo".

---

### Post by nkhosla on 2011-01-18
I did:

```

me@my-computer:~$ gksudo gedit /etc/fstab
(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:16119): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:16119): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


```


What is G_TYPE_CHECK_INSTANCE?

Thanks,
nkk

---

### Post by alyore on 2011-01-22
I get the same errors when I start emacs, not just gedit:

(emacs:18207): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(emacs:18207): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

I'm using Ubuntu 10.04. Any idea what's going on?

---

### Post by Krytarik on 2011-01-22
I wouldn't care about those errors, as long as the respective app works. There are obviously a number of apps which cause the spewing of such -minor- error messages.

---

