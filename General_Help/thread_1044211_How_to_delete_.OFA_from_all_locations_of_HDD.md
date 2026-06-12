---
title: "How to delete *.OFA from all locations of HDD?"
date: 2009-01-19
forum: General Help
---

### Post by timzak on 2009-01-19
Hello,

I'm hoping someone can help me.  I migrated my wife to Ubuntu, and discovered in her photo collection that she has some photo configuration files from an old photo software she no longer uses.  These are *.OFA files that are no longer needed.  I can search them out using the Search For Files... tool under Places, but cannot delete them all in one fell swoop because they are littered through thousands of separate folders.  It appears Nautilus does not have this capability (to delete *.OFA from every location on the HDD).  Rather than manually delete them one by one, I'm sure there must be a quick way to do this through the terminal?  I would certainly appreciate someone's help with this.

Thanks.

---

### Post by any.linux12 on 2009-01-19
> **timzak said:**
> Hello,

I'm hoping someone can help me.  I migrated my wife to Ubuntu, and discovered in her photo collection that she has some photo configuration files from an old photo software she no longer uses.  These are *.OFA files that are no longer needed.  I can search them out using the Search For Files... tool under Places, but cannot delete them all in one fell swoop because they are littered through thousands of separate folders.  It appears Nautilus does not have this capability (to delete *.OFA from every location on the HDD).  Rather than manually delete them one by one, I'm sure there must be a quick way to do this through the terminal?  I would certainly appreciate someone's help with this.

Thanks.

That's easy but be careful

sudo find / -name *.OFA -exec rm -rf {} \;

but first I think that you should do a:

find / -name *.OFA -exec echo {} \; 

just to print and be sure

---

### Post by heindsight on 2009-01-19
> **any.linux12 said:**
> That's easy but be careful

sudo find / -name *.OFA -exec rm -rf {} \;

but first I think that you should do a:

find / -name *.OFA -exec echo {} \; 

just to print and be sure

you don't need rm -rf for that (-r is only necessary to recursively delete an entire directory). Also, I think it's unlikely that these files will really be "all over" the filesystem. Most likely they're all somewhere under your wife's home directory in which case you can do the following (while logged in to your wife's account):
```
find ~ -name "*.OFA" -exec rm \{\} \;
```

---

### Post by any.linux12 on 2009-01-19
> **heindsight said:**
> you don't need rm -rf for that (-r is only necessary to recursively delete an entire directory). Also, I think it's unlikely that these files will really be "all over" the filesystem. Most likely they're all somewhere under your wife's home directory in which case you can do the following (while logged in to your wife's account):
```
find ~ -name "*.OFA" -exec rm \{\} \;
```

Hmm ok thanks I thought it was r (from remove) and R (to recursive)

---

### Post by heindsight on 2009-01-19
> **any.linux12 said:**
> Hmm ok thanks I thought it was r (from remove) and R (to recursive)

nope, -r and -R are synonymous :)

---

### Post by timzak on 2009-01-19
> **heindsight said:**
> you don't need rm -rf for that (-r is only necessary to recursively delete an entire directory). Also, I think it's unlikely that these files will really be "all over" the filesystem. Most likely they're all somewhere under your wife's home directory in which case you can do the following (while logged in to your wife's account):
```
find ~ -name "*.OFA" -exec rm \{\} \;
```

Thanks, I logged onto the directory that houses the .OFA files and tried the command you posted.  I got permission denied results both with and without sudo:

```
tim@tim-desktop:/media/disk-1/Pictures$ find ~ -name "*.OFA" -exec rm \{\} \;
find: /home/tim/.dbus: Permission denied
tim@tim-desktop:/media/disk-1/Pictures$ sudo find ~ -name "*.OFA" -exec rm \{\} \;
find: /home/tim/.gvfs: Permission denied
tim@tim-desktop:/media/disk-1/Pictures$ 

```

Any ideas?

Thank you. :-)

---

### Post by iaculallad on 2009-01-19
Try reading [this]("https://bugs.launchpad.net/gvfs/+bug/225361"), related idea in connection with your FUSE mount point error.

---

### Post by timzak on 2009-01-19
Actually, I just tried any.linux12's suggestion and it worked fine.  I also discovered how to do it in Nautilus.  After selecting Places->Search for Files... I typed *.OFA in the directory tree in question.  After it located all the files, I selected all, right-clicked and selected "Send to Trash."  I manually had to click "Delete" for each file, but was able to speed-click through it fairly quickly.  Both methods worked, with any.linux12's being quickest.

Thanks again.

---

