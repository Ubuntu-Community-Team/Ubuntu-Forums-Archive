---
title: "Directory Disappeared"
date: 2009-01-10
forum: General Help
---

### Post by MC_LA on 2009-01-10
A directory and all of its contents suddenly disappeared. Its not in Trash and I can't find it with some standard tools (e.g. Find, Foremost). 

The last thing I did that likely caused it to disappear was that I used DeVeDe to create image. I pointed DeVeDe to the directory that is now missing to store the image. Bad Idea. 

Does anyone know why DeVeDe would wiped out the directory and is there a way to get it back ?

Many thanks!

---

### Post by kellemes on 2009-01-10
> **MC_LA said:**
> A directory and all of its contents suddenly disappeared. Its not in Trash and I can't find it with some standard tools (e.g. Find, Foremost). 

The last thing I did that likely caused it to disappear was that I used DeVeDe to create image. I pointed DeVeDe to the directory that is now missing to store the image. Bad Idea. 

Does anyone know why DeVeDe would wiped out the directory and is there a way to get it back ?

Many thanks!

Don't use DeVeDe myself..
But could it be the directory is marked hidden?
Or maybe did you maybe created an iso from this directory instead of using it to store the iso you created?
Just guessing..

---

### Post by MC_LA on 2009-01-11
Thanks for the reply. The files aren't hidden. I'm pretty sure I didn't create an ISO of the directory since DeVeDe only ran for a few seconds, and even when it does create an ISO, it shouldn't destroy the source.

The thing that is surprising to me is that the missing directory isn't in Trash. If DeVeDe deleted the directory for some reason, why wouldn't they show up in Trash ?

---

### Post by hikaricore on 2009-01-11
The gnome (and kde) desktop and it's array of software titles may make use of the the "trash" not every program on Linux does this.
Some software actually deletes files instead of moving it.  This is true even in ***dows.

If for anyone reason this DeVeDe deleted your files they would likely just be deleted.

More likely you accidently moved the files somewhere and didn't realize this.
Have you searched your system using the search tool?

---

### Post by pinged on 2009-01-11
Well it may have had a command along the lines of

```
rm -rf name_of_dir
```

And to any new users reading this **_NEVER_** type the command above unless you know what your doing

Plus that doesn't show up in trash

---

### Post by MC_LA on 2009-01-12
That's interesting that not all Linux programs uses Trash. I didn't realize it was optional. Thanks for the info. 

I searched my entire drive and the directory isn't found, and I didn't run the "rm" command. The directory was there before I used DeVeDe and then it was gone afterward. This leads me to think that DeVeDe is the culprit. 

My theory is that DeVeDe somehow corrupted my directory table. Do you think this is possible ? and if so, will I likely have more problems unless I repair it ? 

I tried using Foremost, ddrescue, and fsck to fix my directory and recover the lost files, but I wasn't able to get much useful info from them, probably just my lack of knowledge how to use them. Is there a newbie explanation how to use them or easier tools ?

---

### Post by electrogeist on 2009-01-12
> **MC_LA said:**
> I pointed DeVeDe to the directory that is now missing to store the image.

This is a shot in the dark, and I have neve used devede...could it be possible that you created a image file with the exact same name as the directory you meant to store the image in?  

ie. one can have a directory named /home/me/shite/, or one can have a file named /home/me/shite, but both cannot exist at the same time.  

It would be bad behaviour for a program to let you replace a directory.

Ok so I was curious about this program and just tried it.... Using Ubuntu 8.04 and DeVeDe 3.6 from the repository.  Created a directory /home/me/shite, then created a small file with devede with the name shite under /home/shite.  Devede actually named it shite_01_01.avi -- BUT it still deleted the directory I created with a similar name!!  That sucks.

---

### Post by electrogeist on 2009-01-12
(and I am emailing this to the makers, rastersoft, because I did not see it mentioned in the changelog for newer versions)

---

### Post by MC_LA on 2009-01-18
It's possible that I did use the same name.  Thanks for solving my mystery. :)

---

### Post by electrogeist on 2009-01-18
BTW Rastersoft had replied that they didn't consider it a bug but will fix it in the next version of DeVeDe.  

It will probably be quite a while for that next version to appear in ubuntu tho...considering their current version is 3.11b

---

