---
title: "Disk Assessment - Not displayed"
date: 2018-04-01
forum: Desktop Environments
---

### Post by jman17712 on 2018-04-01
1. Install Ubuntu 16.04.3 Desktop

2. Search for "Disk" & click open

It shows all the disks information (Eg. Model,Size,Serial Number)

My current problem is that 2 disks show "Assessment: OK" but my other 6 same model drives don't show any "Assessment" just a blank space where it should be not even the word "Assessment" appears on the other disks I have worked out that I have two onboard SATA chipsets.

6 BLACK SATA ports (Not showing assessment)
2 WHITE SATA ports (Showing Assessment)

Any idea how I can get my drives on the "6 x BLACK SATA ports" to show assessments?

(Possible thoughts are I might need to enable S.M.A.R.T. at BIOS Level)

Thanks in advance hopefully someone can help me :-)

---

### Post by TheFu on 2018-04-02
Have you considered not using a GUI tool to gather the information?  Perhaps **smartctl** will work better?

---

### Post by jman17712 on 2018-04-10
I agree that way works :-)

I did manage to get it working via "Disk" section the solution was go into BIOS & disable "External SATA" now I can see assessment under my "Disk" section.

This solution of disabling "External SATA" worked on both my two motherboards with ubuntu 16.04.3 LTS installed. 

(You can leave "Hot Plug" enabled as that won't affect it)

Hope this helped people took me ages to work out this BIOS setting caused the issue an no one ever mentioned it & BIOS Settings have this setting enabled by default.

---

