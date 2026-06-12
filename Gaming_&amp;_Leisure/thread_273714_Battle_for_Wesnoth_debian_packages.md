---
title: "Battle for Wesnoth debian packages"
date: 2006-10-08
forum: Gaming &amp; Leisure
---

### Post by MrBlond83 on 2006-10-08
Hi all,

I was just wondering - from looking in the -unstable Debian repositories, I can see that they already have a .deb for version 1.11 of Battle for Wesnoth,  and the data/music/campaign packages too. Would installing the game from those .deb's work fine on Edgy?

It just seems easier than compiling from source, and with the Edgy repositories having v1.08, the multiplayer doesn't work :(

---

### Post by Perfect Storm on 2006-10-09
It's very easy to compile by yourself, I wrote a howto on the topic: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=30&Itemid=63)

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

