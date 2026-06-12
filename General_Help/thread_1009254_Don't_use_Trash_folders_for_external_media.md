---
title: "Don't use Trash folders for external media"
date: 2008-12-12
forum: General Help
---

### Post by chadeldridge on 2008-12-12
All,

I have been unable to find a solution to this via the forums, so I just want to put it out there for everyone.

I would like to disable the usage of the Trash folder on all my mounted file systems inside the /media folder.   I have recently discovered about 200gb of files hanging out on one of my shares sitting in the Trash that caused me to basically run out of space on that network share.  I would to simply not use Trash at all on anything mounted in /media.

Is this possible?

---

### Post by PocketDog on 2008-12-12
I don't know about disabling trash but shift+del will bypass it. Don't get into the habit though, you can't bring something back once it's gone

---

### Post by chadeldridge on 2008-12-12
Yeah i know about the keyboard shortcut to stop the action .. was just wondering if there is a way to just not use the Trashcan for specific places.  

Thanks for the quick responce though.

---

### Post by drs305 on 2008-12-12
> **chadeldridge said:**
> I have recently discovered about 200gb of files hanging out on one of my shares sitting in the Trash that caused me to basically run out of space on that network share.

This would be another of those 'Not what you asked for, but ...' responses. 

For recent versions of ubuntu, partitions may create a trash bin called 'Trash-####' with #### being your UID. Example: /media/myfolder/.Trash-1000  

Any trash user 1000 deletes within that partition will be deposited in this folder. The advantage is that this trash should *also* display in the user's regular trash bin, *and will be deleted when you empty your trash bin*.

It is possible your /media subfolder did not have the .Trash-XXXX folder. If it doesn't, you could create one.

It is also possible that the trash was not the user's but root's, in which case emptying the user's trash would have no effect. Special measures are required to delete trash created by root. You can review information on this by clicking on the Trash link in my signature line.

---

### Post by chadeldridge on 2008-12-12
Yeah that is generally the issue i had with the files that were deleted belonging to Roots UID and not mine.  So for the time being i have just made a script and had cron run it every 20 mins that removes them from all my mounts,  its not a good solution, but until i find out how to turn them off it's the best i got.

---

### Post by ibuclaw on 2008-12-12
This is a rather crude way of achieving it, but you can remove write access to your Trash folders on your external hard drives.
```
sudo chmod -w .Trash-* -R
```

So when you come to delete files/folders, you'll get a semi-warning dialog saying this:
```
**Cannot move file to the Deleted Items folder, do you want to delete permanently?**

The file "foo" cannot be moved to the wastebasket.

*Show more details*
Unable to create wastebasket info file: Permission denied



| **Cancel** |  | **Skip All** |  | **Skip** |  | **Delete All** |  | **Delete** |

```

And then just click the "**Delete All**", or "**Delete**" depending on how cautious you are.

Regards
Iain

---

### Post by chadeldridge on 2008-12-12
Crude indeed .. effective yes.  Thanks this is much better than my script.

---

