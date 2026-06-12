---
title: "Theme help required"
date: 2010-10-22
forum: Desktop Environments
---

### Post by elanning on 2010-10-22
Greetings,

Simple question.  Downloaded maybe half a dozen themes from art.gnome.org and every one that I try to install says "does not appear to be a valid theme"

I tried the drag and drop into the appearance preferences box, and using the install button on the box.  Same result an all themes I tried.

I must be missing something simple, any advice?

Thanks.

---

### Post by ankspo71 on 2010-10-22
Hi,

First, the themes must be in a tar.gz (or .tar.bz2) archive or else they can't be installed via drag and drop (or the install button).

If they are a .tar.gz achive and you still have trouble installing them, then it is because the have been packaged using too many folders. I noticed this happens too many times.

It should be like this:
theme.tar.gz -> themefolder -> theme contents (Gtk + Metacity folder etc).

Not like this:
theme.tar.gz -> themefolder -> [COLOR="Red"]themefolder(again)[/COLOR] -> theme contents (Gtk + Metacity folder etc).

Sometimes themes get packaged twice too (.tar.gz inside a .tar.gz), another reason why they can't install

For any themes that won't install, those themes will have to be manually extracted and installed. You can install them to a hidden folder in your home folder called ".themes". If the folder is not there you will need to create it, and make sure it has a dot in front of the name.

If you have multiple users on your computer, you can install them to /usr/share/themes that way everyone has access to them. 

Hope this helps.

---

### Post by mcduck on 2010-10-22
> **elanning said:**
> Greetings,

Simple question.  Downloaded maybe half a dozen themes from art.gnome.org and every one that I try to install says "does not appear to be a valid theme"

I tried the drag and drop into the appearance preferences box, and using the install button on the box.  Same result an all themes I tried.

I must be missing something simple, any advice?

Thanks.

Could you perhaps give an example of a file you have tried?

There are many kinds of themes that affect different things, an not all of them are installed through the Appearance preferences (As many of the themes have nothing to do with individual user's desktop appearance).

If you are absolutely sure the theme you have downloaded is a GTK2 or Metacity theme, it could be possible that it's just packaged in a wrong way (although that's unlikely as you said you have tried many themes). In that case you can simply extract the theme into ~/.themes manually. Icon thems go to ~/.icons, of course.

---

