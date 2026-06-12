---
title: "Install a Thunderbird plugin to Thunderbird (not the user folder)"
date: 2009-10-03
forum: Desktop Environments
---

### Post by beterhans on 2009-10-03
HI All
I'm using the Thunderbird come with the Ubuntu not from mozilla site

I want to install a plugin, but not in my user folder.

If Im using the Moillz tar.gz version. I know who to do it.  just copy the Plugin folder to /usr/local/thunderbird/extenstions 
them everyone can use this plugin.

but How to do this with a deb thunderbird?

---

### Post by Findarato on 2009-10-03
I don't really get your question, but if you're looking how to install your plugin, you should normally go through the "install extention" in the thunderbird menu somwhere (forgot where exactly it is, but probably under "tools" :)).

---

### Post by beterhans on 2009-10-03
example: Normal Install
Fire up thunderbird and Select the Addon. Install Plugins... reboot...
them the plugin will get installed to your User Folder. /home/username/.mozilla-thunderbird/profile/xxxxx/extenstions/xxxxxxxxxx
Only the user can use this plugin

But I don't want this way. I want install to thunderbird Installation path.
example: thunderbird tar version from mozilla
the Thunderbird is installed at /usr/local/thunderbird
them just mv the  /home/username/.mozilla-thunderbird/profile/xxxxx/extenstions/xxxxxxxxxx to /usr/local/thunderbird/extenstions/xxxxxxxx

them all users can use this plugin.

my question is how to do this on ubuntu deb thunderbird. it doesn't have the extensions folder

---

### Post by wojox on 2009-10-03
Try /usr/lib/thunderbird/extensions/

---

