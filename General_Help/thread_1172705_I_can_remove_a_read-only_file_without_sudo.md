---
title: "I can remove a read-only file without sudo"
date: 2009-05-28
forum: General Help
---

### Post by carlos.mendoza on 2009-05-28
Hi Community

Could anyone tell me why I can remove a read-only file without sudo?

doc1.txt is a read-only file

I type this in konsole:  rm doc1.txt
The konsole shows me a message like this: rm: ¿remove the regular file "doc1.txt " protected against writing?  (y/n)
Then I confirm with "y" and the file is erased!!!!!  why?

I opened Policykit from System Settings and let all the Implicit Authorizations in "No" but that didn't work. 

I have some Explicit Authorizations but I don't sure if I have to change those. 

Any help will be appreciated. ;)

---

### Post by pastalavista on 2009-05-28
sudo only applies to files that are owned by root. If they're owned by you, the user, or have been created by you in a non-system folder, sudo isn't necessary.

---

### Post by Boondoklife on 2009-05-28
Try doing this sudo chown root:root doc1.txt

---

### Post by Brandon Williams on 2009-05-29
To remove a file, you only need write permission for the directory that it's in. You don't need write permission for the file itself. You only need write permission on an existing file if you want to change the contents of the file.

---

### Post by Boondoklife on 2009-05-29
> **Brandon Williams said:**
> To remove a file, you only need write permission for the directory that it's in. You don't need write permission for the file itself. You only need write permission on an existing file if you want to change the contents of the file.

Well i'll be, I never would have thunk it :p. Here I thought it controlled all access to the file PERIOD. Owell learn something new as they say

---

### Post by carlos.mendoza on 2009-05-29
Hi Community

Thanks a lot for your replies.

I removed the write permission to the directory containing doc1.txt and that works, the file can't be erased without sudo. However, this solution doesn't allow me to erase the other files as a normal user and I don't want that: I want restrictions to erase only doc1.txt and not to the other files the directory contains.

I changed the owner of doc1.txt to root (both user and group) but that didn't work: without sudo i can remove the file.

---

### Post by Boondoklife on 2009-05-30
> **carlos.mendoza said:**
> Hi Community

Thanks a lot for your replies.

I removed the write permission to the directory containing doc1.txt and that works, the file can't be erased without sudo. However, this solution doesn't allow me to erase the other files as a normal user and I don't want that: I want restrictions to erase only doc1.txt and not to the other files the directory contains.

I changed the owner of doc1.txt to root (both user and group) but that didn't work: without sudo i can remove the file.

As noted, it just is not possible, you could put the file in its own folder inside that folder and set the rights to it that way.

---

### Post by Yellow Pasque on 2009-05-30
> **carlos.mendoza said:**
> I changed the owner of doc1.txt to root (both user and group) but that didn't work: without sudo i can remove the file.
If you changed the owner and group, you may still have to change the permissions for other users to deny write access:
```
sudo chmod 644 doc1.txt
```

You could also make the file immutable using chattr:

```
sudo chattr +i doc1.txt
```

> A file with the &#8216;i&#8217; attribute cannot be modified: it cannot be deleted or renamed, no link can be created to this file and no data can be written to the file. Only the superuser or a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

---

### Post by pastalavista on 2009-05-30
Open a root file browser ```
kdesu konqueror
```Navigate to filesystem, right click your file's directory, select properties and open the 'permissions' tab. Set the folder to read-write. Then open the folder and right-click your doc1.txt file, select properties and set the permissions for it as read-only. That's the easiest way I've found to do it.

---

### Post by Brandon Williams on 2009-05-30
> **Temüjin said:**
> You could also make the file immutable using chattr

That's the ticket! I had completely forgotten about extended attributes, because I almost never use them.

---

### Post by carlos.mendoza on 2009-06-01
Hi Community

I tried with kdesudo dolphin and i get this errors:

Error: "/var/tmp/kdecache-cmendoza" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-cmendoza" is owned by uid 1000 instead of uid 0.

**doc1.txt is a read-only file** for all the users and its owner is root. I don't know if those errors have some influence in my problem: [COLOR=Red]**I can remove doc1.txt with the command rm but without sudo. **[/COLOR]

Could anyone tell me [COLOR=Red]**WHY**[/COLOR] this are happening? I don't want an alternative solution like the use of the command chattr or letting the container directory without write permission (although these are good alternativies and contributions!!!), I want to know **[COLOR=Red]WHY[/COLOR]** **[COLOR=Blue]are happening something that shouldn't happen!!! [/COLOR]**

Best regards.

---

### Post by pastalavista on 2009-06-01
To know why a file has the permissions it does, we would need to know how it was created or where it was copied from. Sometimes files become read only after being saved to CD-rom. It was easily deleted because the folder it was in had user permissions.

---

### Post by Brandon Williams on 2009-06-02
> **carlos.mendoza said:**
> 
Could anyone tell me [COLOR=Red]**WHY**[/COLOR] this are happening? I don't want an alternative solution like the use of the command chattr or letting the container directory without write permission (although these are good alternativies and contributions!!!), I want to know **[COLOR=Red]WHY[/COLOR]** **[COLOR=Blue]are happening something that shouldn't happen!!! [/COLOR]**

[My previous post](http://ubuntuforums.org/showpost.php?p=7366251&postcount=4) addressed this, though perhaps it wasn't clear enough. The behavior that you are seeing is expected. You simply can't do what you're trying to do because the observed behavior is what is supposed to happen. Technically, you're trying to modify the directory, not the file, so you only need permission for the directory.

You can make it harder to delete the file by setting the sticky bit for the directory. However, in that case, the user who owns the file and/or the directory will still be able to delete the file, and all files in the directory will be impacted, not just the specific one you're trying to protect.

---

### Post by carlos.mendoza on 2009-06-05
Ok, I understood, removing the write permission to a regular file ony guarantees that file won't be modified in its contents. To don't allow to rename or remove a regular file I need to quit the write permission to the directory containing that file...well, at less is an alternative :tongue:

I suppose that this thread can be closed. Thanks a lot for your replies. It is good to belong to the Community.

---

