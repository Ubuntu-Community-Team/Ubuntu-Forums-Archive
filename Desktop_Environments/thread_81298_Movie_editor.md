---
title: "Movie editor"
date: 2005-10-24
forum: Desktop Environments
---

### Post by cazz on 2005-10-24
Hi
I have try Kino but that is some problem to edit MPEG file.

is that any easy and good editor for MPEG file?

I whant to delete some scene in a MPEG file.

---

### Post by WillCooke on 2005-10-24
Have a look at avidemux (or avidemux2).

You might have to compile from source, I cant remember if it's packaged for us.

---

### Post by bored2k on 2005-10-24
I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a LOT better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)

---

### Post by cazz on 2005-10-24
[QUOTE=bored2k]I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a LOT better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)[/QUOTE]


Thanks
I have install it but that is no icon in the menu or when I write avidemux in terminal the terminal say "Command not found" :???:

---

### Post by irish rebel on 2005-10-24
I have cinelerra I found a deb file somewhere and it installed like a charm on breezy  I actually was able to make a family photo music dvd with it.

---

### Post by cazz on 2005-11-12
Hmm I just like to cut (remove) some scene from MPEG file.

---

### Post by tmmuk on 2005-11-13
[QUOTE=irish rebel]I have cinelerra I found a deb file somewhere and it installed like a charm on breezy  I actually was able to make a family photo music dvd with it.[/QUOTE]

Could you post a link to the deb?

thanks

---

### Post by ivomans on 2005-11-13
[quote=bored2k]I have made an avidemux 2.1_branch1 package using SVN. ...
[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html]("http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html")[/quote] 
I just tried installing your package. After installation trying to run the program learns that there are actually a few library dependencies not fullfilled.
What I noticed: it depends on **libsmjs1** and **libfaac0**.
It might be helpfull to others if you add these dependencies to your package.

After installing these libraries avidemux2 seems to run fine.

[quote=cazz]I have install it but that is no icon in the menu or when I write avidemux in terminal the terminal say "Command not found"[/quote] The command is **avidemux2**

---

### Post by cazz on 2005-12-17
I have reinstall my Ubuntu and try now to install the program again from the deb file.
I have install  libsmjs1 abd libfaac0 but he say


```
Unpacking avidemux (from avidemux_2.1_branch-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing avidemux_2.1_branch-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/bin/avidemux2')Errors were encountered while processing:
 avidemux_2.1_branch-1_i386.deb
```

---

