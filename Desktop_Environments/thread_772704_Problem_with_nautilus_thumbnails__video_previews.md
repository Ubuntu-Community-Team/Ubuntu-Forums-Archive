---
title: "Problem with nautilus thumbnails / video previews"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Snyper64 on 2008-04-28
Originally I was having trouble with some of my movie files displaying previews properly in in my folders. I'm not sure what I did but I seemed to have almost fixed that problem completely. Right now all of my video file types are display fine with one exception: Whenever I download something to the Desktop or leave my Azureus folder open while I am downloading the preview will not show up even If I refresh the folder. The only way to get the preview to display is to cut and past the video file into another folder and refresh that folder. In Gutsy I did not have any problems with getting folders to display properly but upon doing a fresh install of Hardy(and switching back to 32 bit) I get this strange problem. I have searched the forums and have found 2 threads that say to delete the .Thumbnail folder and the mime file(which I did) but it still did not help. I remember back in Gutsy that as my files were downloading they would refresh about every 20 seconds and show a quick thumbnail until the file completely finished and it displayed the final thumbnail. Hardy does not seem to do this. Am I missing a lib file or is there a setting somewhere that I am missing?

Any help would be greatly appreciated
Thanks
Snyper64

---

### Post by Snyper64 on 2008-05-02
bump

---

### Post by Snyper64 on 2008-05-04
bump

---

### Post by Snyper64 on 2008-05-08
bump

---

### Post by Snyper64 on 2008-05-30
bump

---

### Post by WarmonkeyUK on 2010-08-30
Sorry to awaken a dead thread, but this is a long-term issue. As I'm sure most people know, if you start say, downloading a video file, and look at the directory in Nautilus, you'll see two files - the final file, and a temporary file, deleted upon successful completion of the download. The problem is that our default thumbnail generator immediately springs into action, attempting to create thumbnails for both files, which both fail, leaving a generic icon. When the temporary file is deleted, the final video file will not have a preview thumbnail.  The only workarounds people have provided are to delete the thumbnail files stored at ~/.thumbnails, or to move the video file to another directory. This has been the case for years, and it's a bit of a crap workaround! What ideally we need is the thumbnail generation program to regenerate a thumbnail when a file changes, or some sort of easy button click to manually force the process, rather than having to use console commands. How much effort would it be to do such a thing?

---

### Post by Snyper64 on 2010-08-30
I don't know, I would think it would be an easy fix to add a reload button for the thumbnails(or add thumbnail regeneration to the reload button). Has anybody made a launchpad report for this?

---

### Post by Mayki8513 on 2010-09-23
I saw this in launchpad already but it doesn't look like anything fancy will be done soon,
if you don't mind workarounds,
here's what I did,
the failed generic thumbnails are saved in:
"$HOME/.thumbnails/fail/gnome-thumbnail-factory"
so I cd to ~/.thumbnails/fail
then change the permissions of gnome-thumbnail-factory to 000 so NOTHING can be saved in it,
because nautilus can no longer save the thumbnail,
it keeps re-attempting,
until of course it finally makes a good thumbnail,
if you do come across a file that seems to load forever,
you can easily assign one yourself by right clicking -> properties,
and clicking on the thumbnail button,
so if you do have a file like that,
just take a snapshot of a movie frame and assign that ;)

---

### Post by Snyper64 on 2010-09-23
Nice trick, I will have to try it out.

---

