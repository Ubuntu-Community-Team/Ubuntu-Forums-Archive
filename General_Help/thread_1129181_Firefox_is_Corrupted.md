---
title: "Firefox is Corrupted"
date: 2009-04-18
forum: General Help
---

### Post by joshaman on 2009-04-18
My bookmarks are gone.  Firefox also opens up as though it's ended unexpectedly every time I open it - with the "Start New Session" or "Restore Session" window.  My entire Bookmarks toolbar, and all bookmarks are gone.  When I click "Organize Bookmarks", firefox closes.  Same thing when I click "Show all History".

Please help - what do I do?

---

### Post by tofiluk on 2009-04-18
> **joshaman said:**
> My bookmarks are gone.  Firefox also opens up as though it's ended unexpectedly every time I open it - with the "Start New Session" or "Restore Session" window.  My entire Bookmarks toolbar, and all bookmarks are gone.  When I click "Organize Bookmarks", firefox closes.  Same thing when I click "Show all History".

Please help - what do I do?

maybe uninstalling then reinstalling firefox will help

---

### Post by Wiebelhaus on 2009-04-18
> **tofiluk said:**
> maybe uninstalling then reinstalling firefox will help

IT will but the User profile that's corrupted will most likely remain , You'll need to delete before the reinstallation.

```
/home/USERNAME/.mozilla/firefox
```

It's hidden in your home directory.

---

### Post by joshaman on 2009-04-18
Wow - the problem was low disk space.  I had 1.1GB free disk space.  Does Ubuntu have a minimum amount of withheld free disk space?  

I'm just happy to get all my bookmarks back.

So I'm just wondering, what's up with the "no disk space" when I clearly have 1.1GB left?

---

### Post by justin_guerin on 2009-04-18
> **sx66gns said:**
> IT will but the User profile that's corrupted will most likely remain , You'll need to delete before the reinstallation.

```
/home/USERNAME/.mozilla/firefox
```

It's hidden in your home directory.
I'd recommend moving the ~/.mozilla/firefox folder to ~/.mozilla/firefox.old.  When you relaunch firefox, it will create a new profile (and a new ~/.mozilla/firefox/ folder).  Once that's done and Firefox is confirmed to be working, quit firefox.  You can then copy bookmarks from the firefox.old directory, and then launch firefox again, and see if it works.

Alternately, once Firefox is working, open the bookmark manager, and select the Import and Backup menu item, and try to restore from one of the backups present in firefox.old.

---

### Post by joshaman on 2009-04-18
Thanks for all the replies - but the problem was apparently no disk space?  But I had 1.1GB left...  So can someone help me figure that out?

josh

---

### Post by justin_guerin on 2009-04-18
> **joshaman said:**
> Thanks for all the replies - but the problem was apparently no disk space?  But I had 1.1GB left...  So can someone help me figure that out?

josh
How do you know the problem was due to low disk space?

Anyway, to figure out what you have remaining, open up a terminal, type the command "df -h" (without the quotes), and post the results.

---

### Post by joshaman on 2009-04-18
Well I figured it out when I tried to copy a backup .json bookmarks file to the profile folder - not enough disk space (Not even 24 KB).  So I deleted a large file and opened firefox, everything's back to normal.

I checked Disk Usage Analyzer before I deleted that large file - said I had 1.1GB free.  However, looking at the "df -h" command, it says that /dev/sda5 has only 698 MB available (which is about the size of the file I deleted).  So it looks like Disk Usage Analyzer is bogus, but it's probably due to some minor details I'm missing.

---

