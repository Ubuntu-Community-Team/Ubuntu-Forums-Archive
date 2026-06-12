---
title: "Xorg.conf configuration resets to default on every boot"
date: 2014-10-04
forum: Desktop Environments
---

### Post by Sami Lehtinen on 2014-10-04
Hi,

I'm wondering why my compex xorg configuration is lost on every boot.

All it says is:
```

 Section "Device"
    Identifier "Default Card 0"
    BusID "PCI:0@0:2:0"
EndSection

```

My multiseat configuration as well as two displays on secondary dispaly adapter aren't working at all. I'm using XFCE and lightdm. Everything was working perfectly before last kernel & i915 driver update. Now I have replaced i915 driver with xserver-org-video-intel, but it didn't help at all. Any clues what do do? I have now to of my four screens totally dead. And logs do not give me any indication what's actually wrong or causing the problem.

I used display settings to get the intel primary adapter to work with two screens on fhd resolution and that's now all good. But what I should do to get the secondary adapter to work, as it did earlier? (Two additional x screens, one for TV and one for chat & notes screen).

 - Thank you

Best regards,
[Sami Lehtinen]("http://www.sami-lehtinen.net")

---

### Post by claracc on 2014-10-05
What way are you trying to generate a xorg.conf file?.

The right way is addressed in this guide: [https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto) , xorg.conf.d paragraph.

Also, I have encountered this bug report: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489) which could be related to your problem?

---

### Post by Sami Lehtinen on 2014-10-08
Yes, the bug mentioned is exactly what I'm expering. I upgraded everything from -proposed because -updates didn't do it. Currently the situation is bit funny, no, it doesn't reset xorg.conf to default config. Instead xorg.conf is deleted on every boot. So so far it isn't yet working as expected.

---

### Post by claracc on 2014-10-11
As you can read in the bug report, the reponsible software package has been fixed:

"This bug was fixed in the package ubuntu-drivers-common - 1:0.2.91.7", so I supposse you will receive the bug fix update soon if not yet.

---

### Post by Sami Lehtinen on 2014-10-12
I've seen so many failed bug fix attempts, that I don't believe it before I see it. Btw. For some strage reason now the display settings IS showing four monitors, but image on those is totally garbled and I can't select right settings. Xorg.conf is still being deleted on every boot. Let's see how long it takes before this gets fixed or there's some kind of work-a-round or new way to get the same stuff done. There's clearly some progress, but it's not working yet.

---

### Post by Sami Lehtinen on 2014-10-18
Just checked, no fix yet. As I assumed. Well, actually this is pretty good. I can do something more meaningful when I can't watch documentaries or movies. ;) Let's see how many months it takes, before real fix is out.

---

