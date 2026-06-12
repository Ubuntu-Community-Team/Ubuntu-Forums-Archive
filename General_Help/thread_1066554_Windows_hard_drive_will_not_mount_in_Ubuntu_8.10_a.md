---
title: "Windows hard drive will not mount in Ubuntu 8.10 after jave install??"
date: 2009-02-11
forum: General Help
---

### Post by cctravis on 2009-02-11
For months I have accessed my windows partition in Ubuntu 8.10 with no problem. Then today after I finally got the 64bit java working my windows harddrive no longer will mount. I do not know if the java install and the harddrive not mounting are related but I need to access this partition often so any help would be great. I searched through the forums but everything suggested did not work for me. I also tried to force mount the partition as suggested in the details when the drive won't mount but that does not seem to work either. 

Please any help or guidance would be great.

---

### Post by mozkill on 2009-02-11
i doubt that the java install caused the problem.  its very unlikely.

i would read this:  [http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/](http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/)

good luck.

---

### Post by cctravis on 2009-02-11
I will try the link you suggested. I just don't understand why it worked perfectly for months and then randomly yesterday stopped working.

---

### Post by cctravis on 2009-02-11
Tried what they said but when I go to edit my fstab file it never lets me save. Always says I do not have permissions to save file.

Any thoughts?

---

### Post by cctravis on 2009-02-11
So frusterating i did everything posted at 
[http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/](http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/)


and my drive still does not work. 

When I go to places my ntfs drive was always called 120.0 GB Media and I could read and write to it for months. Now when I try to access it after doing everything in the link above it just says 

"Can not mount volume. You are not privileged to mount volume."

So frusterating that this can change overnight like this. Any help or thoughts would be so great. Got to get this working tonight.

---

### Post by pastalavista on 2009-02-11
Have you used Windows recently and shut it down in the middle of an update? Or has any Windows program hung and Windows shut down without finishing (cold)?

You may have to boot Widows and let it do its thing and shut down cleanly before Ubuntu will be able to access it.

---

### Post by cctravis on 2009-02-11
That worked and my drive is back. Thanks

---

