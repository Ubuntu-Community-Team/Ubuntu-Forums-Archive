---
title: "APT sources.list mirror selection tool"
date: 2006-07-31
forum: Desktop Environments
---

### Post by charlie. on 2006-07-31
I remember seeing a text-mode tool on a Debian box that would display a list of available APT mirrors and allow you to select one. It would then write your sources.list for you, using the selected mirror. It was rather similar to the text-mode Ubuntu installer.

Can anyone please tell me what this tool was called and whether it is available in Ubuntu?

---

### Post by Titus A Duxass on 2006-07-31
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Google is your friend, try it sometime!

---

### Post by ciscosurfer on 2006-08-01
The source-o-matic page is fine for basic/additional repos.  It does not, however, provide a list of mirrors.

This is the [Ubuntu mirrors link]("https://wiki.ubuntu.com/Archive"). :KS

---

### Post by charlie. on 2006-08-02
Thanks for the lists of mirrors. That is not what I wanted, however. (I knew where to find those.)

The utility I am thinking of is a program that can be run on the box. It displays a list similar to the one displayed at install time. (I presume it uses ncurses or something to do this) I think the commands started with "dpkg..."

This is annoying me, because I knew what the command was. I even wrote it down... somewhere... on notes that must have been recycled by now...)

---

### Post by charlie. on 2006-08-02
Thanks for the lists of mirrors. That is not what I wanted, however. (I knew where to find those.)

The utility I am thinking of is a program that can be run on the box. It displays a list similar to the one displayed at install time. (I presume it uses ncurses or something to do this) I think the commands started with "dpkg..."

This is annoying me, because I knew what the command was. I even wrote it down... somewhere... on notes that must have been recycled by now...)

---

### Post by ciscosurfer on 2006-08-03
The dpkg you refer to is the debian package manager (check out *man dpkg*).  As for the console based program, I don't have any idea.  But keep searching, you'll find it! 

EDIT: I found a [script here]("http://apt-rpm.org/lua/mirror-select/mirror-select.lua") that looks like what you are talking about...I will keep searching.

---

### Post by Hobbes on 2006-12-07
anyone ever find something like this, I think it would be a nice tool, as I often fool around with different mirrors.

---

### Post by Johan! on 2006-12-07
```
 dpkg-reconfigure apt

```

Or something like that?

Edit: Something like dpkg-reconfigure xserver-xorg, or another application.
I can remember there's a tool to configure the sources.list, but I can remember the name.
And it's not synaptic or aptitude ;)

Edit2:
I found it :)
Install the apt-howto package in synaptic, or with apt-get.
Press Alt-F2, run apt-howto
There's the apt howto ;)

[Here]("file:///usr/share/doc/Debian/apt-howto/ch-tricks.en.html#s-netselect") you can find the program: netselect

---

### Post by ciscosurfer on 2006-12-07
> **Johan! said:**
> ```
 dpkg-reconfigure apt

```Or something like that?

Edit: Something like dpkg-reconfigure xserver-xorg, or another application.
I can remember there's a tool to configure the sources.list, but I can remember the name.
And it's not synaptic or aptitude ;)

Edit2:
I found it :)
Install the apt-howto package in synaptic, or with apt-get.
Press Alt-F2, run apt-howto
There's the apt howto ;)

[Here]("file:///usr/share/doc/Debian/apt-howto/ch-tricks.en.html#s-netselect") you can find the program: netselectNetselect works on Debian mirrors, not Ubuntu's mirrors.  It is, however, a nice app.

Another one to try is apt-spy: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apt-spy&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apt-spy&searchon=names&subword=1&version=edgy&release=all) alas, this seems to work only with Debian mirrors as well...but the options to use for it make it seem like modifying some strings/urls/etc would allow for it to work for Ubuntu as well.

---

### Post by charlie. on 2006-12-08
Is netselect the debian app that tests your connection to a whole list of mirrors and tells you which is the fastest available? I remember an app that did that.

I'm happy, because I've found two decent mirrors that work nicely from my country - over HTTP because FTP is all but useless due to port shaping in South Africa.

I'd still like to see something like "netselect" in Ubuntu.

---

