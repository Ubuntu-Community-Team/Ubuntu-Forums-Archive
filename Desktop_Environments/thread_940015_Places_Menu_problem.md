---
title: "Places Menu problem"
date: 2008-10-06
forum: Desktop Environments
---

### Post by RomeoJava on 2008-10-06
Hello all,

I've got a really odd problem which I can't work out how to fix. I upgraded my system from 8.04 to 8.10 Beta by using 'update-manager -d' now, amongst other problems, whenever I try to browse a directory from the Places Menu such as Home Folder or Music, rather than opening it up in Nautilus I get the following message:

Unable to create CD/DVD
The file '/home/user/Music' is not a valid disc image.

If I load Nautilus and use the places menu from the side bar it works fine. Somehow it seems as though the default action has got screwed up but I have no idea how to restore it.. Any help would be most appreciated!

Rj

---

### Post by migah on 2008-10-08
I have almost same problem except my computer opens f-spot viewer every time I click icon in Places menu (not all icons but some of them eg. home folder).

---

### Post by RomeoJava on 2008-10-08
Yes, it isn't all the icons, for me it is all the folders such as Home, Music, Pictures, Desktop, everything above the first separator. Did this happen to you during an upgrade to 8.10?

Rj

---

### Post by migah on 2008-10-08
Yes it happened after upgrade from 8.04 to 8.10. I have also the problem with the first section in places-menu and also with mounted drives in second section.

I think there is wrong config in some configuration file that manages the menu. It should be "nautilus" but I have "f-spot view" and you have "cd\dvd creator".

Does someone know where to find "menu bar" config files?

---

### Post by migah on 2008-10-08
I solved it out!

go to terminal and open

```
gksudo gedit /home/"username"/.local/share/applications/mimeapps.list
```

you should find something like:

```
inode/directory="wrong_entry";
```

now replace that with:

```
inode/directory=nautilus.desktop;
```

and it should work :)

---

### Post by RomeoJava on 2008-10-08
Although I'm not at home to test it, it looks as if it will work, thanks! I'm now wondering how it got screwed up in the first place. If there is some bug in the Intrepid upgrade process, it would be nice to get it fixed before it is released.

Thanks again, 

Rj :)

---

### Post by RomeoJava on 2008-10-08
I've also created the Ubuntu bug report: [https://bugs.launchpad.net/ubuntu/+bug/280138](https://bugs.launchpad.net/ubuntu/+bug/280138) so that the developers can try to prevent this happening to others.

---

### Post by dr_james2k on 2008-10-21
Cheers, this helped me as well.
After upgrading to intrepid the locations under places ran as root so I just removed the sudo command from that line it works properly.
Thanks again.

---

### Post by RomeoJava on 2008-10-21
I've been monitoring the Bug in launchpad and a fix has now been issued for Nautilus. This means that people doing online upgrades from now on shouldn't have the problem. I assume however people using the old CD may still have issues. I'm also unsure if the fix actually repairs problems caused by it so manual repairs may still be necessary.

---

### Post by ScarletEmerald on 2008-11-04
Just did a network upgrade to 8.10 and ran into this problem- hope this fix helps.  Looks like the bug fix didn't make it in in time.

---

### Post by RomeoJava on 2008-11-05
Hi ScarletEmerald,

I think the patch that was introduced didn't actually work as the Ubuntu bug reports are still coming in about it. The workaround should work though. If you want more information about it, take a look here although it is quite confusing!

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

---

### Post by wakaru on 2008-11-06
Same problem here, your solution worked perfect!

How did you work this out?

---

### Post by boehr on 2009-08-13
Thanks so much, migah! Your solution fixed my problem as well - none of the items in my Places menu would open in Nautilus until I applied your fix. Thank you!

> **migah said:**
> I solved it out!

go to terminal and open

```
gksudo gedit /home/"username"/.local/share/applications/mimeapps.list
```

you should find something like:

```
inode/directory="wrong_entry";
```

now replace that with:

```
inode/directory=nautilus.desktop;
```

and it should work :)

---

