---
title: "DMRAID - Can the meta data be recovered?"
date: 2008-01-24
forum: Dell  Ubuntu Support
---

### Post by aikiwolfie on 2008-01-24
I've just converted my PC from Windows XP to Ubuntu 7.10. There are four hard drives in the PC. Under Windows XP they were all set up as nvidia stripe raid 0 arrays (two disks per array). That wasn't my choice. Dell delivered the system like that.

After the conversion I left one array intact as it's 1TB in total with a large number of video files, however installing dmraid caused the boot process to fail. Clearing the meta data with dmraid -rE for each of the disks sorted this. The PC booted and dmraid worked fine. I had my remaining array mount without a hitch.

However now I have a hitch. A few reboots later dmraid can't find the remaining array. When I checked the nvidia ROM utility there was no array set up. It also tells me setting up an array will wipe the disks.

What I need to know is can the meta data be restored and if so, how do I go about it?

---

