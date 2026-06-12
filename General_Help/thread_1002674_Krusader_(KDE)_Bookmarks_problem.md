---
title: "Krusader (KDE) Bookmarks problem"
date: 2008-12-05
forum: General Help
---

### Post by dootzky on 2008-12-05
Hi guys,

   this is my problem: I install clean Ubuntu (8.10), and everything is working fine, yey. Now, I install Krusader (which is a KDE app, Qt4, right?). Everything works fine there also. Weee.

But - when I want to bookmark some folders in Krusader, I can "add" new bookmarks, but I can never again EDIT them. Why is this? 

Same thing happens with KDESVN. I can add new bookmarks, but I can't open the "edit bookmarks" dialog. 

I found a solution before, which would be: I install complete KDE desktop enviroment (sudo apt-get install kubuntu-desktop), and then after a reboot editing bookmarks works.

But I don't want to install complete KDE enviroment on every computer in my office, I just need to know which packages are necessary in order for "editing boomarks" to work for KDE apps.

Thanks for your time and help!
dootzky

---

### Post by dootzky on 2008-12-08
nobody?

---

### Post by dootzky on 2008-12-18
sadly, no one could help me, so after days spent searching for an answer, I've found it:

in order to get "Manage Bookmarks" to work in Krusader, and you're using Gnome, you need to install **Konqueror**.

you can do it from Synaptic, or from terminal:

```

sudo apt-get install konqueror

```

also, if you want Samba to work with your Krusader, you need more KDE depentencies, like kdebase-kio-plugins. Install them trough Synaptic or terminal, again:

```

sudo apt-get install kdebase-kio-plugins

```

I hope this helps someone else also.
Here, I'll put some relevant tags in this solution, so more people can find this post trough google or forum search:

krusader, krusader bookmark problem, krusader manage bookmark problem, krusader bookmarks not working, krusader edit bookmarks, krusader gnome problem, krusader missing dependency

cheers.
dootzky
[http://www.duneprog.com](http://www.duneprog.com)

---

### Post by zorbey on 2009-04-06
I had the exact problems with Krusader and Kdesvn.
Thanks in advance.
--
ZORBeY^

---

### Post by sola on 2009-06-15
I had the exact same problem.

Thanks for the solution !!!

I only installed konquerror and now bookmarking works.

---

### Post by dootzky on 2009-06-22
hey - I'm really happy that my post helped you guys out! :)

long live the community! :popcorn:

---

