---
title: "permissions and networking"
date: 2005-05-29
forum: Desktop Environments
---

### Post by improverrr on 2005-05-29
Using SMB4K i can see  my laptop from my desktop (kubuntu), but I am getting suid 1000 errors.  I know this is a permissions thing since I can goto SMB:/ in kongueror (as root) and see and get to everything, 

how do I fix this?  any help appreciated!

Thanks!

ImproVerrR

---

### Post by improverrr on 2005-05-29
ok for those who have this issue:

open the console (as root)...type:

chmod +s /usr/bin/smbmnt <enter>
chmod +s /usr/bin/smbumount <enter>

good to go now!

---

