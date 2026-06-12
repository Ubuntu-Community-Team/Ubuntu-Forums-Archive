---
title: "Outlook to Thunderbird"
date: 2007-06-04
forum: Desktop Environments
---

### Post by mayamaniac on 2007-06-04
I want to transfer all my emails from Outlook to Thunderbird in Ubuntu, whats the best way to do this? I noticed that in Thunderbird (ubuntu), there's no Outlook option for Import. But I think there's an Outlook option in the windows version of Thunderbird. So should I install Thunderbird in Windows, import the outlook data, then transfer it to ubuntu? Is this the best method?

---

### Post by aysiu on 2007-06-04
Yes, install Thunderbird in Windows and import Outlook.

Then, copy C:\Documents and Settings\mayamaniac\*Application Data*\Thunderbird in Windows to /home/mayamaniac/*.mozilla-thunderbird* in Ubuntu. The italicized folders are hidden folders, by the way.

For more details, check out [Howto: Share Thunderbird & Firefox data between Ubuntu & Windows](http://ubuntuforums.org/showthread.php?t=203524&highlight=share+thunderbird)

---

### Post by mayamaniac on 2007-06-09
Thanks for that, it worked almost perfectly.

There were some emails with attachments in Outlook that refused to import into Thunderbord. I had to delete those emails in order for the import to complete, or else it just stalls and at the same time increase the mailbox size to several gigabytes.

Another thing I didn't know was I had to change permission of all the files and folders that was moved from the Windows version, had to chmod all of them. Afterward, all the emails show up in Thunderbird of Ubuntu.

---

### Post by tIcK_tAcK on 2007-10-27
Hi there! I would like to know how can I import the Outlook files, without outlook, to thunderbird I only have linux in my system now! Thank's!

---

