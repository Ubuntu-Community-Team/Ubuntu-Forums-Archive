---
title: "nautilus doesnt preview videos !!!!"
date: 2004-11-05
forum: Desktop Environments
---

### Post by galatran on 2004-11-05
Hi ! Ubuntu rocks people ! I love it, but the only thing I cant get to work right is Video Thumbnails in Nautilus, Totem is installed, i removed/reinstalled 20 times, with gstreamer and xine, no signs of the video thumbnails (yes, in preferences its set to always preview), but , it works with a realmedia (.rm) file !!! i can see the thumbnail!!! is it a codec issue or what ?? am I missing something of the new MIME type ? Gnome 2.6 did it right.

 I work a lot with videos so its very important to me.   :cry: 

thanks people!

Ubuntu for everyone now.

---

### Post by Nikola on 2004-11-10
This drives me nuts!
I've updated Nautilus, gstreamer, totem (tried both xine and gstreamer), have all codecs, I'm using Hoary now, but still no luck.

---

### Post by ColdSteel on 2004-11-10
Try a del -rf ~/.thumbnails and then a refresh of your directory. Oh and you need to use totem-xine :)

---

### Post by Nikola on 2004-11-10
Yeah, works now  =D>

---

### Post by poptones on 2004-11-10
FWIW and so there's no mystery for others who may look here for help with a similar problem: if you browse a folder without the proper multimedia widgets Nautilus will still make "default" icons for all the media files, and these will remain in your user profile. This means they will still be there AFTER you install the proper multimedia support, so it will look like things are still broken because Nautilus will just use those it has rather than rebuilding them.

After you have changed (for example) gstreamer-totem into xine-totem, open a command prompt and type this: 

rm -rf ~/.thumbnails/normal/*
rm -rf ~/.thumbnails/fail/*

This will wipe out ALL your Nautilus thumbnails, forcing it to recontruct them next time you browse into the folders. Et voila!

---

### Post by WirelessMike on 2005-01-26
I tried everything suggested here in Hoary and am still unable to view thumbnails.  I haven't found, however, a .thumnails directory under my home.  Perhaps this has changed with recent updates to Gnome 2.8?  Would tweaking the .nautilus directory somehow help?  Any suggestions are appreciated!

**UPDATE**

Tried again and it worked.  Go figure.

---

### Post by MaxFun73 on 2005-01-28
I have the same problem, Nautilus doesn't  show me the thumbnails!
If I click on the video (avi, divx, xvid, wmv) either with totem or xine, all works without a flaw. 
Does anibody knows how can I see the thumbnails?

---

### Post by zworlddiver on 2005-02-26
I had a similar problem with gnome 2.6 and the link below helped me solve the issue.  I had already tried to rm my .thumbnails directory to no avail.  Then I edited the user.keys file which fixed it.

In short, edit ~/.gnome/mime-info/user.keys and remove anything AFTER the = in lines with: icon_filename=/some/path/to/your_icon.png

Do this for any files that you would like to have the associated application display previews for.  And don't forget to make a backup FIRST...

The link:
[http://www.neologe.com/tutorials/tutorial_gnome_mimetypes.htm](http://www.neologe.com/tutorials/tutorial_gnome_mimetypes.htm)

---

### Post by lafnlab on 2007-09-01
Nice to dig a thread out of the past. 

I've been having this going one for awhile now - over a year. I recently updated to edgy eft (yes, I know fawn is out and gibbon will be out soon) and I was surprised this didn't get "fixed" by the upgrade. 

I was curious about it, but it only just dawned on me to Google it. 

With Synaptic, I added totem-xine which caused the totem-gstreamer package to be removed. Then I   deleted the thumbnails directories per **poptones** instructions.

I didn't see any files or directories named mime-info or user.keys. I looked in the .gnome, .gnome2, and .nautilus directories. At any rate. It appears I don't have to worry about it since the thumbnails are appearing.

---

