---
title: "X not starting up"
date: 2009-10-22
forum: Desktop Environments
---

### Post by gdonwallace on 2009-10-22
Not sure if this is in the correct forum, as I am running the 9.10 beta.  I started up my laptop this morning and had all kinds of file system problems.  After about 45 minutes of running fsck multiple times, I finally get my system to boot up normally; with the exception that X-Windows does not start automatically.  I can login and start X-Windows from the command line just fine, so I am not sure what the problem is.

Any thoughts?

---

### Post by lovinglinux on 2009-10-22
[Karmic Koala Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by gdonwallace on 2009-10-22
Thanks loving, I will post the question there.

---

### Post by gdonwallace on 2009-10-29
I didn't get a chance to post my "fix" before the karmic koala thread was closed, so it will need to go here.

I think that it was a problem with the MBR.  I re-installed 9.04 and 8.04 and had the same problem.  It would not boot or allow me to start x-windows.  I finally decided to go with an older version of OpenSolaris.  It installed and ran fine...  I then re-installed 9.04 and ran the update to get to the RC and have been running fine ever since.

My thinking on why it was the MBR.  This laptop had Window$ XP on it before I decided to install Ubuntu.  Ubuntu would have modified the MBR to run the linux Kernel, but also left some of the pointer information for FAT and / or FAT32 as Ubuntu can read windows partitions and can use them.  I think that something I may have done that started this could have corrupted the MBR, not 100% certain.  OpenSolaris does not play at all with Windows.  So by installing that, it would have completely over written the MBR with its own entries.  Re-installing Ubuntu 9.04 would have done the same thing, over written an existing MBR to run Linux.

Thats my 2 cents anyway.  Not sure if that was really the problem; but I know have a running 9.10 Ubuntu....and that is all that really matters at this point.

---

### Post by acattard on 2009-10-29
Hi, I am new to this site.  How does one post? I see "new post", I do not see "post".  Thanks in advance.

T

---

### Post by lovinglinux on 2009-10-29
> **acattard said:**
> Hi, I am new to this site.  How does one post? I see "new post", I do not see "post".  Thanks in advance.

T

Welcome to the community.

If you want to create a new thread, then select the forum link in the breadcrumb at the top of the page then click the "New Thread" button.

For example:

Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > [Desktop Environments](http://ubuntuforums.org/forumdisplay.php?f=329)

Desktop Environments is this forum. you can get the list of available forums at [http://ubuntuforums.org](http://ubuntuforums.org)

If you need further assistance see [Forum Feedback & Help](http://ubuntuforums.org/forumdisplay.php?f=48).

---

