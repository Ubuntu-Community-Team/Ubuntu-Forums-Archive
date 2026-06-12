---
title: "File server is readable all the time on all client PCs."
date: 2008-12-30
forum: General Help
---

### Post by Kissell on 2008-12-30
I have a file server and windows users are logged into it 24/7/365 via mapped drives...  they never have to authenticate again, they can just read the information they have access to read...  And they leave their computers on all the time while unattended, even after they've gone home for the day...  I don't have authority to extend security to the desktops, and this data is sensitive, so I need to be able to protect it on the server-side, and file rights/privledges won't do it, beause I do need them to be able to read these files when they NEED them, but I also need to shut off access when they're not actively using them. 

Is there a way I can force them to truely re-authenticate, no cached passwords on drive letters...  I want them to have a mapped drive letter to the file server, but I want it to kick them off when they're idle and not using it...  or next time they go to use it, it asks them for their password again.  

Currently the drives are mapped as SFTP drives using third-party software loaded on windows...  But I can use Samba or whatever else, forcing them to re-authenticate after they've been inactive and timed-out is my primary design consideration, everything else is flexible (as long as they can still map a drive).

---

