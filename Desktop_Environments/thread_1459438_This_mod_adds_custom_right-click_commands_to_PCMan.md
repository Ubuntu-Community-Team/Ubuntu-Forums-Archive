---
title: "This mod adds custom right-click commands to PCManFM"
date: 2010-04-21
forum: Desktop Environments
---

### Post by IgnorantGuru on 2010-04-21
The following modded version of PCMan File Manager adds user-definable commands to the right-click menu, as well as a number of other feature additions/changes and bug fixes.  This is a fork of the current stable PCManFM 0.5.2.  You can get all the details here:
[http://igurublog.wordpress.com/downloads/mod-pcmanfm/](http://igurublog.wordpress.com/downloads/mod-pcmanfm/)

This includes a script that builds it automatically - you just need the same build dependencies that PCManFM requires.  This mod is a few months old now and has been running very well.

Also, the latest update includes a workaround for the GTK 2.20 (2.19?) bug which has crippled some functionality in PCManFM (old and new versions) as well as Thunar.  From bug reports it appears that this bug affects Lucid.  You can see more about this bug [_here_](https://bugzilla.gnome.org/show_bug.cgi?id=612802).

---

### Post by kerry_s on 2010-04-21
i'm using lubuntu(lucid) it has pcmanfm2 which you can now use custom commands just like thunar actions, kind of, it's missing the name part, it would be great if pcmanfm wasn't so buggy. i use thunar in my setup though.

---

### Post by IgnorantGuru on 2010-04-21
> **kerry_s said:**
> i'm using lubuntu(lucid) it has pcmanfm2 which you can now use custom commands just like thunar actions, kind of, it's missing the name part, it would be great if pcmanfm wasn't so buggy. i use thunar in my setup though.

Thanks for the update.  I have spoken with the author and he does plan to add custom commands to pcmanfm2 once the nautilis-derived specs are solidified.  From your screenshot it looks like he's already proceeding with some of that - looks like the mod's Run Command.  He has also implemented some of the other fixes and features from my mod.

I have reviewed pcmanfm2 a few times but for now I'm still using the modded 0.5.2.  Overall I like the pcmanfm design for a clean look and it's pretty capable.  Once he adds custom commands I think it will be great.

I also use Thunar for some purposes but without multiple tabs I find it limiting.

There is a user's screenshot of the mod here to give you an idea - the name of the user commands can be changed as well.
[http://crunchbanglinux.org/forums/topic/7079/pcmanfmmod-custom-actions-and-more/](http://crunchbanglinux.org/forums/topic/7079/pcmanfmmod-custom-actions-and-more/)

---

### Post by kerry_s on 2010-04-21
i think the way you have it done is a lot better. i like my commands separated from the main items.
when i create a command i always have to go to ~/.local/share/applications to put the name i want to show.
i just don't like it that way.

i really like the way it is in thunar, it's just better.

---

### Post by IgnorantGuru on 2011-05-11
Just to bring this thread up-to-date, there are now [_Debian/Ubuntu-compatible packages_](http://igurublog.wordpress.com/downloads/mod-pcmanfm/#deb) available for [_PCManFM-Mod_](http://igurublog.wordpress.com/downloads/mod-pcmanfm/).  And there is a [_PPA_](http://igurublog.wordpress.com/downloads/ppa/) as well, which also contains [_my other software_](http://igurublog.wordpress.com/downloads/).

I recently [_moved from Arch to Aptosid_](http://igurublog.wordpress.com/2011/03/31/my-move-from-arch-to-aptosid/) so its now convenient for me to build these Ubuntu-compatible packages.  Feedback is welcome.  While I may not be able to get them working for every version of Ubuntu, I think most versions should work and I tested it successfully on 11.04 livecd.

Also, PCManFM-Mod has quite a few features added since the last update to this thread.  A screenshot and info can be found on its [_homepage_](http://igurublog.wordpress.com/downloads/mod-pcmanfm/).

---

