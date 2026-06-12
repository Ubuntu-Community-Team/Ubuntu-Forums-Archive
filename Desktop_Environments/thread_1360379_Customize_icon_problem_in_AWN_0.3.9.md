---
title: "Customize icon problem in AWN 0.3.9"
date: 2009-12-20
forum: Desktop Environments
---

### Post by chaopoch on 2009-12-20
There is 'Customize Icon' option for some applications like Thunderbird, Chromium and aMule etc, but not for some applications like Vuze, Iplist and Moovida etc, so how can I change the icon for those applications that don't have 'Customize Icon' option?

Thanks.

---

### Post by chaopoch on 2009-12-20
Here are the screenshots for reference.

[ATTACH]140709[/ATTACH]

[ATTACH]140708[/ATTACH]

---

### Post by moonbeam on 2009-12-20
> **chaopoch said:**
> There is 'Customize Icon' option for some applications like Thunderbird, Chromium and aMule etc, but not for some applications like Vuze, Iplist and Moovida etc, so how can I change the icon for those applications that don't have 'Customize Icon' option?

Thanks.

0.3.9 does not allow customization of icons where it was unable to lookup a desktop file.  This is a deliberate decision with the hope of identifying problem applications.  Please report applications where this occurs on [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) .  When doing so, it would be appreciated if one bug per application was filed, and Dist/version was including in the bug report, along with the name of desktop file associated with the application in question.

At some point customization of icons will be provided in this situation but not till the desktop lookup code becomes a bit more solid.

---

### Post by chaopoch on 2009-12-20
Thanks.

> **moonbeam said:**
> 0.3.9 does not allow customization of icons where it was unable to lookup a desktop file...

All these applications have corresponding desktop files.

> **moonbeam said:**
> ...Please report applications where this occurs on [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) ...

I have reported this bug.

[https://bugs.launchpad.net/awn/+bug/498930](https://bugs.launchpad.net/awn/+bug/498930)

---

