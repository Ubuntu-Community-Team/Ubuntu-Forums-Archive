---
title: "ext3 for File Server ?"
date: 2008-12-21
forum: General Help
---

### Post by ripken204 on 2008-12-21
i am using ubuntu as a home file server and web server.
my OS drive is ext3 and i have 4x1TB drives that are currently NTFS.
the computer that these drives are in is ubuntu only.

should i change over all of my drives to ext3?
is it better to do so? 

i have noticed that just copying from drive to drive is very slow, like 30MB/s. when i had these drives in my windows computer they would transfer at 2-3x the speed. 

will switching to ext3 fix this?
is this because of the ntfs driver that ubuntu is using?

as long as Samba can use the ext3 drives so that my windows machines can access the shares, i think i should be all set.

and how much available space will i have for my 1tb drives if i use ext3?
with NTFS i have 931.5GB available.

so is ext3 > ntfs for my case?

---

### Post by jerome1232 on 2008-12-21
I would say yes ext3 will be better than ntfs.

If your looking for a filesystem with more speed you *may* want to look into xfs and jfs.

While ntfs support has improved in vast amounts the tools to work on them are still limited (no defrager, no good file system checker)

---

### Post by ripken204 on 2008-12-22
well i dont need SPEED, i just dont want the crippled speed that i have right now. it takes forever to transfer things even between 2 hdds on the server.

---

### Post by igknighted on 2008-12-22
You should consider a RAID5 array.  Not only will the speed be much better, but your data will be safe even if one of the drivers were to fail.

And yes, I wouldn't trust linux + ntfs.  Ext3 would work well, as would reiser, XFS, or any other linux file system.  Ext3 is typically the best mix of safety and performance for most users.

---

### Post by ripken204 on 2008-12-22
i will be doing RAID5 eventually, i need to get myself a decent controller first.

---

