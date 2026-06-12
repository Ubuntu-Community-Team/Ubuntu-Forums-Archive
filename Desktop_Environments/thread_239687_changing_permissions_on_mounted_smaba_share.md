---
title: "changing permissions on mounted smaba share?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Redeyes_Gambit on 2006-08-19
}{i,

I have a NAS (network attached storage device) on my network, and have finally gotten it mounted with some help from you guys on the forum and a guide found here: (specifically under the heading of "mounting a samba share") [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

I now have only one last hurtle to cross: I want to have the share permissions where all users can read write and execute. Currently, the file owner is greg (my user name) and the group is "root". Now, the owner can read, write and execute; but the group and others can only write and execute. I have tried using nautilus in sudo mode to change the owner/group of the mounted share, but every time I try I get the error:

You do not have the permissions necessary to change the group (or users when trying to change that) of "RGs_Stuff".

Also, changing the r/w/x permissions won't stick. I check a box for r/w/x and it instantly un-checks itself.

I'm guessing this has to do with the user specified in the etc/samba/user (see the link to the tutorial I used above) being greg, and so I can't change the owner of the share because it's specified in the user file?

I have already tried going into the /etc/samba/user file and changing the "username" to "nobody" (so that "nobody" owns it), and then specifying that user in fstab. But, EVEN THEN I can't change the group from root to users, or any of the r/w/x permissions.

How can I change the mounted share to have r/w/x permissions, and to be owned by "nobody" in the group of "users"?

Thank you :)

---

