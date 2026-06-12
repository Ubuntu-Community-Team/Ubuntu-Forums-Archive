---
title: "/some/folder/thumbs.db vs. /home/user/.thumbnails"
date: 2010-03-14
forum: Desktop Environments
---

### Post by MichaelBurns on 2010-03-14
I suppose that this is specifically a nautilus issue.  My simple question is this:  is there a way to set up nautilus so that it will create a "thumbs.db" (like in windows) in each folder?

I just think that this disparity between windows and ubuntu (nautilus?) introduces unnecessary redundancy.  For instance, if I put pictures on my usb stick, most likely the usb stick will be plugged into a windows machine at some point (if I didn't use windows to put pictures on it in the first place).  Windows will either look for a "thumbs.db" file to generate thumbnails, or it will create one, and this is available once and for all (unless it is deleted).  However, ubuntu (nautilus?) seems to completely ignore the "thumbs.db" file, and instead of creating one, it creates individual thumbnail files in "/home/userx/.thumbnails" which must be recreated for each user.  As much as I hate to hear myself say it, in this case I prefer the windows method to the ubuntu (nautilus default?) method hands down.  (I'm sure that there's a good reason why ubuntu handles thumbnails the way that it does; please don't think that I am complaining about ubuntu.)

I realize that I can just turn off the thumbnailer entirely in order to eliminate the redundancy, but if there is a way to handle thumbnails like in windows, that would be my ideal solution.

---

### Post by MichaelBurns on 2010-03-21
bump

---

### Post by asmoore82 on 2010-03-21
The Gnome behavior is correct and the Windows and Mac behavior is totally Broken.

I don't want junk littered all over my drives.

".DS_Store" anyone??

> **MichaelBurns said:**
> I just think that this disparity between windows and ubuntu (nautilus?) introduces unnecessary redundancy.
"disparity" ~ you are absolutely correct there. But should we all adopt the broken behavior?? I think **_not_**.

Just wait long enough for Micro$oft to "innovate" some more and they will start using the Linux/Gnome behavior.
Just like they did for "$HOME folders" versus "Documents and Settings."
Just like they did with breadcrumb buttons in the file browser's address bar.

You know what Gnome behavior I've loved for years?
When you rename a file, it highlights the name but not the extension.
Take a wild guess what Windows Server 2008 R2 does...

---

### Post by MichaelBurns on 2010-03-21
Just to clarify for anyone who would actually like to help me:

**Please ignore the second paragraph of my OP.**  I am not a developer (not yet); rather, I am a lowly user.  The purpose of this thread is not to voice opinions regarding why ubuntu is better than windows.  I just want to find out how to set nautilus to suit my usage, as per the question in the first paragraph of my OP.  I'm only assuming that nautilus is responsible for "thumbnailing", and I welcome a correction on that point.

> **asmoore82 said:**
> The Gnome behavior is correct and the Windows and Mac behavior is totally Broken.
[...remainder of rant deleted for brevity...]I will try to find out if it is OK to drastically edit my OP after such a response.  I would remove the entire second paragraph of my OP, as it seems to provoke Windows-haters who feel compelled to spew their anti-Windows agenda with no regard for the actual question asked in the OP.  As a fellow Windows hater, I don't blaim asmoore; in retrospect I simply should have refrained from typing the second paragraph in my OP.  I appologize for the confusion.

---

### Post by asmoore82 on 2010-03-22
I would say that you are correct that nautilus is the right place to be looking.
But I doubt that there is an affirmative answer out there, as googling "nautilus thumbs.db"
turns up this thread as the second result :razz:

Beyond the obvious philosophical problems(see rant) with such a "feature,"
I would imagine that those reasons combined with technological hurdles would make it impossible...

The technical hurdles I can foresee would be:

Where is the format of thumbs.db documented?

How often does that format change(XP,Vista,7,etc.)?

It would seem to be a waste to implement read-only support for thumbs.db, why not write to it too?
But what about the thumbnails that Gnome/nautilus does that windoze can't or won't(certain videos, pdf's, postscript)?
Should nautilus store these thumbnails in there too? Would that choke up windoze?

---

### Post by asmoore82 on 2010-03-22
Oops, I honestly didn't already know this, but they already started
moving towards the Gnome/Linux way with Vista..
> **Beginning with Windows Vista, thumbnail previews are stored in a centralized location on the system**.
This provides the system with access to images independent of their location, and addresses issues with the
locality of Thumbs.db files. The cache is stored at %userprofile%\AppData\Local\Microsoft\Windows\Explorer
as a number of files with the label thumbcache_xxx.db (numbered by size); as well as an index used to find
thumbnails in each sized database.
[http://en.wikipedia.org/wiki/Windows_thumbnail_cache#Thumbcache](http://en.wikipedia.org/wiki/Windows_thumbnail_cache#Thumbcache)

---

### Post by MichaelBurns on 2010-04-14
bump

---

### Post by bourrinlepoulpe on 2010-04-18
> , but if there is a way to handle thumbnails like in windows, that would be my ideal solution.
__________________
Don't you dare tell me to use Windows.

That s quite funny ^^

---

### Post by MichaelBurns on 2010-06-28
To anyone out there who actually wants to help:

Please ignore all but the OP (first and third paragraph), as the rest of this thread is worthless.  Thanks.

---

### Post by rac9876 on 2010-08-21
The main problem I see with the Nautilus behaviour is how it leaves permanent traces of drives that are only temporarily mounted. Suppose - purely hypothetically now - that I were to have a Truecrypt volume containing files of - ahem - a graphical nature (cough) that I'd rather others did not see. I mount the Truecrypt volume, do my "research" and, say, 15 minutes later, breathlessly unmount the Truecrypt volume. Nautilus leaves thumbnails of images from the encrypted volume unencrypted under my .thumbnails folder.

In this case would it not be better to put the thumbnails inside the encrypted volume so that they become inaccessible when the volume is unmounted? My example is frivolous but it could be a serious issue if the encrypted volume contained security-sensitive images.

---

### Post by MichaelBurns on 2010-11-20
Thank you, rac, for finally affirming the potential legitimacy of this issue.  It's nice to see that at least someone else here recognizes this as a potential problem instead of bowing to the almighty will of ubuntu.  Unfortunately, you are also apparently also in the same situation as me, not personally competetent enough to fix this problem yourself, so the two of us are just out of luck.  I still haven't gotten over the shock that someone here, on these Linux fora, would use the eventual adoption of a feature by MS Windows in order to support of their argument that the feature is good.  I'm just a lowly user who wants my computer to work in a particular way.  Apparently, instead of doing that, ubuntu (or at least most forum members here) wants to convince me that the ubuntu way is the way that you should want your computer to work, and to hell with anyone who disagrees.  They may have convinced Microsoft; good for them.  I wonder how many others here seriously consider the actions of Microsoft to be in the interest of the computer user.  Or maybe my worst fears are subtly validated ...

---

