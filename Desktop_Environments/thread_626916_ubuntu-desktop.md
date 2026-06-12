---
title: "ubuntu-desktop"
date: 2007-11-29
forum: Desktop Environments
---

### Post by theyain on 2007-11-29
Hello everyone,

I have been trying to build my own distro of Ubuntu for a little while now.  I've been using UCK ( [http://uck.sourceforge.net/](http://uck.sourceforge.net/) ), which is REALLY useful.  But I have some problems.  There are a few programs I want to uninstall (such as 'gnome-btdownload'), but when I try to the package 'ubuntu-desktop' wants to be removed with it.  Is there ANY way I can remove those programs with out removing the desktop?  Is there anyway I can edit the ubuntu package so that it doesn't notice that I removed the packages it *says* it depends on?  Is there ANYTHING I can do at all?

Also, does anyone know of any good HOWTOs on gconf-editor?  I need to figure out how to do some things.  Such as add an object to the top panel through it.

---

### Post by theyain on 2007-11-29
Hello?  Bump

---

### Post by aysiu on 2007-11-29
*ubuntu-desktop* is safe to remove. It is, by definition, an empty package that depends on other packages. So when you remove one of those packages, you remove the empty package as well.

---

### Post by theyain on 2007-11-29
Then how come when I removed it last time GNOME disappeared?  As in when I tried to log back in, GNOME was gone.  Not uninstalled, it just wouldn't start up.

---

### Post by az on 2007-11-29
You probably removed something else while doing it.

If you want to make a custom distro, you can start by making a metapackage.  You can take the ubuntu-desktop package source and change the dependencies to what you like.

It probably would be easier for you to play around with that way.  You install a base system and then add your metapackage.

---

### Post by aysiu on 2007-11-29
> **theyain said:**
> Then how come when I removed it last time GNOME disappeared?  As in when I tried to log back in, GNOME was gone.  Not uninstalled, it just wouldn't start up.
That's a freakish occurrence. Believe me. I've used Ubuntu for two and a half years and have seen literally tens of thousands of support posts in these forums. I have never heard of removing *ubuntu-desktop* removing Gnome completely. This is the first time.

---

### Post by theyain on 2007-11-29
> **az said:**
> You probably removed something else while doing it.

If you want to make a custom distro, you can start by making a metapackage.  You can take the ubuntu-desktop package source and change the dependencies to what you like.

It probably would be easier for you to play around with that way.  You install a base system and then add your metapackage.

Ah, but how do I edit the dependencies?   Thats something I don't know how to do.




> **aysiu said:**
> That's a freakish occurrence. Believe me. I've used Ubuntu for two and a half years and have seen literally tens of thousands of support posts in these forums. I have never heard of removing *ubuntu-desktop* removing Gnome completely. This is the first time.

Wait, really?  Holy crap.  o.o


So basically I can remove it and in doing so all I am doing is removing a list of things it says it depends on?  Well, I can see how that would be useful.  It would definitely help prevent a new user from removing a package that the system actually needs to run.


Oh, and still nothing on a HOWTO for gconf-editor?

---

### Post by atlfalcons866 on 2007-11-29
if he used sudo aptitude it might of removed everything ubuntu-desktop relies on.

---

### Post by aysiu on 2007-11-30
> **theyain said:**
> 
So basically I can remove it and in doing so all I am doing is removing a list of things it says it depends on? Actually, not even.

All you're removing is the empty package itself and none of its dependencies.

Removing one of its dependencies will remove the empty package.

But removing the empty package will not (or should not, anyway) remove its dependencies.

---

