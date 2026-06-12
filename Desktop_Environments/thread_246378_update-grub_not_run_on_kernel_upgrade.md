---
title: "update-grub not run on kernel upgrade"
date: 2006-08-29
forum: Desktop Environments
---

### Post by NoWhereMan on 2006-08-29
does anybody know what config file i should edit to make apt run update-grub on new kernel upgrades? 

my apt isn't doing it on its own (due to a grub installation failure -manually fixed- when i installed dapper), so I guess I should edit some file... 

I don't see anything related to this in the scripts of the .deb kernel packages

thanks :)

---

### Post by ciscosurfer on 2006-08-30
What's wrong with issuing 'sudo update-grub'?

---

### Post by NoWhereMan on 2006-08-30
nothing wrong, just that it's supposed to run automatically when the new kernel is installed (in breezy it did) and I don't understand why it shouldn't do the same now... there MUST be an option to turn that on, I guess...

---

### Post by ciscosurfer on 2006-08-30
Honestly, how often do you upgrade your kernels?

---

### Post by NoWhereMan on 2006-08-30
> **ciscosurfer said:**
> Honestly, how often do you upgrade your kernels?

that's not the point. the point is **why isn't apt doing something that it is supposed to ?** actually I just want to know where this "option" should be... 

I can't really find it anywhere (it's porbably in some oscure config file, but they're many...) and I don't understand why I should be supposed not to know it.

by the way I don't update my kernel very often, but, again, that's not the reason for what I'd like to have the answer ;)

bye

---

### Post by ciscosurfer on 2006-08-30
Have you tried (backing up your important files first, then) removing GRUB, then reinstalling GRUB?

---

### Post by NoWhereMan on 2006-08-30
> **ciscosurfer said:**
> Have you tried (backing up your important files first, then) removing GRUB, then reinstalling GRUB?

actually i didn't... but in fact *it was* installed manually... I tried reinstalling the package i guess, but it didn't work...

---

### Post by jetdog440 on 2008-06-05
I'd have to say that this problem is more than deserving of an answer.  I have very similar circumstances in a debootstrat-constructed ubuntu Hardy installaton (its very close to your standard without the pretty gui's), and for some reason a new kernel just rolled in today (2.6.24.16 -> 17), and APT didn't run update-grub for some reason.  Yes, OBVIOUSLY :confused: manually running update-grub works.

Which config file tells apt/aptitude to run grub-update after a kernel upgrade?  -> it DOES exist.  If you don't know this straight answer, don't bother flaming the issue with philosophical alternatives that just dodge the issue... you keep that attitude up and you'll end up with a 10,000 lines to run after every update.  Like no offense dude but that's against linux's philosophy of convenience through modularity.

Apologies for digging up old threads, but I'm currently having this exact issue in Hardy.

So again, if anyone knows, which config file tells apt to run update-grub after a kernel upgrade?

---

