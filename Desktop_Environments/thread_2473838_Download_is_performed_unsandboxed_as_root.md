---
title: "Download is performed unsandboxed as root"
date: 2022-04-15
forum: Desktop Environments
---

### Post by oygle on 2022-04-15
Installing claws-mail from Synaptic

> W: Download is performed unsandboxed as root as file '/root/.synaptic/tmp//tmp_cl' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

I see mention of changelogs at [https://ubuntuforums.org/showthread.php?t=2443374&p=13957249#post13957249](https://ubuntuforums.org/showthread.php?t=2443374&p=13957249#post13957249) ; I was viewing the changelog from Synaptic prior to the installation.

It has happened before - [https://ubuntuforums.org/showthread.php?t=2456118](https://ubuntuforums.org/showthread.php?t=2456118)

---

### Post by ActionParsnip on 2022-04-16
If you give the user access to the file, does it work OK? Does apt in a terminal work OK? Are there known bugs with Synaptic?

---

### Post by oygle on 2022-04-16
Thanks, they are all good questions. What resolved the issue was to reinstall ; no message this time.

---

