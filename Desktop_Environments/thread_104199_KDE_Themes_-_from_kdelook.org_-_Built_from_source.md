---
title: "KDE Themes - from kdelook.org - Built from source"
date: 2005-12-15
forum: Desktop Environments
---

### Post by pkraus on 2005-12-15
Most of the themes I am finding are source themes.
So i ./configure ./make sudo make install them and everything works fine. I have all the extra libs installed so I have no issues with this process.

However when I then go to kcontrol -> theme manager none of my themes are showing up.

Once I compile and install them how do I select them?

Paul Kraus

---

### Post by Freddy on 2005-12-15
Most of the themes you install from kde-look.org is actually only windowdecorations or styles, so I suggest you check in those tabs.   /// Freddan

Edit: When running the ./configure script, use ./configure --prefix=`kde-config --prefix` when you install KDE stuff, otherwise some stuff can be misplaced.

---

### Post by angrykeyboarder on 2005-12-16
[QUOTE=Freddy]Most of the themes you install from kde-look.org is actually only windowdecorations or styles, so I suggest you check in those tabs.   /// Freddan

Edit: When running the ./configure script, use ./configure --prefix=`kde-config --prefix` when you install KDE stuff, otherwise some stuff can be misplaced.[/QUOTE]

It would be nice if the themes included this in an INSTALL file in the source code.  They rarely do. I can't imagine how theme authors expect us to know this stuff.

On a related note, I did as you specified on the source code for a theme a while ago and configure ran quite smoothly.  Make, on the other hand, was a disaster.  Error messages up the Wazoo.

Chalk up one for GNOME when it comes to themes. You never have to compile from source or install from a package.  It's all just drag and drop (or extract tarballs to the appropriate subdirectories of ~.

I'm really wanting to get several KDE themes installed and it's become quite a hassle. I'm still trying.....

---

### Post by ravenon on 2005-12-16
I have built KDE themes from source sucessfully using the following
./configure --prefix=/usr,  make,  sudo make install

So far this seems to work.

---

### Post by angrykeyboarder on 2005-12-16
[quote=ravenon]I have built KDE themes from source sucessfully using the following
./configure --prefix=/usr,  make,  sudo make install

So far this seems to work.[/quote] 
It won't work for this one....

[http://www.kde-look.org/content/show.php?content=11384]("http://www.kde-look.org/content/show.php?content=11384")

---

### Post by Freddy on 2005-12-16
> On a related note, I did as you specified on the source code for a theme a while ago and configure ran quite smoothly. Make, on the other hand, was a disaster. Error messages up the Wazoo.
Some themes on kde-look is quite old and badly written and several depends on older versions of qt (for example). If that is the case the only thing you can do is ask the maker to do a updated one. If you ever have a problem compiling themes post a message here and I bet that someone will know what's wrong =).   /// Freddan

---

