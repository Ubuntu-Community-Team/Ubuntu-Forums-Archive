---
title: "no such file or directory, even though ls lists it."
date: 2018-12-30
forum: Desktop Environments
---

### Post by bob130 on 2018-12-30
Hi,
I'm trying to use rsync to backup an ntfs drive to a fat32 drive (this can't be changed due to where these drives will eventually be used).
It was giving me strange errors (File has vanished), when i looked into it a bit more there are a few files that appear white in bash and don't appear to exist even though they show up under ls.

Have a look at the screen shot:

[ATTACH=CONFIG]282055[/ATTACH]

The problem files are white, the ok files are green. I don't understand what the colours mean and googling has found lots of results on how to change them, but not what they actually define.
so, in a nutshell:

if is do this:
file elements/Nepalvideos/Tom/day4/2018-12-20/HERO4Silver1/TimeLapse2/G0055910.JPG
I get a sensible answer

If i do this:
file elements/Nepalvideos/Tom/day4/2018-12-20/HERO4Silver1/TimeLapse2/G0055911.JPG
I get No such file or directory

Why is this happening and how do i fix it?
Thanks

---

### Post by TheFu on 2019-01-01
What are the full permissions for the files? ** ls -al **is what we need along with the parent directory permissions and the userid that the rsync is running under.

On unix systems, owners, groups, and permissions matter.  The mount options generally set the permissions for non-Linux file systems like NTFS or FAT.

Also, filenames on Linux file systems and commands are case-sensitive.  Had to say that in case there was any confusion.  

Initially, before seeing the exact file names and directories, I was assuming the problem was due to different file systems not supporting the same characters.  For example, using a ':' is legal on Linux for a directory or filename, but not allowed on either NTFS or FAT-whatever.  There are a few other disallowed characters for NTFS or FAT too.

---

### Post by yancek on 2019-01-01
Isn't it possible for you to copy the files FROM the partition with the WINDOWS filesystem TO another partition with a WINDOWS filesystem with windows?
Do you remember what the "strange errors" you refer to are?

---

### Post by bob130 on 2019-01-02
I used gparted to copy the whole partition and errors came accross.
I used ls -al and the problem files just show as questions marks sorry for not getting the output of this.
I then borrowed a surface pro 3 (win10 i think) and used scandisk on the drive. It fixed it up. and the problem is now resolved.


I did try using fschk on the partition but it just said no errors. and took like half a second. The file format is ntfs and i get the feelign linux doesn't like it very much.

Thanks for your advice.

---

