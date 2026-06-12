---
title: "Changing mimetype icon sets?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by mcmunt on 2005-12-04
I've slowly made Ubuntu 5.10 into something more personalised than the basic brown with themes and associated icon packs. But how to I modify a select few mimetypes to different icons?
eg. I want a different icon for all tar.gz or zip files than what is in the icon pack. I can easily change it on a per-file basis but can't find how to do it for all file types.
Any one care to enlighten me, as I'm sure it's pretty staright forward?;) 

Cheers

---

### Post by mcmunt on 2005-12-05
Bump:smile:

---

### Post by pmj on 2005-12-05
The easiest way is probably to manually replace the icons for the theme you're using. Icons are stored in .icons/<name of theme> in your home directory.

---

### Post by mcmunt on 2005-12-06
Mmm, that's what I thought too.

No one else have any easier way? How does Ubuntu know which icon to use for which mimetype in the theme?

Thanks

---

### Post by pmj on 2005-12-07
The mime information is stored in the files /usr/share/mime/packages/freedesktop.org.xml and ~/.local/share/mime/packages/freedesktop.org.xml.

You can add new mime types in the file ~/.local/share/mime/packages/Override.xml, but as far as I know you can't add a duplicate entry in this file only with a new mime type to get a new icon for it.

The only way I know of to modify an existing mime type is to edit the files I mentioned above. I've read that these files shouldn't be edited, so be careful and make backups before doing anything with them.

Now, say you want to change the icon for .torrent files. To do this, open *both* of the the freedesktop.org.xml files and find the entries for BitTorrent. You'll see a line in each file that says <mime-type type="application/x-bittorrent">. Replace x-bittorrent with something else, like x-bittest. When both files are updated, run the commands "update-mime-database ~/local/share/mime" and "sudo update-mime-database /usr/share/mime".

Now you have to add the new icon to the hicolor theme. In my example it should have the name gnome-mime-application-x-bittest.png and it should be placed in /usr/share/icons/hicolor/48x48/.

The new BitTorrent icon should now stay the same in any icon theme.

Yeah, it's messy, and I wouldn't be surprised if there was a much better way to do this. But it doesn't look like anyone else here knows about it either.

---

### Post by aysiu on 2005-12-07
My mimetype icons for my icon theme are in /home/username/.icons/themename/scalable/mimetypes/

I don't know if that helps...

---

### Post by pmj on 2005-12-07
The problem is that when you download a new theme your custom icons will be gone and you'd have to perform the icon replacing procedure all over again. It's possible to always have the same icon for a certain file type, which I believe is what mcmunt wants. You probably have to be pretty desperate to use my "solution" though. ;)

---

### Post by Perfect Storm on 2005-12-07
pmj's way is the way to go. It's a long and a slow process but worth it.

---

