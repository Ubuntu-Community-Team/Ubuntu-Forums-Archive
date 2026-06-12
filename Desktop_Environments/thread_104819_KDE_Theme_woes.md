---
title: "KDE Theme woes"
date: 2005-12-16
forum: Desktop Environments
---

### Post by angrykeyboarder on 2005-12-16
Why can't KDE make installing themes as easy as it's done in GNOME?  I don't get it.  Don't get me wrong, GNOME sucks at many things too (That's why I use both ;-) ).

It seems you have to be a propeller-head with a pocket-protector to do what should be a simple task.

For example, I'd like to install this theme:

[http://kde-look.org/content/show.php?content=30483](http://kde-look.org/content/show.php?content=30483)

After reading through a few comments, I was compelled to comment with this:

[http://tinyurl.com/chvrm](http://tinyurl.com/chvrm)
(scroll to the bottom and look for the comment from "angrykeyboarder").

---

### Post by ltmon on 2005-12-17
Yeah, themes are a bit sucky because they require source code to create and use.  I think it's being addressed in the next major revision.

Many themes are available as packages however, so you could use them.  Have a poke around in adept.

A quick pointer: On Kubuntu your prefix will always be "/usr".  Configure will always this prefix by default in any case.

So:

./configure --prefix=/usr
make
sudo make install

should get you up and running.

The packages to install before this are:
- build-essential
- kdebase-dev

I think that should do it (I can't check now... gf has stolen my Kubuntu computer to play games :( )

L.

(Oh yeah... I don't wear a pocket protector, but I probably should)

---

### Post by Rackerz on 2005-12-17
I thought this too, and ltmon, thanks for making the packages needed clear. When i went by someone elses install instructions it installed about 30 other packages.

Also i was just wondering, after doing 'make install' where exactly would the files i needed to install the theme be?

---

### Post by angrykeyboarder on 2005-12-17
[quote=ltmon]Yeah, themes are a bit sucky because they require source code to create and use.  I think it's being addressed in the next major revision.[/quote] 
> Many themes are available as packages however, so you could use them. 
I've used every one of them that works.  There are quite a few more that I haven't because they have dependanices that aren't met (mostly because they are older packages).

> Have a poke around in adept. 
Uhhh... what good will that do you?  Do you have some repositories that I'm not aware of with KDE themes?
> 
A quick pointer: On Kubuntu your prefix will always be "/usr".  Configure will always this prefix by default in any case.

[...]

The packages to install before this are:
- build-essential
- kdebase-dev 
This needs to be in user documenttion (or is it already and I missed it?).

---

### Post by angrykeyboarder on 2005-12-17
[quote=Rackerz]I thought this too, and ltmon, thanks for making the packages needed clear. When i went by someone elses install instructions it installed about 30 other packages.

Also i was just wondering, after doing 'make install' where exactly would the files i needed to install the theme be?[/quote]

You wouldn't need any, "make install" installes the theme (or program as the case may be).

On a related note, before you do that.

sudo apt-get install [checkinstall]("http://freshmeat.net/projects/checkinstall")

Then, instead of "make install" type checkinstall.

That will create a .deb package that you can easioly keep track of and uninstall later if need be.

---

