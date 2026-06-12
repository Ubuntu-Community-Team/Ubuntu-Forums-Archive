---
title: "Firefox doesn't save settings"
date: 2009-05-19
forum: General Help
---

### Post by Roberto_Lapuente on 2009-05-19
I don't know if this is important but i will write anyway. I have just installed jaunty and after using it for a while and after i have configured my firefox and  i install VirtualBox, the non opensource version, and then when i open firefox my bookmarks have dissapear and my home page open on a blank page even it is set to google in the preferences. Please help

---

### Post by lovinglinux on 2009-05-19
start Firefox profile manager using this command:

```
firefox -P
```

Then select your old profile. If you have only the Default profile available in the list, then you might have a problem.

Does it save other settings? Try editing other preferences and check if they stick. If they do, then close firefox, open your home folder, hit CTRL+H to display hidden files, then open the folder .mozilla/firefox/ and find the folder of your profile. Open it, backup the file *places.sqlite*, then delete it. Start Firefox again, go to the Bookmark manager (Bookmarks >>> Organize Bookmarks), click the "Import and Backup" button, select the "Restore" list and choose the most recent backup to be restored.

---

### Post by Roberto_Lapuente on 2009-05-19
It worked, Thanks alot!

---

### Post by lovinglinux on 2009-05-19
> **Roberto_Lapuente said:**
> It worked, Thanks alot!

You are welcome. Just curious...did you find another profile or deleted the places.sqlite?

---

### Post by Roberto_Lapuente on 2009-05-19
I had to delete places.sqlite and restore my bookmarks

---

### Post by killabee44 on 2009-05-19
This is a weird problem. I installed Ubuntu on a friend's pc and had the exact same thing happen. He wasnt importing any bookmarks, just a fresh install on a new hardrive. Maybe some corruption happened somewhere along the way? I will try the fix you posted lovinglinux, thanks.

---

### Post by lovinglinux on 2009-05-19
> **killabee44 said:**
> This is a weird problem. I installed Ubuntu on a friend's pc and had the exact same thing happen. He wasnt importing any bookmarks, just a fresh install on a new hardrive. Maybe some corruption happened somewhere along the way? I will try the fix you posted lovinglinux, thanks.

Yes, I think the file gets corrupted. Don't know how or why. A lot of people have been experiencing this problem lately.

---

