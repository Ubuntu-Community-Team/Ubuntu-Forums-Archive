---
title: "Problem with dependencies not being met..."
date: 2009-06-23
forum: General Help
---

### Post by clmbngbkng on 2009-06-23
So I'm trying to install a Zarafa Exchange server on Ubuntu and it needs libical0 0.23-6 but in turn it seemed to have broken a few other programs that were already installed but I don't use. Currently Ubuntu won't let me install anything with apt-get from the command line and all it returns is this.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  evolution: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  evolution-data-server: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  evolution-exchange: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  evolution-plugins: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  evolution-webcal: Depends: libical0 (>= 0.30) but 0.23-6 is to be installed
  gnome-panel: Depends: libical0 (>= 0.30) but 0.23-6 is to be installed
  kdepimlibs5: Depends: libical0 (>= 0.30) but 0.23-6 is to be installed
  libecal1.2-7: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  libedata-cal1.2-6: Depends: libical0 (>= 0.42) but 0.23-6 is to be installed
  python-gnome2-desktop: Depends: libical0 (>= 0.31) but 0.23-6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I don't use Evolution so having that removed wouldn't be bad but there are things like gnome-panel that I'm pretty sure should stay on the system but have a feeling the panel is only tied into a widget for Evolution's calendar. When I try apt-get -f install it tells me it will remove Zarafa which I don't want.

Whats the best way to go around fixing this? Can I tell it to ignore the dependencies for those programs since I know I won't be using them?

---

### Post by clmbngbkng on 2009-06-23
Bump!

---

### Post by dE_logics on 2009-06-23
Try adding the Jaunty main repository, that should resolve the issue.

---

### Post by clmbngbkng on 2009-06-23
I have the main Jaunty repos enabled and yes that could solve the problem with dependencies but I'm looking for more of a way to disable that error message for the libical0 being an old version and if I run into any problems with it in the future then I will undo it, whatever it may be.

I need that old libical0 for Zarafa which is the only thing I need out of all the programs that are tied up in problem.

---

### Post by Therion on 2009-06-23
Open a Terminal and type in:

```
apt-get -f install
```

---

### Post by clmbngbkng on 2009-06-23
Done it and then apt-get wants to remove Zarafa over other programs since it isn't from the Ubuntu repos. :(

---

### Post by clmbngbkng on 2009-06-23
No way to do this? There has to be a way!

---

### Post by clmbngbkng on 2009-06-24
Anyone able to help with this?

---

### Post by elias832 on 2009-07-07
Im having the same problem.... 
I read somewhere that you have to put those two old packages on "hold" so they wont get update/removed, but it didnt work for me.

---

