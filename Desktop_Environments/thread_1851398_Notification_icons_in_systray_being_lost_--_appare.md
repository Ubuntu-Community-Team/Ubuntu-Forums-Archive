---
title: "Notification icons in systray being lost -- apparently deliberately!"
date: 2011-09-28
forum: Desktop Environments
---

### Post by Paddy Landau on 2011-09-28
Here is the situation as I understand it:[INDENT] The notification icons in the systray have been turned off except where explicitly white-listed in 11.04. That means, for example, Skype, HP systray, TrueCrypt, SpiderOak, and so forth will become either hard to use or actually unusable unless explicitly whitelisted.

The whitelisting process is not published, and people have to find it out for themselves (here is a [good tutorial]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html")).
[/INDENT]Alas, if that weren't bad enough, from 11.10 or 12.04 (the next LTS version), *the systray will be removed altogether*. Programs that haven't been converted to use the new notification methods will fail to work!

Does Canonical really expect all programmers to fall in line with Ubuntu? If you pay attention to the sorts of bugs that cause people to try Ubuntu and then leave, this is definitely one of them.

This has been [raised as a bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/779210"). Unbelievably, it has been marked as invalid!

Please tell me my understanding is wrong and that programs such as HP Systray and TrueCrypt will be supported from 12.04!

---

### Post by Frogs Hair on 2011-09-28
Hi Paddy ,

I have used the method at the link and I have installed the dconf editor , which displays my white list I was wondering now that I can view the list could I add items to the list ?

---

### Post by Krytarik on 2011-09-28
> **Frogs Hair said:**
> I have used the method at the link and I have installed the dconf editor , which displays my white list I was wondering now that I can view the list could I add items to the list ?
Sure, the same way as used to edit values in "gconf-editor".
Obviously, you need to know the names to add.

---

### Post by Paddy Landau on 2011-09-28
> **Frogs Hair said:**
> I have used the method at the link and I have installed the dconf editor , which displays my white list I was wondering now that I can view the list could I add items to the list ?
Or, you could just change it to
[FONT=Fixedsys] ['all'][/FONT]
in order to whitelist everything.

But that misses the point: when blacklisting by default, you force programs to fail to work properly. It should whitelist everything by default.

---

### Post by Krytarik on 2011-09-28
> **Paddy Landau said:**
> Or, you could just change it to
[FONT=Fixedsys] ['all'][/FONT]
in order to whitelist everything.
Personally, I wouldn't do that, as it has been reported that this can result in showing some tray icons/indicators twice.

---

### Post by Frogs Hair on 2011-09-28
As long as I know I can add that's great . I won't be using 11.04 much longer and have nothing more I want to add to the panel . We shall see what changes in 11.10 .

---

### Post by nilarimogard on 2011-09-30
Well, at least all Qt applications like Skype, etc. will have an appindicator by default (automatically converted).

---

