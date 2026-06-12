---
title: "How to change the GDM user image?"
date: 2006-12-20
forum: Desktop Environments
---

### Post by raid517 on 2006-12-20
Hi I recently switched from KDM to GDM (although I am still using KDE). The reason I did this is simply because GDM is prettier.

In any case I want to change the user image on my GDM login screen to something more appropriate. (Such as an image of me).

However under 'login window preferences', users, default face, whenever I select anything here it does not show up on my GDM login screen.

How can I get my own image to show up on the screen? (I know it has to be .png format).

Also currently my GDM is of a picture of some cute (as in cartoon cute) little guy in a suit with no face and a sensible hair cut. Where exactly on my system is this image located?

I ask as I have spent quite a bit of time trying to track it down.

---

### Post by Rui Pais on 2006-12-20
hi, 
if you installed gdm you should have too an app called 'gdmphotosetup'
you can call it from a terminal if it wont appear in the KDE menus

---

### Post by ciscosurfer on 2006-12-20
Or go to System > Preferences > About Me if you're using GNOME (or in a Terminal, issue **gdmphotosetup**)

In KDE, in a Terminal, issue [B]gdmphotosetup

[/B]The pic does not have to be a .png file...it can be a jpg or any other number of picture types (although, I've only seen png and jpg used by default).  You can find a whole bunch located here: /usr/share/pixmaps/faces

As for your picture, I couldn't say where it's located (or cached, for that matter).

---

### Post by Ptero-4 on 2007-02-13
I have an account with capital letters in it´s username and a passwordless one. Can I make them show a picture?

---

