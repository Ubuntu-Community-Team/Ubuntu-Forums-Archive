---
title: "thunderbird"
date: 2009-07-04
forum: Desktop Environments
---

### Post by johnh10000 on 2009-07-04
After my diasterous transfer of tux to a bigger harddisk.  Left on the old hd, still in box at the mo, is there anyway I copy my thunderbird mailboxes over intact?

second when I remove he old hd, is it just update grub?

---

### Post by SteveDee on 2009-07-04
> **johnh10000 said:**
> After my diasterous transfer of tux to a bigger harddisk.  Left on the old hd, still in box at the mo, is there anyway I copy my thunderbird mailboxes over intact?

second when I remove he old hd, is it just update grub?

You should be able to access your mail folders by running Thunderbird Profile manager:-
 - Run Profile manager using /usr/lib/thunderbird/thunderbird -P
 - Give profile a name (e.g. “yourName”)
 - Browse to select the old profile folder.

As for Grub, you will need to ensure the info in /boot/grub/menu.lst references the correct drive. This link might help; [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

---

### Post by johnh10000 on 2009-07-04
> **SteveDee said:**
> You should be able to access your mail folders by running Thunderbird Profile manager:-
 - Run Profile manager using /usr/lib/thunderbird/thunderbird -P
 - Give profile a name (e.g. “yourName”)
 - Browse to select the old profile folder.

As for Grub, you will need to ensure the info in /boot/grub/menu.lst references the correct drive. This link might help; [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

Thanks gang, thunderbird mailboxes hang out at ~/.mozillar-thunderbird

webmin delt with grub for me.

only thing to do now, is break it again  ........

thanks  for all the help

---

