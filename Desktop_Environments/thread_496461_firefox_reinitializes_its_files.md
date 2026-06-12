---
title: "firefox reinitializes its files"
date: 2007-07-09
forum: Desktop Environments
---

### Post by kornelix on 2007-07-09
I have had this problem two times in the last 2 months or so:

I start up firefox from a desktop launcher and it displays the home page, bookmarks, etc. from the initial Ubuntu installation ("welcome to ubuntu"). My stuff has disappeared. The only files in /home/user/.mozilla/firefox are the initial installation files.

I do regular backups so I did not lose much. But the problem is scary.

I am using Ubuntu 7.04 since shortly after its release.

Evidently firefox thought it was starting up for the first time and replaced all my files with the initial versions.  

Is there any way I could be doing this?

thanks

---

### Post by Syam on 2007-07-09
If you replace your bookmarks.html file manually when firefox is running, firefox will delete it when you close it. Close firefox first, make sure that  the process is not running, then replace bookmarks file on ~/.mozilla/firefox/<your profile>/. Then start firefox again...

---

### Post by kornelix on 2007-07-09
> **Syam said:**
> If you replace your bookmarks.html file manually when firefox is running, firefox will delete it when you close it. Close firefox first, make sure that  the process is not running, then replace bookmarks file on ~/.mozilla/firefox/<your profile>/. Then start firefox again...

No, I did not do that. Something else is going wrong. Thanks for the try.

---

