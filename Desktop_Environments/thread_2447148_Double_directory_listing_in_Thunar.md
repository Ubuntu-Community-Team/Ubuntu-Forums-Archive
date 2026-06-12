---
title: "Double directory listing in Thunar"
date: 2020-07-13
forum: Desktop Environments
---

### Post by WB0HYQ on 2020-07-13
XFCE Desktop running over 18.04LTS

Thunar began doing this yesterday. When it is started, two listings are shown for "File System". If I click on the top one, I get "Loading", and it stays there forever. There is another directory shown by the same name at the bottom of the left panel. It behaves normally and I can browse through it just fine.

Anyone know why this is happening and what can be done to make it right? I've rebooted several times as well as started Thunar from a terminal. Still get the same results.

Here's a screenshot:

[IMG]https://intellisigsys.net/pics/Screenshot_2020-07-13_12-34-01[/IMG]

Bill

---

### Post by ajgreeny on 2020-07-13
Unfortunately there is not much that can be done to help you as 14.04 is now out of support, and has been so for over 3 years for the specific Xubuntu parts of the OS, and over a year for the main Ubuntu packages.
As a result it is a big security risk to continue using that version; the repositories have been moved and even if you do point the updater to the new EOL repos, the packages will still all be over a year old.

Please update your system, using a clean install, not an upgrade which is no longer a practical proposition from 14.04, to a fully supported version; I suggest Xubuntu-20.04 which has 3 years of support, then come back here again if you still have any problems.

Sorry if this is not what you wanted to hear, but there really is no other sensible alternative.

---

### Post by WB0HYQ on 2020-07-13
I have no explanation as to why I put down I was using 14.04. Age related, perhaps? I am running Bionic Beaver **18.04LTS.** Sorry about that. Actually, I'd love to upgrade to 20.04, so I should probably do that first.

Bill

---

### Post by ajgreeny on 2020-07-14
> **WB0HYQ said:**
> I have no explanation as to why I put down I was using 14.04. Age related, perhaps? I am running Bionic Beaver **18.04LTS.** Sorry about that. Actually, I'd love to upgrade to 20.04, so I should probably do that first.

Bill
Well, Xubuntu 18.04 still has 9 months of support, so there's no rush, but I've found 20.04 to be stable and a good version so far.

As to your problem of the double entries for Filesystem in thunar, I have a suspicion that I used to see that as well, but I simply ignored it.  However, I haven't booted to 18.04 for a very long time now, and have now overwritten that partition with another completely different distro just to see what I think of it; Arcolinux, very good it is too!

Try renaming the hidden ~/.config/Thunar folder in your home and then restart the file manager to see if the zombie entry disappears, assuming one is a zombie.

---

### Post by WB0HYQ on 2020-07-14
I tend to be cautious about upgrading to a new version. Usually I wait until it shows up in Software Updater as the familiar "there is a newer version available". Then I upgrade. Should be happening quite soon I'm thinking.

Renaming the directory didn't work. I killed the Thunar daemon, then renamed the directory and restarted. The two entries were still there. I think I'll do as you did and simply ignore it. What is strange is the Properties:

General Tab: "File System"  <-- not editable // Kind, Modified, Access are all "unknown" // Size = 0 bytes
Emblems Tab: is the normal stuff
Permissions Tab: Owner: Root  //  Access: None  // Group: Root  //  Access: None // Others: None

None of the dropdowns/fields are editable.  At the Terminal, I cannot find any listing for "File System". It simply does not exist. On the screenshot, note that the icons are different. The top one is showing a simple text file icon, while the lower one is showing a mount point.

Perhaps when I upgrade it will go away.

Bill

---

### Post by WB0HYQ on 2020-07-15
Since I upgraded to 19.10, this problem has apparently been fixed. I see today that 20.04 is now available. I'm going to run 19.10 for a while, then upgrade again.

Thanks for the help.

Bill

---

### Post by ajgreeny on 2020-07-15
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

