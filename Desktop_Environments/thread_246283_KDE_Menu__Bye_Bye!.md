---
title: "KDE Menu:  Bye Bye?!?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by gunksta on 2006-08-29
I started with ubuntu-desktop. I installed kubuntu-desktop. All was well. I was playing around with trimming some unnecessary libs from my system and somehow killed my KDE Menu.

I finally discovered that for some reason the file:
/etc/xdg/menus/applications.menu
was missing. So, I reinstalled everything that needed to be and I manually replaced applications.menu with the original file.

Cool. Now GNOME is happy and has a menu again. KDE does not.

I have tried using kbuildsycoca, deleting ~/.config, and other ideas I have seen here on the forums, but I'm not getting anywhere. If anyone has any ideas, I'm all ears.

I've been beating my head against this for long enough. I'm going to bed and hope someone smarter than me has seen this before.](*,) 

--andy

---

### Post by gunksta on 2006-08-29
EDIT: The following will restore your menus but I've just discovered that it leaves Guidance and Kcontrol empty and useless while putting all of the useful stuff in Lost and Found. This is an xdg related problem I think. See my next post.
Thanks
--andy

Woo Hoo.

After more time and effort beating myself up than I will ever admit to in public, I finally figured it out. I'll list the solution here in case it's useful for anyone 
else in the future.

If your KDE menu disappears try these steps. First, try removing ~/.config/ and ~/.local/. If this doesn't change anything, look in /etc/xdg/menus/. You should have several files in there. GNOME uses applications.menu and KDE uses KDE-applications-menu. Somehow, both of these files got deleted on my system so I lost ALL of my menus! Not pretty at all, I assure you.

The KDE menu is hiding in kdelibs-data_version#-ubuntu#_all.deb. I tried simply reinstalling the file, but it didn't work, I had to replace the file manually. Ark can not open .deb files but file-roller can. If you don't have file-roller installed:
```
sudo aptitude install file-roller
```

Copy the latest version of kdelibs-data to your home directory.

```
cp /var/cache/apt/archives/kdelibs-data* ~
```

Use file-roller to open up the latest package if there is more than one...but it shouldn't really matter since this file doesn't change much. Since this is a .deb, you will find a control.tar.gz and a data.tar.gz file. Extract the data.tar.gz file and open it. You now need to locate and extract /etc/xdg/menus/kde-applications.menu to your home directory. Now move it in!
```
sudo mv kde-applications.menu /etc/xdg/menus/
```

If you are worried about it, change the permissions on the file so it is owned by root.
```
sudo chown root kde-applications.menu
sudo chgrp root kde-applications.menu
```

And, that should restore your menu to all it's former glory.

--andy

---

### Post by gunksta on 2006-08-29
If a Kubuntu User could post the contents of /etc/xdg/menus I would like to get a copy of your kde-appliations.menu AND whatever is in kde-applications-merged.

Thanks
--andy

---

