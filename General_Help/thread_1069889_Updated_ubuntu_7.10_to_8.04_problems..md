---
title: "Updated ubuntu 7.10 to 8.04 problems."
date: 2009-02-14
forum: General Help
---

### Post by /home on 2009-02-14
Hi,
I updated my Ubuntu 7.10 laptop to 8.04 using the update manager.
Everything went fine. However, when i rebooted it took a while to start (five mins on a 2GB ram, dual core). And when it finally started up. I got this error message > There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in..
Please help

---

### Post by cariboo on 2009-02-14
Your may not have a complete update, open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

after the above command has finished type:

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

The above commands should make sure your update is complete.

Jim

---

### Post by /home on 2009-02-16
Thanks

---

### Post by stchman on 2009-02-16
Do a fresh install, it is quicker and will be less problematic.

---

