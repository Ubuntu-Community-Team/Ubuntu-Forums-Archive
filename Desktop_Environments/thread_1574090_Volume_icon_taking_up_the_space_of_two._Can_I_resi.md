---
title: "Volume icon taking up the space of two. Can I resize it down? (image posted)"
date: 2010-09-13
forum: Desktop Environments
---

### Post by finny388 on 2010-09-13
Ubuntu 10.04.1

I was just tidying up my panel when I notice the Volume icon is taking up the space of two icons:

[IMG]http://img535.imageshack.us/img535/3483/screenshot1bvk.png[/IMG]

I can right-click and Move it to the left or right

[IMG]http://img826.imageshack.us/img826/8486/screenshot2wc.png[/IMG]

why is it taking up this much room?

---

### Post by finny388 on 2010-09-13
When I opened Transmission it filled in the space.

[IMG]http://img411.imageshack.us/img411/4359/screenshot3ll.png[/IMG]

Transmission and Volume both have Move in their right click

Tomboy and wicd don't.

That must have something to do with it.

hmm

---

### Post by kerry_s on 2010-09-13
was this a clean install or upgrade?

---

### Post by finny388 on 2010-09-14
I have root on sda1
and home on sdb1

so it was a clean install to root but many settings were retained by not wiping sdb1.

---

### Post by kerry_s on 2010-09-14
there you go, it's changed.

open your file manager
press ctrl+h
go to .gconf-> apps
delete the folder "panel"
log out & back in

this will reset your panel, you should then have the new settings.

there are sometimes a lot of changes between releases, keeping your old home on a non rolling release linux is a bad idea. it is better you just create a extra partition to save things.

---

### Post by finny388 on 2010-09-14
thank you Kerry

man oh man, just when I thought I'd found a good setup to preserve my files while clean installing.


1. Resetting my panel - will I lose my applets and icon shortcuts etc?

2. Using a separate partition
[LIST]
[*]how is that laid out?
[*]       all the document folders (I want to preserve) are mixed in with all the hidden files (that I want to 'clean install')
[*]       or I guess I could back up document folders and just restore them after the clean install. hmm.
[/LIST]

---

### Post by kerry_s on 2010-09-14
1. yes, you'll have to add & drag them back.

2. i think you can just use your current home partition. when your installing just select "do not use" & make sure the "format" is not checked. that way your can keep your stuff & just delete what ever is not yours in that folder. it will show in nautilus side panel & you just click on it to mount & use.

save it for next time though, if your install is mostly working, just keep it. if you do have a problem with a program you can look in there for the settings folder/file & just delete it so it can create a new 1.

> man oh man, just when I thought I'd found a good setup to preserve my files while clean installing.

on a rolling release that would work out great, but ubuntu go's like 6 months between releases, linux moves fast by then you can be several versions behind the current, i'm sure you realize how fast things get updated.

---

