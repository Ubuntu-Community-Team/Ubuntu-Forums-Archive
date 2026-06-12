---
title: "Debian Repositories"
date: 2005-12-24
forum: General Help
---

### Post by thermopyl on 2005-12-24
Hi 

In an attempt to get the latest version of Evolution, I have added the debian sources to my source list ->

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free

On update, this has of course brought back a number of potential upgrades (but not evolution!). Is it safe to apply these to my ubuntu system or are they potentially too generic to work?

thanks

---

### Post by RAOF on 2005-12-24
This is a **horribly, horribly bad idea**.  The Ubuntu packages have slightly different names, and are almost certainly not binary compatible with the debian packages (they'll be using a different libc, libstdc++, gcc version).  Further more, some of the Debian packages will likely have a newer version number, so apt will overwrite your Ubuntu libraries with Debian ones which **won't work**.  If you desperately want a new Evolution, download the debs from the Dapper repositories.

**Using Debian repositories is a recipe for breaking your Ubuntu.**

---

### Post by thermopyl on 2005-12-24
ok

no sitting on the fence on this one then!!

thanks for your reply, if i remove the source from my list file will the update notifications disappear?

---

### Post by Sebby on 2005-12-24
[QUOTE=thermopyl]thanks for your reply, if i remove the source from my list file will the update notifications disappear?[/QUOTE]
As long as you do a sudo apt-get update again once you've removed it. :)

---

### Post by thermopyl on 2006-01-10
..."If you desperately want a new Evolution, download the debs from the Dapper repositories"

How do i do this then as my evolution is broke :(

---

### Post by Qrk on 2006-01-10
[http://packages.ubuntu.com/dapper/gnome/evolution](http://packages.ubuntu.com/dapper/gnome/evolution)

---

### Post by thermopyl on 2006-01-11
[QUOTE=Qrk][http://packages.ubuntu.com/dapper/gnome/evolution](http://packages.ubuntu.com/dapper/gnome/evolution)[/QUOTE]

thanks!

before i do this however i also have to install a host of library updates...will i mess up my breezy system???

---

### Post by RAOF on 2006-01-11
[QUOTE=thermopyl]thanks!

before i do this however i also have to install a host of library updates...will i mess up my breezy system???[/QUOTE]
It's possible, yes.  You won't know untill you've tried it, I think.

If your evolution is broke, you could try
```
sudo apt-get install --reinstall evolution
```
to reinstall evolution from the Breezy repositories.  If it's breaking on a library, though, I think you'll need to find which library & reinstall that.

---

