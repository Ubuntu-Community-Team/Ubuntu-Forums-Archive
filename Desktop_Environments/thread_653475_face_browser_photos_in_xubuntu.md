---
title: "face browser photos in xubuntu"
date: 2007-12-29
forum: Desktop Environments
---

### Post by srleffler on 2007-12-29
I am new to Linux, and installed Xubuntu Gutsy on an old laptop. I selected a "face browser" login theme in gdm. How do I set up pictures for each user? I just get default images. Note that I am using Xubuntu (XFCE) not Ubuntu. The System\Preferences option I see referred to elsewhere does not seem to be available.

If there is no graphical interface available in Xubuntu for this, it would be helpful to know where gdm looks for the images (a specific path or filename?)

---

### Post by aidanr on 2007-12-30
/usr/share/pixmaps
> Systemwide directory for face files. The sysadmin can place icons for users here without touching their homedirs. Faces are named after their users' logins. The face images must be stored in gdk-pixbuf supported formats and they must be readable for the GDM user.

---

### Post by x1a4 on 2007-12-30
Hi,

For each user that has a **.face** file in their home directory it will be displayed as the user's avatar.  .face should be a symlink to a PNG or JPEG image.   Although if you save an image as .face it will work also. 

System faces are in /usr/share/pixmaps/faces/

So, for example, say you want your face to be an astronaut you would execute the following in a terminal: 

```
ln -s /usr/share/pixmaps/faces/astronaut.jpg ~/.face
```

Or

```
ln -s ~/path/to/image/myface.png ~/.face
```

---

### Post by teohhanhui on 2008-04-30
Additionally, you have to make sure the owner of the .face file is the user him/herself in order for gdm to access it.

---

