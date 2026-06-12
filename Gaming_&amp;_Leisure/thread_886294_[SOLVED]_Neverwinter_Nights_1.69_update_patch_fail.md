---
title: "[SOLVED] Neverwinter Nights 1.69 update patch failure"
date: 2008-08-11
forum: Gaming &amp; Leisure
---

### Post by WSmart on 2008-08-11
gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

After downloading the patch to end all patches, 1.69, for the Linux port of the Neverwinter Nights game off the Bioware website, I find that I can't extract it.  I get the above error when I try and access the download with the archive manager.  Is it just me?

Downloaded it twice and got the same thing both times.

Posted to the Bioware forum thread which introduces the new patch, but it looks like they have their hands full.  That was a couple weeks ago, and no reponse-though maybe they've fixed it.

Thanks!  Bill

Did you know you can use the alternate CD to upgrade Ubuntu?  Help save the home office bandwidth and do your upgrades via Bit torrent.

---

### Post by Perfect Storm on 2008-08-11
wget it via the terminal should fix the problem.

```
cd <distination>
wget <web adresse + file>
```

---

### Post by Ng Oon-Ee on 2008-08-14
As I recall, there's two different lines of patches, one with an additional 'x' in the patch name, for expansion (SOTU and whatever the other one is called, as well as the diamond/platinum editions).

Perhaps you're trying to use the wrong patch?

---

### Post by WSmart on 2008-08-18
Forsburg would be proud!  That worked, Artifical Intelligence of Denmark. I'm more disturbed now then when it wasn't working, not knowing what the difference is.  I'm using Opera (The Browser that gave us tabbed browsing!) and we're having a terrible time trying to get MS to use standards. I wonder if that's the issue? 

I used wget as you indicated and everything worked great. I was able to view the patch and install normally.  Thanks!

One issue I had, they didn't update their readme file so their install code still had the 168 patch file name.  I just changed the 8 to a 9, since the file names were otherwise identical. This is what they offered,  tar -xzf English_linuxclient168_orig.tar.gz .
 

I updated my post at the Bioware 169 patch thread, too.  And, fyi, this patch appears to be working great with Ubuntu.

Ng Oon-Ee, Yea, there are several patch version, one for each of the modules and then a patch for the different languages too.  You really have to choose carefully, true.  Thanks for the help.

Thanks all,

Bill

Thanks Ubuntu community!

Contribution share ratio = my contribution/(total resources consumed by the project/some community number such as active installs) = my contribution has context and is no longer just a shot in the dark  (Hint Hint)  Communication connects and empowers community.

---

