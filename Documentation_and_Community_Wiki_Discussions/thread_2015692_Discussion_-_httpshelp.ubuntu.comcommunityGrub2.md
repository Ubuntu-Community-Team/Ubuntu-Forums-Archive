---
title: "Discussion - https://help.ubuntu.com/community/Grub2"
date: 2012-07-03
forum: Documentation and Community Wiki Discussions
---

### Post by drs305 on 2012-07-03
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") and all it's associated sub-pages.

Support threads/questions should be posted in normal forums.

Thank you.
__________________

---

### Post by twipley on 2012-10-26
Wiki page is nice, however I think it could benefit from the following improvements:

It should be specified password encryption in somes cases is unjustified, as whenever "sudo update-grub" is ran while a plaintext password is present in the "/etc/grub.d/40_custom" file, the "grub.cfg" file is rendered unreadable to standard users, which by nature should be lacking administrative passwords. (If the password is encrypted, then the file remains readable by anyone.)

Editing through the "40_custom file" is to be preferred, as that way the system continues both to be bootable and to be protected from single-user selection even after release upgrades and various system updates. In other words, it is made future-proof that way, more unbreakable than otherwise.

The sole thing that might be left to be mentioned would then be a more-comprehensive method for preventing standard users to fiddle with the Grub terminal, edit its command lines, or enter the much-powerful recovery mode. Such a method seem hard to translate in practice, such as exemplified out of: [http://ubuntuforums.org/showthread.php?t=2076594](http://ubuntuforums.org/showthread.php?t=2076594)

---

### Post by darekch on 2013-05-25
Please add to the wiki, to grub2 iso examples, menu entry for memtest86+
```

menuentry "Memory test (memtest86+ 4.20)" {
    linux16 /boot/isos/memtest86+-4.20.bin
}

```

I had to do that cause I don't know how I can reach memtest86 which is alread included in ubuntu's iso ([http://ubuntuforums.org/showthread.php?t=2148447&p=12662944](http://ubuntuforums.org/showthread.php?t=2148447&p=12662944))

---

