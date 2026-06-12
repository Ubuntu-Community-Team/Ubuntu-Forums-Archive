---
title: "Read-only file access"
date: 2009-01-17
forum: General Help
---

### Post by moeakhter on 2009-01-17
Hello!

I just installed Ubuntu on my laptop. I am new to this operating system so I apologize if my questions are rudimentary.

I have a burned music CD with tracks I was trying to edit on Audacity. However, the file appears as 'read-only' and will not let me play or edit in Audacity or Rhythm-Box.

How can I access/play these files? Any help is greatly appreciated.

Thanks,

-Moe

---

### Post by taurus on 2009-01-17
Files on CD are read-only.  If you want to edit those files, you first need to copy them to your harddrive, then change the permissions to have write to them before you can edit them.

---

### Post by x33a on 2009-01-18
if you mean that the file you are trying to edit is on the hard drive, then you need to change the permission of the file using chmod.

try chmod go+rw filename.

and, if they are on a disc, then they can be only read, as taurus pointed out.

---

