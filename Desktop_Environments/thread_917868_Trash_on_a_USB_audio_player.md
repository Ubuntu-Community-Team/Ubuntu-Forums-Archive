---
title: "Trash on a USB audio player"
date: 2008-09-12
forum: Desktop Environments
---

### Post by GaryParr on 2008-09-12
The basic problem:

[LIST]
[*]my wife has a Sansa mp3 player
[*]our shared laptop is Ubuntu
[/LIST]

For those who don't connect the dots, what happens is simple. She switches to her account and plugs in the mp3 player. She then fires up Rhythmbox and transfers songs to/from the device. She then right-clicks the device in Rhythmbox and selects "eject" which, un-mounts the device. Sometimes she doesn't remember to do this and just unplugs the player. At this point her deleted files are still there... in the .trash-<UID> folder.

There have been many discussions about trash on removable media. To me, the best solution would simply be a config file on the root of the device that signals gnome/nautilus/whatever NOT to use a .trash folder on that specific device. After all, flash media has a limited read/write lifetime so why move to .trash if you don't want to? Well, since this is just my pipe dream, I have to find another way.

IF my wife were to use the nautilus "unmount" option, she would get prompted to "empty the trash" which, makes sense to me but not to her. Heck, she is *in* Rhythmbox, why should she close and use Nautilus to eject the device? And what's worse... most of the time she forgets to umount/eject and instead just unplugs the player.

Does anyone have any ideas how I can solve this? 

Yes... I could submit bug reports with ubuntu/nautilus/rhythmbox/gnome but I'm thinking that no one will consider this a "bug" since "emptying the trash" is a Linux thing. Unfortunately, I'm the one that has to tell my wife... "yes this worked better under Windows, but really... Linux is better because... err... uh... "  Try explaining to a non-tech savy person why more clicking and having to remember to empty the trash is a good thing.

Ideally, I would like to either a) NOT have a .trash folder on the USB drive OR b) auto-magically remove anything put into .trash on the USB device the moment it is added.

Thanks for any ideas,
-Gary

---

### Post by ffi on 2008-09-12
I always though it was a bug, not a feature, in mandriva that it would move the trash from the removable device to the trash in the home directory instead of the way ubuntu does it...

---

### Post by GaryParr on 2008-09-12
I saw plenty of discussions on that as I searched for an answer to my problem. Without going too off topic, here are what I percieve to be the pros/cons.

pro - moving to local trash keeps items off of the USB device
con - deleting large items requires transfer and thus takes time
pro - your trash stays with your account
con - your trash moves off of the device and potentially to a computer it shouldn't be on.

---

