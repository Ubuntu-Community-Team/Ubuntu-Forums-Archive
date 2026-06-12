---
title: "Industry theme and mouse theme gone"
date: 2005-02-04
forum: Desktop Environments
---

### Post by uggeli on 2005-02-04
I'm not sure is this right place to post this, but this forum is quite confused and this seems to be right place. If this isn't the please don't shot me for that.. :) But now to the problem.

I have using hoary for a long time now, but now when I upgraded my system  this evening I lost my Industry theme and there was some 'Other Theme' in themes list which I first had to save pefore I could browse my themes. Well anyway Industry is gone  (I have reinstalled it but it's not in the list) and so is mouse-theme which was in Ubuntu by default (white arrow and spinner when loading). Now I have Black mouse arrow and when system loads somethin arow change to ugly black wrist watch.. clock.. 

The reason why I'm writing this is that I just would like to know that is this temporarily that those themes are gone, or will those themes change to these ugly-ones when hoary finally comes out? Well it might be that I write this to early cause that update had bad effect to my gimp allso and probably there will be  update which solves those problems and hhopefullly brings themes back aswell. But I was just curious that will themes change and hopefully someone of you can give me an answer for this.

Sure I could possibly install whatever theme I want to mouse too but I'm just newbie here and beside I don't know that theme name what was for mouse.. 

Thansks for possible answers.

---

### Post by piedamaro on 2005-02-04
[QUOTE=uggeli]I'm not sure is this right place to post this, but this forum is quite confused and this seems to be right place. If this isn't the please don't shot me for that.. :) But now to the problem.

I have using hoary for a long time now, but now when I upgraded my system  this evening I lost my Industry theme and there was some 'Other Theme' in themes list which I first had to save pefore I could browse my themes. Well anyway Industry is gone  (I have reinstalled it but it's not in the list) and so is mouse-theme which was in Ubuntu by default (white arrow and spinner when loading). Now I have Black mouse arrow and when system loads somethin arow change to ugly black wrist watch.. clock.. 

The reason why I'm writing this is that I just would like to know that is this temporarily that those themes are gone, or will those themes change to these ugly-ones when hoary finally comes out? Well it might be that I write this to early cause that update had bad effect to my gimp allso and probably there will be  update which solves those problems and hhopefullly brings themes back aswell. But I was just curious that will themes change and hopefully someone of you can give me an answer for this.

Sure I could possibly install whatever theme I want to mouse too but I'm just newbie here and beside I don't know that theme name what was for mouse.. 

Thansks for possible answers.[/QUOTE]
 Industrial mouse theme is under /usr/share/icons/Industrial/cursors/, you can set your mouse theme with gconf-editor under /desktop/gnome/peripherals/mouse/cursor_theme, or install gcursor and set it from there.

---

### Post by uggeli on 2005-02-04
[QUOTE=piedamaro]Industrial mouse theme is under /usr/share/icons/Industrial/cursors/, you can set your mouse theme with gconf-editor under /desktop/gnome/peripherals/mouse/cursor_theme, or install gcursor and set it from there.[/QUOTE]

Thanks for quick answer! Do you happen to know the name of warty's default mouse-theme? Is it Human? I  do use Hoary but I've been using that default mouse-theme allways (so it's the same that is in warty), just that now it was replaced some ugly one.. Well after Hoary filal is out I will not use 'beta' versions anymore it's enough for me to keep on learning official versions..:)

---

### Post by piedamaro on 2005-02-04
I'm on hoary too, and I have no problems with mouse (however I'm using industrial-steel cursor theme).
The default Human theme inherits Industrial for cursor (see here: /usr/share/themes/Human/cursor.theme)

---

### Post by bVork on 2005-02-05
I just updated and had my mouse theme disappear as well. You can get your beloved white cursor back by doing the following:

I downloaded Jimmac's cursor theme (the one found in Industrial, used in the default Human theme and thus Ubuntu's default) from here: [http://www.gnome-look.org/content/show.php?content=6550](http://www.gnome-look.org/content/show.php?content=6550)

Then open up a terminal window, browse to the folder where 6550-Jimmac.tar.gz was downloaded, and do:

tar xvzf 6550-Jimmac.tar.gz
sudo mv /Jimmac/jimmac /usr/X11R6/lib/X11/icons

Then just follow uggeli's earlier instructions and open up gconf (Applications -> System Tools -> Configuration Editor), browse to /desktop/gnome/peripherals/mouse/ and replace the entry in cursor_theme with "jimmac". (Excluding the quotation marks, of course.)

Now all you need to do is restart your computer, and the new cursor settings will take effect.

---

### Post by whatever on 2005-02-05
to get the jimmac cursor in gdm do this:
> tar vzfx 6550-Jimmac.tar.gz
sudo mv Jimmac/jimmac /usr/X11R6/lib/X11/icons/
sudo mv Jimmac/default/index.theme /etc/X11/cursors/jimmac.theme
sudo update-alternatives --install /usr/X11R6/lib/X11/icons/default/index.theme x-cursor-theme /etc/X11/cursors/jimmac.theme 20
 
now you can use
>  sudo update-alternatives --config x-cursor-theme
to select the jimmac cursor and easily set it back to default with
>  sudo update-alternatives --auto x-cursor-theme

this way it works for all users and not only for a specific one as with gconf-editor or gcursor

---

### Post by uggeli on 2005-02-05
Thanks for the answer again!

I got jimmac-theme back, but it loads only after I log in to the sysem. So in Login screen there is that black and ugly theme, but it is just cosmetic problem :) And I did try those commands what whatever wrote here..

Anyway now when mouse-theme works allmost perfect (only that cosmetic problem), do you have any ideas how to get Industry theme back? I have tried to reinstalling it but it's not in to Desktop&#8594;Installation(?)&#8594;Themes anymore. I'm not sure is it "installation" cause I don't use english version of ubuntu, but I'm sure you know what I mean.

---

### Post by crashd on 2005-02-05
is strange, the package gtk2-engines-industrial seems installed..

---

### Post by uggeli on 2005-02-06
Well I checked that out one more time and apt-get said package gtk2-engines-industrial is allready installed and is the newest version. Well I tried once more time to reinstalling it, this time via apt-get with that package name, but no changes.. :(

---

### Post by ups on 2005-02-09
Hi, if you upgraded from Warty and have the Warty CD, do this:

In synaptic, click on gtk2-engines-industrial and then Package->Force Version.
you should see 0.2.36.2 (Warty) there, select that & Click Force Version, Then Apply (you might be asked for the Watry CD, insert it).

Now, u can log out of GNOME and log back in. you'll see the default ubuntu (jimmac) theme.

---

### Post by puelly on 2005-02-14
thanks alot for your tip. worked like a charm. cheers

---

### Post by mahnve on 2005-02-14
I don't have the CD's but I found the package at [http://higgs.djpig.de/ubuntu/www/warty/gnome/gtk2-engines-industrial](http://higgs.djpig.de/ubuntu/www/warty/gnome/gtk2-engines-industrial) and 'dpkg -i'd it in.

---

### Post by mcwtlg on 2005-02-14
[QUOTE=ups]Hi, if you upgraded from Warty and have the Warty CD, do this:

In synaptic, click on gtk2-engines-industrial and then Package->Force Version.
you should see 0.2.36.2 (Warty) there, select that & Click Force Version, Then Apply (you might be asked for the Watry CD, insert it).

Now, u can log out of GNOME and log back in. you'll see the default ubuntu (jimmac) theme.[/QUOTE]

Force version is greyed out...all I have is lock version.  Oh well.  :-D

****************
Update
****************

Added CD and it worked.  Newbie mistake.

---

### Post by piedamaro on 2005-02-15
But why new industrial-engine package comes w/o cursor theme?

---

### Post by ups on 2005-02-15
[QUOTE=piedamaro]But why new industrial-engine package comes w/o cursor theme?[/QUOTE]
 Its a bug, and requires fixing upstream... thats all I know. There's a bug report on it in bugzilla too.

---

### Post by piedamaro on 2005-02-15
[QUOTE=ups]Its a bug, and requires fixing upstream... thats all I know. There's a bug report on it in bugzilla too.[/QUOTE]
 Oh, got it thanks :)

---

