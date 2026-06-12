---
title: "Changing to the the &quot;older&quot; volume display"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by vertigo1980 on 2007-04-20
hi all,

i installed feisty today, and while setting up my programs, installing stuff etc i changed my volume, and i got the "older" volume display:

[img]http://bp2.blogger.com/_JvDB-G93rcY/Rcu_GeNM8qI/AAAAAAAAABI/yLap7Z1-d4I/s320/volume.png[/img]

and i liked it, but remembered they took changed it because apparently it looked too much like mac os x. then i finished setting things up, configured beryl i think, may have edited xorg.conf and a few other things. i rebooted, and i got the one that we are "supposed" to get:

[img]http://bp1.blogger.com/_JvDB-G93rcY/RdtN4ONM8uI/AAAAAAAAAB4/Z8F1UwAgqhw/s320/vol_new1.png[/img]

i really like the first one, anybody know of a way to get it back?

thanks! :D

---

### Post by sumgi on 2007-04-21
I have a large speaker kind of like the one on top but in 6.10 the volume meter was just a little bar, not some huge icon. How do I get the little volume meter bar back?

---

### Post by SimonJW on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/control-center/+bug/99752](https://launchpad.net/ubuntu/+source/control-center/+bug/99752) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**sumgi** - if you turn off "desktop effects" (compiz) you will have the old style display again. I have no idea how to change back to the old one *without* turning off dekstop effects, but would REALLY like to know, as this newer display freezes my computer when using totem ( bug filed at this link [**here**]("https://launchpad.net/ubuntu/+source/control-center/+bug/99752") - does anyone else experience this?)

**vertigo1980** - I have, as far as I know, an entirely up to date version of feisty, but have only ever seen the first image, so I'm afraid I can't help you. How far back in the development cycle did the second version first appear? I guess if it's very recent, it might not have hit my local repo yet...

---

### Post by sumgi on 2007-04-21
> **SimonJW said:**
> **This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/control-center/+bug/99752](https://launchpad.net/ubuntu/+source/control-center/+bug/99752) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**sumgi** - if you turn off "desktop effects" (compiz) you will have the old style display again. I have no idea how to change back to the old one *without* turning off dekstop effects, but would REALLY like to know, as this newer display freezes my computer when using totem ( bug filed at this link [**here**]("https://launchpad.net/ubuntu/+source/control-center/+bug/99752") - does anyone else experience this?)

**vertigo1980** - I have, as far as I know, an entirely up to date version of feisty, but have only ever seen the first image, so I'm afraid I can't help you. How far back in the development cycle did the second version first appear? I guess if it's very recent, it might not have hit my local repo yet...

You are correct, it does change back but only after a reboot. I had temporarily enabled desktop effects to try them out but didn't like them so I guess that's when it changed. Thanks for your help!

---

### Post by vertigo1980 on 2007-04-21
> vertigo1980 - I have, as far as I know, an entirely up to date version of feisty, but have only ever seen the first image, so I'm afraid I can't help you. How far back in the development cycle did the second version first appear? I guess if it's very recent, it might not have hit my local repo yet...

it is a new install of feisty final. i had the same one (the 2nd one) with the feisty beta too. i'm running beryl, but i remember the 2nd one was still being used when i was using compiz.

---

### Post by StevenYap on 2007-04-23
The graphic used for the sound volume pop-up is dependent on the icon theme that's in effect. The former graphic can be had with the Human icons while the latter is available with the Tango and Tangerine icons.

---

### Post by vertigo1980 on 2007-04-23
thanks stevenyap, you're absolutely right :)

guess you already know my next question, but is it possible to change the icon theme to tango and keep the human notification?

---

### Post by StevenYap on 2007-04-23
I don't think the icon theme affects the notification bubbles. This is the notification bubble I get with the Human control and the Tango icons. Is this what you wanted to keep?

---

### Post by vertigo1980 on 2007-04-23
sorry about that, bad choice of words in my last post. i meant the volume notifications, as in my first post :)

---

### Post by benjou on 2007-04-23
I have the same bug as simonJW, namely 15 30s freeze of either totem or rhythmbox, with beryl as a composite manager

Does anybody know how to get rid of that?

---

### Post by StevenYap on 2007-05-02
> **vertigo1980 said:**
> sorry about that, bad choice of words in my last post. i meant the volume notifications, as in my first post :)

Sorry for taking so long to respond to you. The Tango volume icons are[INDENT]/usr/share/icons/Tango/scalable/status/audio-volume-high.svg
/usr/share/icons/Tango/scalable/status/audio-volume-low.svg
/usr/share/icons/Tango/scalable/status/audio-volume-medium.svg
/usr/share/icons/Tango/scalable/status/audio-volume-muted.svg[/INDENT]There are also PNG versions of these 4 files in the directories 16x16, 22x22, 24x24, and 32x32 under the directory /usr/share/icons/Tango/.

I think if these files are removed/renamed, then GNOME will default back to the Mac OS X like icon. The only other files whose names start with "audio-volume" are in the directories /usr/share/icons/gnome and /usr/share/icons/Human, and none of them looks like the Mac OS X like icon.

Hope that helps.

---

### Post by vertigo1980 on 2007-05-03
thanks for that StevenYap, i'll try it out :D

---

### Post by apoth on 2007-05-03
I've had that effect on the volume recently but it's gone away and now I've got the crappy graphics without the transparency and the rounded corners - any idea how I get that back? I've tried enabling and disabling desktop effects but that didn't change anything.

---

### Post by rico2k_uk on 2008-05-27
bump this one - anyone figured out how to get the small version of the volume levels with compfiz running?

---

