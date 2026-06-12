---
title: "Cross Platform file systems"
date: 2005-10-27
forum: Desktop Environments
---

### Post by asdf_46 on 2005-10-27
I have a dual boot setup with Win 2k and Breezy. I would like to have one large partition that they can both read for music and video. The problem is that ext is unstable in windows and ntfs is unstable in linux. fat32 does not have large file support wich I need for video. Is there a better file system for this that I have not found yet? Thanks for any tips or suggestionsin advance.

John (asdf_46)

---

### Post by kairu0 on 2005-10-28
Reiserfs partitions can be read in Windows using rfsgui, but the problem is that they have to be copied with the rfsgui tool to a Windows partition before being read.

---

### Post by Emerzen on 2005-10-28
This is an indirect answer to your question, but I know other distro's don't have difficulty writing to NTFS such as OpenSUSE.  I don't know what packages they add that enable writing to NTFS, but I know they're out there.  Stability?

---

### Post by asdf_46 on 2005-10-28
Thanks for the help. I will look to see what openSUSE is using. I need to be able to access my files from all programs, so the reiser tools won't work.

asdf_46 (John)

---

### Post by mlomker on 2005-10-28
NTFS write can be enabled if you recompile your kernel.  The problem is that errors have been known to delete the entire partition now and then...

The [Paragon driver]("http://www.ntfs-linux.com/") is supposed to be solid but it isn't free.

---

### Post by toorima on 2005-10-28
[http://www.fs-driver.org/](http://www.fs-driver.org/) =D>

---

### Post by asdf_46 on 2005-10-30
Thanks for the help guys! I setteled on just using the ifs tools. I think I was using an older version earlier. Also I used to ext3, when I should have just been using ext2 since I don't really need journaling.

Thanks again.
John

---

### Post by aum11 on 2005-11-06
I am also looking at IFS.   

It sounds good.  What sort of experiences have You had with it?

Any recommendations?

Ta.

---

