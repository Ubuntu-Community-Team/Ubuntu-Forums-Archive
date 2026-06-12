---
title: "Black Screen"
date: 2009-02-23
forum: General Help
---

### Post by haesl on 2009-02-23
Ubuntu 8.04
Computer freeze required manual shutdown. Upon restart, following login screen the monitor turns black, with desktop icons, but no gnome panel and a series of error messages: "An error occurred while loading or saving configuration information for... gnome-panel, update-notifier, evolution-alarm-notify," etc. Another message--"Configuration defaults for gnome power manager have not been installed correctly"--briefly appears. Can access home directory and system using live CD.

Is there a way to repair this without re-installing the OS?

If OS re-installation is required, can installed software, settings, etc. be preserved?

Home folder is on a separate partition: if re-installation is required, how do you preserve the existing home folder in this case?

---

### Post by haesl on 2009-02-23
I solved this problem by deleting the .gconfd/saved_state file in the home folder. See [http://ubuntuforums.org/showthread.php?t=93314](http://ubuntuforums.org/showthread.php?t=93314)

I happened upon this posting shortly after submitting my message. Thanks anyway all.

---

