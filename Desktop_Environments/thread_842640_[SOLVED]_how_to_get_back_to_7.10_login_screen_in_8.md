---
title: "[SOLVED] how to get back to 7.10 login screen in 8.04"
date: 2008-06-27
forum: Desktop Environments
---

### Post by vussvillem on 2008-06-27
Hi! I really do not like Xubuntu 8.04 login screen (Login Window) and I really adore Xubuntu 7.10 default login screen. I've searched internet with no results. Can someone please help me to get Xubuntu 7.10 login screen?

---

### Post by phidia on 2008-06-27
The settings are in > applications>settings>login window>local
You would need to get the graphic from the 7.10 cd and get login to use that.

---

### Post by j1mc on 2008-06-30
I understand that you may not like the Hardy login window - like phidia said, you can get the 7.10 cd, and get the login window from that version.  I'm not sure where the file is stored, but searching on the internet should be able to tell you.

Also, you may want to look on [http://xfce-look.org](http://xfce-look.org) or [http://gnome-look.org](http://gnome-look.org), and look for "GDM" files.  See what ones look attractive to you!

Then you can just drag the downloaded files onto the applications > settings > login window > local application, and they will be installed.  You will still need to select the GDM theme that you want to use, though.

---

### Post by vussvillem on 2008-06-30
I figured it out myself, but thank you for the replies. Yes, the solution was simple. However, I really do not understand why the excellent work of Ubuntu art team seems to be not uploaded to the web sites like ubuntu-art.org, gnome-look.org, xfce-look.org or anywhere else.
  
If someone else is still wondering - first, you have to get Gutsy Gibbon live cd. Look for for gdm themes in /usr/share/gdm/themes. Then you have to copy folder named "xubuntu" from Gutsy Gibbon live cd into your current release of Ubuntu, in the same folder. And because your current official Xubuntu gdm folder has the same name - xubuntu - you have to give to a copied folder a different name. To do all that, of course, you need to use superuser privileges (in order to modify anything else than your home folder). 

After that you can choose that particular gdm theme as any other gdm theme you already have.

---

