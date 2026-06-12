---
title: "Ubuntu Tweak &amp; login window issue"
date: 2010-06-18
forum: Desktop Environments
---

### Post by mrjawbones on 2010-06-18
Running 64-bit Lucid and the other day decided I wanted to customize the login screen.  Ran across a nifty app called Ubuntu Tweak which provides a convenient way to change the login screen background and the little icon on the login box.  After some trial and error, I got the background successfully changed.  Found out in the process that the image must reside in /usr/share/backgrounds.  However, when I changed the icon on the login box, now whenever I login, instead of the icon there is just a grey icon with a red circle and slash thru it presumably indicating that the image can't be found.  Then when I go back into Ubuntu Tweak, sure enough it doesn't show my image, but just a red x.  I'm using home folder encryption, so I thought maybe that was the problem because the image was in my home folder originally.  But I have since moved the image to various locations (including /usr/share/backgrounds) trying it from each, still no luck.

Can anyone tell me if there is a specific folder where this icon has to reside or is there some other way to change it?

---

### Post by sisco311 on 2010-07-07
[http://library.gnome.org/admin/gdm/2.30/gdm.html#facebrowser](http://library.gnome.org/admin/gdm/2.30/gdm.html#facebrowser)

*The icons used by GDM can be installed globally by the sysadmin or can be located in the user's home directories. If installed globally they should be in the <share>/pixmaps/faces/ directory and the filename should be the name of the user. Face image files should be a standard image that GTK+ can read, such as PNG or JPEG. Face icons placed in the global face directory must be readable to the GDM user.*

So copy the file to /usr/share/pixmaps/faces/ and rename it as *mrjawbones* (assuming that *mrjawbones* is your login name).

---

### Post by AlanB66 on 2010-07-15
Running the 32-bit of Lucid Lynx and I'm seeing my face icon (photo) of choice in the Unlock screen. But, at the initial login screen, I cannot get photos of ~/.face or /usr/share/pixmaps/faces/<user> or <user>.jpg to show up.

It's not a show-stopper, but it's a bit annoying.

---

