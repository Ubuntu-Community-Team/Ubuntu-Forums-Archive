---
title: "Gnome Shell"
date: 2010-11-17
forum: Desktop Environments
---

### Post by TNT1 on 2010-11-17
Hi, I followed this: [http://www.linux.com/community/blogs/how-to-install-and-use-gnome-shell-gnome3-on-ubuntu-1004.html](http://www.linux.com/community/blogs/how-to-install-and-use-gnome-shell-gnome3-on-ubuntu-1004.html)
and I can't get gnome shell working, in fact I see nothing. Can someone point me in the right direction?

And now when I try to enable compiz, I get told mutter is running, and I can't. Which is easy to fix with metacity --replace, but if mutter runs, then why don't I see the shell?

---

### Post by TNT1 on 2010-11-17
Anyone got an idea? A how to guide? Some suggestion?

---

### Post by Harry33 on 2010-11-17
> **TNT1 said:**
> Anyone got an idea? A how to guide? Some suggestion?

What is your distro?
Is it ubuntu?
Is it Lucid (10.04), Maverick (10.10) or Natty (11.04)?

Do you have only default sources.list?
Or do you have additional PPA's there?

The site you refer to gives instructions to Ubuntu Lucid.
The official repos in Lucid do not have a working Gnome-Shell, it is very old and crippled.
At the moment only Maverick's official repo's work (gnome-shell_2.31.5).
Natty is out of order regarding Gnome-Shell right now, only additional PPA's work.

---

### Post by TNT1 on 2010-11-17
10.04.1

[IMG]http://img819.imageshack.us/img819/608/screenshotlis.png[/IMG]

---

### Post by CurryNoodles on 2010-11-17
In what circumstances that you assume your gnome shell is not working?

Better if there is a print screen of your error, i guess..

---

### Post by Harry33 on 2010-11-17
Hi TNT1

OK you have lucid.
Me, I dont believe that lucid's official repos offer any usable Gnome-Shell.
And, there are no PPA's in working condition that would offer GS for lucid.

You may find this:
[https://launchpad.net/~tualatrix/+archive/gnome-shell](https://launchpad.net/~tualatrix/+archive/gnome-shell)
But it has a problem with wrong clutter version.

Anyway, it is an old version of GS.

If GS is what you want, try Maverick's 2.31.5.
It just works.

---

### Post by Harry33 on 2010-11-17
Oh yes, and one more thing.

In case there are other issues in your system.
Print here the error messages you get after a reboot and opening terminal
and entering
gnome-shell --replace

---

### Post by TNT1 on 2010-11-17
I don't get any errors, but I also don't get that side menu and top menu thingy that you are supposed to get with gnome shell. that's what I want.

---

### Post by TNT1 on 2010-11-18
Come on, guys, someone help me get the side and top menu/launcher things working. Please?

---

