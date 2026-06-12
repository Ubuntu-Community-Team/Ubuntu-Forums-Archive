---
title: "Help Installing FreedroidRPG"
date: 2011-07-02
forum: Gaming &amp; Leisure
---

### Post by Giraffemonster on 2011-07-02
I've played the game before on the stable release versions, however I tried to install FreedroidRPG from their SVN repository as they don't often give newer stable releases. I would also like to have a look at what's coming up later in the game.

I'm having some trouble getting freedroid set up though. I've downloaded their SVN repository, ran autogen.sh, configured it, and ran make, but there's an error when running "sudo make install"

```
owner@P4M90-M4:~/freedroid$ sudo make install
Making install in src
make[1]: Entering directory `/home/owner/freedroid/src'
make[2]: Entering directory `/home/owner/freedroid/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c freedroidRPG '/usr/local/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/owner/freedroid/src'
make[1]: Leaving directory `/home/owner/freedroid/src'
Making install in gluem
make[1]: Entering directory `/home/owner/freedroid/gluem'
make[2]: Entering directory `/home/owner/freedroid/gluem'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c gluem ungluem explodefont gluefont make_atlas '/usr/local/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/owner/freedroid/gluem'
make[1]: Leaving directory `/home/owner/freedroid/gluem'
Making install in graphics
make[1]: Entering directory `/home/owner/freedroid/graphics'
make[2]: Entering directory `/home/owner/freedroid/graphics'
make[2]: Nothing to be done for `install-exec-am'.
test -z "graphics/obstacles/" || /bin/mkdir -p "graphics/obstacles/"
 /usr/bin/install -c -m 644 obstacles/atlas.txt obstacles/shadow_atlas.txt floor_tiles/atlas.txt 'graphics/obstacles/'
/usr/bin/install: will not overwrite just-created `graphics/obstacles/atlas.txt' with `floor_tiles/atlas.txt'
make[2]: *** [install-atlasDATA] Error 1
make[2]: Leaving directory `/home/owner/freedroid/graphics'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/owner/freedroid/graphics'
make: *** [install-recursive] Error 1

```

I do have all the necessary packages required to run the game, and my system specs are in my sig. I haven't gotten problems like this when running "make install" on other programs. Any help would be greatly appreciated. Thanks.

---

### Post by Perfect Storm on 2011-07-02
> /usr/bin/install: will not overwrite just-created

May be uninstall previous. But in this case it would better not sudo make install and run the game locally from your home folder.

---

### Post by Giraffemonster on 2011-07-03
> **Artificial Intelligence said:**
> May be uninstall previous. But in this case it would better not sudo make install and run the game locally from your home folder.

I had also asked about this on freedroid's forums, and apparently it's an issue related to recent changes which are being fixed.

I'll just keep playing in the source directory until then. :)

---

