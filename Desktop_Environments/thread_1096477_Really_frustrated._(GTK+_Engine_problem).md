---
title: "Really frustrated. (GTK+ Engine problem)"
date: 2009-03-14
forum: Desktop Environments
---

### Post by picapacapopo on 2009-03-14
Ok, so I've been using Ubuntu for quite a while now, and I must say, I love every aspect of it. I recently found out that you can theme it. I have downloaded many themes from Gnome-Looks, and when I try to install it, I have a little message telling me that the theme will not look as intended because the required GTK+ engine is not installed. And it's completely right. The themes are messed up. I have gone to Synaptics and tried to install the GTK+ Engines. Still doesn't work. I've tried a whole bunch of things, yet I still get the error, and my theme still doesn't install correctly. 




Anyone know what to do? Any help at all is greatly appreciated.


Thanks in advance,
Alex

---

### Post by hansdown on 2009-03-15
Hi picapacapopo.

What version of ubuntu are you running?

---

### Post by kerry_s on 2009-03-15
you probably installed the wrong 1's. there's plain gtk which is version 1, not really used any more. the 1's you want are gtk2 which is what is currently used.

in terminal run:
**sudo apt-get install gtk2-engines-***

that should install all the theme engines.

---

### Post by picapacapopo on 2009-03-15
Hi, I'm running 8.10.





The command Kerry_s gave me, I've already used it. I still have the error message, and theme that I want still won't install correctly. It happens with all the themes that I've downloaded from Gnome-Look.org. Maybe I'm not installing them right? It seems like every theme has multiple download links, and multiple folders in each link. I thought I was doing it right, but I'm not 100% sure. Also, in the description of the themes, I see some comments saying it takes the Aurora engine, or whatever. Then they give a download link to it. The problem is, I don't know what to do to install it. I am so used to um...a different operating system (lol) where stuff might just be easier to install than this one. Don't get me wrong though, this operating system is by far my favorite, because its stable as heck, and runs fast as um..crazy? LOL. Anyways, anyone have any help I could use?



Thanks a bunch!

-Alex

---

### Post by hansdown on 2009-03-15
Which theme is giving this message?

---

### Post by Andreas1 on 2009-03-15
i take it you want the aurora engine, despite being quite popular it is not available in the ubuntu repositories (via synaptic), which means you would have to download the [source]("http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438") and compile it yourself. however, there seems to be a [precompiled]("http://www.gnome-look.org/content/show.php/Aurora+Gtk2+Engine+DEB?content=96421") version for ubuntu 8.10. basically this would be the same as something you install from the repositories if you find it trustworthy.

---

### Post by blackened on 2009-03-15
It's all going to come down to what engines you're trying to use, and what the availablility of those engines are. Some will be available in the repos, some you'll have to install from deb packages.

Aurora is under fairly heavy development and is not available in the repositories, so you cannot use apt-get to install it. I've attached a deb that will work in 8.10.

Edit: Oops, use Andreas's version, it's more up to date. Nice find Andreas.

---

