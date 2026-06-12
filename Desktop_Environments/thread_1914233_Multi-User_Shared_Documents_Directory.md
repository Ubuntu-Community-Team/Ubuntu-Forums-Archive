---
title: "Multi-User Shared Documents Directory"
date: 2012-01-23
forum: Desktop Environments
---

### Post by Infatuas on 2012-01-23
Hello all,

I created a "Shared Files" folder in /home and changed the security of this folder to allow rwx access by a group of users (2 users in group). I am trying to redirect their documents, pictures, and videos folder's on these users (/home/userprofile/documents) to point to a single location at (/home/Shared Files/documents) in order to consolidate the location of the files. Is this possible?

I have tried various things such as editing the /home/userprofile/.config/user-dirs.dirs and ect with no avail. Any ideas would be helpful.

---

### Post by GraeW on 2012-01-25
I'm rusty, but it sounds like you want to make a symbolic link between the users individual home/name/Documents folder to the /home/sharedfolder .. I believe the command is something along the line of:

ln - s SOURCEDIR TARGETDIR 

but I cannot be certain I have the command correct there. Someone else with CLI knowledge can hopefully dust off my cobwebs and help?

---

