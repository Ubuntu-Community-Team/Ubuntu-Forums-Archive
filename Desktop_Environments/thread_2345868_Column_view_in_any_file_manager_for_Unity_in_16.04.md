---
title: "Column view in any file manager for Unity in 16.04 LTS?"
date: 2016-12-08
forum: Desktop Environments
---

### Post by ardi2 on 2016-12-08
Hi,

I come from the Mac, and the column view in the file manager is a feature I miss a lot in Ubuntu. Doing a search I found that people suggest to use either Marlin or Pantheon Files. However, it seems it's not possible to install Marlin on 16.04 (see [here]("http://askubuntu.com/questions/797574/how-can-get-mac-os-like-column-view-in-ubuntu-16-04")) because it looks like abandonware, and Pantheon Files is designed for Elementary rather than Ubuntu, and people say it has problems because it's not for Ubuntu (see [here]("http://askubuntu.com/questions/766673/pantheon-on-ubuntu-16-04")).

So, my question is: Do you know of any file manager that supports column view and which is 100% compatible with Ubuntu 16.04 LTS?

Thanks a lot!

---

### Post by vasa1 on 2016-12-08
> **ardi2 said:**
> ... and Pantheon Files is designed for Elementary rather than Ubuntu, and people say it has problems because it's not for Ubuntu (see [here]("http://askubuntu.com/questions/766673/pantheon-on-ubuntu-16-04")).
...
Looks like that's just one person's opinion. Why don't you install the ppa and see how Pantheon Files works for *you*? See [http://askubuntu.com/questions/798899/is-there-a-file-manager-with-mac-os-like-column-view-for-linux](http://askubuntu.com/questions/798899/is-there-a-file-manager-with-mac-os-like-column-view-for-linux) for more.

---

### Post by ardi2 on 2016-12-10
> **vasa1 said:**
> Looks like that's just one person's opinion. Why don't you install the ppa and see how Pantheon Files works for *you*? See [http://askubuntu.com/questions/798899/is-there-a-file-manager-with-mac-os-like-column-view-for-linux](http://askubuntu.com/questions/798899/is-there-a-file-manager-with-mac-os-like-column-view-for-linux) for more.
Thanks a lot. There's one difference, the link I posted seems to be related to installing the whole Elementary desktop, while your link is just about Pantheon Files, which is what I wished. Following it I was able to install it, but, however, it's definitely not designed with Unity in mind: the sizing of the UI is not correct (some buttons are huge, others tiny), and a rotating wheel showing busy status seems to never disappear when you switch to column mode.

Is there any place where I could vote for this feature being added to the Unity file manager? Column browsing was my favorite and most useful mode on the Mac :(

---

### Post by vasa1 on 2016-12-11
> **ardi2 said:**
> ..., it's definitely not designed with Unity in mind...
Is there any place where I could vote for this feature being added to the Unity file manager? Column browsing was my favorite and most useful mode on the Mac :(
The "Unity file manager", as I understand it, is sourced from the GNOME project and then modified a bit to mesh with Unity. In other words, features (even though they may be old in other file managers or operating systems), probably aren't added at the Unity stage but upstream by the GNOME developers. For that, you'll need to look at the GNOME project for pointers on how to request a feature: [https://wiki.gnome.org/Apps/Nautilus](https://wiki.gnome.org/Apps/Nautilus)

BTW, [https://ubuntuforums.org/showthread.php?t=1429929](https://ubuntuforums.org/showthread.php?t=1429929)

---

### Post by coffeecat on 2016-12-11
There is a (list) column view in the default file manager in Ubuntu 16.04, but it lacks decent functionality in my view. If list view is what you mean by column view - apologies if you are referring to something else. Indeed, the modified-from-Gnome file manager in Ubuntu seems to get worse and worse with each iteration - in my view - and is even worse in 16.10. **In my view**. :) Ahem - thanks, gnome project - cough. </s>

What I do now is to install caja file browser from the Mate project. It works just fine in the Unity desktop, it's in the repository, and it has the sort of functionality (and good looks) that gnome abandoned long ago.

---

### Post by vasa1 on 2016-12-11
> **coffeecat said:**
> There is a (list) column view in the default file manager in Ubuntu 16.04, but it lacks decent functionality in my view. If list view is what you mean by column view - apologies if you are referring to something else. ...
I think OP wants "Miller columns": [https://en.wikipedia.org/wiki/Miller_columns](https://en.wikipedia.org/wiki/Miller_columns)

---

### Post by tkroo on 2017-03-30
> **vasa1 said:**
> I think OP wants "Miller columns": [https://en.wikipedia.org/wiki/Miller_columns](https://en.wikipedia.org/wiki/Miller_columns)
Miller columns are available in Nemo and Caja.
There is a ppa which allows Nemo to be used with Unity:[ http://www.webupd8.org/2016/11/nemo-320-with-unity-patches-and-without.html]("http://www.webupd8.org/2016/11/nemo-320-with-unity-patches-and-without.html")

---

