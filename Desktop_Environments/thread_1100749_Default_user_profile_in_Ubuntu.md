---
title: "Default user profile in Ubuntu"
date: 2009-03-19
forum: Desktop Environments
---

### Post by pdoma on 2009-03-19
I'm setting up a few machines with Ubuntu on a college campus and will join them to a windows domain so that users can log in with their windows network accounts.  My question is, is there a way to change the default profile the way one can in windows OS.  Lets say i want to take away a few things from the menu and change the background and so on. And make everyone that logs in to the machine have the same settings.  Second question is, is there a way to lock all those setting so that users cannot make any changes and if they save anything to their home directory it gets wiped out after they log out. Something similar to what Windows Steady State (and similar products) does?

Any help would be appreciated. Thanks.

---

### Post by pdoma on 2009-03-23
Bump. . . No system admins out there? :(

---

### Post by mcduck on 2009-03-23
Contents of /etc/skel are copied to every new user's home, so you can put all setting files for programs there to customize the default setup for new users. You could, for example, create a new user, configure the desktop as you wish, and then copy all dotfiles from that user's home into /etc/skel.

There are also two handy tools for managing user desktops, Sabayon and Pessulus. Sabayon is used for managing the user interface and program settings for user groups, while Pessulus is for locking different desktop settings.

[http://projects.gnome.org/sabayon/]("http://projects.gnome.org/sabayon/")
[http://www.linux.com/feature/62060]("http://www.linux.com/feature/62060")

I'm not sure if there's any ready solution for wiping user homes every time they log out, although the guest session in 8.10 does exactly this. You could probably use a fairly simple script to do that.

---

### Post by pdoma on 2009-04-16
mcduck,

Thanks so much this was exactly what i was looking for.

Cheers.

---

### Post by airmorris on 2009-12-10
Did this work for you? I am trying to do the same thing using Ubuntu Remix for netbooks.

---

### Post by Bakyt Niyazov on 2011-08-17
> **airmorris said:**
> Did this work for you? I am trying to do the same thing using Ubuntu Remix for netbooks.

sorry for bumping such and old thread but this is not working for me.

I coped .gconf and .gnome2 folder into /etc/skel.

New users are still getting their confs from somewhere else.

---

