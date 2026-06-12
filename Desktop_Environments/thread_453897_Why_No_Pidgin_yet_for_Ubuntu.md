---
title: "Why No Pidgin yet for Ubuntu?"
date: 2007-05-24
forum: Desktop Environments
---

### Post by jimbo99 on 2007-05-24
There are many many developers and yet there is no update to the beta of gaim to give us Pidgin?  Shouldn't this be in the repositories by now?

---

### Post by orb9220 on 2007-05-24
Due to the process. A package may take 2-6 weeks to be made availiable in the repo's.
Since Pidgin has only been out a week it will be awhile.

And do you really have a need for Pidgin? There is really no difference than 2.0.0b7 that is in feisty repo's.

---

### Post by house7 on 2007-05-25
> **orb9220 said:**
> 

And do you really have a need for Pidgin? There is really no difference than 2.0.0b7 that is in feisty repo's.

Yeah, i agree with you.. but i think it's fine to change tho. :)

---

### Post by DUNC4N on 2007-05-25
[Check this out]("http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html")

---

### Post by Clay_Banger on 2007-05-25
> **DUNC4N said:**
> [Check this out]("http://http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html")
I think the link you meant is [this.]("http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html")

---

### Post by loathsome on 2007-05-25
Plus, Pidgin is *very* easy to compile yourself ;)

---

### Post by DUNC4N on 2007-05-25
> **Clay_Banger said:**
> I think the link you meant is [this.]("http://www.ubuntugeek.com/howto-install-pidgin-200-on-ubuntu-feisty-with-plugin-pack.html")

Whoops, thanks.:(

---

### Post by Ventrue on 2007-05-25
> **loathsome said:**
> Plus, Pidgin is *very* easy to compile yourself ;)

Agree! :)

**[COLOR="Red"][Click :)]("http://applications.linux.com/article.pl?sid=07/05/08/1853217&tid=13&tid=37")[/COLOR]**

---

### Post by Aryra on 2007-05-25
> **Ventrue said:**
> Agree! :)

**[COLOR="Red"][Click :)]("http://applications.linux.com/article.pl?sid=07/05/08/1853217&tid=13&tid=37")[/COLOR]**

It never works for me :'(

:P

---

### Post by marcozs on 2007-05-25
Well you can get a deb for Feisty here:
[http://www.getdeb.net/release.php?id=817](http://www.getdeb.net/release.php?id=817)

guifications:
[http://www.getdeb.net/app.php?name=Pidgin%20Guifications](http://www.getdeb.net/app.php?name=Pidgin%20Guifications)
libnotify:
[http://www.getdeb.net/release.php?id=843](http://www.getdeb.net/release.php?id=843)

Enjoy!

---

### Post by marcozs on 2007-05-25
By the way: I agree it should be in the official (or backports) repos...

---

### Post by jimbo99 on 2007-05-25
> **marcozs said:**
> Well you can get a deb for Feisty here:
[http://www.getdeb.net/release.php?id=817](http://www.getdeb.net/release.php?id=817)

guifications:
[http://www.getdeb.net/app.php?name=Pidgin%20Guifications](http://www.getdeb.net/app.php?name=Pidgin%20Guifications)
libnotify:
[http://www.getdeb.net/release.php?id=843](http://www.getdeb.net/release.php?id=843)

Enjoy!

Your's is the best answer so far.  

I have done a lot of file transfers with my sister in MN.  With the beta versions of Gaim I had Gaim crash right and left.  That's why I want to get off of the beta.  My exp with the official 2.0 is that the crashes no longer happen.  When I say it crashed right and left I mean it crashes like crazy, especially when transferring to say the yahoo windows client.  Can't have crashes.  They are an absolute NO NO.

I have tried to compile the program only to find that it didn't actually replace the older version when I ran the make install.  Also I found that a lot of the plugins were missing.  There are a couple important ones I wanted that were missing so compiling was out of the question.  Also, the message about which features where to be compiled into it showed mostly "NO" for whether those features would be there.  There was little to no information about what those features were nor how they would affect the overall long term use of the program.  This is very similar to how you would compile amarok where at the end of the ./configure it tells you what features will be implemented.  With Amarok you can figure out what those missing components are and install them then reconfigure, but with pidgin it is much more difficult and there are far more missing.

Somehow when they put feisty together they tied gaim to the desktop environment so when you attempt to remove it to install a new one you get messages about it wanting to uninstall certain aspects of the desktop environment.  Not a good thing.  They need to make a correction so that an instant messenger is only a feature of the overall and not dependent, so that we can remove it totally if we choose.

I did find some .deb files for another linux for pidgin but I have hesitated to install it only because I have no idea what I would loose (as it relates to what I might loose if I choose to compile pidgin myself).

---

### Post by Ventrue on 2007-05-26
You can download from here too: [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/)

---

### Post by Sonix3D on 2007-05-27
Another: [http://www.getdeb.net/release.php?id=955](http://www.getdeb.net/release.php?id=955)

---

### Post by marcozs on 2007-05-27
> **jimbo99 said:**
> Your's is the best answer so far.  
Somehow when they put feisty together they tied gaim to the desktop environment so when you attempt to remove it to install a new one you get messages about it wanting to uninstall certain aspects of the desktop

True, I think it asks you to remove "ubuntu desktop" and "nautilus send-to": the first one is a dummy package linked to the whole basic install of ubuntu, so nothing to worry about removing it, while the nautilus send-to could be usefull to have: I don't use it so I didn't hesitate in removing both... I believe the best would be to have an updated backport repo with all the latest packages. I find myself adding repos from different people compiling debs to have the latest programs installed... I think ubuntu would have a great boost from a well managed backport repo.

---

### Post by marcozs on 2007-05-27
> **Sonix3D said:**
> Another: [http://www.getdeb.net/release.php?id=955](http://www.getdeb.net/release.php?id=955)

Nice... the 2.0.1 is out then! Pidgin is gonna become my favorite IM soon... only thing I miss is the webcam/voice support... when is the old "gaim-vv" be developed and included? Gnome needs these funcionalities cause otherwise KDE is going to win the match with its Kopete. aMsn supports the webcam but it is still too buggy and Skype is not an open protocol (and also it doesnt support webcam on linux yet...).

---

