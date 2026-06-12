---
title: "update-notifier not showing"
date: 2009-06-19
forum: General Help
---

### Post by oKtosiTe on 2009-06-19
Hello. I'm on Ubuntu (Not Xubuntu) 9.04, using a fairly minimal Xfce desktop. The update-notifier daemon is running and launched at login, but does not seem to be working, as I haven't seen it pop up in weeks. When I upen up Update Manager, however, it lists 14 updates.
I have a tray in my panel.
What gives?

```
$ update-notifier

(update-notifier:9286): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible

(update-notifier:9286): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(update-notifier:9286): atk-bridge-WARNING **: IOR not set.

(update-notifier:9286): atk-bridge-WARNING **: Could not locate registry
** (update-notifier:9286): DEBUG: /usr/lib/update-notifier/apt-check returned 14 (security: 0)
** (update-notifier:9286): DEBUG: crashreport_check
```

---

### Post by pedro_orange on 2009-06-19
Working as intended.

Check it: [http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates)

You can get it to pop up if you like. :)

---

### Post by oKtosiTe on 2009-06-19
Thanks for the quick, accurate and brief reply.

---

