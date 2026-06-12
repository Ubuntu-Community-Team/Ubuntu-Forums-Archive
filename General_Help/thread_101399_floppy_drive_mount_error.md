---
title: "floppy drive mount error"
date: 2005-12-09
forum: General Help
---

### Post by emerick7 on 2005-12-09
I installed linux last week, and haven't had to use my floppy drive until now.  When I try to go into the floppy drive folder, a "mount error" pops up saying: "Unable to mount the selected volume - Error: given UDI is not a mountable volume."

Any ideas on how to go about this??

---

### Post by 5-HT on 2005-12-09
Hi, for some reason or another (which I don't have the ability to understand) there seems to be a problem with pmount in breezy which causes this problem (from what I've read in other posts) when mounting a floppy from the GUI.

From that error message you're getting, I believe this is what you're trying to do, but please correct me if I'm wrong.

There is a really easy way to get around this though.

Just open up a terminal and mount the floppy with this:
```
 mount /media/floppy0 
```

Once done, the floopy will be accessible, and you'll even get a desktop icon for it.

When you're done, just unmount it with this:

```
 umount /media/floppy0 
```

HTH

---

### Post by emerick7 on 2005-12-09
Thanks... but do I need to do that every time I want to access my floppy drive?  If so, is there a way to get around that, or will it be mounted from now on??

---

### Post by emerick7 on 2005-12-09
...and how to I get rid of the desktop icon of the floppy drive?? (I like to keep my desktop nice and clean for some reason..)

---

### Post by 5-HT on 2005-12-09
Unfortunately, this procedure must be done every time you want to mount/unmount the floppy (did it work for you though).

There are some alternatives however, but I've never used them and as I always have a terminal open it just takes a second to mount the floppy.

If you do want to get around having to manually mount the floppy from the CLI, you could:

1) Download the pmount for dapper (the next Ubuntu release), in which this bug has been fixed.

2) Check out supermount (however, I don't know if this will work for a floppy)

3) Create an alias for mounting the floppy. Basically an alias is an abbreviation you create that when typed, executes the command it defines.

If you want to either check out the new pmount, the best way is to search around as I know there are many posts on it, and as I haven't done it and don't consider myself anywhere near a fully competent Linux user it would be best to get advice from those in the know (which have already been posted many times).

If you want to learn about aliases, again there are many posts about them, but I can guide you through that as I use many myself.

About using supermount and having them automatically mounted...I don't believe you can really do this with a floppy, but again, I may be wrong and a search (or someone else posting in this thread) may be able to help you with that.

In terms of getting rid of the floppy icon, simply go to ```
Applications > System tools > configuration editor > apps > nautilus > desktop 
``` and uncheck the "volumes visible" option.

Note that this will get rid of all volume icons on the desktop though (floppy, cd, etc.).

Hope this helps.

---

### Post by DarkW0lf on 2005-12-25
What happened inpmount between Ubuntu 5.04 and 5.10 ?
It worked in the previous version.

So the manual option is the only one right now ?
I have to manually mount the floppy but it unmounts fine just right clicking the desktop icon, I don't have to unmount manually.
Any idea why that might be ?

---

### Post by canadianwriterman on 2005-12-25
Rather than all the terminal entries and creating an icon on your desktop, etc., I prefer to have the functionality working as it was really designed to.

Unfortunately, there were many people (myself included) for whom this function did not work. There was a bug in the pmount file that controls mounting. Developers fixed the file, but it was not sent out as an update. But, you can update it yourself.

To update pmount, go to:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

Download and install pmount_0.9.6-1_i386.deb

Now, just insert your floppy, open Computer and right click on the floppy drive. You'll have a menu option to Mount and then Unmount it. Hope that helps.

---

### Post by Tosa on 2005-12-25
Thanks a lot,
my floppy finally works !!!

---

### Post by sarah_b on 2005-12-26
[QUOTE=canadianwriterman]
To update pmount, go to:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

Download and install pmount_0.9.6-1_i386.deb[/QUOTE]

Hi canadianwriterman,
I did this and now I am left without a desktop icon for my floppy drive and I can no longer even manually mount it. Do you or anyone else know how I can get my manual mount and umount process back ? It is broke !

---

