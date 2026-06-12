---
title: "SAMBA   Error Installing service for File Sharing"
date: 2011-04-25
forum: Desktop Environments
---

### Post by c0dekiddie on 2011-04-25
Hi,

     I am a total newbie of Ubunu, i have Maverick Meerkat distribution installed on my machine.. I want to share folders on a workgroup.. I created a test folder and i tried to share it.. using SAMBA Service When I was prompted by Install Service.. I installed it and i expected that the result will be fine but unfortunately it wasn't.. I have already installed it but it prompts again to install SMB  or NFS.. and there is also an error when i try to share using the sharing options.. 

Please Help me... Thank you in advance

---

### Post by Morbius1 on 2011-04-25
Open Nautilus
Right click on the "test folder"
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.

If you tried this and you get an error then please post the exact error.

---

