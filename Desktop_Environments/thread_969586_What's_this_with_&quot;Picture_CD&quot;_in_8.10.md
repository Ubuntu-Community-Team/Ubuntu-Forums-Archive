---
title: "What's this with &quot;Picture CD&quot; in 8.10?"
date: 2008-11-03
forum: Desktop Environments
---

### Post by SamNSane on 2008-11-03
I don't remember seeing this before 8.10.

Every time I mount a drive of ANY kind to these systems I get told that I have inserted a Picture CD and asking if I'd like to open Brasero or CD Creator. When I look at the contents of my Modular Bay drive or the USB connected HD on this system the top of the right pane in Nautilus tells me that I'm looking at a Picture CD, and it's got a button there for launching Brasero.

Huh? How do I get rid of this somewhat annoying behavior? I hated it in Windows, too. It was easy to turn off in Vista. The easiest way to get rid of it in WinXP was to install TweakUI and turn it off from within the Explorer settings.

This automatic recognition of stuff is a little exasperating. I already know that I stuck something in the danged machine. And I usually know what it was I stuck in there. If that's the case, I don't wish to be told about it -- especially if the machine is WRONG! It ain't a picture CD. It doesn't have a single freakin' picture on it!

Somebody clue a newbie in, please! I'm sure it's got to be easy, but I'm looking in all the wrong places.

---

### Post by crash0 on 2008-11-03
i have a similar problem: i have an encrypted folder, and when i mount it, it says that it's a picture CD and offers to use f-spot (or whatever the name is) to open it.

i set "do nothing" in nautilus for all types of media, from audio discs to blu-rays, but nothing changed.

---

### Post by ad_267 on 2008-11-03
Go to System - Preference - Removable Drives and Media and make sure everything is disabled there. Then in the file manager go to Edit - Preferences - Media and select "Do Nothing" for everything you want. Or just tick "Never prompt or start programs on media insertion."

---

### Post by SamNSane on 2008-11-03
> **crash0 said:**
> i have a similar problem: i have an encrypted folder, and when i mount it, it says that it's a picture CD and offers to use f-spot (or whatever the name is) to open it.

i set "do nothing" in nautilus for all types of media, from audio discs to blu-rays, but nothing changed.

Yeah, f-spot was the first thing I uninstalled -- and then the system found something else to use instead.

I find that I overlooked some of the settings in Nautilus. Don't know how I missed that whole Media tab -- except I don't think of an internal modular drive as "media" -- but whatever. This time around I went onto the Media tab, and I told it to do NOTHING for EVERYTHING, and then I checked the Never Prompt box on the Media tab. We'll see how that works. I'll bet it works.

And I didn't miss it because I was a newbie. I missed it because I was in a hurry and being dumb.

I hope it works better for me than it did for you.

;)

---

### Post by SamNSane on 2008-11-03
> **ad_267 said:**
> Go to System - Preference - Removable Drives and Media and make sure everything is disabled there. Then in the file manager go to Edit - Preferences - Media and select "Do Nothing" for everything you want. Or just tick "Never prompt or start programs on media insertion."

I'm not finding that location you mention under System | Preferences, but I did find the Media tab in Nautilus Preferences. I hope that will do the trick. Thanks.

---

### Post by Reg67 on 2008-11-04
Everything is disabled in "Removable Drives and Media" and in nautilus I've ticked "Never Prompt or Start Programs upon media insertion".

It is still giving me the message about a Picture CD for a remote drive mounted with sshfs.

---

### Post by Reg67 on 2008-11-04
remounted and the message has gone :).

---

### Post by SamNSane on 2008-11-04
Well, it doesn't work for me. I applied "no action" to all settings, enabled the "no prompt" setting, unmounted, remounted -- system doesn't give a dang. It still insists that the blooming usb drive and the modular drive (both ext3) are picture CDs.

This is a minor glitch as glitches go, but it IS annoying.

---

### Post by ad_267 on 2008-11-04
> **SamNSane said:**
> Well, it doesn't work for me. I applied "no action" to all settings, enabled the "no prompt" setting, unmounted, remounted -- system doesn't give a dang. It still insists that the blooming usb drive and the modular drive (both ext3) are picture CDs.

This is a minor glitch as glitches go, but it IS annoying.

You could file a bug on launchpad against nautilus then. It shouldn't still be doing that. Also it really should realise it's not a picture CD.

---

### Post by SamNSane on 2008-11-04
> **ad_267 said:**
> You could file a bug on launchpad against nautilus then. It shouldn't still be doing that. Also it really should realise it's not a picture CD.

I'll look into it. If there isn't something filed already, I'll file a bug report.

---

### Post by SamNSane on 2008-11-05
There's already a bug report filed.

[https://bugs.launchpad.net/bugs/258936](https://bugs.launchpad.net/bugs/258936)

When I looked up the bug report I learned that this is caused by having a folder named "Pictures" off the root of the drive / partition. So, despite the fact that Nautilus was looking at what was obviously a HD file system, it was calling it a Picture CD.

For the time being the workaround, obviously, is to not have a Pictures folder off the root of a drive. (Once you rename the folder, just umount the drive, and then mount it again.)

---

