---
title: "Uninstall Old Games (not in Ubuntu Software Centre)"
date: 2013-12-22
forum: Gaming &amp; Leisure
---

### Post by Drowz0r on 2013-12-22
Hello all

Recently Steam/Valve has been really pushing Linux support so a great deal many of my games that were running with Wine or had native installers outside of Steam were throughout my computer. Most of these I've re-downloaded/installed through steam and removed the other version from my computer using the Ubuntu Software Centre.

However there are a number of titles that I can still see when I use the Dash search but they do not appear in the Ubuntu Software Centre. Also when I try the old "sudo apt-get remove <gamename>" it doesn't find the game - I suspect the files are named something other than the title.

Can someone assist? Is there a way for Ubuntu Software Centre to show all games/apps in full or another way to remove these things? :confused:

Thanks

---

### Post by deadflowr on 2013-12-22
You should be able to remove wine games with the wine uninstaller program.
Other games will probably need to be removed based on the kind of installation it was.

---

### Post by Drowz0r on 2013-12-22
Yeah the Wine ones went with PoL pretty easily.

The other ones are a little more difficult and varied.

Some installers were .rpm others .deb and I think some used a .sh installer or something. Quite varied.

---

### Post by deadflowr on 2013-12-23
Well I know nothing on installing or uninstalling rpm packages on Ubuntu except b y using alien, which is suppose to convert to deb files anyway.
As far as the .sh installers go, I would assume, that for the most part , they where part of a tarball which might have had whatever commands would be needed, if any, to uninstall them.
But the deb files shouldn't be too hard, by using dpkg --purge.

---

### Post by Drowz0r on 2013-12-23
That's good to know, but how to I uninstall a game, such as "Splice" when the terminal always shows "warning: there's no installed package matching Splice".

---

### Post by dannyboy79 on 2013-12-23
where or how did you install Splice? I see it within the USC as well as on Steam. If you installed a game using sh, which just tells the program to run using the bourne shell, there may be a --uninstall or --remove option for the installer. You'd have to read the README or any other documentation that came with the software.

---

### Post by Drowz0r on 2014-03-03
Maybe I should have put this in the absolute beginners section :/

I have a few games that were installed in different ways. I kind of expected just some way to remove them through the software centre or something.

I mean, say you don't remember which method you installed a game or application by. Surely there is a way to find out and remove it?

---

