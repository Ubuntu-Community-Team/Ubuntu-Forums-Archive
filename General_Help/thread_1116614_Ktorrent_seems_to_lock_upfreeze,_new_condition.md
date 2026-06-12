---
title: "Ktorrent seems to lock up/freeze, new condition"
date: 2009-04-05
forum: General Help
---

### Post by stir-crazy on 2009-04-05
Honestly no idea when this began (could be weeks), but now Ktorrent just becomes unresponsive very shortly after starting.  It seems to work for the first 15 seconds are so.  After that, the only thing I seem to be able to do with it is send the kill command!

I've tried uninstalling/reinstalling, including using the -f option.  Same result.  I do not like Transmission at all and would like to get Ktorrent running the way it used to.

Any ideas here?

---

### Post by lovinglinux on 2009-04-05
I have no idea, but have you tried Deluge? It is a great torrent client, easy to configure, has a nice interface and all important features.

---

### Post by stir-crazy on 2009-04-05
Not seeing Deluge in the repositories.  Only rarely do I install outside of them, not sure I want to for something like this.

Thanks though; I might break down later, or just use the torrent client on the windows machine.

---

### Post by majamba on 2009-04-05
check you /var/logs files

it could help if you can provides us with some information

what version of ubuntu are running 

or try compiling yourself by dowloading the latest

[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads) 

what happens when you upgrade your package list

---

### Post by lovinglinux on 2009-04-05
> **stir-crazy said:**
> Not seeing Deluge in the repositories.  Only rarely do I install outside of them, not sure I want to for something like this.

Thanks though; I might break down later, or just use the torrent client on the windows machine.

It should be. 

```
sudo apt-get install deluge-torrent
```

Anyways, you can add the PPA repository if you want to get the most recent updates. See [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa) 

You can also get the deb file from GetDeb [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

There is also a Windows version [http://download.deluge-torrent.org/windows](http://download.deluge-torrent.org/windows)

---

