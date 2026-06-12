---
title: "Grub2-gfxmenu"
date: 2009-06-10
forum: General Help
---

### Post by NeoFax on 2009-06-10
Just installed grub2 and everything works great and was very easy to do on Jaunty.  However, I would like to now add in the gfxmenu portion so it is like my old grub.  I see Colin Bennett made code for this and that there is a overlay for Arch, but no debs for Ubuntu.  Does anyone know where I can find debs for this or is it safe to just grab the Arch gfxmenu overlay to get a graphical menu?

---

### Post by Quarkrad on 2009-06-10
Sorry to butt in - but what is grub2?  I have been struggling to get a graphical grub using message.ubugrey as the background to work.  So far not too much luck.

---

### Post by Agrezar on 2010-03-31
Some links you might want to look at:

This has one theme that works with the latest grub-pc, v98 i think.

[http://www2.apebox.org/wordpress/linux/228/]("http://www2.apebox.org/wordpress/linux/228/")

There is a version of grub called "Burg" you can install through the repositories visit this site. Add the PPA and install both burg-pc and burg-themes from synaptic for it to work. You will need to copy the /etc/default/burg file from /usr/share/burg/defaut in order to set the theme and resoloution as it doesnt make one. They called it burg so that grub2 can reside in the system aswell. All headers are "burg" (/etc/burg.d/01_header.. etc) ${prefix} will change to burg aswell. If you are booting from a stripped raid, burg does not work. 

[https://help.ubuntu.com/community/Burg]("https://help.ubuntu.com/community/Burg")

---

