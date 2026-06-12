---
title: "Low-bandwidth mode"
date: 2009-02-16
forum: General Help
---

### Post by Nathan_M on 2009-02-16
Hi,
I'd like to know if anyone has any suggestions for creating a low-bandwidth mode that I can use when I'm connected through my mobile phone. I thought I could create a new user with different settings in Firefox, etc, but that doesn't solve the problem of automatic updates... I don't want to be charged £1/MB for going over my daily limit.
Presently I have a cron job running as root, which downloads updates for me, and I'd idealy like to keep this functionality, except when in my low-bandwidth mode.

---

### Post by fragos on 2009-02-16
The update manger let's you delay updates from repositories in the Software Sources Preferences Updates tab. You can even choose to only manually check for updates. In my case I use the default which to automatically check for updates daily but don't install unless maually confirmed. Those updates initiated by applications don't come under that control -- Firefox extensions in particular. If you wish fully automatic except when on a low bandwidth connection you could dual boot two like versions of Ubuntu which are configured according to low or high bandwitdth. Select the one you want at power up. This would however create a situation where the two distro versions would still need to be individually updated.

---

