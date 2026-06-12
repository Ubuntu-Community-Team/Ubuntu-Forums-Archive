---
title: "Nautilus File Previews"
date: 2005-04-15
forum: Desktop Environments
---

### Post by ions on 2005-04-15
Why does Nautilus preview some files and not others automatically?  Sometimes I'll download an avi and it will automatically do that nice preview icon and sometimes it won't.  Now to make it change the standard non-preview icon all I have to do is change the filename and it automatically becomes a preview icon.  

Here's an example in pics if I haven't explained this well:

[Before](http://home.cogeco.ca/~ionsvw/images/FilePreviewBefore.jpg)
[After](http://home.cogeco.ca/~ionsvw/images/FilePreviewAfter.jpg)

Notice the icon has changed for Wobbly Windows as well as the filename, I changed the filename, that's how I got the icon to change.  In that screenshot there are two .swf files.  Neither of which have had their filenames changed yet one automatically shows as a preview.

I'd like this preview to be automatic.  I have looked at the System -> Preferences -> File Management settings and have it set to 'Show thumbnails: Always'  'Only for files smaller than: 1GB'.  Nothing changed.

Any ideas how to make this preview automatic?

---

### Post by kassetra on 2005-04-16
[QUOTE=ions]Why does Nautilus preview some files and not others automatically? Sometimes I'll download an avi and it will automatically do that nice preview icon and sometimes it won't. [/QUOTE]

Ok, here's the issue you're facing:
When nautilus constructs the previews for a folder, it looks to see what codecs are installed.  If you don't have the correct codecs installed, it creates a list of icons instead of preview thumbnails.

Now, when you add a new file to that folder, if you have the codecs installed, a preview thumbnail will show, but the files nautilus previously rendered as icons will not change.  If you rename the file, it will change nautilus' thumbnail cache.

If you want this to be "permanent" ... you have to make sure that you remove the ~/.thumbnails directories after you have the codecs installed.  Since you now have them installed, judging from the preview thumbnail screenshot.  Simply remove that ~/.thumbnails directory out of all of the folders you want preview in.

---

