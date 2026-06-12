---
title: "Sharing a folder with multiple users"
date: 2005-10-17
forum: Desktop Environments
---

### Post by david_finlayson on 2005-10-17
It there a way to make a folder permently accessible for two different users?

My wife and I each have an account on our home machine. We both record music and take pictures. We want a folder that is common to us both for storing the music and photos.

So far I have set up a group called "share" which we both belong to. I set up a directory that belonged to "share". Then I set the permisions to chmod g+rwxs to set the gid bit. I thought that anything created in this directory would be accessible to both of us. Not so. It seems that most programs (gThumbs, Sound Juicer) ignore the setgid bit and create new files with restrictive permisions anyway. I have to go back manually every time and change the group and file permisions so that my wife can read/play the new photos and music.

What am I doing wrong?

David

---

### Post by jobezone on 2005-10-17
I tried some months ago to do what you needed, and also got mixed results.

Optionally, couldn't you create a bash script which will chmod recursively that directory, and use it as a cron job, or as a button you push from time to time?

---

### Post by doclivingston on 2005-10-17
What making a directory setgid does, is ensure that any files created in there have their group set to the same group as the folder.

The problem is probably that by default files are created with group-read permissions but not group-write permissions. The effect of which is that both of you would be able to read the files, but only the owner can write to them.


I don't know of any way to automatically give both of you write access to everything under that directory, besides a) having a cron-job that regularly makes all the files g+w, or b) using access control lists.

(b) is a much nicer way of doing it, but can be a bit more complicated. Although I haven't looked to closely at it, there is a page in the wiki about [ACLs](https://wiki.ubuntu.com/HelpOnAccessControlLists)

---

### Post by gazzerh on 2005-10-17
When you create the directory you need to set a umask mode on that directory. Which is an octal value which is like the rwxrwxrwx values. This will set the default permissions when files are created in it.

---

### Post by p_schott on 2005-10-23
I am also interested in sharing a folder. It would be very helpful for me if you could give some information about how it is possible to set such an umask mode on a folder. Anyway, thank you very much fot your help.

---

