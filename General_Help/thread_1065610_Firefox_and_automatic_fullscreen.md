---
title: "Firefox and automatic fullscreen"
date: 2009-02-10
forum: General Help
---

### Post by BuntuFirstTimer on 2009-02-10
Every time I open up Firefox, it goes into an awkwardly *semi-full screen* mode. The GNOME GUI panels (up and down) in Ubuntu suddenly disappears from that awkward full screen mode.

Any ideas what is going on?

---

### Post by zika on 2009-02-10
if that happens in Compiz:
System->Preferences->CompizConfig_Settings_Manager->Workarounds->Legacy_Fullscreen_Support(uncheck)

---

### Post by BuntuFirstTimer on 2009-02-10
[IMG]http://i608.photobucket.com/albums/tt170/smallfullmoon/Screenshot.png[/IMG]

My screenshot when I first click on the Firefox icon. It isn't completely a fullscreen mode and I can't minimalize the firefox window with my mouse. I always have to double-press F11 button instead.

---

### Post by BuntuFirstTimer on 2009-02-10
> **zika said:**
> if that happens in Compiz:
System->Preferences->CompizConfig_Settings_Manager->Workarounds->Legacy_Fullscreen_Support(uncheck)

Can't find the CompizConfig nor the Setting Manager in the Preference tab.

---

### Post by zika on 2009-02-10
> **BuntuFirstTimer said:**
> Can't find the CompizConfig nor the Setting Manager in the Preference tab.
System->Preferences->Main_menu->Preferences->CompizConfig_Setting_Manager(check)
than do the above.

---

### Post by BuntuFirstTimer on 2009-02-10
> **zika said:**
> System->Preferences->Main_menu->Preferences->CompizConfig_Setting_Manager(check)
than do the above.

No luck finding CompizConfig... Did I do something wrong? Or I need to install Compiz from scratch?

---

### Post by zika on 2009-02-10
sudo apt-get install simple-ccsm (I think, not sure, it might be just ccsm) (might try just Alt-F2 ccsm)

---

### Post by BuntuFirstTimer on 2009-02-10
> **zika said:**
> sudo apt-get install simple-ccsm (I think, not sure, it might be just ccsm)

Did it.

But I wonder why my Firefox always does this? Automatic fullscreen mode that isn't even complete... Can't use the GNOME GUI panels because it's all covered from the weird fullscreen mode.

Could this be a bug?

So far, it looks okay. I'll keep my eyes on this issue for a bit, just in case.

---

### Post by zika on 2009-02-10
> **BuntuFirstTimer said:**
> Did it.

But I wonder why my Firefox always does this? Automatic fullscreen mode that isn't even complete... Can't use the GNOME GUI panels because it's all covered from the weird fullscreen mode.
F11,F11, Unmaximize, Resize to something that comfortably resides on Your desktop, close, re-open.

---

### Post by BuntuFirstTimer on 2009-02-10
> **zika said:**
> F11,F11, Unmaximize, Resize to something that comfortably resides on Your desktop, close, re-open.

I did it like that for the longest time.

To me, I'll just consider this as a bug for now.

---

### Post by sahabcse on 2009-02-10
Login to another user and check the firefox, there also same issue means  try to reinstall the firefox. I have fixed using reinstall the firefox. 

sudo apt-get --reinstall install firefox

---

### Post by zika on 2009-02-10
> **BuntuFirstTimer said:**
> I did it like that for the longest time.
I thought so, that is why I mentioned it last. but even though it doesn't matter if You did it earlier, it has to be done again until is solved through ccsm. did You try ccsm? it worked for lot of people ...

---

### Post by BuntuFirstTimer on 2009-02-10
> **zika said:**
> I thought so, that is why I mentioned it last. but even though it doesn't matter if You did it earlier, it has to be done again until is solved through ccsm. did You try ccsm? it worked for lot of people ...

I mentioned "Did it" to you several minutes ago... which means I already did what you say. So far, I'll wait and see.

---

