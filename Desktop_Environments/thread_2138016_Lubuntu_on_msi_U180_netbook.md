---
title: "Lubuntu on msi U180 netbook"
date: 2013-04-22
forum: Desktop Environments
---

### Post by Richard B on 2013-04-22
There have been problems with Linux on this model due to:
[LIST=1]
[*]It comes with four primary partitions already in use with Windows 7. 
[*]Graphic resolution was only 800x600 with various releases because no driver installed. Suggested work-a-rounds were not straight forward.
[/LIST]
Mine is now working (with correct screen resolution - 1024x600) using Lubuntu 13.04 beta 2 (32bit version). Here is the basic approach used, retaining the ability to use the original Windows 7 starter edition:
[LIST]
[*]Delete 4th partion (an empty D: in Windows 7 on this device)
[*]Create a new extended partition
[*]Create a new, smaller "D:" within this and format to NTFS for Windows use
[*]Install Lubuntu in the freed space.
[/LIST]
Of course, you should first backup anything you have added while using Windows. Also, create Windows recovery DVDs - I found this worked best by creating image files and writing them to DVDs later.

---

