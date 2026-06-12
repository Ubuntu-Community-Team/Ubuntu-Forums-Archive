---
title: "File Associations for PDF and torrent files wrong: MIME issues"
date: 2009-08-03
forum: Desktop Environments
---

### Post by ToT)SiLeNcE( on 2009-08-03
Hello,

I am using Ubuntu Jaunty 9.04 and I am having issues with the default applications for PDF files and torrent files.

PDF files open with gimp if I double click on a downloaded file in firefox. It doesn't happen in Nautilus. The same with torrent files: They open with KTorrent instead of Transmission.

I have been able to fix this temporarily by editing /usr/share/applications/mimeinfo.cache changing the order of the .desktop entries there.

The file type associations are now correct, but they cease being after a certain while. I believe this is caused by the "update-desktop-database" script, which gets called once packages are updated in apt. update-desktop-database restores the wrong order of applications again.

Question is now: What do I have to do to fix this? Is there some way to tell "update-desktop-database" the order of applications I prefer to have?

Best regards
Bastian

---

### Post by dlmarti on 2009-08-03
system->preferences->prefered applications

---

### Post by ToT)SiLeNcE( on 2009-08-04
Sadly this doesn't help...

---

### Post by kpkeerthi on 2009-08-04
I usually change the preferred application by right-clicking the file -> Open With -> select program. Works for me.

---

### Post by ToT)SiLeNcE( on 2009-08-04
Yes this works in nautilus for me too... But firefox has its own rules it seems. Wouldn't be too big of an issue, but I have to download lots of PDFs in Firefox each day and it gets annoying...

---

### Post by kpkeerthi on 2009-08-04
> **ToT)SiLeNcE( said:**
> Yes this works in nautilus for me too... But firefox has its own rules it seems. Wouldn't be too big of an issue, but I have to download lots of PDFs in Firefox each day and it gets annoying...

I'm lost here. Firefox... what?

---

### Post by ToT)SiLeNcE( on 2009-08-04
Quoting myself from above:

"PDF files open with gimp if I double click on a downloaded file in firefox. It doesn't happen in Nautilus. The same with torrent files: They open with KTorrent instead of Transmission."

Should have put in in the thread title I guess...

---

### Post by boombox1387 on 2009-08-09
Shoot, I was hoping this thread would have a useful answer because I'm having the same problem.  Torrent files keep opening with Miro even though the system default is set to Transmission.  Similarly, all media files open with Totem instead of Banshee, which is set as my system default.

Since the system defaults are already set the way I want them to be, changing the system's preferred applications won't do anything.  Changing Firefox's preferences (Edit > Preferences > Applications tab) also doesn't seem to work.

So I guess I'll keep looking for an answer and I'll post back here if I find anything.  For the record: Jaunty x64, Firefox 3.0, Transmission from GetDeb, and Banshee compiled from source.

---

### Post by boombox1387 on 2009-08-09
Well, I found the solution to my problem, which most likely won't solve yours, but just in case:

I had been telling Firefox to point at .desktop files (in /usr/share/applications), which didn't work.  To fix this, in the Applications tab of Firefox's preferences, I told Firefox to use /usr/bin/banshee-1 and /usr/bin/transmission instead.

---

