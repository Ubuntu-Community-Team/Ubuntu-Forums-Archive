---
title: "per user samba permissions?"
date: 2009-01-02
forum: General Help
---

### Post by Darth_tater on 2009-01-02
Before I upgraded to 8.10, I had a perfectly working smb.conf file.  I forgot to back the file up and have had to go from scratch since.

My problem is this:

Many directories that I share are public to all, but only a few have permission to write / delete files. 
Samba runs as ‘sambauser’ not the actual user on the machine, so I cannot enforce many of the per user permissions mentioned above.
  
How can I enforce per user folder permissions that go beyond the simple allow / deny access directive in the smb.conf file?  Is there a way to make the samba software run as each different user?  So instead of asking to perform a file operation with the name ‘sambauser’ it supplies ‘bob’ or ‘Alice’ instead?

Thanks for any and all help!  It is much appreciated!!!

Oh, and happy 2009!  May it be a better year for us all.

---

