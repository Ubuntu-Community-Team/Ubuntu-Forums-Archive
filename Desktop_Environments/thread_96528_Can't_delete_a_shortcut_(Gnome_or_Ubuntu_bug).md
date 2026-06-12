---
title: "Can't delete a shortcut (Gnome or Ubuntu bug)"
date: 2005-11-29
forum: Desktop Environments
---

### Post by ad noiseam on 2005-11-29
Hello,

I have the following problem: I placed a shortcut / link on my desktop, pointing to a folder on a FAT32 partition. I have all the rights on this partition, can access it without any problem. Till here, everything is fine.

However, when I try to delete the shortcut, I get an error message telling me:

```

Error "Not on the same file system" while deleting (name of my shortcut)"

```

Is there anyway I could *still* remove the shortcut?

Thank you for your help.

Nicolas

---

### Post by akiro.yamamoto on 2005-11-29
Open a terminal and enter this code:
CODE:
cd Desktop && sudo rm (name of your shortcut)

Post any errors (if any) you recieve...
But this is rather unusual :smile:
If you're unsucessful you may have to unmount the partion first, then retry the above code..... then if sucessful remount the partition.
Regards.

---

### Post by ad noiseam on 2005-11-29
It might have worked, but it didn't. My shortcut is called "photos-high resolution" (with a space between "high" and "resolution").

I tried to do what you told me and:
```

rm: cannot remove `photos-high': No such file or directory
rm: cannot remove `resolution': No such file or directory

```

---

### Post by akiro.yamamoto on 2005-11-29
TRY This 
CODE:
cd Desktop && rm photos-high\ resolution
Report back if it works or not and we'll try something else.
:smile:

---

### Post by akiro.yamamoto on 2005-11-29
I think it's just the space between the two, that's what causing the problem.
If "rm " fails try "rmdir" and see if bash will auto complete it for you:
Example: rmdir ph [TAB]
should complete out unless you have other directories starting with "ph"
:smile:

---

### Post by ad noiseam on 2005-11-29
[QUOTE=akiro.yamamoto]
cd Desktop && rm photos-high\ resolution
[/QUOTE]

This worked, thanks a lot.

Still, shouldn't a bug be filled about this?

---

### Post by Canuckelhead on 2005-11-29
If you edit your nautilus config and tell it not to show volumes... you can then make "shortcuts" to anything you want without having them show up on your desktop....

for esample look under system tools/ config editor/apps/nautlius/desktop/

volumes visible....

if you uncheck it .. the volumes you mount will no longer appear on desk top...
You can then select the suff you want on desktop by creating a launcher on the desktop...

---

### Post by ad noiseam on 2005-11-29
Yes, I know I could replace a mounted volume by a shortcut. The problem is, however, to delete the shortcut when you don't want or need it anymore. What I was told to do above works fine, but one shouldn't have to know a command line to delete a link on the dekstop.

---

### Post by dafl00 on 2005-11-29
[QUOTE=ad noiseam]Yes, I know I could replace a mounted volume by a shortcut. The problem is, however, to delete the shortcut when you don't want or need it anymore. What I was told to do above works fine, but one shouldn't have to know a command line to delete a link on the dekstop.[/QUOTE]

:confused: what O.S. are *you* using?? lol
this is linux.. if you want something done right you write the patch urself :wink:

---

### Post by ad noiseam on 2005-11-29
That's the problem. I am a "human being", not a programmer. :)

---

### Post by dafl00 on 2005-11-29
it IS good to see so many regular users comming into linux.. unfortunately, we still have a bit to go in order to get all the interfaces right.. 

my suggestion is stick around the GNOME newsgroups and forums... 

we, as programmers, need a better sense of human-computer interaction, so we definitely need regular users like yourself helping us along the way .. it's hard enough getting our heads out of geek-space on our own ](*,)

---

### Post by ad noiseam on 2005-11-29
Good luck. :)

I have nothing against trying and learning but, yes, I am not a programmer.
Ubuntu is the first Linux distribution I ever try, and I am happy with it, but yes, there is still some work to do here and there (more on the applications than on the whole feel / look / functionnality, I believe). Anyway, count me on to report bugs. :)

Which leads me to another question: is the problem at the origin of this post a Gnome or an Ubuntu problem (i.e., to which Bugzilla should I report this)?

---

### Post by dafl00 on 2005-11-29
definitely GNOME.. feature reqeuests can be done [here]("http://bugzilla.gnome.org/")

---

### Post by ad noiseam on 2005-11-29
Thanks.

Actually, a bug has already been filed for this:
[Bug 312506 - can't delete symlink to other filesystem](http://bugzilla.gnome.org/show_bug.cgi?id=312506)

Nicolas

---

