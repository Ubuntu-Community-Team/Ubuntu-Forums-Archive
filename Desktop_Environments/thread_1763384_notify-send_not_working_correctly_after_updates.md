---
title: "notify-send not working correctly after updates"
date: 2011-05-20
forum: Desktop Environments
---

### Post by kevinsu22 on 2011-05-20
Hi all

I've been using Ubuntu 11.04 for a couple of weeks now, and I can't seem to get notify-send to work correctly (yes, I did install libnotify-bin)

Yesterday, I reinstalled Ubuntu 11.04 and the first thing I did was install libnotify-bin to try notify-send on a fresh install.

It worked fine after the reinstallation until I did sudo apt-get upgrade. Immediately after the updates finished, I tried notify-send again and it failed to display a notification.

No error messages, command exits correctly, no indication of anything going wrong except no notification pops up.

I'm on a lenovo thinkpad t420, 64bit ubuntu. Anyone else experiencing this?

---

### Post by Graipher on 2011-05-28
Yes, I seem to have the same problem here. I did'nt try reinstalling yet, since I need my laptop for work.

Right after the upgrade to natty it still worked fine, it must've gotten broke sometime during the last week.

What I did observe, though, is that if you flag the messages with critical urgency aka do:
notify-send -u critical "test" "test123" it still works.
Without the urgency flag or using the other two levels (low and normal) the message is not displayed.

Also pidgin/other im-clients which also use the notify-osd won't show their messages either.

What still works are the notifications when adjusting volume/brightness (if brightness adjustment worked, anyway)

Using DISPLAY=:0.0 notify-send "test" does not work either

I'm on an Asus UL50-Ag, natty 64 bit, linux-2.6.38-9-generic, compiz as compositing

I just noticed you are running the 64 bit version as well...might it be something in the 64bit version of notify-osd?

---

### Post by Graipher on 2011-05-28
I just found a solution [here]("http://ubuntuforums.org/showthread.php?t=1752997")
It seems like caffeine, an indicator to block the screensaver, also blocks libnotify, for whatever reason. If you quit caffeine it should work again! :)

---

### Post by Graipher on 2011-05-29
There's even a patch for caffeine.
just download it at the bottom of this bugreport:
[https://bugs.launchpad.net/caffeine/+bug/593649](https://bugs.launchpad.net/caffeine/+bug/593649)
and install via:
sudo patch /usr/share/pyshared/caffeine/core.py /path/to/downloaded/patch.diff
You might want to backup the existing core.py before, just in case something goes wrong.
This should remove the issue with caffeine blocking the notifications, you might have to restart caffeine to make it work, though.

---

### Post by Mike_Longbow on 2011-07-01
It seems to happen when there is any application blocking the screensaver.

It was happening to me for a while until I read this and it made me remember I often leave a virtualbox vm running on fullscreen in one of my workspaces. That was causing the problem. When I switched the vm to non fullscreen mode the notifications worked again.

Thanks for the insight.

---

