---
title: "Gnome apps don't obey umask"
date: 2008-05-27
forum: Desktop Environments
---

### Post by laliebijard on 2008-05-27
Hello.

I'd like to set up a folder shared by several users (I want newly created subdirs to have permissions rwxrwxr-x). So I put umask 002 into /etc/profile and reboot. Command mkdir works well in shell, but folders created by Nautilus (or other Gnome programs) have permissions rwxr-xr-x.

I found some info about bug in gnome-vfs [http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249) which should have been fixed.

Am I doing anything wrong? Can anyone reproduce or disconfirm this behaviour?

I have ubuntu 8.04.

---

### Post by wattana on 2008-06-25
Hi man.

I have the same issue in my office. I've installed Ubuntu migrating from fedora due the promise of stability...

It's true, but the nautilus umask ignore "feature" is terrible... I have to manually change all permissions...

I've created a bug report in bugzilla, but no one have taked it yet.. or marked as confirmed... or nothing...

It's a nasty bug if you use gnome in your office with a few users...

Hope someone can fix it...

Sorry about my bad english...

Regards!

---

### Post by ranamalo on 2008-09-12
I had the same problem.  I resolved it by creating the file .gnomerc in my home directory with the appropriate umask command.  I wanted to have nautilus create directories with the permissions owner=rwx group=rwx and others=rx.  So what I did was:
cd /home/user
vi .gnomerc

then in this file I put:
umask 002

save that and restart the session.  I believe all GUI programs should now use the umask 002.  Hope this is helpful to someone

---

