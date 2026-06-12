---
title: "Denied access to a folder after changing permissions"
date: 2009-05-30
forum: General Help
---

### Post by Iteria on 2009-05-30
I'm running Xubuntu 9.04. I installed Rainlender on my computer and for some reason Rainlendar  doesn't puts its skins folder in the home folder. That's if rainlendar is installing the skin for your, but sometimes you have to do it manually. I decided that the easiest way to solve this problem was to change the permissions for just the skins folder. I enter these commands:

```

cd /usr/share/rainlendar2
chmod g=rw skins
chmod g=r skins
chmod o=rw skins

```

When I use Thunar to look at the permissions to make sure that I had a) put the g permissions back and b) sucessfully changed the others permissions there was this warning: The folder permissions are inconsistent. You may not be able to work with the files in this folder.

I tried to open the folder through Thunar, but I got a permission denied dialog. I changed the permissions back to the way I found them, and the warning was still there and I still couldn't access the folder through thunar. I can't access the folder through the command line either. I had Rainlendar attempt to reload its skin to see if it could and it failed also, so it looks like everything is locked out of the folder.

I'm out of ideas. Anyone have a suggestion?

---

