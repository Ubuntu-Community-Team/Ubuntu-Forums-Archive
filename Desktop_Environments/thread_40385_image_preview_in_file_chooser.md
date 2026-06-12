---
title: "image preview in file chooser"
date: 2005-06-08
forum: Desktop Environments
---

### Post by mrt on 2005-06-08
is there a plugin or anything that would add thumbnail previews for images in the File Chooser?  It's hard to believe its not like that by default.

---

### Post by bored2k on 2005-06-08
[QUOTE=mrt]is there a plugin or anything that would add thumbnail previews for images in the File Chooser?  It's hard to believe its not like that by default.[/QUOTE]
 Nautilus file manager does preview images by default. Go to edit - preferences - previews to re-set that up.

---

### Post by mrt on 2005-06-08
I don't think you understood me.  I'm not talking about Nautilus the file manager; I'm talking about the File Chooser:
[IMG]http://i5.photobucket.com/albums/y159/p1200tog/Screenshot.png[/IMG]
It would be very convenient if small previews of the currently selected image were shown.

---

### Post by paszczak on 2006-10-10
that's damn good question, when i send mail with attach the preview is avalible, but when i'm uploading images to google' picasa web album there is no preview...any ideas?

---

### Post by SergeiFranco on 2006-12-05
I'm desperatly after that feature aswell, maybe it is possible to force file chooser to use preview option all the time? I would expect something like that to have a "view" option where you can select list->icons->thumbnails.... It just makes it really complicated when you have folder with hundreds of pics with names looking like PBXXXXXX.jpg and have no option to preview....
If there is no option, my other choice would be swithcing to konquerer (I'm already running xfwm4 instead of metacity...).
Here is the related thread by someone else:
[http://ubuntuforums.org/showthread.php?t=234598]("http://ubuntuforums.org/showthread.php?t=234598")

BTW I'm after that feature for Firefox and Thunderbird....

---

### Post by SergeiFranco on 2006-12-06
I found the hack to make Firefox and Thunderbird use the KDialog instead of gnome filepicker (hack consists of replacing nsFilePicker.js files in the firefox and explorer program folders found here [http://www.kde-look.org/content/show.php?content=13967]("http://www.kde-look.org/content/show.php?content=13967")).
The problem with it is that the screen redraw behind the KDialog is not very reliable (i'm using gnome) if you resize or move the dialog....

---

### Post by leona on 2006-12-07
oh, well I'm glad I'm not the only one having this problem, yes it would be nice to see a preview of an image befor eyou attach / upload it, guess its anothe for the 'to do' list.  
Seems a bit odd that this has been overlooked, again its something windows has done for years, why is linux still playing catch up?
I mean what use is a a list of filenames if its off a camera?  How are you supposed to kow which one you want? Doesn't even show you file sizes either.

---

### Post by CarpKing on 2006-12-08
> **SergeiFranco said:**
> I found the hack to make Firefox and Thunderbird use the KDialog instead of gnome filepicker (hack consists of replacing nsFilePicker.js files in the firefox and explorer program folders found here [http://www.kde-look.org/content/show.php?content=13967]("http://www.kde-look.org/content/show.php?content=13967")).
The problem with it is that the screen redraw behind the KDialog is not very reliable (i'm using gnome) if you resize or move the dialog....

I seem to recall hearing that this fix gave the KDE file dialog but without thumbnails.  Is this not the case?

---

### Post by SergeiFranco on 2006-12-18
It is possible to choose "thumbnails" view option which is a lot better than just a file name. Still this hack is very buggy. But it works for both Firefox and Thunderbird, it involves replacing file FilePicker.js in both application.

---

### Post by Wide on 2007-05-17
Has there been any update on this?

Trying to upload a picture file has been quite difficult to choose without opening a second view

  :)

---

### Post by Beatbreaker on 2007-07-08
BUMP - are there any updates on this one?

---

### Post by Beatbreaker on 2007-08-01
ok i see a solution to this - dump Ubuntu and start using Sabayon.

Done.

---

### Post by thegreenman on 2007-08-12
Bump, still looking at icons instead of thumbnails which is just plain bad. 

Someone has to have figured this out.... no? 

Thanks

TGM

---

### Post by battleroyalex on 2007-10-22
any updates for this?

---

### Post by ms-07 on 2007-10-24
i'm a new Ubuntu user and this is bugging the hell out of me.

---

### Post by aysiu on 2007-10-24
No updates that I know of, apart from ditching Firefox for Galeon or Konqueror.

---

### Post by Wide on 2007-10-24
> **aysiu said:**
> No updates that I know of, apart from ditching Firefox for Galeon or Konqueror.

Thank you for seeing this post, hopefully it may get picked up:)

---

### Post by pixelstuff on 2008-02-26
bump!!
I am working with LOTS of pictures - any new solutions out there? There must be a script or something... ](*,) I also need such a feature in Gimp who has a preview window - no use in clicking on 200 images and waiting for their previews to load! I want all the files as thumbnails like in nautilus in all programs or even their mini-icons replaced with thumbnails! :lolflag:

---

### Post by sicofante on 2008-04-15
I just can't believe this hasn't been addressed by Gnome developers, who are supposedly so worried about usability. This post is almost three years old. Just amazing.

---

### Post by Victor_Os on 2008-04-16
This had been fixed in GNOME 2.22. Ubuntu 8.04 will have it.

---

### Post by sicofante on 2008-04-16
I'm trying the beta and I can't see it. I can see a preview of each image I click on, is that what you mean? This is not what's needed, obviously. A thumbnail view **of all images at once** (instead of file names), like the one you get in Nautilus, is the only sensible approach.

---

### Post by aysiu on 2008-04-16
> **sicofante said:**
> I'm trying the beta and I can't see it. I can see a preview of each image I click on, is that what you mean? This is not what's needed, obviously. A thumbnail view **of all images at once** (instead of file names), like the one you get in Nautilus, is the only sensible approach. I've got to disagree with you there. A thumbnail view of all images at once is the *best* (or ideal) approach. But the previewing of each image you click on is still better than what we had before (which was no preview at all).

I think it's a lame compromise, but it is still an improvement (however minor).

---

### Post by Victor_Os on 2008-04-17
I see both a large preview of the selected image on the right side of the file picker window, and small thumbs of the images as the file icons. This behaviour is similar to nautilus in list view.

I agree that large thumbnails would be better, but we will have to wait a bit more.

PS: I was going to post a screenshot, but couldn't figure out how.

---

### Post by aysiu on 2008-04-17
> **Victor_Os said:**
> 
PS: I was going to post a screenshot, but couldn't figure out how. [This](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4) should help.

---

### Post by Victor_Os on 2008-04-17
aysiu, thanks.

I am attaching a screen shot that shows how this works in Hardy.

---

### Post by aysiu on 2008-04-17
> **Victor_Os said:**
> aysiu, thanks.

I am attaching a screen shot that shows how this works in Hardy.
Thanks. That's not how it looked in Hardy Alpha. Glad to know they've fixed it since.

---

### Post by binary.koala on 2008-05-01
hi, in my nautilus 2.22.2 (gutsy -> hardy) i still have to preview. do i need to fix something using gconf-editor? perhaps preference files did not get updates or so... any clue?

--
update, there is no preview when picking a file with firefox (2.0.0.14), otherwise in preview works, changing background for example.
still, how do i get the same in firefox?

--
update2, okay, they say it's fixed for firefox 3, but e-x-c-u-s-e me, that thing sucks, at least for now. whatta pity.

thanks,
d

---

