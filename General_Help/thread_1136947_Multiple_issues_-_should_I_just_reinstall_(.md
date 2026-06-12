---
title: "Multiple issues - should I just reinstall? :("
date: 2009-04-25
forum: General Help
---

### Post by Xero Xenith on 2009-04-25
I'm having several problems with my Jaunty install, which I've had since alpha 5. Just wondering if a reinstall would be the best way out.

**_#1 - notifications are old-style._**
They used to be all new and swish, as Jaunty promises - but ever since around the time I installed the beta, they're back to how they were in Intrepid.

**_#2 - user switcher doesn't work at all._**
Again, this used to work perfectly. But one day, when I started my computer, I got this error:
[IMG]http://i42.tinypic.com/r1x7hi.png[/IMG]
...so I removed it. I now get the very same error when I try and add it back to the panel.

[SIZE="2"](For the tasty Google spider, the text of the error is '"User Switcher" has quit unexpectedly. If you reload a panel object, it will automatically be added back to the panel.' 'Reload' 'Don't Reload' are the buttons.) [/SIZE]

**_#3 - video tearing with nVidia drivers._**
This only really applies to Movie Player - the tearing there is pretty damn bad. There's slight tearing in SMPlayer, but nowhere near as much. Compiz effects also result in tearing...

So any suggestions for any of these would be very helpful. :)

---

### Post by joeyknuccione on 2009-04-25
1- Do:

System > Preferences > Pop-Up Notifications

Change to Ubuntu theme

2- Sorry, can't help

3- Maybe try with VLC or another media player, and compare results.

VLC is in repos, or here:

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by Mike_IronFist on 2009-04-25
> **Xero Xenith said:**
> I'm having several problems with my Jaunty install, which I've had since alpha 5. Just wondering if a reinstall would be the best way out.

**_#1 - notifications are old-style._**
They used to be all new and swish, as Jaunty promises - but ever since around the time I installed the beta, they're back to how they were in Intrepid.

**_#2 - user switcher doesn't work at all._**
Again, this used to work perfectly. But one day, when I started my computer, I got this error:
[IMG]http://i42.tinypic.com/r1x7hi.png[/IMG]
...so I removed it. I now get the very same error when I try and add it back to the panel.

[SIZE="2"](For the tasty Google spider, the text of the error is '"User Switcher" has quit unexpectedly. If you reload a panel object, it will automatically be added back to the panel.' 'Reload' 'Don't Reload' are the buttons.) [/SIZE]

**_#3 - video tearing with nVidia drivers._**
This only really applies to Movie Player - the tearing there is pretty damn bad. There's slight tearing in SMPlayer, but nowhere near as much. Compiz effects also result in tearing...

So any suggestions for any of these would be very helpful. :)

If you don't mind backing up some files and reinstalling the programs you have, then you definitely should. I had lots of issues after upgrading to the Jaunty Beta from Intrepid. But when I wiped my Jaunty partition and installed the beta via disc, I had no problems afterward. So go for it, if you don't mind the work involved in restoring your stuff.

---

### Post by Xero Xenith on 2009-04-25
> **joeyknuccione said:**
> 1- Do:

System > Preferences > Pop-Up Notifications

Change to Ubuntu theme

2- Sorry, can't help

3- Maybe try with VLC or another media player, and compare results.

VLC is in repos, or here:

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

Strangely, System > Preferences > Pop-Up Notifications doesn't exist... Should it? :S

And VLC seems pretty smooth, as smooth as SMPlayer - maybe it's the backend that only Totem (aka Movie Player) uses.

> **Mike_IronFist said:**
> If you don't mind backing up some files and reinstalling the programs you have, then you definitely should. I had lots of issues after upgrading to the Jaunty Beta from Intrepid. But when I wiped my Jaunty partition and installed the beta via disc, I had no problems afterward. So go for it, if you don't mind the work involved in restoring your stuff.

I don't really need to back up; all my data is on a separate hard drive, so the time for a reinstall wouldn't be too big an issue. That said, getting my printer to work took a little while, as did amassing my collection of programs, so I'd rather at least try and fix these before reinstalling. Thanks for the advice though :)




I'll look into the pop-up notifications, a whole menu entry being missing seems rather strange to me...

---

### Post by Xero Xenith on 2009-04-28
OK, today I decided to reinstall. So I prepared to do an AptOnCD (makes life easier)... and now I'm freaked out.

I removed KDE [using the command here]("http://www.psychocats.net/ubuntu/puregnome"), and ran "sudo apt-get autoclean" to remove extra accumulated crap. I restarted and now... everything works. I'm freaked out :P

EDIT: oh, I still have video tearing. But that's nothing.

EDIT 2 (30 Sep '09) I solved video tearing a while back. Way I did it was install compizconfig settings manager, general options -> display tab, enable "sync to vblank". Scout through the menus of the NV driver menu, enable all options related to vblank. Also make sure if using TwinView, that all linked monitors have the same resolution!

---

