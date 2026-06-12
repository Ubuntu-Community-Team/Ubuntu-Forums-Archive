---
title: "installing as root??"
date: 2004-12-11
forum: Desktop Environments
---

### Post by Lighthouse on 2004-12-11
I'm a ubuntu newbie, with some limited experience using linux. This is the first time I've installed a linux os on a fresh machine and i'm confused about getting it the way I want it.

I understand that when I log in to my ubuntu desktop, I am a regular user w/o root privs, but what exactly does that mean to me? Here's why I'm asking: I noticed that my Firefox needs the Flash plugin. I was able to d/l but can't open it as I'm accustomed to. I assume this is b/c I'm not running as "root". (I did notice that I can install FF Extensions w/ no problem.)

I looked through the docs and saw somethign about "Synaptic" something or other under the heading "installing new s/w", but that appears to be only for core linux stuff. I didn't see any way to add new s/w there that isn't on the list. I don't think I should have to log into a term window as root to install s/w and I'm guessing that I don't have to, but I really don't know how to do even begin installing anything.

I'm asking specifically about installing a plugin now, but I'm sure that there will be other s/w in the future that I would want to install as well. Thanks.

Lighthouse

PS: Curiously, I noticed when I went tothe FF site that "Plugins" weren't displayed as they are when I go there on my windows box. They also don't show up in my TOOLS menu on FF. Does FF for linux handle this differently? I only found the right plugins page by doing a search on the mozilla site.

---

### Post by Rancoras on 2004-12-11
As a self-professed "newbie", you really need to check this page out.  It's a great resource that will cover many questions that you may have while exploring the world that is linux.

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Lighthouse on 2004-12-12
[QUOTE=Rancoras]As a self-professed "newbie", you really need to check this page out.  It's a great resource that will cover many questions that you may have while exploring the world that is linux.

[http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE]

Thanks. I didn't know about that guide. I can follow that, but it really seems like there should be a better way. ](*,)

---

### Post by Lighthouse on 2004-12-12
[QUOTE=Rancoras]As a self-professed "newbie", you really need to check this page out.  It's a great resource that will cover many questions that you may have while exploring the world that is linux.

[http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE]

Ok, i went there and read the 2 pertinent links. However, when I went to do this:
 "[COLOR=Blue]$ sudo gedit /etc/apt/sources.list[/COLOR]" I noticed that the changes I was supposed to make to install Flash were already done, but I still have no Flash plugin working. Where do I turn now?

---

### Post by adbak on 2004-12-12
Is your problem that Synaptic/apt-get tells you that it can't find the package you're looking for?  If so, open Synaptic, click Settings, then Repositories, and then check the currently unchecked boxes that say something about Universe (they should be the fourth and fifth boxes).  Click OK then on the main page for Synaptic click Reload, which is in the upper right corner.  Now click Search and look for flashplayer-mozilla.  you should find a package now.

---

