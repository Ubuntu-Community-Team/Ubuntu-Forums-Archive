---
title: "[SOLVED] Adept Updater/Notifier does not notify me of available updates"
date: 2008-12-12
forum: General Help
---

### Post by utkjamie on 2008-12-12
Sometime after upgrading to Intrepid, Adept Updater/Notifier stopped notifying me of available updates. I don't have any error messages. It's just that I'll realize from time to time that I've gone several weeks without having any updates and will run "sudo apt-get update" from the command line and then I will see the Adept Notifier show up in my system tray telling me I have about a dozen available updates.

If I were to guess, I'd say that Adept Updater isn't running. But I really don't know.

UPDATE:
Silly me. Simple solution is to add a root cron job for Adept Updater.

---

