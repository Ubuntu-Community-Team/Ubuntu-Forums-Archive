---
title: "Wesnoth 1.1.12 for Edgy?"
date: 2006-11-21
forum: Gaming &amp; Leisure
---

### Post by finferflu on 2006-11-21
Hi all,
I've just learnt that the latest version of Wesnoth is out, it's 1.1.12, but the only available in the Edgy repositories is 1.1.8, but I've noticed that the 1.1.12 is now available in the Feisty repositories.

Do you know any way to get the latest package for Edgy, or, is it fine to install the Feisty package in Edgy (but I guess not)?

Thank you.

---

### Post by Perfect Storm on 2006-11-21
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)

---

### Post by finferflu on 2006-11-21
Ok, thanks for the tutorial, I'm always worried about compiling because of my past failures (even though they were mostly on VectorLinux). My other question is, if I will need to upgrade, will it be fine to just follow the same procedure? Or do I need to remove the current version first?

---

### Post by Perfect Storm on 2006-11-21
If you use the same way and same place to install to it will just overwrite the previous version.

---

### Post by mikl on 2006-12-02
Well, it's much easier (and cleaner) to use the packages from the Debian repositories. I just went to [http://ftp.us.debian.org/debian/pool/main/w/wesnoth/](http://ftp.us.debian.org/debian/pool/main/w/wesnoth/) and downloaded all files matching /.*_1.1.12-1_(i386|all)/ (replace i386 with your arch) with the DownThemALL Firefox extension (enable regular expressions)

That gives me these files:
```
-(mikl@ariel)-(6/pts/0)-(~/Desktop/Downloads)-
-($ ls | grep wesnoth
wesnoth_1.1.12-1_i386.deb
wesnoth-data_1.1.12-1_all.deb
wesnoth-editor_1.1.12-1_i386.deb
wesnoth-ei_1.1.12-1_all.deb
wesnoth-httt_1.1.12-1_all.deb
wesnoth-music_1.1.12-1_all.deb
wesnoth-server_1.1.12-1_i386.deb
wesnoth-trow_1.1.12-1_all.deb
wesnoth-tsg_1.1.12-1_all.deb
wesnoth-ttb_1.1.12-1_all.deb
wesnoth-utbs_1.1.12-1_all.deb
```

Then just run ```
sudo dpkg -i wesnoth*.deb
``` where you downloaded the file, and bam!, you've got the newest version of Wesnoth, and when you upgrade to Feisty or Wesnoth gets packported, you'll automatically get the latest version.

---

### Post by finferflu on 2006-12-28
Thanks for that! I'm just using your suggestion to install Wesnoth 1.2

---

