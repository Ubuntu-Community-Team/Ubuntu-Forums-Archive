---
title: "can not open .jpg from smb mount"
date: 2005-12-31
forum: General Help
---

### Post by Mcclamm on 2005-12-31
Hi all, I have just installed Ubuntu this week and so far all is going great with one minor exception.  I have built this machine for my wife to use as a general purpose machine providing internet access and the ability to browse her huge picture archive  that stored on a Win XP machine (sorry).  So far I have been able to access the XP machines file share using Nautilus and then I created a bookmark so the share is easy to find dirrectly under the places menu.  

Now this is where things get a bit odd, the images do not appear with a thumbnail (just a slide icon) and if I right click and select open with anything other then firefox (such as Image Viewer) the file never opens.  If I copy the file to my local desktop from the share all works perfect.   Any ideas?

Not sure if this information will help or not but if use firefox and enter the URL  smb://video/Pictures/Pictures%202000/ I can see the directory listing but no thumbnails here either, if I click anyone of the jpg's they open properly in firefox.  Unfortunatly this is not really a work around unless someone knows how to make firefox preview jpg's in a dirrectory listing as the digital cameras file names are not very descriptive and opening up each picture one by one kind of defeats the point of browsing your photos (she has Gigs of photos in many directories).

Any advice would be great,
 - Mike

---

### Post by Mcclamm on 2006-01-02
Bump - Can someone please help?  I am taking a bit of flax from my wife on the fact that I replaced her machine with Ubuntu.  Other than this one thing it is working great for us.

Should I be posting somewhere else?

Thanks in advance,
 - Mike

---

### Post by Mcclamm on 2006-01-09
Please reply.  Any assistance would be great.

---

### Post by zoiks on 2006-01-09
Images not appearing in the thumbnails when using a url with nautilus is default.  You can change it by going to "Edit|Preferences", selecting the Preview tab, and changing the "Show Thumbnails" setting.

To open an image out of a folder, try using "Open With..." and choosing the gThumb Image Viewer.  That seems to work for me.

You can also try mounting the share to your filesystem in fstab, using the type "smbfs".  Then it will just act like your files are part of your local filesystem.

Hope this helps.

---

### Post by Mcclamm on 2006-01-09
thanks, appricate the help.

What should the entry in fstab look like?  I have 

//192.168.0.167/video   media/pictures  smbfs  rw  0   0

any idea why it does not work?

---

### Post by zoiks on 2006-01-09
You should put a slash in front of "media".  Also, you might need options like "credentials=<path to credentials file>,uid=xxx,gid=yyy".  You can check "man mount" and "man smbmount" for information on the options.  Also, make sure the mount point /media/pictures is rw-able by either world or the user you are mounting it for.

This might be old info, but I haven't actually mounted smbfs in a year or two.  When I did, it overall worked, but my systems had problems if the network connection got flakey or the server was rebooted.  Things may be a lot better now.

For permanent mounts, I use nfs now.  If you aren't worried about accessing from Winblows, you might look at this.  It's bascially the same idea as mounting via smbfs, but it's mroe *nix native and seems to be more stable, as well as faster.

If you can just change the Preferences as I described earlier, and use gThumb for picture viewing, that should still be a valid option, too, using smb://... within nautilus.

---

