---
title: "Sharing volume between users: umask, acl... oh my!"
date: 2007-04-23
forum: Desktop Environments
---

### Post by Jhongy on 2007-04-23
I want to share a volume (internal, formatted as ext3) between users on the same machine.

OK, how will this work... ?

I'll mount the shared documents disk in /home/shared , then i'll put symlinks in /home/user/shared to /home/shared for each user

I'll add all users I want to access this folder to a group, say, the "sharedocs" group

I'll install acl and eicel

I'll add "acl" as an option to the fstab for this entry

In eicel, I'll set owner as me, read/write access to group "sharedocs"


So, after all this, will this work as a shared document repository for users in the "sharedocs" group?


What happens if I just mount the partition with umask=000 instead? Would that work better? What's the difference?

---

### Post by AtrejuT on 2007-04-23
I don't think you need all this acl stuff. From what I read recently you should add a group for your shared files, make all useres that require access members of this group and set the group as owner of the shared files with r/w rights as you require them...

good luck

---

### Post by mojoman on 2007-04-23
> **AtrejuT said:**
> I don't think you need all this acl stuff. From what I read recently you should add a group for your shared files, make all useres that require access members of this group and set the group as owner of the shared files with r/w rights as you require them...

good luck

But what if a member of the group uploads a file, will the other members have access to it? I don't think so and therefore you probably have to solve it with umask, especially if it is folders within a partition that we're talking about.  I'm having this problem myself but haven't made any headway.

[http://ubuntuforums.org/showthread.php?t=366956](http://ubuntuforums.org/showthread.php?t=366956)

I sure could use a solution to this.

/mojoman

---

### Post by AtrejuT on 2007-04-23
they do if zou set the shared directorys SGID bit: I took this from here:
[http://ubuntuforums.org/showthread.php?t=363898&highlight=file+sharing+between+users](http://ubuntuforums.org/showthread.php?t=363898&highlight=file+sharing+between+users)

unless I misunderstand this should do what you want.

---

### Post by Jhongy on 2007-04-23
So now we have three choices:

UMASK

ACL

SGID


Which to choose and why? What are the advantages and disadvantages?

---

### Post by mojoman on 2007-04-23
> **AtrejuT said:**
> they do if zou set the shared directorys SGID bit: I took this from here:
[http://ubuntuforums.org/showthread.php?t=363898&highlight=file+sharing+between+users](http://ubuntuforums.org/showthread.php?t=363898&highlight=file+sharing+between+users)

unless I misunderstand this should do what you want.

Yes, as far as I've understood it should BUT as is clear from the link in my first post I have already set SGID on these folders and yet the files created in them do not have the same group permissions as the folder but I have no idea why... :confused:

---

### Post by mojoman on 2007-04-23
Ok, i played around some more and this is what I've concluded. 

SGID will only make all files created in a directory set with SGID to belong to the same group. I've got a group called private that owns some SGID-directories in my /home. All files and directories created in these directories will belong to the group private.

Now, all is good so far but this is not enough, at least for my purposes. The default umask setting is 022 and this will give all newly created files and directories the permission 755, i.e. full access to owner and readable/executable by the group and the world. I need the the group to have full access to all files in these directories.

Perhaps a simple bash script in the file governing the umask settings (/etc/profile) could solve this by keeping the default umask settings for all other directories but these. A good umask setting for these directories could be 007 (which would give owner and group full access and no access at all to the world), 003 (same as 007 for owner and group but the world can read) or 002 (the world can read and execute).

Now, as I don't know anything about bash scripting that option is out and the remaining option would be to change the default umask setting, which is a bit unsettling as this effects the entire system. However, that's what I've done and my umask is now set to 002. I opted for that setting as it "only" gives more access to the groups and keeps the default access for the world. That way, it shouldn't interfere in with any system processes. The home-folders are owned by the owner and their identical group so they will not be effected, nor will files owned by, for examle, root. All in all, I think that the security is minimally compromised and it gives me a setup for the shared folders that are at least acceptable and workable. Still, I would prefere a nice bash script in my /etc/profile to do this for me. Well, I suppose I have to read up on bash...

/mojoman

EDIT: a found a slightly better way than changing umask in /etc/profile and this is to keep the original setting and instead edit the .bashrc in the relevant users home directories. I just added the line umask 007 in the file .bashrc and now all files that *these users only* create are fully accessible to owner and group and the world have no access at all. Still not as good as an eloquent script but it's a step forward...

---

### Post by Jhongy on 2007-04-24
An update:

I installed ACL and eiciel. I added acl as an option to my /etc/fstab. 

Then I let the missus use the computer, telling her it was great and would be easy.

It was a mess. She could write to some folders, not others. Since the shared folders are symlinked in various places, accessing them through some symlinks worked, while others didn't. It was incredibly irritating.

So, back to square 1.

Since all these documents are on a separate volume, can I just set UMASK=003 in my /etc/fstab? Everyone talks about UMASK from a user profile perspective, not from a file perspective, but I'm guessing this will work....

?

---

### Post by mojoman on 2007-04-24
> **Jhongy said:**
> An update:

I installed ACL and eiciel. I added acl as an option to my /etc/fstab. 

Then I let the missus use the computer, telling her it was great and would be easy.

It was a mess. She could write to some folders, not others. Since the shared folders are symlinked in various places, accessing them through some symlinks worked, while others didn't. It was incredibly irritating.

So, back to square 1.

Since all these documents are on a separate volume, can I just set UMASK=003 in my /etc/fstab? Everyone talks about UMASK from a user profile perspective, not from a file perspective, but I'm guessing this will work....

?

Yes, you should be able to set the umask to 003 in /etc/fstab for that volume and that should give all directories and files created on it the permission 774 (i.e. full access to user and group and readable to the world). Then you just have to set the group ownership for the shared directories as SGID to ensure that it everything created goes to the right group. 

I didn't know it could be set in /etc/fstab so I had to look it up myself. This would be an option for me as well, and slightly better then the one I got now.

/mojoman

EDIT: You probably shouldn't have the shared documents in a subdirectory to any users home folder as the home folder itself is set as SGID (I think). I got it set up with a /home on a separete partition and besides the users' home folders there are several other folders (e.g. /home/movies; /home/music; /home/download etc) and these folders are set as SGID to a group that all users belong to (in your example this would be the group "sharedocs"). This setup won't involve symlinks either.

---

### Post by Jhongy on 2007-04-24
Cool

Right now the volume is mounted in /mnt/docstore

I'll set its UMASK to 003 and run chmod -R g+s /mnt/docstore

It's symlinked to home/Shared Documents, which is in turn symlinked to /home/user1/Shared Documents and /home/user2/Shared Documents

I've also set /home/<user>/Windows Documents as a symlink to /home/Shared Documents/Windows Documents, and also /home/<user>/Windows Desktop to /home/Shared Documents/Windows Desktop

The users' desktops also contain symlinks to the various locations into /home/Shared Documents.

Are you saying that these symlinks are likely to screw things up? Hoping to keep them.

---

### Post by mojoman on 2007-04-24
> **Jhongy said:**
> Cool

Right now the volume is mounted in /mnt/docstore

I'll set its UMASK to 003 and run chmod -R g+s /mnt/docstore

It's symlinked to home/Shared Documents, which is in turn symlinked to /home/user1/Shared Documents and /home/user2/Shared Documents

I've also set /home/<user>/Windows Documents as a symlink to /home/Shared Documents/Windows Documents, and also /home/<user>/Windows Desktop to /home/Shared Documents/Windows Desktop

The users' desktops also contain symlinks to the various locations into /home/Shared Documents.

Are you saying that these symlinks are likely to screw things up? Hoping to keep them.

I'm not sure, I really don't know anything about symlinks but what I was thinking about is that you might not want to give SGID to files located in your home directory, since files in his directory are owned by user:user and you want the shared files to be owned by user:group. I don't know if this might cause any problems, like I said, I really don't know anything about symlinks.

---

### Post by Jhongy on 2007-04-24
Well scratch all that.. UMASK can't be set for ext3, so it seems.

---

### Post by mojoman on 2007-04-24
> **Jhongy said:**
> Well scratch all that.. UMASK can't be set for ext3, so it seems.

That sounds *really* strange, I use ext3 (though I haven't set it in /etc/fstab) and umask works for me. I suppose it can't be set for FAT32 though, as it doesn't support permissions.

---

