---
title: "Jaunty - slow to open drives"
date: 2009-05-01
forum: General Help
---

### Post by Joe of loath on 2009-05-01
Hi;

I just uploaded to jaunty today. Apart from a slow first boot, first impressions were great! However, as my windows partition died a few days ago (after deleting boot.ini ON ITS OWN!), I needed to back up the user data to the external drive. I clicked on the icons in the places menu, and the PC slows down to a crawl, but the window doesn't open properly. It goes blank, then disappears. After 10 minutes it just appeared again, and I could transfer the files, but it's down to 500kb/s (between IDE and USB 2, so it should be faster). I can't browse through the terminal either.

any help?
thanks
Joe

---

### Post by charonred on 2009-08-18
If Windows didn't shut down properly, then it's pretty normal for Linux OS's not to 'mount' the Windows drive - it's sort of a protection against corrupting data on the drive (at least that's how I've interpreted it).

I can only suggest doing a Windows 'repair' install; that'll leave your existing Windows data intact, but will replace all Windows OS files so that it runs again. 

Once installed and booting correctly again, simply shut down Windows properly, and you should be able to mount the drive correctly from Ubuntu and backup all data from the Windows drive without a problem - yeah it's long winded, but should 'rescue' your data.

I can't recall the exact steps cause it's been a while, but should be along these lines;

Boot up from Windows install cd and go through the steps of installing a new OS (ignore the 1st suggestion of repairing the system), wait till you get to where it detects an existing install of Windows on the hard drive/partition, and asks whether you want to clean install, or repair existing... select repair and follow prompts; once done you should be able to run Windows again.

If you're unsure of the steps, then you may want to troll some Windows forums for advice on exact method.

I'm assuming that Windows & Ubuntu are on separate drives, and not dual booting off one disk; if they're dual booting, then it may be a little trickier cause Windows doesn't like installing on drives where a Linux partition exists (sees the disk as 'corrupt'), you may need to get advice from someone more experienced in the area of dual boot.

good luck.

---

