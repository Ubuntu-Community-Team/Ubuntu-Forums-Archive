---
title: "Specifying directories"
date: 2009-04-07
forum: General Help
---

### Post by dE_logics on 2009-04-07
We can specify many /home directories (right?).


But this cant be done for all directories, for instance the root :P.


So can you pls give me a list which specifies which directories are 1 in number and which are multiple.

---

### Post by HermanAB on 2009-04-07
Uhmmm... You got something wrong somewhere.

Linux has a single file tree starting at "/".  So each subdirectory in the tree is unique.

---

### Post by coffeecat on 2009-04-07
> **dE_logics said:**
> We can specify many /home directories (right?).

No, there can only ever be one /home directory. I think where you're getting confused is that you can set up several accounts, and each account will have its own directory in /home, thus:

/home/fred
/home/mary
/home/george
/home/sally

and so on.

You can't set up multiple accounts in /root (if that's what you're saying) because there can only ever be one root account.

---

### Post by dE_logics on 2009-04-07
So what will happen to the other drives?


And the home directories contain user files right?...I mean for all sorts of storage or is it like containing the My documents folder and all?

---

### Post by dE_logics on 2009-04-07
What I mean by specifying many home directories is that many drives will be mounted as home.

But only one drive can be mounted as boot.

I guess I'm wrong.

---

### Post by coffeecat on 2009-04-07
**dE_logics**, before we go any further, please read this: [Linux != Windows]("http://linux.oneandoneis2.org/LNW.htm"). You are using a whole load of misconceptions from the Windows world. It will only trip you up. Specifically:

> **dE_logics said:**
> So what will happen to the other drives?

Forget C:, D: and so on. This is Windows rubbish. Linux refers to devices (partitions, CDROMS, floppies, USB drives, etc, etc) and mounts them on mountpoints, which are specific folders. You navigate to/open the mountpoint folder and, lo and behold, there are all the files on the mounted device.

> **dE_logics said:**
> And the home directories contain user files right?...I mean for all sorts of storage

Yes, personal files, and hidden files which have your personal configurations for the desktop and applications.

> **dE_logics said:**
>  or is it like containing the My documents folder and all?

Forget My Documents - more Windows rubbish. My Documents is more or less equivalent to your Linux home folder, but not exactly the same.

> **dE_logics said:**
> What I mean by specifying many home directories is that many drives will be mounted as home.

:-k

> **dE_logics said:**
> But only one drive can be mounted as boot.

:-k :-k :-k


> **dE_logics said:**
> I guess I'm wrong.

Don't worry. You'll soon get the hang of it. :wink:

---

### Post by dE_logics on 2009-04-08
> please read this: Linux != Windows

:lolflag: nice.

Knew that.

Yeah I'm classified as an expert user in windows...so sorta feel messy when I don't know at least the fundamental mechanics of an OS.

> and mounts them on mountpoints, which are specific folders.

But there are limited number of mount points right?

Suppose I want to use the partition not as limited directories like /home, /var, /etc etc... (cause they they are limited in quantity...furthermore only 1 home directory)
So is there sorta...any mount point which's unlimited and can be automatically mounted on boot? (for instance '/dev1'...I can specify this '/dev1' to like...20 partitions so they'll mount automatically on boot)

> Yes, personal files, and hidden files which have your personal configurations for the desktop and applications.

But applications or binaries are in the /usr/bin or /usr/sbin , /bin and /sbin directory right?

> Forget My Documents - more Windows rubbish. My Documents is more or less equivalent to your Linux home folder, but not exactly the same.

Yeah...that what I meant.

[quote=dE_logics]What I mean by specifying many home directories is that many drives will be mounted as home.[/quote]

For instance I have 2 partitions, both of them will be mounted as home.

Anyway, I realized that's not possible.

---

### Post by dE_logics on 2009-04-08
Ok I'm completely confused.



Can someone give me a link to this mount at...mount to etc...

---

### Post by dE_logics on 2009-04-08
Ok...doing the installation you specify which partitions can be used as which directories...right?

For instance sda1 as / and sda2 as /home etc...

After installing, when you mount a partition/CD ROM, it means mounting 'in' one of these directories...right?



So after installation, is there anyway to change the specified /var or /home etc... partitions?

I mean suppose I specified /home in sda5...can I move this to sda7?

---

