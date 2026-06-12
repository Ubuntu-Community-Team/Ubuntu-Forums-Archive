---
title: "Gfax crashes on start"
date: 2007-07-10
forum: Desktop Environments
---

### Post by Master One on 2007-07-10
My ISP offers access to their HylaFax server, and I just wanted to setup my fresh Ubuntu Feisty installation to be able to send faxes, but Gfax just keeps crashing.

At first it started normally, and I could setup all the necessary settings for using Hylafax as transport. After the setup was completed, it told me to restart Gfaxl, and since then it keeps crashing right after start with the following error message (shown when started from a console):```
$ gfax

Unhandled Exception: System.ArgumentOutOfRangeException: < 0
Parameter name: length
  at System.String.Substring (Int32 startIndex, Int32 length) [0x00000] 
  at gfax.Hylafax.get_ip_addr (System.String ipdata) [0x00000] 
  at gfax.Hylafax.asyncgetfolder (System.String folder) [0x00000] 
  at gfax.Hylafax.asyncstatus (System.String queue) [0x00000] 
  at gfax.Fax.async_get_server_status () [0x00000] 
  at gfax.Gfax.async_update_status () [0x00000] 
  at gfax.Gfax..ctor (System.String fname, System.String[] args) [0x00000] 
  at gfax.gfax.Main (System.String[] args) [0x00000]
```
Any idea?

I think Gfax should be the best solution for my intended use, so I really would like to have this operational.

---

### Post by Master One on 2007-07-10
I just filed a bugreport ([#125003](https://bugs.launchpad.net/ubuntu/+source/gfax/+bug/125003)) on launchpad.

Is there any real alternative to Gfax, that I could try? As mentioned, I need a good GTK+ client for accessing a remote HylaFax server.

---

### Post by Master One on 2007-07-10
I just compiled Gfax from source, and unfortunately it results in the same error. This problem only exists, if HylaFax is selected as transport, it seems to be working normally with efax.

---

