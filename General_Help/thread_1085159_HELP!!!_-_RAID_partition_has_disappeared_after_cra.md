---
title: "HELP!!! - RAID partition has disappeared after crash"
date: 2009-03-02
forum: General Help
---

### Post by hotweiss on 2009-03-02
I tried to put my computer to sleep, but for some reason I could not resume. I rebooted but I failed to boot up Ubuntu. I got the error "no block devices found" four times, "ALERT! /dev/mapper/myraidpartition does not exist. Dropping to shell!", and then I was at the "(initramfs)" prompt. I have important files that I want to recover! I am using dmraid. Any help would be appreciated, thanks.

---

### Post by fjgaude on 2009-03-02
What kind of raid are you running, raid0, 1? BIOS fakeRAID?

---

### Post by hotweiss on 2009-03-02
> **fjgaude said:**
> What kind of raid are you running, raid0, 1? BIOS fakeRAID?

fakeRAID using dmraid and I have it set to RAID0.

---

### Post by hotweiss on 2009-03-02
Typing "dmraid -ay" at the prompt gives me a memory corruption error.

---

