---
title: "Enabling Desktop Icons"
date: 2008-12-13
forum: General Help
---

### Post by gobstopper on 2008-12-13
I am an occasional Ubuntu user (not an absolute noob, but by no means an expert!) running 8.04 with the Gnome desktop environment on an old PC which I use to tinker with, and I remember coming across an article in a magazine some time ago where someone wrote in asking if it was possible to have desktop icons appear along the same lines as that *other* operating system.

Thinking it was useful tip I kept and then promptly lost the article in question. A quick google search pointed me in the direction of gconf-editor (which I remember being mentioned in said article), so I ran this from a terminal command (using sudo) and navigated to the apps -> nautilis -> desktop section where, sure enough, I found a series of options which I could enable to display the Computer, Home, Network and Trash can icons on the desktop. According to the on-line article ([here](http://linux.about.com/od/ubuntu_doc/a/ubudg10t16.htm)) these changes should take effect immediately. However, I am not seeing the promised results, even after a re-boot.

Can anyone please advise where am I going wrong?

Many Thanks.

---

### Post by blakjesus on 2008-12-13
I'm not sure what you got wrong, but an easy way to accomplish what you want to do is to install ubuntu-tweak.

[You can get it here.]("http://ubuntu-tweak.com/downloads")

---

### Post by gobstopper on 2008-12-13
Thanks for that. I'll give it a try.

---

### Post by gobstopper on 2008-12-13
Well, the .deb package installed easily enough and after a fruitless search for a link in the various application group menus, I found that 'sudo ubuntu-tweak' did the job nicely of launching the application.

However, visiting the desktop settings I found all the options which I had enabled using gconf-editor where still enabled. But, alas, even after a couple of further re-boots, the icons in question are still not appearing.

*scratches head* and goes away to have a think...

Thanks for the pointer anyway, because it looks like a useful app.

---

### Post by sigurnjak on 2008-12-13
Maybe you can try going into applications -system tools and opening ubuntu tweak as a user instead of root . My opinion is that you applied changes in root desktop . On my pc i run u-tweak as a user.

---

