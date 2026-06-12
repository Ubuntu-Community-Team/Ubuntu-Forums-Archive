---
title: "[SOLVED] Weird (MP3) Permissions Issue with External Drive"
date: 2008-10-25
forum: Desktop Environments
---

### Post by mtbsoft on 2008-10-25
Sorry for the long post but I want to include as much detail as possible...

I've just today started playing with Intrepid beta (with all the latest patches) - did an upgrade over a spare Hardy install, all works sweet... except...

I have a 2Gb WD MyBook, configured as NTFS for my remaining Windows machines, connecting via USB - Hardy would recognise it but not auto-mount it, whereas Intrepid auto mounts it just fine (nice).

I'm just trying to tidy up my MP3 collection, renaming all the paths and files to a better standard and tidying up the tags. I used to use mp3tag but couldn't seem to get it to write under Wine so tried EasyTAG and got the same issue (file permissions).

Basically the drive has mounted in what appears to be a read-writable state but only seems to allow NEW files or directories to be written to, not permitting changes to existing data.

If I try to change the tags of any of the existing MP3s, none of my tagging programs allow me.

I've tried all manner of ways of mounting it, changing permissions and owner and nothing seems to work to change the behaviour. 

[list]
[*]I can create directories and files no problem, I can then change and delete them.
[*]I can delete existing directories and files no problem.
[*]I can COPY existing files to a new directory on the same disk then put them back and they CAN then be changed.
[*]I can MOVE existing file to a new directory on the same disk then put them back and they CANNOT be changed.
[/list]

I've looked at the directory ownership and permissions (root, drwxrwxrwx) and the file ownership and permissions (root, -rwxrwxrwx), both of the new and the old files (changeable and non-changeable) and they're identical!!!

I really am at a loss. 

I know that I could go to one of the Windows boxes and "fix" it there but that would be admitting defeat - I want to understand what is going on here and how to fix it.  Yes, I could also copy all the files into one new folder, change them there using EasyTAG and let it create the new file structure but that would also be avoiding the problem.

So... can anyone start me down the correct path to identifying what the hell is going on here, please?

---

### Post by mtbsoft on 2008-11-03
Eventually took the thing to work and ran chkdsk over it, then copied (not moved) all the files - seemed to be the only solution so I guess it must have been an issue with NTFS.  Would have been nice to know the reasons though.

---

