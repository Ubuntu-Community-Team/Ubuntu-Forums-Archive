---
title: "About Hidden File [Window &amp; Ubuntu]"
date: 2008-09-22
forum: Desktop Environments
---

### Post by Likesh on 2008-09-22
Is that possible that ubuntu can create a hidden file that also can hidden in window?

and if i have 2 SD card, 1 have hidden data (for window) and 1 is empty,i insert 2 sd card and copy the hidden data to the empty SD card. but the copy one won't be hidden(for window).

is that any solution for that?hope you all can help, thanks lot:)

---

### Post by vanadium on 2008-09-22
Linux uses its own file system, but can also read the Windows file system. Windows, though, can only read its own file system. That could explain a behavour like you explain. However, it is unlikely that you would have formatted one of your cards in a linux file system.

Another possibility (more likely) is that the file system of one of the cards is damaged by not properly removing the cards. In that case, the file system of the card needs to be checked and repaired, or the card must be formatted again.

To see how the cards are formatted, open an terminal, insert the disk and run the command
```

sudo blkid

```
(you will need to provide your root user password. Remove the disk safely (right-click icon on desktop, select 'Unmount' before fysically removing the card), put in the other, wait a little bit and issue the same command. The "TYPE=..." tells you about the file system.

---

