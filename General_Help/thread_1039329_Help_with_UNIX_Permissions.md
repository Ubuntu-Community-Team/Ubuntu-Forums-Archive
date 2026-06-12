---
title: "Help with UNIX Permissions?"
date: 2009-01-14
forum: General Help
---

### Post by kachofool on 2009-01-14
Hey!

I want to create a shared space for several users, such that each user has RO access to everything inside the shared folder. However, inside the shared folder, that user will also have their own personal directory which they have full RW permissions for.

So I'm unsure about a couple of things regarding UNIX permissions. If I wanted to set the above up, I can change the directory permissions, but what about the actual files? The file content will solely of individuals uploading their own data to their personal folders. What permissions will these files take by default? All these files need to have always have the same permissions as their parent folder (which is RW for that specific user and RO for everyone else).

I'd appreciate some advice in setting this up.


Regards,

KF

---

### Post by fragos on 2009-01-14
When you right click a folder and select the permissions tab you'll find a button on the bottom of the window labeled "Apply Perissions to Enclosed files".

---

