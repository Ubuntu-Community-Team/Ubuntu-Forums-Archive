---
title: "Struggle with maverick and e17 tclock"
date: 2010-10-13
forum: Desktop Environments
---

### Post by Lord_JABA on 2010-10-13
I'm really into speed. So i decided that instead of "dist upgrade" i will install clean 10.10 maverick ubuntu-minimal and e17 from official ubuntu repo.
I got it working with slim login manager and it works great BUT...
I'm used to digital clock and tried to install tclock from svn 
```
cd e/trunk/E-MODULES-EXTRA/tclock
./autogen.sh
make
```and i got this:

```

(...)
/usr/include/enlightenment/e_gadcon.h:292: note: expected ‘int’ but argument is of type ‘struct E_Menu *’
e_mod_main.c:190: error: too many arguments to function ‘e_gadcon_client_util_menu_items_append’
make[2]: *** [e_mod_main.lo] Error 1
make[2]: Leaving directory `(...)/e/trunk/E-MODULES-EXTRA/tclock/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `(...)/e/trunk/E-MODULES-EXTRA/tclock'
make: *** [all] Error 2

```I think is because I don't have rest of e17 from svn. I'm right??
I'm lazy person and really want to stick to repo version.
Is there any other way to install tclock module?
Or I'm just doing something wrong with svn?

---

### Post by VCoolio on 2010-10-13
It looks more like a broken revision; try to get the one from which your packages were built; I'm guessing that's revision 49898 (or 51480, which is the alpha release, or 52995, which is the beta release). So, first
```
svn checkout -r 49898 http://svn.enlightenment.org/svn/e/trunk/E-MODULES-EXTRA/tclock
``` then try again. But if you're installing from a repo it should have a package for it like e17-modules or whatever. Check that first. It's always a bad idea to mix packages from a repo with compiled packages. If it doesn't work, compile all of the e17 stuff; you'll be more up-to-date and it's supported in irc /freenode #e or the e-users mailing list.

---

### Post by Lord_JABA on 2010-10-14
Thanks! I give it a try tomorrow. Problem with Ubuntu is it has only one package called e17 (and another e17-dev) no separate modules or anything. Hope that cannonical will work on the repo.

---

### Post by kerry_s on 2010-10-14
Lord_JABA, how is the e17 running? is most of the features there?

i saw it in the repo, but didn't want to deal with a half a$$ wm, when i tried it in the past there was always things missing that were needed or stuff just didn't work at all. thinking about trying it, but i like to hear your thoughts on it's current state.

can you post a pic of what the repo version looks like?

thanks

never mind, tried it, hated it, removed it.

---

### Post by Lord_JABA on 2010-10-16
E17 is running and is doing it fast. Most features work correct but there are some bugs.
One of them is the e17 crushes when I try to resize shelf's in some themes. I just revert to default theme resize what I want and go back to my theme. There is a bug in wallpaper preview but it's nearly unnoticeable. (sometimes is shows only a part of image)
I got automount working. (You only need dbus and hal installed)
Animated icons are great. For ex. home directory icon puff's smoke from chimney, firefox globe its turning around... . I must figure out how to make my own animated icons cause the are only a few of them on the net. 
Attaching some screenshot's.
PS. [VCoolio]("http://ubuntuforums.org/member.php?u=769402") as you see your method to get tclock worked. 
[kerry_s]("http://ubuntuforums.org/member.php?u=132335") i assume your gnome woks smooth, but i hawe "strange" nvidia Quadro FX Go1400 (this card is in only one model of laptop as far as I know) and it's not well supported so gnome-compiz was very unresponsive. Also I heard e17 is not working well aside with gnome- maybe this was your issue.

---

