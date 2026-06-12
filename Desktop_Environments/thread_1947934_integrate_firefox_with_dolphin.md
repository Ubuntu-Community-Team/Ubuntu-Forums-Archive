---
title: "integrate firefox with dolphin"
date: 2012-03-27
forum: Desktop Environments
---

### Post by forsubhi on 2012-03-27
when the download completed in firefox and I click on open containing directory ,I want  to open the dolphin program not  Nautilus 

how can I do this ?

---

### Post by Zorael on 2012-03-29
System Settings -> Default Applications -> File Manager, pick Dolphin.

---

### Post by forsubhi on 2012-03-30
it is the Default , but firefox still open  Nautilus in kubuntu 11.10

---

### Post by SeijiSensei on 2012-03-30
In firefox, Edit > Preferences > Applications.  What application do you have associated with "file"?  On my Kubuntu machine it says "dolphin".

---

### Post by Zorael on 2012-03-31
To be honest I don't know where Firefox looks to see what file browser to open.

Could you try this in a terminal, please?
```
$ xdg-mime query default inode/directory
```
It should say **dolphin.desktop**. Likewise running '**xdg-open ~**' should open your home directory in Dolphin.

If it doesn't, that's curious.

---

### Post by SeijiSensei on 2012-03-31
> **Zorael said:**
> To be honest I don't know where Firefox looks to see what file browser to open.

Did you read my answer just above yours?  Firefox maintains its own list of file associations managed from Edit > Preferences > Applications.

---

### Post by Zorael on 2012-03-31
Yes, but is it a compatibility thing? Does it really ignore the xdg mime-cache this way?

---

### Post by SeijiSensei on 2012-03-31
> **Zorael said:**
> Yes, but is it a compatibility thing? Does it really ignore the xdg mime-cache this way?

Who knows?  Firefox has managed its own application assignments for as long as I can remember.  It probably arose from the need to make it cross-platform.  And, frankly, I don't see whether it matters if it ignores xdg mime-cache or not.  The OP wanted to tell firefox to use dolphin for files and directories.  I doubt he/she cares about xdg either.

---

### Post by Zorael on 2012-03-31
> **SeijiSensei said:**
> Who knows?  Firefox has managed its own application assignments for as long as I can remember.  It probably arose from the need to make it cross-platform.  And, frankly, I don't see whether it matters if it ignores xdg mime-cache or not.  The OP wanted to tell firefox to use dolphin for files and directories.  I doubt he/she cares about xdg either.
I'm sorry, but it seems to me it very well does if Firefox prioritises those settings. xdg being xdg is quite beside the point; as an analogy, I don't care a single whit about how my printer works (or the makers behind it) as long as it prints what I ask it to. It's printing the wrong page here, and saying that it doesn't matter if it ignores the mime-cache is akin to saying that it doesn't matter if the printer prints my pages in webdings, just as long as the paper tray isn't empty. In both cases the printer would be useless to me, and you would be ruling out one possible cause.

I'm sinking into details, but as you likely well know XDG (freedesktop) itself is an effort towards cross-platform standards. The command I listed would quickly and painlessly make apparent to what degree Firefox complies.

Changing the setting in System Settings should make the necessary file changes (mimeapps.list), which after a mime-cache update would make all and every xdg-aware application (like Firefox) use the new setting; *unless* they have their own file/mime association records which they favor instead. Casual googling shows that xdg-utils debuted in 2006, and we all know that Mozilla-later-Firefox has been around for much longer. Ironically, those own settings makes it *less* cross-environment-friendly.

- If it favors those Preferences entries above the mime-cache, then yes, changing those would make it open Dolphin. *Deleting* those would make it open Dolphin.
- If it favors the xdg setting, then entry changes will have zero effect -- and my easily-copypasted one-line command would tell.

It's not difficult to imagine arguments for prioritising either setting above the other.

We can judge likelihoods, but *we don't yet know* if this is due to System Settings failing to make the changes (eg. bad file permissions), mime-cache refresh failing (eg. xdg-utils and/or kbuildsycoca4 error), or Firefox not listening to the cross-platform cross-environment easily-change-it-here-instead-of-individually-per-application xdg settings, doing its own race instead. It may very well be Firefox, but unless you know more than Firefox than I do, *there is not yet enough data to tell* before we know the output of the xdg-mime query.

---

### Post by forsubhi on 2012-03-31
In firefox, Edit > Preferences > Applications.  What application  do you have associated with "file"?  On my Kubuntu machine it says  "dolphin".

I didn't find file in 
In firefox, Edit > Preferences > Applications 

and I try 

xdg-mime query default inode/directory It should say **dolphin.desktop**. Likewise running '**xdg-open ~**

and it work good , but the problem still occur
[IMG]http://img7.imagebanana.com/img/lble8bxw/Selection_004.png[/IMG]

---

### Post by forsubhi on 2012-03-31
by mentioning scholarship , Do you know any good scholarship ? :lolflag:

---

### Post by caco3 on 2012-05-27
I have the same issue.
There is no entry "file" in my firefox. Also there is no way to add it.

I tried to remove nautilus and add a symbolic link to dolphin:
ln -s /usr/bin/dolphin /usr/bin/nautilus
The link works, how ever firefox now opens gwenview as filemanager.
This is very annoying... :(


xdg still correctly uses dolphin.

---

### Post by mniasfreemag on 2012-07-28
If anybody still has the problem with firefox opening with nautilus, try changing the inode/directory at this location "/usr/share/applications/defaults.list". Here chande the inode/directory fron nautilus.desktop to dolphin.desktop.

That  did the trick for me

---

### Post by X_Splinter on 2013-01-15
> **mniasfreemag said:**
> If anybody still has the problem with firefox opening with nautilus, try changing the inode/directory at this location "/usr/share/applications/defaults.list". Here chande the inode/directory fron nautilus.desktop to dolphin.desktop.

That  did the trick for me

Didn't work for me :sad:

---

### Post by X_Splinter on 2013-01-15
Now it works, the solution was to install kmozillahelper

---

