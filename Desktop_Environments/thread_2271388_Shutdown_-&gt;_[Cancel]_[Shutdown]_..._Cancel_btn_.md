---
title: "Shutdown -&gt; [Cancel] [Shutdown] ... Cancel btn is the same"
date: 2015-03-29
forum: Desktop Environments
---

### Post by Unterseeboot_234 on 2015-03-29
The only Ubuntu I can run is 14.04 from a clean install of the .iso download to a formatted HDD. Then mod the install with 
```
sudo apt-get install gnome-session-fallback
```
the original classic desktop. In my pile of hardware: all other Ubuntu flavors freeze the mouse because any Ubuntu after 11.10 doesn't like PS/2 keyboard with a USB-Mouse combination. So, my question with Gnome2 Desktop pertains to Suspend, Restart, Shutdown. If I select a ending I get two buttons 'Cancel' and 'OK' in a modal dialog box. In each case 'Cancel' is the same as 'OK'. Is there something I can change in 14.04 or does Gnome2 need a fix such as purge desktop and re-install?

---

### Post by Unterseeboot_234 on 2015-03-30
This is a known bug in 14.04, which was branched and fixed in 14.10. 

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1363630](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1363630)

( Many thanks to the great folks on the mail list at GNOME )

---

### Post by Kleenux on 2015-03-31
> This is a known bug in 14.04, which was branched and fixed in 14.10.
And they didn't bother fixing this in 14.04 - which is LTS ?

Really...

And how come this is flagged "SOLVED"? Not solved at all...

---

### Post by grahammechanical on 2015-03-31
If a bug is not reported and fixed during the 26 week development period then the fix comes under the category of Stable Release Update. There are stringent conditions that have to be met before a bug fix can be pushed out to a released version of Ubuntu. And this is especially true of LTS releases because people expect stability for the whole period of the 5 year support term. Fixing one bug can introduce other bugs. It can cause bugs that have been fixed to re-appear. These are called regression bugs.

And do not forget that this is not a bug in Ubuntu but in a add-in package for Ubuntu. The developers of gnome-session-fallback and gnome-session-flashback are the ones to fix this. And then they have to get the fix past the conditions set for a Stable Release Update. And it seems that the Gnome developers are not doing that.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

You think that this is all so easy, do you not?

[http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

> [COLOR=#333333][FONT=Ubuntu Beta]Users of the official release, in contrast, expect a high degree of stability. They use their Ubuntu system for their day-to-day work, and problems they experience with it can be extremely disruptive. Many of them are less experienced with Ubuntu and with Linux, and expect a reliable system which does not require their intervention.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Stable release updates are automatically recommended to a very large number of users, and so it is critically important to treat them with great caution. Therefore, when updates are proposed, they must be accompanied by a strong rationale and present a low risk of regressions.[/FONT][/COLOR]


---

