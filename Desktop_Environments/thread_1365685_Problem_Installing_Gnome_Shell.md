---
title: "Problem Installing Gnome Shell"
date: 2009-12-27
forum: Desktop Environments
---

### Post by FatalChaos on 2009-12-27
I'm trying to build the latest version of gnome shell in karmic koala, and everything works fine until I try jhbuild build. Here's the error I end up getting: 

make[2]: *** No rule to make target `Pango-1.0.gir', needed by `Gdk-2.0.gir'.  Stop.
make[2]: Leaving directory `/home/william/gnome-shell/source/gir-repository/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/william/gnome-shell/source/gir-repository'
make: *** [all] Error 2
*** error during stage build of gir-repository: ########## Error running make   *** [2/7]

Any ideas?

---

### Post by bruno9779 on 2009-12-27
same here

---

### Post by dr88dr88 on 2009-12-28
I have the same problem i have not yet found a solution.

---

### Post by bruno9779 on 2009-12-28
I haven't found a solution, but a workaround: install it from repos

```
sudo apt-get install gnome-shell
```

then run with:

```
gnome-shell --replace
```

to go back to your gnome desktop type in the Alt+F2 prompt:

```
debugexit
```

Check this out for some more tricks and shortcuts:

[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

It works perfectly for me and looks real good.

---

### Post by bruno9779 on 2009-12-28
Here goes what it looks like on my box:

[IMG][[img]http://www.ubuntu-pics.de/thumb/35765/screenshot_002_cSawU1.png[/img]](http://www.ubuntu-pics.de/bild/35765/screenshot_002_cSawU1.png)[/IMG]

---

### Post by BobCFC on 2009-12-30
Unfortunately I can tell from the screenshot that the repos are quite old.

As I write this the builds from Git are working again:)

It's not hard once you get used to it - I build gnome-shell most mornings when I log in.


EDIT: sometimes it helps to delete the gnome-shell directory and start a clean build, but you will loose your working desktop if it doesn't work so maybe just rename the directory.

---

### Post by bruno9779 on 2009-12-30
so, jbuild and automake 1.8 are deprecated since jaunty and hardy, I have only some old debs for that
is this really the way to go? a dependency hell for a tech demo?
gnome-shell devs, maybe should put up a ppa or something with the dependencies needed by their code...

---

### Post by sathyz on 2009-12-30
same here. Any Solution ??

---

### Post by ijefferies@fastmail.net on 2009-12-31
Same problem also using script but all works fine from repo.

---

### Post by FatalChaos on 2009-12-31
I just tried building it on lucid lynx (figured I'd give lucid lynx a try since I've been having bad luck w/ karmic and my experience w/ testing karmic koala was pretty good), but it still gives me the same error. Could someone who has managed to successfuly build gnome-shell (recently) post a guide?

---

### Post by BobCFC on 2010-01-05
I just tried on a fresh install and got stuck again it looks like I had some files left over from a previously successful build.

I got it working by copying these Pango files over from my other partition, SORRY 64bit ONLY I think:

Put the two **.gir** files in **gnome-shell/install/share/gir-1.0**


Put the two **.typelib** files in **gnome-shell/install/lib64/girepository-1.0**


Finally make a second copy of **Pango-1.0.gir** and put it in a different folder: **gnome-shell/source/gir-repository/gir**

---

### Post by MikeCamel on 2010-01-05
I've managed to build on a machine which I'd previously had working, though I needed to remove the gnome-shell directory, .jhbuildrc and start from scratch.

However, on a clean karmic 32bit machine, it won't build.  I don't seem to have anything called Pango*.gir at all in my gnome-shell tree.

Any suggestions?

-Mike.

---

### Post by MikeCamel on 2010-01-06
> **MikeCamel said:**
> I've managed to build on a machine which I'd previously had working, though I needed to remove the gnome-shell directory, .jhbuildrc and start from scratch.

However, on a clean karmic 32bit machine, it won't build.  I don't seem to have anything called Pango*.gir at all in my gnome-shell tree.



Oh, and though it builds, it won't run, so that's no good.

---

### Post by kamembe on 2010-01-11
For those wanting to build it themselves, there's been a bug raised for gnome-shell. You can find it here:

[https://bugzilla.gnome.org/show_bug.cgi?id=605724](https://bugzilla.gnome.org/show_bug.cgi?id=605724)

The same thing happens on Fedora 12, which I use. Looking forward to it's being fixed, and being able to see the latest gnome-shell again. Loving it so far.

---

