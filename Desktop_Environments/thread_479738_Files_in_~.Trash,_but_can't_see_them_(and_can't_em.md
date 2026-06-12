---
title: "Files in ~/.Trash, but can't see them (and can't empty)"
date: 2007-06-20
forum: Desktop Environments
---

### Post by jakemikey on 2007-06-20
Hi all,

I have a strange problem with my ~/.Trash folder:  There are items in ~/.Trash when I navigate there in Nautilus (and the terminal), but when I go to the trash: URI in Nautilus (or click on the trash panel applet), there's nothing there.  These aren't hidden or root-owned files, either.  Since they don't show up at the trash: URI, the "empty trash" command doesn't work.

I have the proper permissions on .Trash, etc.  Anyone have an idea on how to fix this?  Having to delete contents via the terminal is irritating.

FYI I'm running Feisty.

---

### Post by dannyboy79 on 2007-06-20
sudo rm -rf ~/.Trash/*

that will remove all files and folders within the .Trash folder that's located within the current usrs's home directory. otherwise, not sure what to tell you.

---

### Post by jakemikey on 2007-06-20
> **jakemikey said:**
>   Having to delete contents via the terminal is irritating.



Thanks for the quick reply, but I indicated that I know how to delete the files.  It's just that the Nautilus end isn't working correctly - that's what I'm trying to resolve.

---

### Post by dannyboy79 on 2007-06-20
i actually have the same issue. I have some stuff in the trash that is connected to the icon in the lower panel. it shows 2 things in it that I placed there when I had my dapper install but for some reason when I click empty trash, it says I don't have permissions per the second picture. then when I use the nautilus script to go to that trash location as root, the 2 folders are no longer there. I have ust been living with it.

[[IMG]http://img383.imageshack.us/img383/3377/trashke7.th.png[/IMG]](http://img383.imageshack.us/my.php?image=trashke7.png)

[[IMG]http://img214.imageshack.us/img214/5156/trasherrorjn3.th.png[/IMG]](http://img214.imageshack.us/my.php?image=trasherrorjn3.png)

so at least your not the only one. and no I have not filed a bug yet but maybe now 1 of us should.

---

### Post by jakemikey on 2007-06-21
I'm not sure we're experiencing the same thing, but this is definitely a bug (still unresolved):

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247)

Looks like a lot of people have been experiencing this since pre-Dapper (if not earlier).

---

### Post by BluewookieJim on 2007-07-03
> **dannyboy79 said:**
> sudo rm -rf ~/.Trash/*

that will remove all files and folders within the .Trash folder that's located within the current usrs's home directory. otherwise, not sure what to tell you.

Thanks for the tip. I had the same problem and this was just what I needed.

---

