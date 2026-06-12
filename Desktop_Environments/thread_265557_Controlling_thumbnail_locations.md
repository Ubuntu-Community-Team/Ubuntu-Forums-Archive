---
title: "Controlling thumbnail locations?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Blueshell on 2006-09-26
I'd like the File Browser's thumbnailer to use a .thumbnails directory inside each directory it's thumbnailing, instead of ~/.thumbnails.  I've done a bit of searching and also looked at likely options in gconf-editor, but don't see a way to do this.  The current behavior is incredibly irritating if large directories of images get moved around, because Nautilus (a) spends a long time regenerating thumbnails it already had in the old location, and (b) never cleans up after itself, which means ~/.thumbnails winds up with large amounts of stuff that will never go away.  (Yeah, I could get clever with a cron job and GQView's orphan-thumbnail detection, but that seems really painful compared to just keeping the thumbnails with the associated files.)

Is there any way to handle this in a more-elegant fashion?  My preference would be to have the File Browser and GQView agree on where thumbnails go, and for that to be associated with the directory in which the original images are.

Tnx.

---

### Post by VON_CAPO on 2007-12-04
OK, I believe I found a smart workaround (until the Gnome developers in a very far future fix it)

---> [http://linux.softpedia.com/get/Multimedia/Graphics/updateThumbnails-28899.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/updateThumbnails-28899.shtml)

This plus GQview should help. :)

---

### Post by Blueshell on 2007-12-05
Wow, thanks!  After 14 months, I'd forgotten I'd even -written- that, much less thought there'd be an easy solution...

I'll download it and give it a whirl; if it works, I'll just never use Nautilus again, probably.  (I do all my image viewing with GQView anyway.)

---

### Post by VON_CAPO on 2007-12-07
I have a collection of around 120.000 pictures, some folders have more than 1000 pictures.

And, yes, to browse with Nautilus is very painful.

I did not try it yet, but I will next week.

I will post the results.

---

