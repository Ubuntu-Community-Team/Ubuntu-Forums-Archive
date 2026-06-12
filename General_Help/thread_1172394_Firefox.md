---
title: "Firefox"
date: 2009-05-28
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-05-28
I recently started having malfunctions with firefox. Bookmarks...I bookmark a page and when I try the link It stores a completely different site. Even though in the menu it shows the site I bookmarked...very strange. And also, wont store no history at all (I do have it set to keep all history) And 1 more thing, When i try fullscreen (not f11) fullscreen buttons in whatever player im using. It automatically goes back to normal mode, unless I quickly hold the mouse button while its going into fullscreen. Wondering if I'm the only 1 having these issues.

---

### Post by ptn107 on 2009-05-28
You can completely reinstall firefox and clear its settings by typing the following lines in a terminal (Applications -> Accessories -> Terminal) back up any bookmarks (Bookmarks -> Organize Bookmarks -> Import and Back Up) you wish to keep before doing this:
```
sudo aptitude purge firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support
rm -r ~/.mozilla/firefox/
sudo aptitude install firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support
```

---

### Post by Feelin_froggy8877 on 2009-05-28
appreciate the reply. I'll give it a shot.

---

### Post by Feelin_froggy8877 on 2009-05-28
The following packages are BROKEN:
  ubufox 
The following packages will be REMOVED:
  firefox{p} firefox-3.0{p} firefox-3.0-branding{p} 
  firefox-3.0-gnome-support{p} firefox-gnome-support{p} 
0 packages upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4309kB will be freed.
The following packages have unmet dependencies:
  ubufox: Depends: firefox but it is not installable or
                   abrowser but it is not installable or
                   firefox-3.0 but it is not installable or
                   firefox-2 which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
ubufox

Score is 119

Accept this solution? [Y/n/q/?] 

I went forward with the process, ran the second command and reinstalled ubufox, but did not clear any settings. And after the ubufox reinstall, I ran the first command to remove firefox. And ubufox came up broken again.

(edit) and I just noticed that newly bookmarked sites are pulling up random sites (different site each time I click it)

---

### Post by Feelin_froggy8877 on 2009-05-28
Alright, Not sure how all this happened, but I just ended up deleting the (.mozilla) folder and reinstalled. All good now

---

### Post by lovinglinux on 2009-05-28
You are not the only one with this problem and there are several threads about this.

There is no need to reinstall when you face this kind of problem, which is usually a consequence of a corrupted file on your Firefox profile folder. While deleting ~/.mozilla usually solves the problem, it also deletes all your Firefox settings.

If you face this problem again in the future, just delete the file *places.sqlite* inside your profile folder under ~/.mozilla/firefox/ this will delete your bookmarks, but you can restore them from automatic backups using the bookmark manager.

---

### Post by Feelin_froggy8877 on 2009-05-28
Well it did fix the bookmarking and history issues, but still having the same problem with the full-screen, as I mentioned in my first post. That's actually been going on for a while now.

---

