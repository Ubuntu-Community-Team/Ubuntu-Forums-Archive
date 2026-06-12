---
title: "Inspiron 1420"
date: 2008-02-20
forum: Dell  Ubuntu Support
---

### Post by keyboardgnome on 2008-02-20
Greetings,

I've got a few problems with 7.10 on this system that I havent been able to sort out yet. I've tried various resolutions to them, but none of them work.

Suspend:
-There is no suspend to RAM, only suspend to disk. Is there a suspend to RAM available?

Audio:
-Audio works, until it suspends to disk. Upon resume, there is no audio. I've tried all the various scripts people have posted, removing modules and adding them, killing apps. Nadda. Only a reboot brings the sound back. I'm out of idea's on this one.

Freezes:
-After the system has been on for about a week, the wireless ethernet activity LED goes NUTS (constantly blinking very quickly). No new apps startup. If I go into the console, I log in as a lower priv'd user, but if I try to sudo, the session hangs. Ctrl-alt-del doesnt work. Only a full power off then back on will bring it back.

-Reboot freezes, the system goes to a blank screen that is still powered whenever the system is told to reboot.

Any suggestions, ideas, etc for above?

Thanks.

There is no 802.11n in this one. I've also got VMware running on it. Outside of that, nothing fancy about the system at all.

---

### Post by natehall on 2008-02-20
How was Ubuntu loaded on the 1420N? The [Dell DVD]("http:///linux.dell.com/wiki/index.php/Ubuntu_7.10")? A preload from the factory or the typical Ubuntu CD?

---

### Post by keyboardgnome on 2008-02-21
To clarify, this isnt a 1420N, it's a 1420 (there's no N on the label or on the model number).

The only option when spec'ing it for OS choice was Vista, so Ubuntu was loaded from the Ubuntu CD.

---

### Post by notwen on 2008-02-21
Your wireless issue is probably due to the use of the iwl3945 module over the previous ipw3945 module, look at the link provided by natehall and you'll see all issues related to the Inspiron 1420 and the fix/workaround available for that specific issue. If you just prefer a clean start, I would also recommend using Dell's custom Ubuntu image DVD for re-install the OS.  Best of luck.

---

### Post by keyboardgnome on 2008-05-01
Greetings

Things have only gotten worse. Now, the system randomly hangs. The same issues as before (even with the dell iso) *still* exist. If we cant fix this in the next week or two, we're going to go the way of Vista.

Any ideas?

---

### Post by keyboardgnome on 2008-05-01
In the meantime, I'm going to try to upgrade to 8.04 LTS

---

