---
title: "Crazy dependancies??"
date: 2006-04-30
forum: Desktop Environments
---

### Post by st0kes on 2006-04-30
I just install Azureus for bit torrent downloads (as it's far superior to the gnome bit torrent program), but when I try to remove "bittorrent" using synaptic, it tells me that the following will also need to be removed ... 

gnome-btdownload
ubuntu-desktop

I can't believe that ubuntu desktop needs a bittorrent client to work correctly?? Is this a bug?

---

### Post by Ramses de Norre on 2006-04-30
Ubuntu-desktop is a meta package, it has all the gnome programs as dependency but doesn't really content anything. So you can just remove it and you wont loose anything. 
But removing it will cause problems with dist-upgrade so you'll want to reinstall it before you dist-upgrade.

---

### Post by Thirsteh on 2006-04-30
ubuntu-desktop is a package that links all the Ubuntu Desktop packages together, it's simply a package that installs a heck load of packages with it as it's installed. You can safely remove ubuntu-desktop, it won't tear your whole desktop apart :P

I was like "!!?!" the first time I saw this as well.

---

### Post by st0kes on 2006-04-30
OK thanks for the sanity check!! I think I will leave it installed for the dist-upgrade when dapper is finally ready.

---

### Post by Roberto Rosselli on 2006-05-05
[QUOTE=Ramses de Norre]Ubuntu-desktop is a meta package, it has all the gnome programs as dependency but doesn't really content anything. So you can just remove it and you wont loose anything. 
But removing it will cause problems with dist-upgrade so you'll want to reinstall it before you dist-upgrade.[/QUOTE]

Hi there,
so you have to re-install ubuntu-desktop and all the packages it points to before a dist-upgrade? This wouldn't bother me, if it wasn't for the fact that **many** packages ubuntu-desktop depends on look completely useless to me. For instance, I'd like to get rid of all the foreign language fonts I'm not ever going to use (don't have much space on my laptop!) but it seems a waste of space and time having to reinstall them all again.

Has anybody filed a bug report/feature request asking that ubuntu-desktop include far less packages than it currently does?

Ciao

---

### Post by Ramses de Norre on 2006-05-05
I don't know whether it's always the case but I've seen a lot of people struggling with dist-upgrade if they didn't had ubuntu-desktop nomore.

---

