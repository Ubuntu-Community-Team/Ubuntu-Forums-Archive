---
title: "Deleting Ghost Account"
date: 2009-06-01
forum: Desktop Environments
---

### Post by Jesdisciple on 2009-06-01
I had a huge mishap based on a misconception.  Long story short, I had to empty my main profile folder because I put corrupted data in it.  But little did I know the data went to a trash folder (.Trash-0, which I Googled) which even root couldn't delete from; the files would just be renamed because the OS was confused.  

Then I couldn't login to the main account because the config files were gone.  I tried to create an account called "dummy" so I could copy them over, but the disk was full because nothing really got deleted.  Logging into "dummy" didn't work, because the disk didn't have room to create it.

I finally chased the trash down with a combination of *sudo nautilus* and *sudo rm -rf*.  "dummy" didn't show up anymore in the Users and Groups application, so I tried to create it.  Some record of this non-existent account apparently remains, so I used "dummy2" instead and deleted it when I was done.

Now I'm wondering how I can get rid of this ghost?

Thanks in advance.

---

