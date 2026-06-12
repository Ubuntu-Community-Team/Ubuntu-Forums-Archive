---
title: "Ubuntu starts my computer"
date: 2006-01-19
forum: General Help
---

### Post by wbh1 on 2006-01-19
Hi,

I started a new post because this problem is so utterly odd, I've never encountered it before with any OS or distribution besides ubuntu.  My computer just turned *itself* on last night, about 1:30 am.  _I have disabled all wake on events in my bios!_

I really do not understand why this is happening, and why this only happens with ubuntu.  This is not the first time this has happened either, I had previously installed the ubuntu preview release, but I was so freaked out about my pc turning itself on, that I reinstalled slackware.

Now, I'm a pc technician by trade, so there is little out there I have not seen, but I have never seen a powersupply or motherboard fail in such a way that it turns the computer on only when certian software is present.  This is african voodoo to me...

If anyone else out there has ever heard of this problem, please let me know.  I would love to know how to control this, or at least disable it.

---

### Post by jasmuz on 2006-01-19
By the way did you happen to install this?
nvram-wakeup - A tool to read/write the WakeUp time from/to the BIOS

If not, i find it absolutely strange how Ubuntu would talk to your BIOS and tell itself to turn on at a latter time.

---

### Post by lha on 2006-01-19
Some PSU's turn computer on after blackouts. You can try if your PSU has this 'feature' by plugging out your power cable (when computer is not on) and then plugging it in.

---

### Post by smaller on 2006-01-19
I agree, I highly doubt this has been caused by Ubuntu. Probably your bios allows you to configure what to do after a power failure. Mine does, I can configure it to do 1 of 3 things:
[LIST=1]
[*] turn the system on
[*] leave the system off
[*] return to the last state before the power failure
[/LIST]

---

### Post by Azion on 2006-01-19
There are alot of other Wake On Events in some bioses. You should check them out too, I know mine has alot of different ones

---

