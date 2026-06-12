---
title: "PCManFM bookmarks not being respected by other applications"
date: 2013-08-05
forum: Desktop Environments
---

### Post by IbsUser on 2013-08-05
I've just migrated from Lubuntu 12.10 to Lubuntu 13.04 and PCManFM bookmarks are not working properly.

PCManFM Bookmarks work fine when on PCManFM but if you goto to Firefox, Chromium, Leafpad, LibreOffice or any other application and try to access your Bookmarks from those applications, I can see only an old set of bookmarks. It was not a really fresh install: I keep my /home in a separate partition, so /root and /swap are the fresh ones.  The only fresh install was Lubuntu 11.10 sometime ago.

The file .gtk-bookmarks at my /home folder seems to be updated correctly from what I checked. So every bookmark changed on PCManFM is changed on that file.

More info: If I open Leafpad (it could be any other application except PCManFM), menu File>Open> and from that window I bookmark another folder, that folder won't be available on Bookmarks at PCManFM but it will be available as a bookmarked folder on the other applications (Leafpad, Chromium and so on). Finally, when modifying PCManFM bookmarks from this window, the file .gtk-bookmarks at my /home folder will not  be updated as expected, confirming the modification is not acknowledged by PCManFM but acknowledged by the other applications.

More info 2: besides the file .gtk-bookmarks at my /home folder, I noticed there's a file called bookmarks at /home/username/.config/gtk-3.0. So now I realise that my applications (Leafpad, LibreOffice, Chromium) are seeing that file inside that path and not seeing the file .gtk-bookmarks at my /home folder.

More info 3: I've just set up Lubuntu 13.04 fresh in a VM and I can see the same odd behaviour described above, so I'd say it looks like a bug on PCManFM dealing with GTK3. However I'm not a dev so I need confirmation.

Is that a bug or is it expected?
Any suggestions?

Thank you in advance for your help!

---

### Post by IbsUser on 2013-08-06
I've managed to find a workaround: 1) looks like there's an issue with GTK 3.0 and PCManFM.


2) rename /home/username/.config/gtk-3.0/bookmarks to bookmarks.old


3) make a symlink:


    ```
ln -s /home/username/.gtk-bookmarks /home/username/.config/gtk-3.0/bookmarks
```


Now everything should be fine.


You can find more info at the bug report: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1208681](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1208681)

---

### Post by Bucky Ball on 2013-08-06
Quick fix. Good news and thanks for sharing. Marking the thread 'solved' by following the link in my signature will be even more helpful. ;)

---

### Post by IbsUser on 2013-08-08
Unsolving bug/thread.

Reason: [COLOR=#000000][FONT=arial]the symlink did not survive a reboot on my laptop so the bug is alive again.

Besides the bug I listed above, there's a thread going on Lubuntu users list:
[/FONT][/COLOR][https://lists.ubuntu.com/archives/lubuntu-users/2013-August/005299.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-August/005299.html)

I'll keep following the bug in order to see how it evolves.

Thank you in advance if someone has any other advice.

---

### Post by Bucky Ball on 2013-08-08
I'm no expert, but have you tried moving it to /.bookmarks at the same path rather than /bookmarks? With the period rather than without? A symlink should survive a reboot. Once created, they stay, so something mysterious is happening.

---

### Post by IbsUser on 2013-08-12
Hi BB,

Thank you for your reply! 

I'm no expert either, but the file bookmarks at the path /home/username/.config/gtk-3.0/ is automatically created by the GTK 3 applications when they're opened for the first time.
 
So I'm not sure why creating a hidden file symlinked would work once it's automatically created based on the initial bookmarks set on fresh installation.

Anyway, I've just made a symlink as you suggested. I'll report here after next reboot.

Best regards.

---

### Post by IbsUser on 2013-08-13
Thank you for your suggestion BB! Worked like a charm.

Kind of odd that making the symlink with period worked instead of making the symlink without the symlink. I'm updating the bug to leave this tip to the devs.

For those that find this thread useful, check the command below:

```
[COLOR=#000000][FONT=Ubuntu Mono]ln -s /home/username/.gtk-bookmarks /home/username/.config/gtk-3.0/.bookmarks[/FONT][/COLOR]
```

Best regards!

---

### Post by Bucky Ball on 2013-08-13
Excellent news! Bit of a stab in the dark on my part but I think my thinking was that /bookmarks might not exist whereas /.bookmarks might. A lot's happened since then so not positive. I presume it survived the reboot. Great.

To help others, please mark thread as solved by following the link in my sig. Happy trails! ;)

---

