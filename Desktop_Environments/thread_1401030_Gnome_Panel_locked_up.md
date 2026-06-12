---
title: "Gnome Panel locked up"
date: 2010-02-07
forum: Desktop Environments
---

### Post by jonnan on 2010-02-07
I was working on configuring some shortcuts for firefox, and created a new panel, set to autohide.

Exited the panel configuration, the panel hid - and gnome locked up. Can't click anything at all on any panel or the desktop. Rebooted, and the desktop populates, I see all my icons, I cannot click *anything*. The paenels are there but never populate, no logoff options, just empty.

I can boot into a commandline as root, and I'me sure there's *some* .directory I can delete, but I can see at least four contestants, and none of them are obviously strong contenders, so I really have no desire to just start deleting folders.

Searchs haven't beared fruit on this - if I can even narrow down the likely folders it would be appreciated.

Thanks - Jonnan

---

### Post by jenaniston on 2010-02-07
> **jonnan said:**
>  . . . gnome locked up. Can't click anything at all on any panel or the desktop. Rebooted, and the desktop populates, I see all my icons, I cannot click 

I can boot into a commandline as root, and **I'me sure there's *some* .directory I can delete**, 
. . .
if I can even narrow down the likely folders it would be appreciated.


Well, why do you think that you need to*** delete*** folders ?

My gnome desktop behaves on reboots about the same . . .  desktop populates with all the icons etc., 
and desktop works for about a minute but then mouse / cursor / any open window freezes up - 
I have to unplug power cord to shutdown even.

In my case, it is the refresh rate that may need to be set / reconfigured - 
and I'm now looking at maybe xrandr utility to help me.

But as a suggestion . . . I doubt that you need to* delete* **anything**. 
I would look into maybe something similar as my desktop with *configuration* though.

Good luck.

---

### Post by jonnan on 2010-02-07
> **jenaniston said:**
> Well, why do you think that you need to*** delete*** folders ?

My gnome desktop behaves on reboots about the same . . .  desktop populates with all the icons etc., 
and desktop works for about a minute but then mouse / cursor / any open window freezes up - 
I have to unplug power cord to shutdown even.

In my case, it is the refresh rate that may need to be set / reconfigured - 
and I'm now looking at maybe xrandr utility to help me.

But as a suggestion . . . I doubt that you need to* delete* **anything**. 
I would look into maybe something similar as my desktop with *configuration* though.

Good luck.
Well, typically my experience is that if something gets misconfigured badly deleting the settings folder will allow Ubuntu to recreate default settings from scratch. Unfortunately, although I'm comfortable enough dropping to the CLI as needed for specific tasks, my skill level is insufficient to try to fix this running *solely* from the command line, and I can't access anything from the GUI - even things like ctrl-alt-del, function keys et al are locked up from the GUI as soon as it starts. 

Which leaves me playing on the CLI in the dark with no feedback from the GUI, booting, and if it doesn't work killing power on a caching file system repeatedly - not a good policy even on NTFS, but the stuff of stories told to scare geek-children on spooky nights in Linux filesystems - <G>. I've got all these pics of Movie Stars I don't wanna lose to the filesystem getting corrupted y'know - <G>.

Sooooo - yeah, barring a simple and better solution I can implement from the command line, I think killing the corrupted config folder and letting Ubuntu resurrect gnome-panel with default settings is probably the wisest course. 

Jonnan

---

### Post by jenaniston on 2010-02-08
> **jonnan said:**
>  . . . and gnome locked up. Can't click anything at all on any panel or the desktop . . . I really have no desire to just start deleting folders.

. . . if I can even narrow down the likely folders it would be appreciated.


> **jonnan said:**
>  . . . if something gets misconfigured badly deleting the settings folder will **allow Ubuntu to recreate default settings** from scratch. 

. . . yeah, barring **a simple and better solution I can implement from the command line**, 
I think killing the corrupted config folder and letting Ubuntu resurrect gnome-panel with default settings is probably the wisest course. 


Well ok . . . your second post reveals that you really want to just recreate the default settings . . .

 xrandr just might be a suggestable command line solution even to get to default settings . . . 
it is what I am trying anyhow . . . but I dunno for your case.

 **xrandr**  . . . " to set the screen size, orientation and/or reflection. It is **cool command line based tool**."
[http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html](http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html)

---

### Post by doas777 on 2010-02-08
I don't suppose you have the gnome weatherreport applet on one of your panels do you?
if so you may have run afoul of this:
[http://ubuntuforums.org/showthread.php?t=1293789](http://ubuntuforums.org/showthread.php?t=1293789)

---

### Post by jonnan on 2010-02-14
Apologies for the late AAR - work was hectic the last two weeks.

Re: recreating the defaults. Yeah, afraid so - I wasn't nearly in love enough with any particular panel configuration to care if I kept it. xrandr didn't seem to do what I needed there, so I ended up just blowing away the relevant folders and letting Ubuntu recreate them from defaults, which I main mention because that turns out to have zero effect on shortcuts placed in the applications menu.

Which is important because (for once) I was well behaved and had the good sense to put all my customized shortcuts in a folder in the application menu (admin>gksudo nautilus, various specialized FF profiles, et al) which meant I didn't have to recreate them.

So, for whoever searches and find this later, if you've created all your shortcuts using the "applications>Edit Menus" options on the menu, those will happily survive deleting .gconf, .gconfd, and .gnome2. 

Which, insofar as *this* n00b is concerned, is a feature. Even if it means Jennifer Anniston is a bigger *nix guru than I am - {G}.

Jonnan

---

