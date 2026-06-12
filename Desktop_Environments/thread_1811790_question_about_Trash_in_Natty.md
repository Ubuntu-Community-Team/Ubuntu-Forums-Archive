---
title: "question about Trash in Natty"
date: 2011-07-25
forum: Desktop Environments
---

### Post by malspa on 2011-07-25
From what I gather, there's no way to remove the Trash icon from the Unity launcher, or to hide it; is this true?

I noticed that if I delete ~/.local/share/Trash, the file re-appears if I click on the Trash icon in the launcher.

---

### Post by samuelm on 2011-07-25
> **malspa said:**
> From what I gather, there's no way to remove the Trash icon from the Unity launcher, or to hide it; is this true?

I noticed that if I delete ~/.local/share/Trash, the file re-appears if I click on the Trash icon in the launcher.

Hi malspa,
Deleting ~/.local/share/Trash deletes the files in your trash and the information about those files. It does not delete the icon. [This thread]("http://askubuntu.com/questions/37776/how-to-remove-trash-icon-from-unity-launcher") says that removing the Trash icon in the sidebar is currently impossible. Also, Mark Shuttleworth's comment on [this bug]("https://bugs.launchpad.net/unity/+bug/628081") in launchpad seems to indicate that the Ubuntu devs don't plan on allowing this behavior.

samuelm

---

### Post by malspa on 2011-07-25
> **samuelm said:**
> Hi malspa,
Deleting ~/.local/share/Trash deletes the files in your trash and the information about those files. It does not delete the icon. [This thread]("http://askubuntu.com/questions/37776/how-to-remove-trash-icon-from-unity-launcher") says that removing the Trash icon in the sidebar is currently impossible. Also, Mark Shuttleworth's comment on [this bug]("https://bugs.launchpad.net/unity/+bug/628081") in launchpad seems to indicate that the Ubuntu devs don't plan on allowing this behavior.

samuelm

Thanks. I did run across the askubuntu thread earlier.

> The Trash item stays in the Launcher because it's a direct drag target
for cases when people want to delete files.

Interesting comment by Mr. Shuttleworth. Doesn't really explain why there can't be an option for the user to remove the Trash item from the launcher if so desired. Many of us don't even use the Trash.

---

### Post by mc4man on 2011-07-26
Things that aren't in the 'design' and or require new code paths can be a longshot to get altered, combine that with a user configurable option and that's a wall not likely to be scaled.
During natty dev I suggested that a gui tool to acces the unity plugin settings be provided so users didn't have to install ccsm where many could get into trouble if messing around
You can see how that went - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)

Same goes for the expo icon in the launcher - even if the plugin is disabled the icon stays
(will disappear if you only have 1 workspace.

The Applications and Files & folders icons can be removed though not thru a config option
(I remove them here, if needed I use the dash

---

### Post by horned0wl on 2011-07-26
> **samuelm said:**
> ...Also, Mark Shuttleworth's comment on [this bug]("https://bugs.launchpad.net/unity/+bug/628081") in launchpad seems to indicate that **the Ubuntu devs don't plan on allowing this behavior.** samuelm

...This is exactly the reason I'm staying with Ubuntu 10.10 until I find a reasonable distro to move to. I left Winders and Mac as home machines because they tried to force "their way or the highway" down my throat. I took the highway, and I haven't looked back. 

I used to also ***_TEACH_*** Ubuntu as a solid alternative to Windows in my CompTIA A+ pre-certification courses. Not any more.

I'd imagine, as long as Shuttleworth and the folk at Canonical maintain this similar approach to what once was an OS of flexibility and choice (I started with 6.06), I'll likely stop in my tracks, switch gears, and go another direction. Thanks for the good times, Ubuntu. I'll be back when you've come to your senses.

Cheers;
Ed Tillman
San Antonio, Texas, USA

---

