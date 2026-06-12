---
title: "No updates are shown to install"
date: 2010-04-04
forum: Desktop Environments
---

### Post by chiwi on 2010-04-04
Hi There, I'm sorry if this question has been covered in another thread, but I really didn't know how to look for it, since there are a LOT of matches for the same keywords.

The thing is that I recall Ubuntu/gnome would prompt me a window every day or so, with the updates that could be done to the system. In that window I could see the changelog of the applications, a description...etc.

That windows does not prompt any more. To update the system, i have to go to the terminal and 'sudo apt-get upgrade' myself.

How do I turn it on again??

Thanks a lot.

Chiwi.

---

### Post by gzarkadas on 2010-04-04
Go to {System|Administration|Software Sources|Updates tab} and verify that the appropriate boxes are checked.

---

### Post by chiwi on 2010-04-04
Thanks for the reply, I set the options as the attachment show.

I'll let you know in a couple of days how it went!

Thanks again

Chiwi.

---

### Post by garvinrick4 on 2010-04-04
Here are just a few simple command line that you can use if you want.
Always make sure your cache is cleaned if you want to fetch new packages or
you just get the ones saved in the cache.
 I threw in a couple I use like opening CD with my laptop and finding drivers and
cards. If they are of value keep them if not someone else might use them.


To clean out your cache of packages so you can fetch fresh ones:

sudo apt-get clean

To upgrade a package.

sudo apt-get install --reinstall (package name)  no quotes

To check and see if package is installed, version, depends and what it does.

aptitude show (package name) without quotes.

Update and upgrade:

sudo apt-get update && sudo apt-get upgrade

Cards and drivers:

lspci -v | less

Open CD tray:

sudo eject /dev/scd0

---

### Post by chiwi on 2010-04-07
gzarkadas,
unfortunately, the fix didn't work. I still don't get any window asking to update new items. The setting you told me to check has been set for a couple of days, and there are new updates to install:

```

chiwi@Brunette:~$ sudo apt-get upgrade
[sudo] password for chiwi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg-extra
  chromium-codecs-ffmpeg-nonfree libdvdnav4 tzdata
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.9MB of archives.
After this operation, 139kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

any ideas ? 

Thank you

chiwi.

---

### Post by mcduck on 2010-04-07
> **chiwi said:**
> Thanks for the reply, I set the options as the attachment show.

I'll let you know in a couple of days how it went!

Thanks again

Chiwi.

Keep in mind that the Update Manager is set to only open automatically once every seven days (if there are updates available). If you update manually, the counter is reset.

So you'll only see the Update Manager popping open automatically if A) there are updates available and B) you haven't updated in the last seven days.

Security updates are of course an exception and are handled immediately.

The interval how often the Update Manager is allowed to pop up automatically can be set through gconf-editor, and it's also possible to switch back to the old behavior (showing an icon in the Notification Area immediately when there are updates available, and never opening the Update Manager window itself automatically).

---

### Post by wojox on 2010-04-07
This fixed it for me:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

### Post by chiwi on 2010-04-07
> **wojox said:**
> This fixed it for me:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

What does that do? What I understand from that line, is that you are disabling the update_notifier, which is exactly the opposite I want.

I've just checked in gconf-tool, and it's set to true.

MCDUCK, do you know how to set that interval ? I can look it up tomorrow in google though, i'm about to go to sleep :)

THanks again

Chiwi.

---

### Post by mcduck on 2010-04-08
> **chiwi said:**
> What does that do? What I understand from that line, is that you are disabling the update_notifier, which is exactly the opposite I want.

I've just checked in gconf-tool, and it's set to true.

MCDUCK, do you know how to set that interval ? I can look it up tomorrow in google though, i'm about to go to sleep :)

THanks again

Chiwi.

Tthe settings are in gconf. *apps/update_notifier/regular_auto_launch_interval* sets the interval, and disabling the *apps/update_notifier/auto_launch* changes the update Notifier back to the old behaviour (icon in notification area instead of a window popping up).

---

